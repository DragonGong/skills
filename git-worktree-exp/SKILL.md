---
name: git-worktree-experiment-isolation
description: Use this skill when running local or remote experiments that need isolated code changes, branch management, shared datasets/caches, and cleanup through git worktree.
---

# Git Worktree 实验隔离 Skill

## 适用场景

当用户要做实验、改模型、调参数、开新分支、远程跑实验、本地跑实验、复现实验结果时，优先使用这个流程。

目标是：

1. 用 `git worktree` 隔离代码实验环境。
2. 不复制大数据、cache、embedding、模型权重等重文件。
3. 实验数据、cache、outputs 默认仍然生成到原项目目录。
4. 实验报告写回原分支所在的原项目目录。
5. 实验完成后删除新建的 worktree，避免目录堆积。

---

## 核心原则

### 1. 原项目目录负责数据和产物

原项目目录是数据根目录，也是实验产物根目录。

例如：

```text
ORIG_DIR=/data/xxx/project
```

所有这类内容都应该放在原项目目录下：

```text
$ORIG_DIR/data/
$ORIG_DIR/cache/
$ORIG_DIR/outputs/
$ORIG_DIR/logs/
$ORIG_DIR/docs/
```

不要把这些大文件复制到 worktree 里。

### 2. worktree 只负责隔离代码

worktree 只用来隔离代码改动，例如：

```text
/data/xxx/project-worktrees/exp-xxx
```

worktree 里面可以修改代码、跑训练脚本、跑评估脚本，但数据路径和输出路径要显式指向原项目目录。

### 3. 实验报告必须写回原项目目录

实验报告不要留在临时 worktree 里。默认写到：

```text
$ORIG_DIR/docs/experiments/YYYY-MM-DD-exp_name.md
```

如果项目已有约定目录，就按项目约定写，例如：

```text
$ORIG_DIR/docs/
$ORIG_DIR/reports/
$ORIG_DIR/outputs/exp_name/report.md
```

### 4. 实验完成后删除 worktree

实验结束后，必须清理新建的 worktree：

```bash
git worktree remove "$WT_DIR"
git worktree prune
```

如果 worktree 中有未提交代码、未迁移产物或失败日志，先处理，再删除。

分支是否删除要看用户需求。默认保留实验分支，方便以后追溯代码；只删除临时 worktree 目录。

---

## 标准流程

### 第一步：确认原项目目录

先在原项目目录执行：

```bash
pwd
git rev-parse --show-toplevel
git branch --show-current
git status --short
```

记录：

```text
ORIG_DIR=<原项目根目录>
BASE_BRANCH=<当前分支>
```

如果原目录已有未提交改动，不要乱动。只记录状态，并说明：原目录只用于数据、产物和报告，不在原目录改实验代码。

---

### 第二步：创建实验分支和 worktree

推荐命名：

```text
BRANCH=exp/<实验主题>
WT_DIR=<原目录同级或指定worktrees目录>/<实验主题>
```

本地例子：

```bash
ORIG_DIR="/mnt/d/workspace/code/project"
WT_PARENT="/mnt/d/workspace/code/project-worktrees"
EXP_NAME="dense-int-pair-ablation"
BRANCH="exp/${EXP_NAME}"
WT_DIR="${WT_PARENT}/${EXP_NAME}"

mkdir -p "$WT_PARENT"
cd "$ORIG_DIR"
git worktree add -b "$BRANCH" "$WT_DIR" HEAD
```

远程例子：

```bash
ORIG_DIR="/data/ganpa/dragongong/project"
WT_PARENT="/data/ganpa/dragongong/project-worktrees"
EXP_NAME="dense-int-pair-ablation"
BRANCH="exp/${EXP_NAME}"
WT_DIR="${WT_PARENT}/${EXP_NAME}"

mkdir -p "$WT_PARENT"
cd "$ORIG_DIR"
git worktree add -b "$BRANCH" "$WT_DIR" HEAD
```

如果分支已经存在：

```bash
git worktree add "$WT_DIR" "$BRANCH"
```

---

### 第三步：在 worktree 中改代码

进入 worktree：

```bash
cd "$WT_DIR"
git status --short
```

只在这里改实验代码。

不要在原项目目录直接改模型代码、训练代码、配置代码，避免污染当前运行目录。

---

### 第四步：跑实验时显式指定数据和输出路径

所有数据路径、cache 路径、输出路径都指向原项目目录。

推荐统一变量：

```bash
export ORIG_DIR="/data/ganpa/dragongong/project"
export DATA_ROOT="$ORIG_DIR/data"
export CACHE_ROOT="$ORIG_DIR/cache"
export OUTPUT_ROOT="$ORIG_DIR/outputs/$EXP_NAME"
export LOG_ROOT="$ORIG_DIR/logs/$EXP_NAME"

mkdir -p "$OUTPUT_ROOT" "$LOG_ROOT"
```

运行脚本时，尽量显式传参：

```bash
cd "$WT_DIR"
python train.py \
  --data_root "$DATA_ROOT" \
  --cache_dir "$CACHE_ROOT" \
  --output_dir "$OUTPUT_ROOT" \
  2>&1 | tee "$LOG_ROOT/train.log"
```

