---
layout: post
title: "Git常用命令"
description: "Git常用命令"
categories: [blog]
tags: [博客,git,常用,命令]
redirect_from:
  - /2018/04/24/
---
# 常用功能命令

```
git --version   //查看git的版本信息
git config --global user.name   //获取当前登录的用户
git config --global user.email  //获取当前登录用户的邮箱
git add .  //添加所有文件
git add -A      //全部添加到缓存区
git status //显示目录的状体 有没有添加或者修改文件
git config --global user.name 'userName'    //设置git账户，userName为你的git账号，
git config --global user.email 'email'
touch .gitignore    //不需要服务器端提交的内容可以写到忽略文件里
git log --oneline   //查看版本
git diff   //比较的是暂存区和工作区的差异
git diff --cached  //比较的是暂存区和历史区的差异 
git diff master //比较的是历史区和工作区的差异（修改）
git checkout index.html //用暂存区中的内容或者版本库中的内容覆盖掉工作区
git reset HEAD index.html //取消增加到暂存区的内容（添加时）
git rm index.html --cached //删除暂存区(保证当前工作区中没有index.html,使用--cached 表示只删除缓存区中的内容)
git reset --hard HEAD/commit_id //回滚最近的一个版本 git log
git reflog  //回滚到未来
```
分支功能:
```
git branch dev //创建分支
git checkout dev //切换分支
git checkout -b dev //创建分支并切换分支
git branch -d dev //删除分支
git commit -a -m 'dev1' //在分支上提交新的版本
git merge dev //合并分支
git log --oneline --graph --decorate //分支的合并后显示log

```
在分支开发的过程中遇到其他问题需要切换其他分支  
保留写好的内容在切换到主干  

```
git stash //保留内容
git stash apply //在次切换分之后需要应用一下保留的内容
git stash drop //丢掉保存的内容
git stash pop //使用并丢掉

```
最佳分支  
有的时候开发需要合并指定的内容，而不是合并所有的提交，所以我们需要挑选最好的，自己生产版本

```
git rebase  //合并分支把树杈掰到主干上
```
添加远程的仓库  
```
git push origin master -u   //获取最新代码
git remote add origin 仓库的地址 //连接远程仓库
git remote -v //查看远程仓库
git remote rm origin //删除远程仓库
```
与添加有关的：
```
将当前目录变为仓库：git init  
将文件添加到暂存区：git add 文件名 [可选：另一个文件名]  
将暂存区提交到仓库：git commit –m "描述"
```
与查询有关的：
```
查询仓库状态：git status
比较文件差异（请在git add之前使用）：git diff 文件名
查看仓库历史记录(详细)：git log
查看仓库历史记录(单行)：git log --pretty=online 或 git log --online
查看所有版本的commit ID：git reflog
```
与撤销有关的：
```
撤销工作区的修改：git checkout -- 文件名
撤销暂存区的修改：git reset HEAD 文件名
回退到历史版本：git reset --hard 该版本ID
回退到上个版本：git reset --hard HEAD^
上上版本是HEAD^^，也可用HEAD~2表示，以此类推
```

与标签有关的：
```
为当前版本打标签：git tag 标签名
为历史版本打标签：git tag 标签名 该版本ID
指定标签说明：git tag –a 标签名 –m "标签说明" [可选：版本ID]
查看所有标签：git tag
查看某一标签：git show 标签名
删除某一标签：git tag –d 标签名
```

与GitHub有关的：
```
先有本地库，后有远程库，将本地库push到远程库

关联本地仓库和GitHub库：git remote add origin 网站上的仓库地址
第一次将本地仓库推送到GitHub上：git push –u origin master

先有远程库，后有本地库，从远程库clone到本地库

从远程库克隆到本地：git clone 网站上的仓库地址

网站地址可以选择HTTPS协议（https://github.com...）、SSH协议（git@github.com...）。
如果选择SSH协议，必须将Ubuntu的公钥添加到GitHub上。见下一步
SSH Key

生成SSH Key：ssh-keygen –t rsa –C "你的邮箱@xx.com"
生成Key时弹出选项，回车选择默认即可。
Key保存位置：/root/.ssh
登陆GitHub，创建new SSH key，其内容为/root/.ssh/id_rsa.pub中文本

已经有了本地库和远程库，二者实现同步

本地库的改动提交到远程库：git push origin master
更新本地库至远程库的最新改动：git pull
```

