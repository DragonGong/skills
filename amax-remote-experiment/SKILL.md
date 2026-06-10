---
name: amax-remote-experiment
description: "Run, debug, and test ML experiments on the user's shared remote GPU servers: ganpa/AMAX (ssh -p 22 ganpa@10.103.68.253) and rtxpro6000 (ssh yunlong@166.111.73.159). Use when the user asks to run ML experiments, train models, debug runtime failures, execute tests, build data/cache artifacts, or use GPU jobs remotely. Covers Windows-host SSH access, server selection, local WSL vs remote code-editing rules, git sync, conda environments, data/cache setup, GPU selection, tmux sessions, logs, and shared-server safety. DO NOT USE for unrelated local-only coding tasks."
---

# Remote GPU Experiment Skill

## Purpose

Use this skill when the user wants an agent to edit code and run, debug, test, evaluate, or build data/cache artifacts on a shared remote GPU server.

There are two supported remote servers:

- `ganpa` / `AMAX`: `ssh -p 22 ganpa@10.103.68.253`
- `rtxpro6000`: `ssh yunlong@166.111.73.159`

## Mandatory Server Selection

When the user asks to run, debug, test, evaluate, prepare data/cache, or launch experiments and does not explicitly name a server, ask first:

```text
Use ganpa/AMAX or rtxpro6000?
```

Skip this question only when the user explicitly names one of:

- `ganpa`
- `AMAX`
- `10.103.68.253`
- `rtxpro6000`
- `166.111.73.159`
- `yunlong@166.111.73.159`
- `ubuntu@166.111.73.159`

After the user chooses a server, use that server consistently for SSH commands, paths, environment setup, runs, logs, and final summaries.

## Environment Roles

1. **Windows host**
   - Runs Codex / Claude Code / CC Switch.
   - Handles SSH login to remote servers using Windows OpenSSH.
   - Use `functions.shell_command` with `login: false` for remote SSH commands when possible, to avoid slow or blocking PowerShell profile startup.

2. **Local WSL**
   - Main local development environment for `ganpa` / AMAX workflows.
   - Used for code reading, editing, refactoring, local git commits, and git push before AMAX pulls the branch.
   - Not used for running project code, tests, training, evaluation, data preprocessing, or cache building unless the user explicitly asks for a local run.

3. **Remote GPU servers**
   - Shared machines used for project execution, tests, debugging, data/cache generation, experiments, and logs.
   - `ganpa` / AMAX is not the default code-editing workspace; it should pull code that was committed and pushed from local WSL.
   - `rtxpro6000` may be used as a direct code-editing workspace, but only under `~/dragongong`.

## Server Catalog

### ganpa / AMAX

- Canonical name: `ganpa` or `AMAX`
- IP: `10.103.68.253`
- Port: `22`
- Username: `ganpa`
- Windows SSH command: `ssh -p 22 ganpa@10.103.68.253`
- Observed hostname/prompt: `amax`
- Remote project root: `~/dragongong`
- Login lands in: `~`
- Known project directories:
  - `~/dragongong/ann`
  - `~/dragongong/music-crs`
  - `~/dragongong/URM`
- Observed GPU status:
  - 4 x NVIDIA GeForce RTX 3090
  - About 24 GB VRAM per GPU
  - Driver version observed: `575.64`
  - CUDA version observed by `nvidia-smi`: `12.9`

Example Windows SSH command:

```powershell
ssh -p 22 ganpa@10.103.68.253
```

Example `functions.shell_command` usage:

```json
{
  "command": "ssh -p 22 ganpa@10.103.68.253 \"echo ok; hostname; date\"",
  "login": false
}
```

### rtxpro6000