如果项目参数名不同，就使用项目真实参数名，例如：

```bash
--data_dir
--dataset_dir
--cache_path
--output_path
--save_dir
--log_dir
--embedding_dir
```

关键要求：不要让脚本默认把大文件写到 worktree 内部。

---

## 路径检查规则

实验前检查：

```bash
cd "$WT_DIR"
pwd
git status --short
```

实验后检查 worktree 是否误生成大文件：

```bash
find "$WT_DIR" -type f -size +100M | head -50
```

如果发现大文件：

1. 能复现的临时文件，删除。
2. 有价值的实验产物，移动到原项目目录的 outputs 或 logs 下。
3. 不要复制一份留在两个地方。

推荐移动：

```bash
mkdir -p "$ORIG_DIR/outputs/$EXP_NAME"
mv "$WT_DIR/path/to/heavy_file" "$ORIG_DIR/outputs/$EXP_NAME/"
```

---

## 实验报告要求

实验完成后，在原项目目录写报告。

默认路径：

```bash
REPORT_PATH="$ORIG_DIR/docs/experiments/$(date +%F)-$EXP_NAME.md"
mkdir -p "$(dirname "$REPORT_PATH")"
```

报告至少包含：

```markdown
# 实验报告：<实验名>

## 1. 实验目的

说明为什么做这个实验，要验证什么假设。

## 2. 代码环境

- 原项目目录：
- worktree 目录：
- base branch：
- experiment branch：
- commit：

## 3. 数据与产物路径

- data：
- cache：
- outputs：
- logs：
- report：

## 4. 改动内容

列出改了哪些文件，每个文件改了什么。

## 5. 运行命令

贴关键命令，不要只写“已运行”。

## 6. 实验结果

列指标表，包含 baseline 和实验版本。

## 7. 结论

直接说明：涨了、跌了、持平，是否值得继续。

## 8. 风险和后续

说明可能的问题、过拟合风险、数据泄漏风险、下一步建议。

## 9. 清理状态

- worktree 是否已删除：是/否
- 大文件是否留在 worktree：无/有
- 实验分支是否保留：是/否
```

报告必须写到 `$ORIG_DIR` 下，不要只存在于 `$WT_DIR`。

---

## 清理 worktree

清理前先检查：

```bash
cd "$WT_DIR"
git status --short
find "$WT_DIR" -type f -size +100M | head -50
```

如果代码改动需要保留，先提交到实验分支：

```bash
cd "$WT_DIR"
git add <changed_files>
git commit -m "exp: <实验主题>"
```

如果不需要提交，但报告已经写回原项目目录，可以丢弃 worktree 改动后删除：

```bash
cd "$ORIG_DIR"
git worktree remove "$WT_DIR" --force
git worktree prune
```

如果已经提交，正常删除：

```bash
cd "$ORIG_DIR"
git worktree remove "$WT_DIR"
git worktree prune
```

删除后确认：

```bash
git worktree list
```

要求最终回复用户时明确写：

```text
worktree 已删除 / 未删除，原因是 xxx
实验报告已写到 xxx
实验输出在 xxx
实验分支是 xxx
```

---

## 分支管理建议

默认策略：

1. 每个实验一个 `exp/...` 分支。
2. 每个实验一个临时 worktree。
3. 实验结束删除 worktree。
4. 实验分支默认保留，方便追溯。
5. 如果用户明确说不保留分支，再删除分支。

删除分支前必须确认：

```bash
git branch --contains <commit>
```

如果只是临时试验，且用户明确要求删除分支：

```bash
git branch -D "$BRANCH"
```

如果分支已推送远端，删除远端分支需要用户明确要求，不要默认删除。

---

## 最终回复格式

实验完成后，回复用户时用这个结构：

```markdown
完成了。

**隔离环境**
- 原项目目录：...
- 实验 worktree：已删除 / 未删除
- 实验分支：...

**数据与产物**
- 数据目录：...
- cache 目录：...
- 输出目录：...
- 日志目录：...
- 实验报告：...

**主要结果**
| 配置 | 指标1 | 指标2 | 结论 |
|---|---:|---:|---|
| baseline | ... | ... | ... |
| experiment | ... | ... | ... |

**结论**
一句话说清楚是否值得继续。
```

如果实验失败，也要写失败报告，并清理 worktree：

```markdown
实验没有跑通。

失败原因：...
已写失败报告：...
worktree 清理状态：已删除 / 未删除，原因是 ...
```

---

## 禁止事项

不要这样做：

```bash
cp -r data "$WT_DIR/"
cp -r cache "$WT_DIR/"
cp -r outputs "$WT_DIR/"
rsync -a data "$WT_DIR/"
```

不要把大文件提交进 git。

不要在原项目目录直接改实验代码。

不要让报告只存在于临时 worktree。

不要实验结束后留下没人知道用途的 worktree 目录。

---

## 一句话执行标准

代码在 worktree 里隔离，数据和产物回到原目录，报告写回原目录，实验结束删除 worktree。
