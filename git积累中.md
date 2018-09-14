


## git stash（暂存）
+ 暂存当前工作区和缓存区的内容
``` shell
git stash
```

+ 取回某个暂存编号的内容，恢复到工作空间和缓存区
``` shell
git stash pop
```

## git reset（重置）
+ 只重置本地仓库的内容
``` shell
git reset --soft [<commitId>]
```

+ 默认是这种情况，重置本地仓库和缓存区的内容
``` shell
git rest --mixed [<commitId>]
```

+ 重置本地仓库、缓存区以及工作空间的内容
``` shell
git rest --hard [<commitId>]
```

## git checkout（检出：功能较杂）
+ 切换分支
``` shell
git checkout <branchName>
```

+ 新建分支
``` shell
git checkout -b <branchName>
##等价如下两条命令
##1. git branch newBranch 
##2. git checkout newBranch
```

+ 强制新建分支
``` shell
git checkout -B <branchName>
```

+ 选择一个提交记录为起点去创建新分支
``` shell
git checkout -b <new_branch> [<start_point>]
```
## git diff（比较差异）
+ 比较工作区和暂存区
``` shell
git diff
```
+ 比较暂存区与最新本地版本库（本地库中最近一次commit的内容）
``` shell
git diff --cached  [<path>...] 
```

+ 比较工作区与最新本地版本库
``` shell
git diff HEAD [<path>...] 
##如果HEAD指向的是master分支，那么HEAD还可以换成master
```
+ 比较工作区与指定commit-id的差异
``` shell
git diff commit-id  [<path>...] 
```
+ 比较暂存区与指定commit-id的差异
``` shell
　　　　　　git diff --cached [<commit-id>] [<path>...] 
```
+ 比较两个commit-id之间的差异
``` shell
git diff [<commit-id>] [<commit-id>]
```

## git cherry-pick/rebase(自定义合并)
+ 只挑选某几条提交记录合并到该分支
``` shell
git cherry-pick <commitId1> [<commitId12>] ...
```
+ 将A分支所有新提交的内容以B分支为基准合并
``` shell
git rebase B
##前提是当前在A分支上
```

+ 仅将A分支某个提交号以后的内容以B分支为基准合并
``` shell
git rebase --onto B <commitId>
##前提是当前在A分支上
```

## git rm（git常用的删除）
+ 删除暂存区或分支上的文件,同时工作区也不需要这个文件了
``` shell
git rm file_path
git commit -m 'delete somefile'
```

+ 删除暂存区或分支上的文件, 但本地又需要使用, 只是不希望这个文件被版本控制
``` shell
git rm --cached file_path
git commit -m 'delete remote somefile'
```

## 强制操作
+ 强制将分支指向某一提交记录）
``` shell
git branch -f <branchName> <commitId>
```

+ 更改某一次提交的内容
``` shell
git commit --amend [<commitId>]
```

+ 强制推送本地的版本覆盖远程分支的内容
``` shell
git push -f 
```

## 常用查看技巧
+ 更为紧凑的git status
``` shell
git status -s
```

+ 带差异的显示最近两条提交记录
``` shell
git log -p -2
```

+ 将每个提交放在一行显示
``` shell
git log --pretty=oneline 
```
+ git log --pretty=format 常用的选项：
``` shell
git log --pretty=format:"%h - %an, %ar : %s
```
```
选项|说明
-|-|-
%H|提交对象（commit）的完整哈希字串 
%h|提交对象的简短哈希字串 
%T|树对象（tree）的完整哈希字串 
%t|树对象的简短哈希字串 
%P|父对象（parent）的完整哈希字串 
%p|父对象的简短哈希字串 
%an|作者（author）的名字 
%ae|作者的电子邮件地址 
%ad|作者修订日期（可以用 --date= 选项定制格式） 
%ar|作者修订日期，按多久以前的方式显示 
%cn|提交者(committer)的名字 
%ce|提交者的电子邮件地址 
%cd|提交日期 
%cr|提交日期，按多久以前的方式显示 
%s|提交说明 
```