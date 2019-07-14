---
title: macOS终端、vim美化(Solarized主题)
date: 2019-07-14 13:44:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20190714-3.jpg
summary: 利用Solarized主题对mac终端进行优化
categories: 分享
tags:
  - macOS
  - 终端美化
---

## 优化原因
macOS自带的终端一开始是不好看的（个人向），黑底白字。在操作的时候不美观也不高效，就像下面这样：
![](https://gitee.com/wenguang0816/blogPic/raw/master/20190714-1.jpg)
所以本着好看的原则，对macOS的终端进行一波优化。优化后的效果见图：
![](https://gitee.com/wenguang0816/blogPic/raw/master/20190714-2.jpg)

## 优化方法
这里优化用到的是Solarized主题[GitHub](https://github.com/altercation/solarized)。Solarized是目前最完整的 Terminal/Editor/IDE 配色项目，几乎覆盖所有主流操作系统（Mac OS X, Linux, Windows）、编辑器和 IDE（Vim, Emacs, Xcode, TextMate, NetBeans, Visual Studio 等），终端（iTerm2, Terminal.app, Putty 等）。让我们看一下Solarized主题在mac终端上的效果，主题氛围Dark和Light两种。
![](https://gitee.com/wenguang0816/blogPic/raw/master/20190714-3.jpg)

### 主题安装
1. 主题可以通过两种方式获取
+ 从[GitHub](https://github.com/altercation/solarized)仓库中的`release`中下载作者发布的压缩包
+ 通过终端克隆仓库的方式进行获取
    ```bash
    # 在终端输入
    git clone git://github.com/altercation/solarized.git
    ```
2. 下载好主题后，从下载的文件中找到`osx-terminal.app-colors-solarized`文件夹，文件内容如图所示：
![](https://gitee.com/wenguang0816/blogPic/raw/master/20190714-4.jpg)
文件中有Dark和Light两种主题，读者可以根据上文中的效果图选择安装（双击即可）。*在安装中可能会遇到安全提示，在`系统偏好设置\安全性与隐私`中允许即可。*
3. 打开终端，进入`偏好设置`便可以在`描述文件`中看到新安装的主题了，将新安装的主题设置为**默认**。并在`通用`设置为启动时打开刚才设置为默认的描述文件。
![](https://gitee.com/wenguang0816/blogPic/raw/master/20190714-5.jpg)
![](https://gitee.com/wenguang0816/blogPic/raw/master/20190714-6.jpg)
现在主题就安装好了。

### vim配置
1. 将Solarized主题的vim文件拷贝到系统的vim目录
    ```bash
    cd solarized
    cd vim-colors-solarized/colors
    mkdir -p ~/.vim/colors
    cp solarized.vim ~/.vim/colors/
    ```
2. 修改vim设置:`vim ~/.vimrc`，在该文件中添加一下内容
    ```bash
    syntax on
    set background=dark # 背景为dark，也可选light
    colorscheme solarized
    ```
修改后如图所示：（版本不同，效果可能有所不同）
![](https://gitee.com/wenguang0816/blogPic/raw/master/20190714-7.jpg)

### 高亮
安装Solarized主题后，终端中执行`ls`等命令时，文件都是同一个颜色，没有高亮，可以在`.bash_profile`中添加一下设置
```bash
# vim ~/.bash_profile
export GREP_OPTIONS='--color=auto'
export TERM="xterm-color"
PS1='\[\e[0;33m\]\u\[\e[0m\]@\[\e[0;32m\]\h\[\e[0m\]:\[\e[0;34m\]\w\[\e[0m\]\$ '
```
设置后如图所示：
![](https://gitee.com/wenguang0816/blogPic/raw/master/20190714-8.jpg)


