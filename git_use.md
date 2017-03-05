### 1.git init
初始化仓库。

### 2.git add [file]/git commit [-a] [-m "message"]
添加文件到暂存区/提交文件到仓库。

### 3.git branch [new_branch]/git checkout -b [new_branch]
新建分支/新建并切换分支。

### 4.git checkout [file/branch]
检出恢复文件/分支。

### 5.git tag [tag_name] [hash_id]
使用最近一次提交[或特定hash_id]创建标签。

### 6.git mv/rm [file]
在仓库中移动/重命名/删除文件。

### 7.git fetch origin master
取回远程分支（但不合并）。然后git merge origin/master，进行合并。

### 8.git merge [source_branch]
将来源分支与现处分支合并。

### 9.git diff
git diff: 显示工作区与暂存区的区别。
git diff [...]: 显示工作区与[...]的区别
git diff [..1] [..2]: 显示[..1]与[..2]的区别

### 10.git reset [--hard/--mixed/--soft] [hash_id]
重置为特定版本。
hard: 暂存区stage清空，工作区清空（即改动清空）。
mixed(默认): 暂存区stage清空，工作区不清空（即改动没有git add）。
soft： 暂存区stage不清空，工作区不清空（即改动已经git add，但没有git commit）。

---------------------------------------------------------
## 远程操作

### 1.git clone [repository]
克隆仓库。

### 2.git pull [origin] [remote_branch]:[local_branch]
拉取远程分支,与本地分支合并。

### 3.git push [origin] [local_branch]:[remote_branch]
推送本地分支,与远程分支合并。

### 4.git remote add [origin] [repository]
为本地仓库添加远程仓库。

---------------------------------------------------------
## 显示操作
### 1.git show [objects]
显示对象。
### 2.git status
显示工作区状态。
### 3.git log/reflog
显示现在仓库的日志/历史日志（可用来在reset之后恢复）。
### 4.git remote [-v]
显示远程仓库。
### 5.git branch [-v/-a/-r]
现示分支。
