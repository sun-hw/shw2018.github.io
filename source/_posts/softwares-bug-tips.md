---
title: 常用软件bug调试与使用tips
date: 2019-08-12 16:42:05
top: true
cover: true
img: /medias/banner/4.jpg
coverImg: /medias/banner/7.jpg
password:
toc: true
mathjax: false
summary: 
tags:
- Softwares
- Bugs
- 常用软件
- Tips
categories:
- 软件安装与配置
---


# Ubuntu18.04 安装 Visual Studio Code出现问题的解决
---
## 一、前述

关于ubuntu安装Visual Studio Code这里不在说明。这里记录两点自己安装过程中遇到的问题。
## 二、umake安装出现问题解决
```
usage: umake web [-h] {firefox-dev,phantomjs} ...
umake web: error: argument framework: invalid choice: 'visual-studio-code' 
```

安装不是用web进行安装的，网上好多教程都是使用这种方式，只要修改为ide即可：
```
sudo umake ide visual-studio-code
```
## 三、安装完成后打不开vscode或者说打开闪退问题解决

```bash
cd ~/.config 
sudo rm -rf ./Code/ 
```
vscode的配置文件被root用户加上了权限，把权限去除即可。

## 四、vscode安装插件出现

安装插件时，发现点击“install”,右下角会提示“failed to install”，这是因为vscode的扩展文件夹没有用户权限，命令行中添加如下代码即可：
```bash
sudo chown -R 你的用户名 ~/.vscode/extensions
```

目前就遇到两个问题，有其他问题在陆续更新。。。


# linux下安装nodejs并配置全局变量
---
**linux：**命令行安装：
```bash
sudo apt-get install nodejs
sudo apt-get install npm
```
不过不推荐命令行安装，有时候有问题，建议直接到官网去下载编译好的压缩文件，如下所示:![](1.png)，然后解压到你指定的文件夹即可，比如我解压到我系统的`/home/shw/MySoftwares`目录下了，如图:![](2.png)
> 注意本压缩包是`.tar.xz`格式的，需要两次解压

配置一下环境变量
```bash
sudo vim /etc/profile
```
复制下面两行到刚打开的`profile`文件最底部(注意`node`的安装地址`/home/shw/MySoftwares/node-v12.8.0-linux-x64`换成自己的)：
```bash
export NODE_HOME=/home/shw/MySoftwares/node-v12.8.0-linux-x64
export PATH=$PATH:$NODE_HOME/bin
```
保存后退出，再执行下面命令将环境变量生效：
```bash
source /etc/profile
```
将目录软链接到全局环境下（命令后面的`/usr/local/bin/node`是固定的）
```bash
sudo ln -s /home/shw/MySoftwares/node-v12.8.0-linux-x64/node /usr/local/bin/node
sudo ln -s /home/shw/MySoftwares/node-v12.8.0-linux-x64/npm /usr/local/bin/npm
```
这样安装好了以后使用`npm`安装的包(比如：`ionic serve`)，使用包的命令时可能会提示找不到命令，没关系，在用户目录下终端执行下面命令(固定写法)：
```bash
echo -e "export PATH=$(npm prefix -g)/bin:$PATH" >> ~/.bashrc && source ~/.bashrc
```
这样我们在所有用户下，都可以使用`npm`，也可以使用`npm`安装的包的命令。成功的将`nodejs`安装并配置到全局环境下。

安装完后，打开命令行终端，输入:
```bash
node -v
npm -v
```
检查一下有没有安装成功

### 添加国内镜像源
---
如果没有梯子的话，可以使用阿里的国内镜像进行加速。

```bash
npm config set registry https://registry.npm.taobao.org
```