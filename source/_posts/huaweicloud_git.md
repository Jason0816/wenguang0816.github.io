---
title: 华为云代码托管服务及团队协作教程
date: 2019-03-05 23:51:56
img: https://upload-images.jianshu.io/upload_images/14484228-d9cd99ebf0b356a4.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
summary: 在华为云实现代码托管服务以及完成团队协作开发任务
categories: 分享
tags:
  - git
  - 华为云
  - 代码托管
  - 团队协作
---
## 连接华为云仓库

### 注册账号
在华为云[官网](https://www.huaweicloud.com/?locale=zh-cn)注册账号

### 新建仓库
1. 进入项目管理
![进入项目管理](https://upload-images.jianshu.io/upload_images/14484228-ff10131724ce0407.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2. 通过左侧菜单栏进入代码托管
![代码托管](https://upload-images.jianshu.io/upload_images/14484228-bb944beaff06d6df.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
3. 根据自己的需求新建仓库
![新建仓库](https://upload-images.jianshu.io/upload_images/14484228-13625af197158062.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 连接华为仓库
1. 设置SSH密钥
![设置我的SSH密钥](https://upload-images.jianshu.io/upload_images/14484228-6d86fc7c297486f9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![添加SSH密钥](https://upload-images.jianshu.io/upload_images/14484228-9cefaa877952082b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2. 从本地获取SSH公钥
如果之前设置过github或gitee，那么系统是存在密钥的，密钥路径为`~/.ssh/id_rsa.pub`。
如果没有系统不存在密钥，那么在根目录执行以下命令创建密钥:
```bash
ssh-keygen -t rsa -C "您的email"
```
*在回车中会提示你输入一个密码，这个密码会在你提交项目时使用，如果为空的话提交项目时则不用输入，建议采用不输入密码方式。*
可以采用两种方法将密钥复制到密钥栏：
```bash
#1查看密钥并手动复制
cat ~/.ssh/id_rsa.pub
#2使用命令复制密钥到剪切板
#Windows
clip < ~/.ssh/id_rsa.pub
#Mac
pbcopy < ~/.ssh/id_rsa.pub
#Linux
xclip -sel clip < ~/.ssh/id_rsa.pub
```
接下来，我们尝试将新建的仓库克隆到本地
### 克隆仓库及常用git指令
1. 获取仓库地址
![仓库地址](https://upload-images.jianshu.io/upload_images/14484228-2a2f547bb1ef3853.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2. 在终端执行克隆指令
```bash
git clone 刚复制的地址
```
就可以将远程仓库克隆到本地了
3. 常用git指令：
```bash
#添加文件
git add filename
#添加所有文件
git add .
#确认提交
git commit -m '修改原因'
#push到远程仓库,分支可选
git push origin master
```
想学习更多，请戳廖雪峰大神[Git教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)

## 团队协作
这里介绍一下如何团队协作

### 添加成员
1. 进入项目**设置**界面
![设置](https://upload-images.jianshu.io/upload_images/14484228-3f9c2be21ab371cb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2. 在**成员管理**中添加成员，通过链接邀请
![邀请成员](https://upload-images.jianshu.io/upload_images/14484228-4286aee7a16d917d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
3. 在**待审核**界面通过审核，即可在项目成员中看到所邀请的用户，可以根据角色权限说明来自行决定项目角色。
*PS：个人仓库可以最多五个人协同开发*
4. 之后进入对应仓库的**成员**页面，添加成员即可
![添加成员到仓库](https://upload-images.jianshu.io/upload_images/14484228-4df135ee0783de63.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
*PS：被邀请成员也要设置好SSH密钥，才能克隆远程仓库*
基本内容就这些了，以后想到再补充！








