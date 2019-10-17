---
title: Mac终端oh-my-zsh配置
date: 2019-10-10 15:00:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20191010-1.jpg
summary: Mac终端oh-my-zsh配置
categories: 分享
tags:
  - macOS
  - 终端美化
---

## bash到zsh
在今年金秋，苹果公司发布了macOS Catalina(10.15)，在迎来了一系列重大更新之后，macOS的默认shell也从`bash`变成了`zsh`。

*PS：新版本macOS为我们带来了随航功能，可以将iPad变成mac的另一块屏幕，不过需要注意：随航功能只适用于能够使用Apple pencil的iPad以及2016年之后发布的mac产品，笔者手里的2015款 MacBook Pro只能看着眼馋了。*

## oh-my-zsh
zsh本身功能强大，但是对于普通用户来说不太友好，但是伟大的程序猿无处不在，国外一名程序猿就开发了一款能够让大家快速上手`zsh`的项目：[oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)，借助该项目，只需要极为简单的安装配置，就可以享用`zsh`了

### 安装zsh
macOS Catalina中默认安装了`zsh`，如果你使用的macOS的其他版本并且想使用`zsh`的话，可以利用`homebrew`安装
1. 查看已安装的shell
```bash
cat /etc/shells

/bin/bash
/bin/csh
/bin/dash
/bin/ksh
/bin/sh
/bin/tcsh
```
2. 使用homebrew安装zsh
```bash
brew install zsh
```
3. 切换为zsh
```bash
chsh -s /bin/zsh
```
4. 重启终端即可使用zsh

### 安装 oh-my-zsh
打开终端执行以下命令：
```bash
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
在执行该命令时，可能会遇到以下错误：
```bash
xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun
Error: git clone of oh-my-zsh repo failed
```
可以执行以下命令之后，再执行一次安装命令(时间可能有点久T_T))：
```bash
xcode-select --install
```
当看到`oh my zsh`的标志，就代表安装成功了

## zsh配置
安装好oh-my-zsh，我们可以在`.zshrc`文件中进行自定义配置
```bash
vim ~/.zshrc
```
大家可以根据自己的使用习惯和喜好自行更改
### 主题配置
刚刚安装好的zsh可能是这样的：

![](https://gitee.com/wenguang0816/blogPic/raw/master/20191010-2.jpg)

*ps：这里的终端配色使用了`Solarized`主题，可以参见本人另一篇博客：[macOS终端、vim美化(Solarized主题)](https://blog.wenguang0816.top/2019/07/14/environment/beautify_terminal/)*

如果大家想换一个主题呢，可以前往oh-my-zsh的[官方Wiki](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes)查看主题的样式和呈现效果，然后将`.zshrc`文件中`ZSH_THEME`的值修改为对应的主题即可，我这里选择的`af-magic`:
```bash
ZSH_THEME="af-magic"
```
效果如下：
![](https://gitee.com/wenguang0816/blogPic/raw/master/20191010-3.jpg)

### 补充
从bash转换到zsh后可能导致原来配置的一些工作环境无法正常使用，这是因为`bash`的环境变量配置在了`.bash_profile`中，当使用`zsh`时，要在`.zshrc`中配置环境变量，直接将`.bash_profile`中的环境变量拷贝到`.zshrc`即可。另外zsh可以配合很多插件来提高工作效率，留给大家去探索啦！

#### 参考博客：
1. [让你的 Mac 提前用上 macOS Catalina 的 Shell——Oh My Zsh 配置指南](https://sspai.com/post/55176)
2. [Mac 终端 oh-my-zsh 配置](https://www.jianshu.com/p/64344229778a)
3. [(Mac)在bash和zsh配置环境变量path的几种方法](https://www.jianshu.com/p/020f3d02f538)







