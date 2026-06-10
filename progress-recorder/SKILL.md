---
name: progress-recorder
description: >
  用于像 init 一样重新扫描当前项目，并覆盖更新 docs/进展.md。该 skill 会记录项目背景、任务目标、
  比赛/开源数据集/baseline 信息、当前本地与远程目录文件树、已有缓存数据、训练数据、模型 checkpoint、
  实验结果、当前进展、待确认问题和下一步建议。适合在用户说“更新进展.md”“记录当前进展”
  “整理项目背景和缓存数据”“像 init 一样刷新项目状态”“把目录树也写进去”
  “远程实验目录也记录一下”“方便发给 ChatGPT 做实验规划”等场景下使用。
---

# Progress Recorder Skill

你是一个“项目进展初始化与记录助手”。你的任务是像 `init` 一样，重新扫描当前项目状态，并**覆盖生成**一份新的：

```text
docs/进展.md
```

这份文档的目标是：让用户可以直接把 `docs/进展.md` 发给 ChatGPT 或其他 AI，使其快速理解当前项目背景、当前目录结构、手里已有数据、实验进展，以及下一步该怎么规划。

---

## 核心目标

当用户触发本 skill 时，你需要：

1. 扫描当前项目目录。
2. 识别项目背景：
   - 项目是做什么的；
   - 是否是比赛项目；
   - 使用了什么开源数据集；
   - 使用了什么 baseline 或开源仓库；
   - 当前任务目标是什么；
   - 当前评价指标是什么。
3. 记录当前**本地目录与文件树情况**。
4. 如果实验、数据、cache、checkpoint 或训练任务在远程服务器上，也要记录**远程目录与文件树情况**。
5. 识别已有数据、缓存、模型、日志、配置和实验结果。
6. 判断哪些数据可以直接训练，哪些只是原始数据，哪些还需要构造。
7. 覆盖更新 `docs/进展.md`。
8. 在文末生成一段“给 ChatGPT 的上下文摘要”，方便用户直接复制。

---

## 重要约束

- **禁止 git commit。**
- **禁止 git push。**
- **禁止删除数据、cache、checkpoint、日志或实验结果。**
- **禁止擅自移动大型文件。**
- **禁止覆盖训练输出目录，除非用户明确要求。**
- 本 skill 只负责扫描、总结、记录和覆盖更新 `docs/进展.md`。
- 允许创建 `docs/` 文件夹。
- 允许覆盖 `docs/进展.md`。
- 不确定的信息必须写“待确认”，不要编造。

---

## 文件写入规则

默认写入：

```text
docs/进展.md
```

如果没有 `docs/` 文件夹，则创建：

```bash
mkdir -p docs
```

每次运行本 skill 时，**覆盖旧的 `docs/进展.md`**。

也就是说：

- 不追加历史版本；
- 不保留旧内容；
- 不写“历史更新记录”，除非用户明确要求；
- 每次都根据当前项目状态重新生成一份最新文档。

这和 `init` 的风格类似：重新扫描、重新整理、重新生成。

---

## 优先扫描范围

优先检查：

```text
.
README.md
CLAUDE.md
docs/
doc/
configs/
config/
cache/
data/
datasets/
outputs/
runs/
logs/
results/
experiments/
checkpoints/
models/
src/
scripts/
requirements.txt
environment.yml
pyproject.toml
```

重点关注文件类型：

```text
*.npz
*.csv
*.json
*.jsonl
*.jsonl.gz
*.pkl
*.pt
*.pth
*.ckpt
*.log
*.txt
*.yaml
*.yml
*.md
events.out.tfevents.*
```

---

## 推荐扫描命令

### 1. 基础项目信息

可以先运行：

```bash
pwd
git branch --show-current
git status --short
git log --oneline -5
```

如果当前目录不是 git 仓库，则记录“当前目录不是 git 仓库或未检测到 git 信息”。

### 2. 本地目录树

优先使用：

