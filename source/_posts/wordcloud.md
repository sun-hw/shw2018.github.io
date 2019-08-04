---
title: python生成词云（附带QQ聊天记录生成词云实战）
top: false
cover: false
toc: true
mathjax: true
date: 2019-07-27 22:39:05
password:
summary:
tags:
- 词云
- 自然语言处理
categories:
- 软件安装与配置
---

很多同学对词云很感兴趣，就是给一段文本，然后根据它的词频，生成出好看的词云，就像下面这张图一样：
![](1.png)

生成这个其实很简单，python代码我已经放在github上面了，大家下载下来就能直接用：[地址](https://github.com/godweiyang/wordcloud)

下面我讲讲怎么使用这个代码。

# 环境配置
首先需要python3环境，推荐使用Anaconda安装。

然后需要`jieba`和`wordcloud`库，所以运行下面两条命令安装两个库：
`pip3 install jieba`
`pip3 install wordcloud`

# 文件目录
这个代码文件夹是如下结构：
- data
    - templates
        这个文件夹下放所有你词云想要的样式图片，背景色最好简单一点。
    - `stopwords.txt`
        这是停止词文件，对于你不想在词云中出现的词，你都可以添加到这个文件中过滤掉它。
- fonts
    这个文件夹下放词云中显示的字体。
- `create_word_cloud.py`
    这是词云的主代码。
- `preprocess.py`
    这是用来预处理QQ聊天记录的。

# 使用方法
对于一般的文本文件，直接运行`python3 create_word_cloud.py filename.txt`就能生成词云了，效果如下：
![](2.jpg)

# 生成QQ聊天记录词云
首先打开消息记录，点击下方的消息管理器：
![](3.jpg)
然后在需要导出的聊天对象上面右键点击导出消息记录：
![](4.jpg)
然后保存类型选择`txt`，点保存，并将文件保存在`wordcloud`根目录下：
![](5.jpg)
然后打开命令行运行`python3 preprocess.py filename.txt`，用来去掉聊天记录中的昵称和时间等信息：

最后运行`python3 create_word_cloud.py __filename.txt`就能生成词云了。