- Canonical name: `rtxpro6000`
- IP: `166.111.73.159`
- Port: `22`
- Normal experiment username: `yunlong`
- Normal Windows SSH command: `ssh yunlong@166.111.73.159`
- Original/admin bootstrap account: `ubuntu@166.111.73.159`
- Observed hostname/prompt: `ubuntu-K14PA-U12`
- Remote project root: `~/dragongong`
- Absolute project root for normal use: `/home/yunlong/dragongong`
- Login lands in: `~`
- This machine and its GPU are shared, but the `yunlong` Linux user is for the user's own work.
- Direct source-code editing is allowed only under `~/dragongong`.
- The `yunlong` user is isolated from the original `ubuntu` account and is the user's normal account: its home directory is `/home/yunlong`, with separate SSH, git, conda, cache, config, and token files.
- Use `ubuntu` only for explicit admin/bootstrap maintenance. Do not use `ubuntu` for normal code edits, git work, env setup, or experiments unless the user explicitly asks.
- The `yunlong` account has `sudo`, `video`, `render`, and `users` group membership. Use `sudo` only when the user explicitly approves the exact operation.
- Observed GPU status:
  - GPU: `NVIDIA RTX PRO 6000 Blackwell Workstation Edition`
  - Driver version: `595.58.03`
  - CUDA version shown by `nvidia-smi`: `13.2`
  - Total memory shown: `97887 MiB`
  - Example observed memory usage: about `13334 MiB / 97887 MiB`

Example Windows SSH command:

```powershell
ssh yunlong@166.111.73.159
```

Example `functions.shell_command` usage:

```json
{
  "command": "ssh yunlong@166.111.73.159 \"echo ok; hostname; date\"",
  "login": false
}
```

## SSH Rules

- Use direct SSH from the Windows host terminal, not WSL SSH, unless the user explicitly asks otherwise.
- Do not ask for a password.
- Do not use `sshpass`.
- Do not store passwords in scripts, project files, logs, commits, or skill files.
- Always start remote project work by moving to `~/dragongong` or a repository under it.

Basic remote verification:

```bash
hostname
pwd
ls -ld ~/dragongong
nvidia-smi
```

## Git Rules

### ganpa / AMAX Git Rules

The remote account is shared. Git identity is specially configured for the user's directory.

Remote `~/.gitconfig` contains:

```gitconfig
[filter "lfs"]
        clean = git-lfs clean -- %f
        smudge = git-lfs smudge -- %f
        process = git-lfs filter-process
        required = true

[includeIf "gitdir:~/dragongong/"]
  path = ~/.gitconfig_dragongong
```

Remote `~/.gitconfig_dragongong` contains:

```gitconfig
[user]
 name = dragongong
 email = dragongong20040318@gmail.com
```

Remote `~/.ssh/config` contains:

```sshconfig
Host github.com-decof
    HostName github.com
    User git
    IdentityFile ~/.ssh/github-decof
    IdentitiesOnly yes

Host github-dragongong
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_dragongong
  IdentitiesOnly yes
```

Private repositories belonging to the user should be cloned or pulled using the `github-dragongong` SSH host alias on ganpa / AMAX:

```bash
git clone git@github-dragongong:OWNER/REPO.git
```

For an existing repository, check and fix the remote if needed:

```bash
git remote -v
git remote set-url origin git@github-dragongong:OWNER/REPO.git
```

### rtxpro6000 Git Rules

These rules apply to the normal `yunlong` login on rtxpro6000.

Git identity is configured only for repositories under `~/dragongong`, matching the ganpa style:

```gitconfig
[includeIf "gitdir:~/dragongong/"]
  path = /home/yunlong/.gitconfig_dragongong
```

Remote `~/.gitconfig_dragongong` contains:

```gitconfig
[user]
 name = dragongong
 email = dragongong20040318@gmail.com
```

GitHub SSH access is configured and verified for `yunlong` using the normal `github.com` host. Do not use the `github-dragongong` alias on rtxpro6000; that alias is only for shared-account workflows such as ganpa / AMAX.

Remote `~/.ssh/config` contains:

```sshconfig
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_dragongong
  IdentitiesOnly yes
```

The public key file is:

```bash
~/.ssh/id_ed25519_dragongong.pub
```