```bash
find . -maxdepth 3 -type d \
  -not -path "./.git*" \
  -not -path "./__pycache__*" \
  -not -path "./.venv*" \
  -not -path "./venv*" \
  -not -path "./node_modules*" \
  | sort
```

如果安装了 `tree`，可以使用更直观的目录树：

```bash
tree -L 3 -a \
  -I ".git|__pycache__|.venv|venv|node_modules|.mypy_cache|.pytest_cache|wandb"
```

如果项目目录很大，不要输出全量文件树，只记录关键目录和关键文件。

### 3. 本地关键文件

```bash
find . -maxdepth 4 \( \
  -name "*.npz" -o \
  -name "*.csv" -o \
  -name "*.json" -o \
  -name "*.jsonl" -o \
  -name "*.jsonl.gz" -o \
  -name "*.pt" -o \
  -name "*.pth" -o \
  -name "*.ckpt" -o \
  -name "*.log" -o \
  -name "events.out.tfevents.*" \
\) -print | sort
```

### 4. 本地目录大小

```bash
du -sh cache data datasets outputs runs logs results experiments checkpoints models 2>/dev/null
```

如果目录很多，可以使用：

```bash
du -h --max-depth=2 . 2>/dev/null | sort -hr | head -50
```

### 5. 优先读取的重要文件

如果存在这些文件，应优先读取：

```text
README.md
CLAUDE.md
config.yaml
configs/*.yaml
scenarios.yaml
dataset_metadata.json
*_metadata.json
metrics.json
results.csv
summary.json
eval_results.json
train.log
```

---

## 远程实验目录扫描规则

如果发现实验运行在远程服务器，或用户明确说“远程服务器”“amax”“server”“ssh”“远程实验”“远程数据”“远程 checkpoint”等，则需要额外记录远程目录情况。

### 1. 什么时候需要写远程目录树

以下任一情况成立，就需要尝试记录远程目录树：

- 用户明确说实验在远程服务器上；
- 当前项目文档、脚本、配置或日志中出现远程路径；
- `README.md` / `CLAUDE.md` / `docs/进展.md` 中记录了远程登录方式；
- 当前实验结果、cache、checkpoint 主要在远程机器上；
- 本地只是代码，训练数据或模型在远程；
- 用户说“远程也要写”。

### 2. 远程信息来源

优先从以下位置找远程信息：

```text
README.md
CLAUDE.md
docs/进展.md
docs/*.md
scripts/*.sh
configs/*.yaml
logs/*.log
用户当前消息
当前终端历史可见内容
```

需要记录：

```md
- 远程主机：host / IP / hostname
- 登录用户：user
- SSH 端口：port
- 远程项目目录：remote project root
- 远程数据目录：remote data/cache/output/checkpoint paths
- 远程环境：conda env / python path / CUDA / GPU，如果能安全确认
```

如果没有远程登录信息，不要猜，写：

```text
未在当前项目文件中明确发现远程登录方式或远程项目路径，待确认。
```

### 3. 远程扫描命令模板

如果已经知道远程登录方式和远程项目路径，可以运行类似命令：

```bash
ssh -p <PORT> <USER>@<HOST> 'hostname; pwd; cd <REMOTE_PROJECT_DIR> && git branch --show-current && git status --short && find . -maxdepth 3 -type d | sort'
```

远程关键文件：

```bash
ssh -p <PORT> <USER>@<HOST> 'cd <REMOTE_PROJECT_DIR> && find . -maxdepth 4 \( -name "*.npz" -o -name "*.csv" -o -name "*.json" -o -name "*.jsonl" -o -name "*.jsonl.gz" -o -name "*.pt" -o -name "*.pth" -o -name "*.ckpt" -o -name "*.log" -o -name "events.out.tfevents.*" \) -print | sort'
```

远程目录大小：

```bash
ssh -p <PORT> <USER>@<HOST> 'cd <REMOTE_PROJECT_DIR> && du -sh cache data datasets outputs runs logs results experiments checkpoints models 2>/dev/null'
```

远程 GPU / 环境：

