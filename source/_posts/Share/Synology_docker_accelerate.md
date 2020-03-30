---
title: 群晖Docker加速
date: 2020-03-30 11:15:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20200330-1.jpg
summary: 为群晖中的Docker进行加速
categories: 分享
tags:
  - 群晖
  - Docker
---
# 群晖Docker镜像下载失败
群晖的套件中心虽然很强大，但是套件中心并不能完全满足我们的使用需求，好在群晖支持Docker容器技术，我们可以通过Docker来实现很多新的功能，而且Docker更容易备份。

但是在使用Docker是总是镜像下载失败，尝试很多次都是如此。
![下载失败](https://gitee.com/wenguang0816/blogPic/raw/master/20200330-2.jpg)

# 镜像加速
查阅网上资料，很多网友出现的问题都是镜像下载速度满，通过配置镜像加速就可以了，本着死马当活马医，所以进行尝试。

这里，我选择了Azure的公开镜像：https://dockerhub.azk8s.cn。操作步骤如下：

打开Docker，选择`注册表——>设置`
![Docker设置](https://gitee.com/wenguang0816/blogPic/raw/master/20200330-3.jpg)

选择`Docker Hub`，然后进行编辑
![编辑存储库](https://gitee.com/wenguang0816/blogPic/raw/master/20200330-4.jpg)

在编辑注册表界面中，勾选`启用注册表镜像`，在`注册表镜像URL`中填入镜像地址，最终确认即可。
![image.png](https://gitee.com/wenguang0816/blogPic/raw/master/20200330-5.jpg)

通过这种方式，完美解决了镜像下载失败的问题，笔者本人使用了Azure的公开镜像，大家也可以尝试其他公开镜像加速地址（本人未尝试）：
> 七牛云加速器: [https://reg-mirror.qiniu.com](https://reg-mirror.qiniu.com/)
>
> 网易: [http://hub-mirror.c.163.com](http://hub-mirror.c.163.com/)
>
> 华为云: [https://05cec16ef1800f790fabc01198b68720.mirror.swr.myhuaweicloud.com](https://05cec16ef1800f790fabc01198b68720.mirror.swr.myhuaweicloud.com/)

#### 参考博客：
[群晖 NAS Docker 容器镜像加速](https://blog.holegots.com/2019/11/06/SynologyDockerSpeed/)