Do not copy private keys from the `ubuntu` account into `yunlong`. Keep SSH keys separated by Linux user.

Private repositories belonging to the user should be cloned or pulled using normal GitHub SSH URLs on rtxpro6000:

```bash
git clone git@github.com:OWNER/REPO.git
```

For existing repositories on rtxpro6000, use the current `origin` unless it is wrong:

```bash
git remote -v
```

If needed, set it to:

```bash
git remote set-url origin git@github.com:OWNER/REPO.git
```

Do not modify SSH keys, `~/.ssh/config`, or private key files on rtxpro6000 unless the user explicitly asks.

## Code Editing Rules By Server

### ganpa / AMAX

Local WSL is the source of truth for source code.

Allowed local WSL actions:

- read code
- modify code
- create files
- refactor
- run static inspection commands that do not execute project code or create data/cache artifacts
- commit changes
- push branches

Allowed AMAX remote actions:

- `git fetch`
- `git checkout <branch>`
- `git pull`
- create or activate project-specific conda environments
- install dependencies into the project conda environment
- download datasets/cache/model weights
- run project code, tests, debugging commands, evaluation scripts, preprocessing, cache-building, and experiments
- inspect logs/results
- copy result files back if needed

Do not directly edit source code on AMAX with `vim`, `nano`, `sed -i`, `cat > file`, file patches, or remote IDE edits unless the user explicitly approves emergency remote debugging.

If a bug is found on AMAX:

1. Inspect the remote error/log.
2. Explain the likely code change.
3. Apply the fix locally in WSL.
4. Commit and push locally from WSL.
5. SSH to AMAX.
6. Pull the updated branch on AMAX.
7. Rerun remotely.

### rtxpro6000

Direct source-code editing is allowed on rtxpro6000 only inside `~/dragongong`.

Before editing code on rtxpro6000, always verify:

```bash
hostname
pwd
git status
git branch --show-current
git remote -v
```

Do not edit code if:

- the current path is outside `~/dragongong`
- the repository has unexpected uncommitted changes
- the wrong branch is checked out
- the user asked to work on ganpa / AMAX instead

Allowed rtxpro6000 project actions under `~/dragongong`:

- read code
- modify code
- create files
- refactor
- run git commands
- commit changes
- push branches
- create/activate project-specific conda environments
- install dependencies into project envs
- run tests, debugging commands, preprocessing, cache-building, evaluation, and experiments
- inspect logs/results

Do not edit files outside `~/dragongong` except for explicitly requested `yunlong` account setup checks or when the user explicitly approves a specific change.

## Conda Environment Rule

Remote GPUs are shared, and ganpa / AMAX is a shared account. On rtxpro6000, `yunlong` is the user's own Linux account, but project environments should still be isolated. Never use the global `base` environment for project experiments.

Always create or use a project-specific conda environment:

```bash
conda create -n <project-env> python=3.10 -y
conda activate <project-env>
```

Before installing packages, verify:

```bash
which python
python --version
which pip
conda info --envs
```

Install packages only inside the activated conda environment:

```bash
python -m pip install -U pip
python -m pip install -r requirements.txt
```

Do not run:

```bash
sudo pip install ...
pip install ...
```

unless it is clear that the correct conda environment is already activated. Prefer `python -m pip`.

## Data And Cache Rule

Data, checkpoints, model weights, generated artifacts, and cache files should live on the selected remote server, not on the local machine, by default.

Avoid building local datasets or caches during debugging. Even small local runs can unexpectedly materialize large files, so project execution, preprocessing, dataset indexing, embedding generation, checkpoint creation, and HuggingFace/model cache population should happen on the selected remote server unless the user explicitly asks for a local run.

Recommended locations on the selected server:

```bash
~/dragongong/<repo>/cache
~/dragongong/<repo>/data
~/dragongong/<repo>/outputs
~/dragongong/<repo>/checkpoints
~/dragongong/<repo>/logs
```