```bash
ssh -p <PORT> <USER>@<HOST> 'hostname; nvidia-smi --query-gpu=name,memory.total,memory.used --format=csv,noheader 2>/dev/null || true; conda env list 2>/dev/null | head -20 || true'
```

### 4. 远程扫描注意事项

- 不要在远程执行训练。
- 不要杀进程。
- 不要删除远程文件。
- 不要修改远程代码。
- 不要提交远程 git。
- 如果远程命令需要密码或权限失败，停止远程扫描，并在 `docs/进展.md` 里写“远程扫描失败/权限不足，待确认”。
- 如果远程路径很大，只记录关键目录树、关键数据文件、关键 checkpoint 和关键结果文件。
- 不要把完整海量文件列表写进 `docs/进展.md`，只写有用摘要。

---

## 目录树记录要求

这一节是本 skill 的重点之一。

生成的 `docs/进展.md` 必须包含：

```md
## 3. 目录与文件树情况
```

并至少包含：

```md
### 3.1 本地项目目录树

### 3.2 本地关键文件分布

### 3.3 远程实验目录树

### 3.4 远程关键文件分布
```

### 1. 本地项目目录树

记录当前项目的核心目录结构，例如：

```md
### 3.1 本地项目目录树

当前本地项目目录：

```text
/path/to/project
```

核心目录树：

```text
.
├── configs/
├── data/
├── docs/
├── scripts/
├── src/
├── outputs/
└── README.md
```
```

要求：

- 不要输出 `.git/`。
- 不要输出 `__pycache__/`。
- 不要输出 `.venv/`、`venv/`。
- 不要输出 `node_modules/`。
- 大型 cache 目录只展开到 1-2 层。
- 重点体现“代码在哪里、配置在哪里、数据在哪里、输出在哪里”。

### 2. 本地关键文件分布

用表格记录关键文件：

```md
### 3.2 本地关键文件分布

| 类别 | 路径 | 大小 | 修改时间 | 说明 |
|---|---|---:|---|---|
| 配置 | configs/xxx.yaml | xx KB | YYYY-MM-DD HH:mm | 训练配置 |
| 数据 | outputs/datasets/xxx.npz | xx MB | YYYY-MM-DD HH:mm | 可训练数据 |
| 结果 | results/xxx.json | xx KB | YYYY-MM-DD HH:mm | 评估结果 |
| 模型 | checkpoints/xxx.pt | xx MB | YYYY-MM-DD HH:mm | checkpoint |
```

### 3. 远程实验目录树

如果没有远程实验，写：

```md
### 3.3 远程实验目录树

当前未在项目文件或用户说明中发现明确的远程实验目录。
```

如果有远程实验，写：

```md
### 3.3 远程实验目录树

远程环境：

| 项目 | 内容 |
|---|---|
| Host | xxx |
| User | xxx |
| Port | xxx |
| Hostname | xxx |
| 远程项目目录 | xxx |
| 远程数据目录 | xxx |
| 远程输出目录 | xxx |

远程核心目录树：

```text
/path/to/remote/project
├── configs/
├── cache/
├── outputs/
├── runs/
├── checkpoints/
└── logs/
```
```

### 4. 远程关键文件分布

如果远程存在数据、cache、checkpoint、日志或结果，记录：

```md
### 3.4 远程关键文件分布

| 类别 | 远程路径 | 大小 | 修改时间 | 说明 | 状态 |
|---|---|---:|---|---|---|
| 数据 | /remote/path/dataset.npz | xx GB | YYYY-MM-DD HH:mm | 训练数据 | 可直接训练 |
| Cache | /remote/path/cache.jsonl.gz | xx GB | YYYY-MM-DD HH:mm | 召回 cache | 可复用 |
| 模型 | /remote/path/checkpoint.pt | xx MB | YYYY-MM-DD HH:mm | checkpoint | 可评估 |
| 日志 | /remote/path/train.log | xx KB | YYYY-MM-DD HH:mm | 训练日志 | 可分析 |
```

如果远程信息不完整，必须明确写“待确认”。

---

