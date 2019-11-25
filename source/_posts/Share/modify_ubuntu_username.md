---
title: 修改ubuntu用户名
date: 2019-11-25 19:06:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20191125-1.jpg
summary: 通过命令行修改ubuntu的用户名
categories: 分享
tags:
  - ubuntu
  - 命令行
  - 用户名
---
### 起因
从腾讯云申请的云服务器(ubuntu系统)的默认用户名为`ubuntu`，一般来说可以也接受，但是作为自己要使用的机器还是要有点个性化。通过网上的帖子，摸索了半天才修改完成，现在将自己的经验分享给大家。

### 切换到root账户
因为修改普通账户的用户名，所以建议切换到`root`用户，这样可以避免一些权限的问题和其他不必要的影响。新申请或安装的机器`root`用户是没有密码的，所以可以先为`root`账户设置密码：
```bash
# 如果设置了密码可跳过此步
ubuntu@VM-0-4-ubuntu:~$ sudo passwd root
# 为用户修改密码也可以使用此命令
```
然后切换到`root`用户(需要输入密码）：
```bash
ubuntu@VM-0-4-ubuntu:~$ su root
Password:
root@VM-0-4-ubuntu:/home/ubuntu#
```

### 修改用户名
修改用户名我们需要进行四步操作：

#### 1.修改`/etc/passwd`文件: `vim /etc/passwd`
    ```bash
    ubuntu:x:500:500::/home/ubuntu:/bin/bash
    # 把用户名ubuntu改成：你想要的用户名，其他都不要修改
    test:x:500:500::/home/test:/bin/bash
    # 打开文件后回发现很多内容，可以利用替换指令进行修改
    # :1,$s/ubuntu/test/g
    # 解释: 替换第 1 行开始到最后一行中每一行所有 ubuntu 为 test
    ```
最后输入`:wq!`保存退出

*ps：这里网上有帖子说用`gedit`进行修改，不过在新申请或安装的机器中是没有`gedit`的，所以可以使用`vim/vi`来代替*

#### 2.修改`/etc/shadow`文件: `vim /etc/shadow`
```bash
ubunt:$6$ULolz...EMVYj/:18222:0:99999:7:::
# 把用户名ubuntu改成：你想要的用户名，其他都不要修改
test:$6$ULolz...EMVYj/:18222:0:99999:7:::
```

#### 3.修改`/etc/group`文件: `vim /etc/group`
```bash
ubunt:x:1:root,bin,ubuntu
#...
# 这个文件中的原用户名有很多，可以使用第一步中提到的替换指令修改:
:1,$s/ubuntu/test/g
```

#### 4.修改用户目录
```bash
mv /home/ubuntu /home/test
```
此时，我们就可以更改万用户名了，可以切换到新的用户名测试一下：
```bash
root@VM-0-4-ubuntu:~$ su test
test@VM-0-4-ubuntu:~$
```

#### 参考博客
[CSDN: Ubuntu 修改用户名-OneDay-X](https://blog.csdn.net/zhaokx3/article/details/64127454)








