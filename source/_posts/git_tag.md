---
title: git分支(branch)和标签(tag)操作
date: 2019-04-01 10:50:00
img: https://upload-images.jianshu.io/upload_images/14484228-41398eed6fdb4297.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
summary: 汇总git中branch和tag的常用命令，更好的进行版本管理
categories: 分享
tags:
  - git
  - branch & tag
---
## 分支相关操作
1. 查看分支
```bash
git branch
```
2. 创建分支
```bash
git branch <name>
```
3. 切换分支
```bash
git checkout <name>
```
4. 创建+切换分支
```bash
git checkout -b <name>
```
5. 合并某分支到当前分支
```bash
git merge <name>
```
6. 删除本地分支
```bash
git branch -d <name>
```
7. 删除远程分支
```bash
git branch -f -d origin/<name>
git branch origin :<name>
```

## 标签相关操作
1. 新建标签
```bash
git tag <tagname>
```
2. 新建带有信息的标签
```bash
git tag -a <tagname> -m 'label'
```
3. 查看所有标签
```bash
git tag
```
4. 删除本地标签
```bash
git tag -d <tagname>
```
5. 删除远程标签
```bash
git push origin :refs/tags/<tagname>
```
