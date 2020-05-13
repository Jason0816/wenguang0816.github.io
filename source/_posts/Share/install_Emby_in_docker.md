---
title: 群晖docker安装Emby并开启硬件解码
date: 2020-05-06 22:00:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20200506-1.jpg
summary: 群晖docker安装Emby并开启硬件解码
categories: 分享
tags:
  - 群晖
---

最近在群晖中安装了Emby，使用体验很不错，现在将自己的安装过程分享出来
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200506-1.jpg)
目前群晖中安装emby主要有两种方式，一是通过在套件中心中添加源来安装，二是通过docker来安装。我选择的是通过docker进行安装，虽然过程稍微有些复杂，但是备份迁移都要比群晖套件有优势。
硬件解码可以让显卡接过视频解码转码的重任，为CPU分担压力，不过有部分机器不支持硬件解码，群晖支持硬件解码的必要条件是：
+ 群晖系统为DS 918+
+ CPU支持硬件解码

通过ssh连接到群晖，输入`ls /dev/dri`，如果和下图一样，那么恭喜你，你可以开启硬件解码
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200506-2.jpg)

需要说明的是，emby开启硬件加速功能是需要会员的，当然也有免费的替代品——Jellyfin，Jellyfin是emby的一个分支，拥有emby的大部分功能，大家可以自行选择。

### 在docker中安装emby
#### 下载emby镜像
在docker注册表中搜索emby，选择`emby/embyserver`下载
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200506-3.jpg)

#### 启动硬件加速
1. 下载完映像之后，不要直接启动，开启群晖的SSH，打开控制面板，在终端机开启
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200506-4.jpg)

2. 通过ssh工具登录到群晖，输入`sudo -i`切换到`root`账户，会要求输入密码
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200506-5.jpg)
3. 输入以下代码启动emby容器
```bash
docker run \
    --name=emby \ # 容器名称
    --device=/dev/dri:/dev/dri \ #开启硬件解码
    --net host \ # 配置网络
    emby/embyserver # 要运行的映像名称
```
这里通过`--net host`是该容器使用`docker host`网络，即与docker主机网络相同。目的是解决emby无法刮削元数据的问题，因为emby使用`theMovieDb`进行刮削，详情可见[解决tinyMediaManager无法刮削的问题](https://www.jianshu.com/p/5ca8f1c04926)。这样只要在修改群晖`hosts`文件，便可以解决emby无法刮削的问题。不过建议直接使用tMM进行刮削，tMM也可以通过docker安装了——[群晖Docker安装tinyMediaManager并解决无法刮削的问题](https://www.jianshu.com/p/1f09ad93a9f0)

4. 此时可以在群晖docker容器中看到正在运行的emby容器，将容器关闭并进行以下配置
+ 添加卷
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200506-6.jpg)
+ 修改`UID`和`GID`
![](https://gitee.com/wenguang0816/blogPic/raw/master/20200506-7.jpg)
5. 应用并开启emby容器，在浏览器中输入IP+8096就可以进入emby了


怎么使用emby就交给大家去探索了！

#### 参考博客：
1. [打造低功耗家庭影音NAS：i3-8100更换 华擎J5005ITX 群晖下Jellyfin硬解！](https://post.smzdm.com/p/akmgnkdk/)
2. [docker 网络-host](https://www.jianshu.com/p/1dd65ab5b997)