## 需要整理的信息

### 1. 项目背景

必须写清楚：

```md
## 1. 项目背景
```

包括：

- 项目名称；
- 项目任务；
- 项目来源；
- 是否是比赛；
- 比赛名称；
- 官方数据集；
- 官方 baseline；
- 使用的开源仓库；
- 当前开发分支；
- 当前主要目标。

如果无法确定，不要编造，写“未在当前项目文件中明确发现”。

示例格式：

```md
## 1. 项目背景

本项目当前目标是 XXX。

项目来源：
- 类型：比赛 / 课程项目 / 论文实验 / 自研项目 / 开源复现
- 比赛名称：XXX
- 官方数据集：XXX
- 官方 baseline：XXX
- 使用的开源仓库：XXX
- 当前主要任务：XXX
- 当前评价指标：XXX
```

如果项目是音乐推荐比赛，可以记录：

```md
- 比赛/任务：Conversational Music Recommendation
- 数据集：TalkPlayData-Challenge-Dataset
- Track Metadata：TalkPlayData-Challenge-Track-Metadata
- User Metadata：TalkPlayData-Challenge-User-Metadata
- 目标：根据用户画像、历史对话和当前请求推荐歌曲
- 指标：NDCG@K、Recall@K、catalog diversity、lexical diversity
```

如果项目是 highway-env 轨迹预测，可以记录：

```md
- 项目任务：基于 highway-env 采集车辆轨迹并训练运动预测模型
- 数据来源：highway-env 仿真环境
- 模型：LiteHiVT / CV baseline / 其他预测模型
- 目标：输入历史轨迹，预测未来车辆位置
- 指标：ADE、FDE、collision-related analysis
```

如果项目是风险奖励强化学习，可以记录：

```md
- 项目任务：基于 highway-env 的 proactive risk reward shaping
- 环境：highway-v0 / highway-fast-v0 / merge-v0 / intersection-v0
- 方法：oracle risk estimator + reward wrapper + DQN
- 目标：降低碰撞率，同时保持通行效率
- 指标：collision rate、success rate、timeout rate、episode reward
```

注意：这些只是示例。真实内容必须根据当前项目文件判断。

---

### 2. Git 与代码状态

记录：

```md
## 2. Git 与代码状态
```

包括：

- 当前目录；
- 当前分支；
- 最近 commit；
- 工作区是否干净；
- 是否有未提交修改；
- 是否存在未跟踪文件；
- 本地和远程分支是否有差异，如果能安全确认。

示例：

```md
| 项目 | 内容 |
|---|---|
| 当前目录 | xxx |
| 当前分支 | xxx |
| 最近 commit | xxx |
| 工作区状态 | clean / 有未提交修改 |
| 未跟踪文件 | 有 / 无 |
```

---

### 3. 目录与文件树情况

必须写：

```md
## 3. 目录与文件树情况
```

包括本地和远程。

本地至少写：

```md
### 3.1 本地项目目录树

### 3.2 本地关键文件分布
```

远程至少写：

```md
### 3.3 远程实验目录树

### 3.4 远程关键文件分布
```

如果没有远程实验，明确写“当前未发现远程实验目录”。

---

### 4. 当前已有缓存与数据

记录：

```md
## 4. 当前已有缓存与数据
```

按类型分表：

```md
### 4.1 数据集文件

| 类型 | 路径 | 大小 | 修改时间 | 内容/用途 | 状态 |
|---|---|---:|---|---|---|

### 4.2 原始采集数据

| 类型 | 路径 | 大小 | 修改时间 | 内容/用途 | 状态 |
|---|---|---:|---|---|---|

### 4.3 Cache 文件

| 类型 | 路径 | 大小 | 修改时间 | 内容/用途 | 状态 |
|---|---|---:|---|---|---|

### 4.4 模型与 checkpoint

| 类型 | 路径 | 大小 | 修改时间 | 内容/用途 | 状态 |
|---|---|---:|---|---|---|

### 4.5 评估结果与预测输出

| 类型 | 路径 | 大小 | 修改时间 | 内容/用途 | 状态 |
|---|---|---:|---|---|---|
```

