---
title: Git.md
date: 2020-08-31 16:09:55
tags: git代码
---

#Git
###版本控制软件
集中化版本控制：svn
分布式版本控制系统：git

###分布式版本特点
联网运行，支持多人协作，性能优秀，用户体验良好
###分布式原理
客户端也是服务器的完整备份
支持断网本地提交
服务器故障或损坏后，可使用任何一个客户端进行恢复

##svn和git比较

###SVN特点
**差异比较**
记录文件的变化 差异
优点：节省磁盘空间
缺点：耗时、效率低

###Git特点
**记录快照**
1.直接记录快照，而非差异比较
2.近乎所有操作都是本地执行

Git快照是在原有文件版本的基础上重新生成一份新的文件，类似于备份，如果没有修改，直接保留一个链接指向之前存储的文件。
缺点：占用磁盘较大
优点：版本切换非常快、以空间换时间


###Git中的三个区域
工作区  暂存区  版本库

###Git中的三个状态
已修改 modified
已暂存 staged
已提交 committed

##Git代码

###常用代码

查看config命令
`git help config`
在终端内查看帮助手册
`git config -h`
在现有目录初始化仓库
`git init`
添加文件到暂存区
`git add +文件名`
查看文件状态
`git status (-s)`
提交到本地仓库
`git commit -m +提交提示`
显示提交的所有记录
`git log`
###其他代码
撤销所有修改 (危险度较高 不建议使用)
`git checkout +文件名`
从暂存区中移除对应的文件
`git reset HEAD +文件名`
跳过暂存区 直接提交到git仓库
`git commit -a -m +提示 也可以-am`
同时移除工作区和仓库
`git rm -f+文件名`
只移除仓库区但保留工作区文件
`git rm --cached +文件名`
展示仓库的所有提交状态
`git log`
查询提交项目历史简写
`git reflog`
回退到某个版本 commitID是log中唯一标识
`git reset --hard commitID`


###需要忽略的文件 无需纳入git管理
添加到.gitignore文件中 =简化版正则 
gitignore代码格式
```js
//忽略所有.a文件
*.a //*零个或多个任意字符
//跟踪所有lib.a 即使在前面忽略了.a文件 ！取反
!lib.a
//只忽略当前目录下的TODO文件，不忽略子目录下的TODO
/TODO //斜线不递归的意思
//忽略任何目录下名为build的文件夹
build/
//忽略doc/notes.txt但不忽略doc/server/arch.txt
doc/*.txt
//忽略doc/目录及其所有子目录下的.pdf文件 
//**表示匹配任意中间目录 doc文件夹内的所有叫*.pdf的文件
doc/**/*.pdf
```

##git远程
###代码
查看分支列表
`git branch`
创建新分支(只创建不切换)
`git  branch +分支名称`
切换分支开发 切换之前一定要提交add和commit
`git checkout +分支名称`
分支的快速创建和切换(既创建也切换)
`git checkout -b +分支名称`
合并到主分支 将子分支代码复制到主分支
`git checkout master`
`git merge login`
删除分支
`git branch -d +分支名称`
强制删除分支
`git branch -D +分支名称`
修改分支名
`git branch -m 原分支名 新分支名`
将本地分支推送到远程仓库(第一次推送需要加-u 以后的推送不需要加) 仓库里的分支
`git push -u 远程仓库别名 本地分支名称:远程分支名称`
`git push -u origin payment：pay `
查看本地分支
`git branch`
查看远程分支
`git branch -r`
查看所有分支
`git branch -a`
拉取远程最新代码 pull之前一定要先将自己代码复制一遍，防止被覆盖
`git pull`
删除远程分支
`git push 远程仓库名称 --delete 远程分支名称`
`git push origin --delete pay`
从远程仓库中将对应的远程分支下载到本地仓库
`git checkout 远程分支的名称`
从远程仓库中将对应的远程分支下载到本地仓库 并且重命名
`git checkout -b 本地分支名称 远程仓库名称/远程分支的名称`
示例：
`git checkout -b payment origin/pay`

