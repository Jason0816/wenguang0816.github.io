---
title: 解决tinyMediaManager无法刮削的问题
date: 2020-04-13 21:25:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20200413-1.jpg
summary: tinyMediaManager域名被ban
categories: 分享
tags:
  - 群晖
---
# 起因
在看了阿文菌的帖子[手把手教您用tMM刮削影片信息，让KODI、Jellyfin、PLEX、使用本地媒体电影墙！](https://post.smzdm.com/p/a4wkqw37/)后开始使用tinyMediaManager代替emby原始的刮削工具，但是在换了电脑之后发现tinyMediaManager无法使用了。
> 报错信息：java.net.SocketTimeoutException:connect timed out

![](https://gitee.com/wenguang0816/blogPic/raw/master/20200413-2.jpg)

起初以为是java环境的问题，重装了几次无果，后来才知道是该工具的域名被ban了，需要科学上网。

其实不需要科学上网，也可以解决网络问题，需要我们人为去修改客户端的`hosts`文件，将tMM所使用的域名映射到没有被ban的IP地址上。

# 解决方法

## windows上修改`hosts`文件
1. 打开`C:\WINDOWS\system32\drivers\etc`路径
2. 找到`hosts`文件并复制到桌面上
3. 用记事本打开`hosts`文件，在最后一行添加以下内容后保存
  ```bash
  13.224.161.90   api.themoviedb.org
  ```
4. 将`hosts`复制到`C:\WINDOWS\system32\drivers\etc`路径并覆盖

## mac上修改`hosts`文件的方法
1. 打开终端，切换到`root`账户
  ```bash
  sudo -i
  # 会提示输入密码，输入即可
  ```
2. 修改`hosts`文件
  ```bash
  vim /etc/hosts
  ```
3. 按下`i`键进入编辑模式，在最后一行添加以下内容
  ```bash
  13.224.161.90   api.themoviedb.org
  ```
4. 按下`Esc`退出编辑模式，并输入`:wq`保存退出

现在，就可以正常使用tMM进行刮削了

#### 参考博客：
[群晖Docker里安装TinyMediaManager并开启中文支持(完美解决)](http://www.gebi1.com/thread-295644-1-1.html)



