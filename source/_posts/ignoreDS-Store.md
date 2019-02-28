---
title: macOS下忽略.DS_Store文件
date: 2019-02-26 18:58:56
summary: macOS平台使用git时全局忽略.DS_Store文件
categories: 分享
tags:
  - git
  - 全局忽略
---
# macOS下忽略.DS_Store文件
在macOS平台下会自动生成`.DS_Store`文件，在使用git提交的过程中，会发现git将`.DS_Store`文件一并提交了，这是我们不需要的。我们可以在项目中新建一个`.gitignore`文件，将`.DS_Store`添加进去，但是这种方式只对当前项目有效，新建项目之后仍会出现上述问题，所以这里介绍全局忽略`.DS_Store`的方法。
1. 在`home`目录下新建`.gitignore_global`文件，文件内容如下
```bash
# .gitignore_global
.DS_Store
.DS_Store?
```
2. 编辑在`home`目录下的`.gitconfig`文件，使其引入`.gitignore_global`的设置。`.gitconfig`的内容如下：
```bash
[user]
	name = yourname
	email = yourname@github.com
[core]
	excludesfile = /Users/yourname/.gitignore_global
```
*home路径中的yourname和自己的对应*

3. 如果项目中已经出现了`.DS_Store`文件并且已经提交了，我们需要将`.DS_Store`文件删除，并再次提交。
+ 删除项目中的所有.DS_Store。这会跳过不在项目中的 .DS_Store
```bash
find . -name .DS_Store -print0 | xargs -0 git rm -f --ignore-unmatch
```
+ 更新项目
```bash
git add --all
git commit -m '.DS_Store banished!'
```
4. 当然也可以在终端通过修改系统设置来禁止生成`.DS_Store`（*不推荐此做法*）。
+ 禁止`.DS_Store`生成：
```bash
defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool TRUE
```
+ 恢复`.DS_Store`生成
```bash
defaults delete com.apple.desktopservices DSDontWriteNetworkStores
```
参考博客：

1. [简书-iOSReverse-如何删除GIT中的.DS_Store](https://www.jianshu.com/p/fdaa8be7f6c3)

2. [个人博客-aoenian](https://aoenian.github.io/2018/12/19/git-ignore-config/)
