---
title: 群晖安装Aria2和AriaNg
date: 2020-05-13 22:00:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20200513-14.jpg
summary: 利用群晖docker安装Aria2和AriaNg
categories: 分享
tags:
  - 群晖
---

最近在群晖上安装了Emby来做影音服务器，那么就需要通过下载获取影音资源，PT下载用的Transmission，BT下载对比之后发现还是用Aria2比较好，配合AriaNg的UI界面，使用起来还是很不错的

#### 安装Aria2
1. 打开群晖docker，搜索aria2，这里我们选择`p3terx/aria2-pro`映像下载，这个映像虽然没有集成webui，但是对Aria2的配置进行了很多优化。相对于其他的捆绑包来说，更简洁实用。关于这个映像的更多介绍，可以去大佬的[博客](https://p3terx.com/archives/docker-aria2-pro.html)查看
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200513-1.jpg)
2. 在下载的过程中，我们可以去创建一个文件夹用于存放aira2的配置，文件夹位置看个人习惯。下载完成后，我们启动映像，点击高级设置
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200513-2.jpg)
+ 设置自动重启
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200513-3.jpg)
+ 映射文件夹：下载目录`/downloads`，配置目录`/config`
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200513-4.jpg)
+ 进行端口设置，容器端口不可更改，本地端口自行设置
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200513-5.jpg)

+ 添加环境变量，在环境变量中添加红框中的五个变量，其中`RPC_SECRET`是Aira2的连接密钥，这里以`123456`为例
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200513-6.jpg)
+ 最后点击应用启动容器，在docker容器中便可以看到启动后的Aria2了

#### 安装AriaNg
前面说过，这个映像是没有WebUI的，所以需要配合WebUI或者APP进行使用，我们这里选择AriaNg，AriaNg是一个 Aria2 的 Web 前端，你可以在Github项目的 [releases](https://github.com/mayswind/AriaNg/releases) 页面下载
1. 群晖安装Web Station套件，可以直接在套件中心直接下载安装，安装之后，会增加一个`web`的共享文件夹，将我们下载好的AriaNg文件上传到该共享文件夹
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200513-7.jpg)
2. 打开Web Station套件，点击`虚拟主机`中的`新增`按钮
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200513-8.jpg)
3. 对web站点进行设置，我们选择`基于端口`，选择`HTTP`，端口号自选。`文档根目录`选择我们刚才上传的AiraNg文件目录，选择后端服务器和PHP，确定即可。
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200513-9.jpg)
4. 在浏览器输入`群晖IP`+`HTTP端口号`，我这里是192.168.148.12:10086，便可以打开AiraNg界面了，将界面语言设置为中文，可以看到Aira2状态显示未连接
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200513-10.jpg)
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200513-11.jpg)

#### AiraNg连接Aria2
1. 按照步骤依次填入IP、端口和之前设置的密钥
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200513-12.jpg)
2. 刷新之后便可以看到Aira2已经连接了
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200513-13.jpg)
3. 接下来，我们下载一个种子（[ubuntu19.10](http://releases.ubuntu.com/19.10/ubuntu-19.10-desktop-amd64.iso.torrent)）并添加测试，可以看到速度还可以
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200513-14.jpg)


现在我们就可以愉快的利用Aria2进行下载了