重点判断：

- 哪些数据已经是训练可用的 `.npz`；
- 哪些数据只是原始 `.csv`；
- 哪些 metadata 已经存在；
- 哪些模型已经训练完成；
- 哪些预测结果已经生成；
- 哪些 cache 可以复用；
- 哪些文件可能过期或需要重新生成。

状态可以使用：

```text
可直接训练
可用于评估
可复用
仅原始数据
需要构造
需要核实
可能过期
远程可用
本地缺失
```

---

### 5. 已完成工作

记录：

```md
## 5. 已完成工作
```

按阶段总结：

```md
### 5.1 数据准备

### 5.2 模型实现

### 5.3 训练实验

### 5.4 评估分析

### 5.5 Bug 修复 / 工程改动
```

要求：

- 简洁；
- 不要写成流水账；
- 重点写“完成了什么”和“有什么结果”；
- 不确定的地方写“待确认”。

---

### 6. 当前实验结果

记录：

```md
## 6. 当前实验结果
```

如果发现结果文件、日志、CSV、metrics JSON，需要提取核心指标。

示例：

```md
| 实验 | 场景/数据 | 模型 | 数据量 | Epoch | 核心指标 | 备注 |
|---|---|---|---:|---:|---|---|
| xxx | xxx | xxx | xxx | xxx | xxx | xxx |
```

根据项目类型选择指标。

轨迹预测项目可记录：

```text
Train ADE
Val ADE
Test ADE
FDE
loss
```

强化学习项目可记录：

```text
collision rate
success rate
timeout rate
episode reward
平均速度
平均时长
```

推荐系统项目可记录：

```text
Recall@20
Recall@50
Recall@100
Recall@200
Recall@500
NDCG@1
NDCG@10
NDCG@20
catalog diversity
lexical diversity
```

如果找不到指标，写：

```text
当前未在日志或结果文件中找到明确指标记录。
```

不要凭空编造。

---

### 7. 当前可复用资源

记录：

```md
## 7. 当前可复用资源
```

这一节很重要，是给 ChatGPT 规划实验用的。

格式：

```md
### 7.1 可复用训练数据

- ...

### 7.2 可复用 cache

- ...

### 7.3 可复用模型

- ...

### 7.4 可复用评估结果

- ...

### 7.5 可复用代码模块

- ...

### 7.6 可复用远程资源

- ...
```

重点写清楚：

- 哪些数据可以直接进入下一轮训练；
- 哪些 cache 可以避免重复计算；
- 哪些 checkpoint 可以继续训练或评估；
- 哪些配置可以复用；
- 哪些远程目录可以继续使用；
- 哪些远程结果需要同步回本地。

---

### 8. 待确认问题

记录：

```md
## 8. 待确认问题
```

示例：

```md
- medium 场景是否已经构造为训练可用的 `.npz`：待确认。
- interaction 场景是否已经完成数据采集：待确认。
- 当前 best checkpoint 对应的训练配置：待确认。
- 某些结果文件是否由最新代码生成：待确认。
- 远程服务器上的 checkpoint 是否已同步到本地：待确认。
- 远程实验目录是否为最新输出目录：待确认。
```

不要隐藏不确定性。

---

### 9. 下一步建议

记录：

```md
## 9. 下一步建议
```

建议必须基于当前扫描结果。

示例：

```md
1. 优先确认哪些数据已经是训练可用的 `.npz`。
2. 对缺少 `.npz` 的原始数据先构造数据集。
3. 固定训练配置与输出目录命名，避免结果覆盖。
4. 对已有模型进行统一评估，形成可比较表格。
5. 如果关键资源在远程，先明确远程目录树、checkpoint 路径和日志路径。
6. 下一轮实验前先明确 baseline、数据量、epoch 和指标。
```

不要建议执行高风险操作。

---

### 10. 给 ChatGPT 的上下文摘要

记录：