For HuggingFace-related projects:

```bash
export HF_HOME=~/dragongong/.cache/huggingface
export TRANSFORMERS_CACHE=~/dragongong/.cache/huggingface/transformers
export HF_DATASETS_CACHE=~/dragongong/.cache/huggingface/datasets
mkdir -p ~/dragongong/.cache/huggingface
```

Do not download large datasets to random shared locations.

## GPU Usage Rule

Before running GPU jobs, always check current GPU usage:

```bash
nvidia-smi
```

Select GPU(s) explicitly:

```bash
CUDA_VISIBLE_DEVICES=0 python train.py
```

For multiple experiments, avoid occupying all GPUs unless the user explicitly asks.

Good defaults:

- use one free GPU for a single experiment
- use `tmux` for long-running experiments
- save logs to a file
- record the exact command used

Example:

```bash
tmux new -s <session_name>
cd ~/dragongong/<repo>
conda activate <project-env>
CUDA_VISIBLE_DEVICES=0 <experiment command> 2>&1 | tee logs/<run_name>_$(date +%Y%m%d_%H%M%S).log
```

Detach tmux:

```text
Ctrl-b d
```

Check and reattach:

```bash
tmux ls
tmux attach -t <session_name>
```

## Dangerous Remote Operations

Because both remote machines are shared servers, ask the user before dangerous operations.

Dangerous operations include:

- deleting large directories
- running `rm -rf`
- killing other users' processes
- using `sudo`
- changing global conda/base environment
- changing system CUDA, driver, apt, kernel, or OS packages
- modifying `~/.ssh/config`
- modifying `~/.gitconfig`, except explicitly requested `yunlong` git identity setup/checks on rtxpro6000
- deleting datasets, caches, checkpoints, or logs
- running jobs that occupy all GPUs
- running extremely long training jobs without user approval
- changing file permissions recursively
- moving project directories outside `~/dragongong`
- force-pushing Git branches from a remote server
- editing source code on AMAX without explicit approval
- editing source code outside `~/dragongong` on rtxpro6000

Allowed without asking:

- `pwd`
- `ls`
- `du -sh`
- `df -h`
- `nvidia-smi`
- `git status`
- `git fetch`
- `git checkout`
- `git pull`
- activating conda environments
- installing Python dependencies into a project-specific conda env
- running small remote test/debug commands
- running remote data-preparation or cache-building commands requested for the project
- running user-requested experiments
- reading logs
- creating logs/output directories inside the project

## Standard Workflow

When the user asks to run, debug, test, evaluate, or prepare data/cache remotely:

1. Select the server using the mandatory server selection rule.
2. Verify the selected server, project path, branch, env, and GPU.
3. Follow the server-specific code editing rule.
4. Run from a project-specific conda environment.
5. Save logs and report the selected server metadata.

### Workflow For ganpa / AMAX

In local WSL:

```bash
pwd
git status
git branch --show-current
```

Make code changes locally in WSL. Do not run project code locally unless the user explicitly requests it.

Then:

```bash
git add .
git commit -m "<clear commit message>"
git push origin <branch-name>
```

From Windows:

```powershell
ssh -p 22 ganpa@10.103.68.253
```

On AMAX:

```bash
cd ~/dragongong/<repo>
git fetch origin
git checkout <branch-name>
git pull origin <branch-name>
git status
```

If the repository is missing:

```bash
cd ~/dragongong
git clone git@github-dragongong:OWNER/REPO.git
cd <repo>
```

### Workflow For rtxpro6000

From Windows:

```powershell
ssh yunlong@166.111.73.159
```

On rtxpro6000:

```bash
cd ~/dragongong/<repo>
hostname
pwd
git status
git branch --show-current
git remote -v
```

Make code changes directly on rtxpro6000 only under `~/dragongong`.

If the repository is missing:

```bash
cd ~/dragongong
git clone git@github.com:OWNER/REPO.git
cd <repo>
```

Then, if changes should be recorded:

