# Git Learning Notes 3.31


## `git commit` 
 save delta or changes 

## `git branch <branch name>`
point to new branch
-branch early

## `git checkout <name>`
- put us on the new branch before commit
- `git checkout -b [yourbranchname]`
    - create a new branch AND check it out at the same time
## `git swich`
-merge the end of branch to main

## `git merge <yourbranchname>`
- creates a special commit that has two unique parents

## `git rebase`


## push简单理解：
命令 作用 频率
git init 初始化仓库 一次
git remote add origin ...绑定远程仓库 一次
git branch -M main设置主分支名 一次
git push -u origin main首次推送并绑定分支 一次

git add .暂存改动 每次
git commit -m "..."提交 每次
git push推送 每次