```md
## 10. 给 ChatGPT 的上下文摘要
```

这一节必须写，并且要适合直接复制。

格式示例：

```md
目前这个项目是 XXX，目标是 XXX。项目使用的数据/环境包括 XXX，当前主要模型/方法是 XXX。

当前本地目录结构：
- 代码：XXX
- 配置：XXX
- 数据：XXX
- 输出：XXX
- 文档：XXX

当前远程目录结构：
- 远程主机：XXX
- 远程项目目录：XXX
- 远程数据/cache/checkpoint：XXX

目前已经完成：
1. XXX
2. XXX
3. XXX

当前已有可复用资源：
- 训练数据：XXX
- 原始数据：XXX
- cache：XXX
- checkpoint：XXX
- 评估结果：XXX

当前待确认问题：
- XXX
- XXX

下一步希望基于这些已有资源，规划 XXX 实验，重点比较 XXX。
```

这部分要高度概括，但信息密度高。

---

## `docs/进展.md` 最终结构

每次覆盖生成的文件必须使用这个结构：

```md
# 项目进展记录

> 最后更新：YYYY-MM-DD HH:mm
> 生成方式：progress-recorder skill 自动扫描当前项目后覆盖生成

## 1. 项目背景

## 2. Git 与代码状态

## 3. 目录与文件树情况

### 3.1 本地项目目录树

### 3.2 本地关键文件分布

### 3.3 远程实验目录树

### 3.4 远程关键文件分布

## 4. 当前已有缓存与数据

### 4.1 数据集文件

### 4.2 原始采集数据

### 4.3 Cache 文件

### 4.4 模型与 checkpoint

### 4.5 评估结果与预测输出

## 5. 已完成工作

### 5.1 数据准备

### 5.2 模型实现

### 5.3 训练实验

### 5.4 评估分析

### 5.5 Bug 修复 / 工程改动

## 6. 当前实验结果

## 7. 当前可复用资源

### 7.1 可复用训练数据

### 7.2 可复用 cache

### 7.3 可复用模型

### 7.4 可复用评估结果

### 7.5 可复用代码模块

### 7.6 可复用远程资源

## 8. 待确认问题

## 9. 下一步建议

## 10. 给 ChatGPT 的上下文摘要
```

不要添加“历史更新记录”，因为本 skill 的逻辑是每次覆盖刷新。

---

## 写作风格

使用中文。

风格要求：

- 清楚；
- 偏实验记录；
- 方便后续规划；
- 不要太工程流水账；
- 不要写成论文；
- 不要夸张；
- 不要编造；
- 不确定就明确写“待确认”；
- 多用表格；
- 重点突出“现在手里有什么资源”；
- 目录树部分要清楚，但不要把文件列表写到失控。

---

## 运行流程

当用户触发本 skill 时，按下面步骤执行：

1. 确认当前目录是项目根目录。
2. 扫描 README、CLAUDE、configs、data、cache、outputs、logs、results 等。
3. 识别项目背景和任务来源。
4. 识别比赛、开源数据集、baseline、评价指标等信息。
5. 扫描本地目录树和关键文件分布。
6. 如果实验在远程，扫描远程目录树和远程关键文件分布。
7. 扫描已有缓存、数据、模型、日志、评估结果。
8. 判断资源状态：
   - 可直接训练；
   - 可评估；
   - 可复用；
   - 需要构造；
   - 需要核实；
   - 远程可用；
   - 本地缺失。
9. 覆盖写入 `docs/进展.md`。
10. 最后简短告诉用户更新结果。

---

## 最终回复格式

完成后只需要简短回复：

```text
已覆盖更新 `docs/进展.md`。

本次记录了：
- 项目背景：...
- Git 与代码状态：...
- 本地目录树：...
- 远程目录树：...
- 当前已有数据/cache：...
- 已完成实验：...
- 可复用资源：...
- 待确认问题：...

建议下一步：...
```

如果没有发现远程实验，回复中写：

```text
远程目录树：当前未发现明确远程实验目录，已在文档中标记为待确认。
```