```bash
git add .
git commit -m "<clear commit message>"
git push origin <branch-name>
```

### Environment Setup

On the selected server:

```bash
conda info --envs
conda activate <project-env>
```

If the env does not exist:

```bash
conda create -n <project-env> python=3.10 -y
conda activate <project-env>
python -m pip install -U pip
python -m pip install -r requirements.txt
```

### Data/Cache Preparation

On the selected server:

```bash
mkdir -p data cache outputs logs checkpoints
```

Download datasets or model weights to the selected remote server only.

### Run/Debug/Test Remotely

On the selected server:

```bash
nvidia-smi
CUDA_VISIBLE_DEVICES=0 <experiment command> 2>&1 | tee logs/<experiment_name>_$(date +%Y%m%d_%H%M%S).log
```

For CPU-only tests or preprocessing, still run on the selected remote server from the project-specific conda environment:

```bash
<test-or-preprocess-command> 2>&1 | tee logs/<run_name>_$(date +%Y%m%d_%H%M%S).log
```

For long jobs:

```bash
tmux new -s <session_name>
```

## Project-Specific Defaults

### `music-crs`

Remote path on selected server:

```bash
~/dragongong/music-crs
```

Recommended env:

```bash
conda activate music-crs
```

Before running:

```bash
cd ~/dragongong/music-crs
git status
git branch --show-current
conda activate music-crs
nvidia-smi
```

### `URM`

Remote path on selected server:

```bash
~/dragongong/URM
```

Use a project-specific conda env. Do not reuse base.

### `ann`

Remote path on selected server:

```bash
~/dragongong/ann
```

Use a project-specific conda env. Do not reuse base.

## Safety Checklist Before Every Remote Run

Before running anything expensive on the selected server, verify:

```bash
hostname
pwd
git status
git branch --show-current
git rev-parse --short HEAD
which python
python --version
conda info --envs
nvidia-smi
```

Do not continue if:

- no server was selected and the user did not explicitly name one
- the current directory is not under `~/dragongong`
- the wrong branch is checked out
- the code has unexpected uncommitted changes
- the active Python is from `base` when a project env is expected
- GPU is already heavily occupied
- the command would delete or overwrite important data
- the task requires source-code edits on AMAX that have not been explicitly approved
- the task requires source-code edits outside `~/dragongong` on rtxpro6000

## Response Style

When reporting back to the user, be concise but include enough experiment metadata.

Preferred format:

```markdown
### Remote Run Summary

- Selected server: `<ganpa/AMAX | rtxpro6000>`
- Windows SSH command: `<ssh command>`
- Remote path: `~/dragongong/<repo>`
- Branch: `<branch>`
- Commit: `<hash>`
- Conda env: `<env>`
- GPU: `<gpu id or CPU>`
- Command:
  ```bash
  <command>
  ```
- Log: `logs/...`
- Output: `outputs/...`

### Result

...

### Issues

...
```

Useful commands:

```bash
git rev-parse --short HEAD
nvidia-smi
tail -n 80 logs/<log_file>.log
ls -lh outputs
```

## Core Principle Reminder

- Ask which server to use unless the user explicitly named one.
- Windows host = SSH login using the selected server's SSH command.
- ganpa / AMAX = local WSL code editing, commit/push, then remote pull and run.
- rtxpro6000 = normal login is `yunlong@166.111.73.159`; the `yunlong` account is user-specific, normal Git remotes use `git@github.com:OWNER/REPO.git`, and direct code editing is allowed only under `~/dragongong`.
- Selected remote server = prepare isolated conda env, download data, run/debug/test/evaluate project code, build caches/artifacts, collect logs.
- Do not use base conda env for experiments.
- Do not run project code locally for normal debugging or verification unless explicitly requested.
- Do not perform dangerous remote operations without explicit user approval.
- Do not ask for SSH password; direct Windows SSH is already configured.
- Do not use WSL SSH for remote login unless the user explicitly asks.
