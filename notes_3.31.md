# Git Learning Notes 3.31

## `git commit`
Save staged changes as a new commit.

Additional notes:
- `git commit` records only staged changes.
- Before committing, run `git add <file>` or `git add .`.
- Use clear commit messages, for example: `git commit -m "feat: ..."` .

## `git branch <branch-name>`
Create a new branch pointer.
- Branch early.

Additional notes:
- `git branch <branch-name>` only creates a branch; it does not switch to it.
- A branch is a movable pointer to commits, usually created from your current `HEAD`.
- List local branches with `git branch`.

## `git checkout <name>`
- Switch to an existing branch named `<name>`.
- `git checkout -b <your-branch-name>`
  - Create a new branch and check it out at the same time.

Additional notes:
- `git switch` is now preferred for branch switching because it is clearer.
- `git checkout` is more general and can also restore files.

## `git switch`
- Switch to another branch.
- `git switch -c <new-branch-name>` creates and switches to a new branch.

Additional notes:
- `git switch` does not merge anything; it only changes your current branch.
- To bring feature branch changes into `main`, use `git merge` or `git rebase`.

## `git merge <your-branch-name>`
- Create a merge commit that has two parent commits.
- Merge `your-branch-name` into the current branch (often `main`).

Additional notes:
- Switch to the target branch first, then merge. Example:
  1. `git switch main`
  2. `git merge feature/login`
- If there are no conflicts, merge completes automatically. If conflicts appear, resolve them and commit.

## `git rebase <your-branch-name>`
- Replay commits on top of another base commit.

Additional notes:
- A common workflow is running `git rebase main` on your feature branch to replay commits on top of the latest `main`.
- Rebase rewrites commit history, so be careful if commits were already pushed to a shared branch.
- The main benefit is a cleaner, more linear history.

## Simple Push Workflow

| Command | Purpose | Frequency |
| --- | --- | --- |
| `git init` | Initialize a repository | One-time |
| `git remote add origin <url>` | Connect a remote repository | One-time |
| `git branch -M main` | Set the default branch name | One-time |
| `git push -u origin main` | First push and set upstream branch | One-time |
| `git add .` | Stage changes | Every time |
| `git commit -m "..."` | Create a commit | Every time |
| `git push` | Push commits to remote | Every time |

Additional notes:
- The most common daily flow is: `add -> commit -> push`.
- `-u` sets the upstream branch, so later you can run `git push` / `git pull` directly.
- Prefer small, focused commits with messages that explain what changed and why.
- git pull --no-rebase origin main --allow-unrelated-histories
  - ### 如有冲突先解决并提交
  - git push -u origin main



| VS Code 图形操作 | 对应 Git 命令 | 作用 |
|---|---|---|
| 打开 `Source Control` 看变更 | `git status` | 查看当前改动状态 |
| 点文件旁 `+`（Stage） | `git add <file>` | 暂存某个文件 |
| 点 `Stage All Changes` | `git add .` | 暂存全部改动 |
| 输入消息后点 `Commit` | `git commit -m "message"` | 提交暂存内容 |
| 点 `Push` | `git push` | 推送到远程仓库 |
| 点 `Pull` | `git pull` | 拉取远程更新 |
| 点 `Sync Changes` | `git pull` + `git push` | 先拉后推 |
| 左下角点分支名切换 | `git switch <branch>` | 切换分支 |
| 创建新分支 | `git switch -c <new-branch>` | 新建并切换 |
| 合并分支（UI 菜单） | `git merge <branch>` | 把某分支合并到当前分支 |

你接下来就按这个思路：**先用 GUI，卡住就看右边命令对应**。