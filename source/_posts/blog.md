---
title: Hexo+Github博客搭建记录
date: 2019-08-10 21:44:44
author: 洪卫
img: /medias/banner/7.jpg
coverImg: /medias/banner/4.jpg
top: true
cover: true
toc: true
password: 
mathjax: true
summary: 阅读须知:注意，这篇文章篇幅较长，主要针对新手，每一步很详细，所以可能会显得比较啰嗦，所以建议基础比较好小伙伴根据目录选择自己感兴趣的部分跳着看，不要文章没看，上来先喷一下！谢谢( ⊙ o ⊙ )
tags:
- Hexo
- Github
- 博客
categories:
- 软件安装与配置
---

# 阅读须知
---
> 注意，这篇文章篇幅较长，主要针对新手，每一步很详细，所以可能会显得比较啰嗦，所以建议基础比较好小伙伴根据目录选择自己感兴趣的部分跳着看，不要文章没看，上来先喷一下！谢谢( ⊙ o ⊙ )

# 前言
---
去年在博客园注册了自己的第一个博客，当时初衷就是想拿来作为自己的在线笔记本，做做学习记录，分享一些学到的东西，使用第三方提供的博客服务其实也挺方便，现在市面上提供类似服务的博客网站也很多，如CSDN，博客园，简书等平台，可以直接在上面发表，用户交互做的好，写的文章百度也能搜索的到。但是缺点是比较不自由，会受到平台的各种限制和恶心的广告，个性化不足。而自己购买域名和服务器，搭建博客的成本实在是太高了，不光是说这些购买成本，单单是花力气去自己搭这么一个网站，还要定期的维护它，对于我们大多数人来说，也是没有这样的精力和时间。那么，我们能不能自己定制一个自己喜欢的个性化博客，同时也不用付出太高的成本啦？

这就引出了第三种选择，基于开源框架搭建博客，然后直接在`github page`平台上托管我们的博客。这样就可以安心的来写作，又不需要定期维护，基于这个想法，今年8月初的时候开始搭建第一个属于自己的独立博客，前后断续弄了近一周，到现在稍微有点模样了。我想可能有很多小伙伴应该也想过搭建一个自己的博客，当然，网上也有一堆详细教程。写这篇博客的目的大概有两个，第一个是当做自己的搭建记录，方便以后自己随时查看提示修改，第二个是稍稍总结一下具体的搭建步骤以及一些支持个性化定制的博客源码修改的教程，稍稍分享一下这些修改经验，当然，更多的一些个性化操作需要你自己以后在这个基础上慢慢去摸索，有些写的不太好的地方还希望看到的小伙伴多多包涵。

博客初步的页面效果可以参观一下我的博客：[sunhwee.com](http://shw2018.github.io)，欢迎大家支持。

本博客基于[Hexo](https://hexo.io/zh-cn/)，所以首先要了解一下我们搭建博客所要用到的框架。`Hexo`是高效的静态网站生成框架，它基于`Node.js`，快速，简单且功能强大，是搭建博客的首选框架。大家可以进入[hexo](https://hexo.io/zh-cn/)官网进行详细查看，因为`Hexo`的创建者是台湾人，对中文的支持很友好，可以选择中文进行查看。通过`Hexo`，你可以直接使用`Markdown`语法来撰写博客。相信很多小伙伴写工程都写过`README.md`文件吧，对，就是这个格式的！写完后只需两三条命令即可将生成的网页上传到`github`或者`coding`等代码管理托管平台，然后别人就可以浏览你的博客网页啦。是不是很简单？你无需关心网页源代码的具体生成细节，只需要用心写好你的博客文章内容就行了。
> 简单总结：`Hexo`, 产品成熟，使用简单，功能强大，有丰富的各种插件资源；但，像发布后台、站内搜索，评论系统类似诉求，虽然有对应的工具，但也需要自己折腾下，后续我们一步一步介绍。

教程大致分三个部分，
* 第一部分：`hexo`的初级搭建还有部署到`github page`上，以及个人域名的绑定。
* 第二部分：`hexo`的基本配置，更换主题，实现多终端工作，以及在`coding page`部署实现国内外分流
* 第三部分：`hexo`添加各种功能，包括搜索的`SEO`，阅读量统计，访问量统计和评论系统等。

# 第一部分  搭建
---
`hexo`的初级搭建还有部署到`github page`上，以及个人域名的绑定。
## Hexo搭建步骤

- 1.安装`Git`
- 2.安装`Node.js`
- 3.安装`Hexo`
- 4.`GitHub`创建个人仓库
- 5.生成`SSH`添加到`GitHub`
- 6.将`hexo`部署到`GitHub`
- 7.设置个人域名
- 8.发布文章

## 1. 安装Git
---
为了把本地的网页文件上传到`github`上面去，需要用到工具———Git[[下载地址]](https://git-scm.com/download)。`Git`是目前世界上最先进的分布式版本控制系统，可以有效、高速的处理从很小到非常大的项目版本管理。`Git`非常强大，建议每个人都去了解一下。廖雪峰老师的`Git`教程写的非常好，大家可以看一下。[Git教程](https://www.liaoxuefeng.com/wiki/896043488029600)

**windows：**到`git`官网上下载`.exe`文件,[Download git](https://git-scm.com/download/win),安装选项还是全部默认，只不过最后一步添加路径时选择`Use Git from the Windows Command Prompt`，这样我们就可以直接在命令提示符里打开`git`了。
> 顺便说一下，`windows`在`git`安装完后，就可以直接使用`git bash`来敲命令行了，不用自带的`cmd`，`cmd`有点难用。

**linux：**对`linux`来说实在是太简单了，因为最早的`git`就是在`linux`上编写的，只需要一行代码
```bash
sudo apt-get install git
```
安装完成后在命令提示符中输入`git --version`来查看一下版本验证是否安装成功。


## 2. 安装nodejs
---
`Hexo`是基于`node.js`编写的，所以需要安装一下`node.js`和里面的`npm`工具。

**windows：**下载稳定版或者最新版都可以[Node.js](http://nodejs.cn/download/)，安装选项全部默认，一路点击`Next`。
最后安装好之后，按`Win+R`打开命令提示符，输入`node -v`和`npm -v`，如果出现版本号，那么就安装成功了。

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

## 3. 安装Hexo
---
前面`git`和`nodejs`安装好后，就可以安装`hexo`了，你可以先创建一个文件夹`MyBlog`，用来存放自己的博客文件，然后`cd`到这个文件夹下（或者在这个文件夹下直接右键`git bash`打开）。

比如我的博客文件都存放在`D:\Study\MyBlog`目录下。

在该目录下右键点击`Git Bash Here`，打开`git`的控制台窗口，以后我们所有的操作都在`git`控制台进行，就不用`Windows`自带的`cmd`了。

定位到该目录下，输入`npm install -g hexo-cli`安装`Hexo`。可能会有几个报错，无视它就行。
```bash
npm install -g hexo-cli
```
安装完后输入`hexo -v`验证是否安装成功。

至此`hexo`就安装完了。

接下来初始化一下`hexo`,即初始化我们的网站，输入`hexo init`初始化文件夹
```bash
hexo init MyBlog
```
这个`MyBlog`可以自己取什么名字都行，然后，接着输入`npm install`安装必备的组件。
```bash
cd MyBlog      //进入这个MyBlog文件夹
npm install
```
新建完成后，指定文件夹`MyBlog`目录下有：
- `node_modules:` 依赖包
- `public：`存放生成的页面
- `scaffolds：`生成文章的一些模板
- `source：`用来存放你的文章
- `themes：`主题** 
- `_config.yml:` 博客的配置文件**

这样本地的网站配置也弄好啦，输入`hexo g`生成静态网页，然后输入`hexo s`打开本地服务器，
```bash
hexo g
hexo server(或者简写:hexo s）)
```
然后浏览器打开[http://localhost:4000/](http://localhost:4000/)，就可以看到我们的博客啦，效果如下：
![](3.png)

按`ctrl+c`关闭本地服务器。

## 4. 注册Github账号创建个人仓库
---
接下来就去注册一个`github`账号，用来存放我们的网站。大多数小伙伴应该都有了吧，作为一个合格的程序猿（媛）还是要有一个的。

打开[https://github.com/](https://github.com/)，新建一个项目仓库`New repository`，如下所示：
![](4.png)
然后如下图所示，输入自己的项目名字，后面一定要加`.github.io`后缀，`README`初始化也要勾上。
![](5.png)
> 要创建一个和你用户名相同的仓库，后面加.http://github.io，只有这样，将来要部署到`GitHub page`的时候，才会被识别，也就是http://xxxx.github.io，其中xxx就是你注册`GitHub`的用户名。例如我的：http://shw2018.github.io

## 5. 生成SSH添加到GitHub
---
生成`SSH`添加到`GitHub`，连接`Github`与本地。
右键打开`git bash`，然后输入下面命令：
```bash
git config --global user.name "yourname"
git config --global user.email "youremail"
```
这里的`yourname`输入你的`GitHub`用户名，`youremail`输入你`GitHub`的邮箱。这样`GitHub`才能知道你是不是对应它的账户。例如我的：
```bash
git config --global user.name "shw2018"
git config --global user.email "hwsun@std.uestc.edu.cn"
```
可以用以下两条，检查一下你有没有输对
```bash
git config user.name
git config user.email
```

然后创建`SSH`,一路回车
> `ssh`，简单来讲，就是一个秘钥，其中，`id_rsa`是你这台电脑的私人秘钥，不能给别人看的，`id_rsa.pub`是公共秘钥，可以随便给别人看。把这个公钥放在`GitHub`上，这样当你链接`GitHub`自己的账户时，它就会根据公钥匹配你的私钥，当能够相互匹配时，才能够顺利的通过`git`上传你的文件到`GitHub`上。

```bash
ssh-keygen -t rsa -C "youremail"
```

这个时候它会告诉你已经生成了`.ssh`的文件夹。在你的电脑中找到这个文件夹。或者`git bash`中输入
```bash
cat ~/.ssh/id_rsa.pub
```
将输出的内容复制到框中，点击确定保存。

打开[github](http://github.com)，在头像下面点击`settings`，再点击`SSH and GPG keys`，新建一个`SSH`，名字随便取一个都可以，把你的`id_rsa.pub`里面的信息复制进去。如图：![](6.png)

在`git bash`输入`ssh -T git@github.com`，如果如下图所示，出现你的用户名，那就成功了。
![](7.png)


## 6. 将hexo部署到GitHub
---
这一步，我们就可以将`hexo`和`GitHub`关联起来，也就是将`hexo`生成的文章部署到`GitHub`上，打开博客根目录下的`_config.yml`文件，这是博客的配置文件，在这里你可以修改与博客配置相关的各种信息。

修改最后一行的配置：

```yml
deploy:
  type: git
  repository: https://github.com/shw2018/shw2018.github.io
  branch: master
```

`repository`修改为你自己的`github`项目地址即可，就是部署时，告诉工具，将生成网页通过`git`方式上传到你对应的链接仓库中。

这个时候需要先安装`deploy-git` ，也就是部署的命令,这样你才能用命令部署到`GitHub`。
```bash
npm install hexo-deployer-git --save
```
然后
```bash
hexo clean
hexo generate
hexo deploy
```
其中 `hexo clean`清除了你之前生成的东西，也可以不加。 `hexo generate `顾名思义，生成静态文章，可以用 `hexo g`缩写 ，`hexo deploy `部署文章，可以用`hexo d`缩写

> 注意`deploy`时可能要你输入`username`和`password`。

得到下图就说明部署成功了，过一会儿就可以在http://yourname.github.io 这个网站看到你的博客了！！
![](8.png)

## 7. 设置个人域名
---
现在你的个人网站的地址是` yourname.github.io`，如果觉得这个网址逼格不太够，这就需要你设置个人域名了。但是需要花钱。

> **不过，这一步不是必要的，如果目前还不想买域名可以先跳过，继续看后面的，以后想买域名了在还看这块**

首先你得购买一个专属域名，`xx`云都能买，看你个人喜好了。

这篇以腾讯云为例，腾讯云官网购买：![](9.png)
然后实名认证后进入腾讯云控制台，点云解析进去，找到你刚买的域名，点进去添加两条解析记录，如下图所示：
![](10.png)

然后打开你的`github`博客项目，点击`settings`，拉到下面`Custom domain`处，填上你自己的域名，保存：
![](11.png)

这时候你的项目根目录应该会出现一个名为`CNAME`的文件了。如果没有的话，打开你本地博客`/source`目录，我的是`D:\Study\MyBlog\source`，新建`CNAME`文件，注意没有后缀。然后在里面写上你的域名，保存。最后运行`hexo g`、`hexo d`上传到`github`。

过不了多久，再打开你的浏览器，输入你自己的专属域名，就可以看到搭建的网站啦！

## 8. 写文章、发布文章
---
首先在博客根目录下右键打开`git bash`，安装一个扩展`npm i hexo-deployer-git`。

然后输入`hexo new post "article title"`，新建一篇文章。

然后打开`D:\Study\MyBlog\source\_posts`的目录，可以发现下面多了一个文件夹和一个`.md`文件，一个用来存放你的图片等数据，另一个就是你的文章文件啦。
你可以会直接在`vscode`里面编写`markdown`文件，可以实时预览，也可以用用其他编辑`md`文件的软件的工具编写。
编写完markdown文件后，根目录下输入`hexo g`生成静态网页，然后输入`hexo s`可以本地预览效果，最后输入`hexo d`上传到`github`上。这时打开你的`github.io`主页就能看到发布的文章啦。


到这儿基本第一部分就完成了，已经完整搭建起一个比较简陋的个人博客了，接下来我们就可以对我们的博客进行个性化定制了。


# 第二部分  定制
---
我们要定制自己的博客的话，首先就要来了解一下`Hexo`博客的一些目录和文件的作用，以及如何平滑更换漂亮的主题模板并加入自己的定制源代码实现个性化定制

## 1. Hexo相关目录文件
### 1.1 博客目录构成介绍
---
从上图可以看出，博客的目录结构如下：
```
- node_modules
- public
- scaffolds
- source
	- _posts
	- about
	- archive
	- img
	- tags
- themes
```
`node_modules`是`node.js`各种库的目录，`public`是生成的网页文件目录，`scaffolds`里面就三个文件，存储着新文章和新页面的初始设置，`source`是我们最常用到的一个目录，里面存放着文章、各类页面、图像等文件，`themes`存放着主题文件，一般也用不到。

我们平时写文章只需要关注`source/_posts`这个文件夹就行了。

### 1.2 hexo基本配置
---
在文件根目录下的`_config.yml`，就是整个`hexo`框架的配置文件了。可以在里面修改大部分的配置。详细可参考官方的[配置描述](https://hexo.io/zh-cn/docs/configuration)。

#### 1.2.1 网站
---
参数描述`title`网站标题`subtitle`网站副标题`description`网站描述`author`您的名字`language`网站使用的语言`timezone`网站时区。`Hexo` 默认使用您电脑的时区。时区列表。比如说：`America/New_York, Japan`, 和 `UTC` 。

其中，`description`主要用于`SEO`，告诉搜索引擎一个关于您站点的简单描述，通常建议在其中包含您网站的关键词。`author`参数用于主题显示文章的作者。

#### 1.2.2 网址
---
参数描述`url`网址`root`网站根目录`permalink`文章的 [永久链接](https://hexo.io/zh-cn/docs/permalinks) 格式`permalink_defaults`永久链接中各部分的默认值

在这里，你需要把`url`改成你的**网站域名**。

`permalink`，也就是你生成某个文章时的那个链接格式。

比如我新建一个文章叫`temp.md`，那么这个时候他自动生成的地址就是`http://yoursite.com/2018/09/05/temp`。

以下是官方给出的示例，关于链接的变量还有很多，需要的可以去官网上查找 [永久链接](https://hexo.io/zh-cn/docs/permalinks)  。

> 参数结果:year/:month/:day/:title/2013/07/14/hello-world:year-:month-:day-:title.html2013-07-14-hello-world.html:category/:titlefoo/bar/hello-world

再往下翻，中间这些都默认就好了。
```yml
theme: landscap
```
`theme`就是选择什么主题，也就是在`themes`这个文件夹下，在官网上有很多个主题，默认给你安装的是`lanscape`这个主题。当你需要更换主题时，在官网上下载，把主题的文件放在`themes`文件夹下，再修改这个主题参数就可以了。

#### 1.2.3 Front-matter
---
`Front-matter` 是`md`文件最上方以 `--- `分隔的区域，用于指定个别文件的变量，举例来说：

```
title: Hexo+Github博客搭建记录
date: 2019-08-10 21:44:44
```
下是预先定义的参数，您可在模板中使用这些参数值并加以利用。

参数描述`layout`布局`title`标题`date`建立日期`updated`更新日期`comments`开启文章的评论功能`tags`标签（不适用于分页）`categories`分类（不适用于分页）`permalink`覆盖文章网址

其中，分类和标签需要区别一下，分类具有顺序性和层次性，也就是说` Foo`,` Bar `不等于` Bar`, `Foo`；而标签没有顺序和层次。
```yml
---
title: Hexo+Github博客搭建记录
date: 2019-08-10 21:44:44
author: 洪卫
img: /medias/banner/7.jpg
coverImg: /medias/banner/7.jpg
top: true
cover: true
toc: true
password: 5f15b28ffe43f8be4f239bdd9b69af9d80dbafcb20a5f0df5d1677a120ae9110
mathjax: true
summary: 这是你自定义的文章摘要内容，如果这个属性有值，文章卡片摘要就显示这段文字，否则程序会自动截取文章的部分内容作为摘要
tags:
- Hexo
- Github
- 博客
categories:
- 软件安装与配置
---
```
#### 1.2.4 layout（布局）
---
**1.2.4.1 post**

当你每一次使用代码
```bash
hexo new XXX
```
它其实默认使用的是`post`这个布局，也就是在`source`文件夹下的`_post`里面。

`Hexo` 有三种默认布局：`post`、`page` 和 `draft`，它们分别对应不同的路径，而您自定义的其他布局和 `post `相同，都将储存到 `source/_posts `文件夹。

而new这个命令其实是：
```bash
hexo new [layout] <title>
```
只不过这个`layout`默认是`post`罢了。

**1.2.4.2 page**

如果你想另起一页，那么可以使用
```bash
hexo new page newpage
```
系统会自动给你在`source`文件夹下创建一个`newpage`文件夹，以及`newpage`文件夹中的`index.md`，这样你访问的`newpage`对应的链接就是http://xxx.xxx/newpage

**1.2.4.3 draft**

`draft`是草稿的意思，也就是你如果想写文章，又不希望被看到，那么可以
```bash
hexo new draft newdraft
```
这样会在`source/_draft`中新建一个`newdraft.md`文件，如果你的草稿文件写的过程中，想要预览一下，那么可以使用
```bash
hexo server --draft
```
在本地端口中开启服务预览。

如果你的草稿文件写完了，想要发表到`post`中，
```bash
hexo publish draft newdraft
```
就会自动把`newdraft.md`发送到`post`中。


## 2. 更换主题
---
我们在了解`Hexo`博客文件基础之后，知道主题文件就放在`themes`文件下，那么我们就可以去Hexo官网下载喜欢的主题，复制进去然后修改参数即可。
网上大多数主题都是github排名第一的`Next`主题，但是我个人不是很喜欢，我在网上看到一个主题感觉还不错：[hexo-theme-matery](https://github.com/blinkfox/hexo-theme-matery)，地址在[传送门](https://github.com/blinkfox/hexo-theme-matery)。这个主题看着比较漂亮，并且响应式比较友好，点起来很舒服，功能也比较很多。

> 当然，人各有异，这个主题风格也不一定是你喜欢，那么你也可以跟着这教程类似的方法替换成你喜欢的就行了。

>特性：
- 简单漂亮，文章内容美观易读
- [Material Design](https://material.io/) 设计
- 响应式设计，博客在桌面端、平板、手机等设备上均能很好的展现
- 首页轮播文章及每天动态切换 `Banner` 图片
- 瀑布流式的博客文章列表（文章无特色图片时会有 `24` 张漂亮的图片代替）
- 时间轴式的归档页
- **词云**的标签页和**雷达图**的分类页
- 丰富的关于我页面（包括关于我、文章统计图、我的项目、我的技能、相册等）
- 可自定义的数据的友情链接页面
- 支持文章置顶和文章打赏
- 支持 `MathJax`
- `TOC` 目录
- 可设置复制文章内容时追加版权信息
- 可设置阅读文章时做密码验证
- [Gitalk](https://gitalk.github.io/)、[Gitment](https://imsun.github.io/gitment/)、[Valine](https://valine.js.org/) 和 [Disqus](https://disqus.com/) 评论模块（推荐使用 `Gitalk`）
- 集成了[不蒜子统计](http://busuanzi.ibruce.info/)、谷歌分析（`Google Analytics`）和文章字数统计等功能
- 支持在首页的音乐播放和视频播放功能

他的介绍文档写得非常的详细，还有中英文两个版本。效果图如下：
![](12.png)

首先先按照文档教程安装一遍主题，然后是可以正常打开的，如果你是一般使用的话，基本没啥问题了。不过有些地方有些地方可以根据你自己的习惯和喜好修改一下， 下面记录一下我这个博客修改了的一些地方。

### 2.1 新建文章模板修改
---
首先为了新建文章方便，我们可以修改一下文章模板，建议将`/scaffolds/post.md`修改为如下代码：
```json
---
title: {{ title }}
date: {{ date }}
top: false
cover: false
password:
toc: true
mathjax: true
summary:
tags:
categories:
---
```
这样新建文章后 一些`Front-matter`参数不用你自己补充了，修改对应信息就可以了。

### 2.2 添加404页面
---
原来的主题没有`404`页面，我们加一个。首先在`/source/`目录下新建一个`404.md`，内容如下：
```json
title: 404
date: 2019-08-5 16:41:10
type: "404"
layout: "404"
description: "Oops～，我崩溃了！找不到你想要的页面 :("
```
然后在`/themes/matery/layout/`目录下新建一个`404.ejs`文件，内容如下：
```html
<style type="text/css">
    /* don't remove. */
    .about-cover {
        height: 75vh;
    }
</style>

<div class="bg-cover pd-header about-cover">
    <div class="container">
        <div class="row">
            <div class="col s10 offset-s1 m8 offset-m2 l8 offset-l2">
                <div class="brand">
                    <div class="title center-align">
                        404
                    </div>
                    <div class="description center-align">
                        <%= page.description %>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>

<script>
    // 每天切换 banner 图.  Switch banner image every day.
    $('.bg-cover').css('background-image', 'url(/medias/banner/' + new Date().getDay() + '.jpg)');
</script>
```

### 2.3“关于”页面增加简历（可选）
---
修改`/themes/matery/layout/about.ejs`，找到`<div class="card">`标签，然后找到它对应的`</div>`标签，接在后面新增一个`card`，语句如下：
```html
<div class="card">
    <div class="card-content">
        <div class="card-content article-card-content">
                <div class="title center-align" data-aos="zoom-in-up">
                    <i class="fa fa-address-book"></i>&nbsp;&nbsp;<%- __('myCV') %>
                </div>
                <div id="articleContent" data-aos="fade-up">
                    <%- page.content %>
                </div>
        </div>
    </div>
</div>
```
这样就会多出一张`card`，然后可以在`/source/about/index.md`下面写上你的简历了，当然这里的位置随你自己设置，你也可以把简历作为第一个`card`。

### 2.4 数学公式渲染和代码高亮
---
**2.4.1 解决mathjax与代码高亮的冲突**

如果你按照教程安装了代码高亮插件`hexo-prism-plugin`，单独使用是没有问题的，但如果你又使用了`mathjax`，并且按照网上教程，安装`kramed`插件并修改了`js`文件里的正则表达式（为了解决`markdown`和`mathjax`的语法冲突），好了，那你的代码就无法高亮了。解决方法很简单，别用`kramed`插件了，还用原来自带的`marked`插件，直接改它的正则表达式就行了。

**2.4.2 加数学公式显示**

打开`D:\study\program\blog\themes\beantech\layout\post.ejs`，在最下方粘贴如下代码：
```javascript
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>
```
由于`markdown`语法与`mathjax`语法存在冲突，所以还需要修改源文件。

打开`D:\Study\MyBlog\node_modules\marked\lib\marked.js`
`escape: `处替换成：
```js
escape: /^$[`*\[\]()#$+\-.!_>])/
```
`em: `处替换成：
```js
em: /^\*((?:\*\*|[\s\S])+?)\*(?!\*)/
```
这时在文章里写数学公式基本没有问题了，但是要注意：
**数学公式中如果出现了连续两个{，中间一定要加空格！**

举个例子:
行内公式：$y = f(x)$
代码：
```
$y = f(x)$
```
行间公式：
\\[y = {f_{ {g_1}}}(x)\\]
代码：
```
\\[y = {f_{ {g_1}}}(x)\\]
```
> 注意上面花括号之间有空格！

### 2.5 增加建站时间
---
修改`/themes/matery/layout/_partial/footer.ejs`文件，在最后加上：
```js
<script language=javascript>
    function siteTime() {
        window.setTimeout("siteTime()", 1000);
        var seconds = 1000;
        var minutes = seconds * 60;
        var hours = minutes * 60;
        var days = hours * 24;
        var years = days * 365;
        var today = new Date();
        var todayYear = today.getFullYear();
        var todayMonth = today.getMonth() + 1;
        var todayDate = today.getDate();
        var todayHour = today.getHours();
        var todayMinute = today.getMinutes();
        var todaySecond = today.getSeconds();
        /* Date.UTC() -- 返回date对象距世界标准时间(UTC)1970年1月1日午夜之间的毫秒数(时间戳)
        year - 作为date对象的年份，为4位年份值
        month - 0-11之间的整数，做为date对象的月份
        day - 1-31之间的整数，做为date对象的天数
        hours - 0(午夜24点)-23之间的整数，做为date对象的小时数
        minutes - 0-59之间的整数，做为date对象的分钟数
        seconds - 0-59之间的整数，做为date对象的秒数
        microseconds - 0-999之间的整数，做为date对象的毫秒数 */
        var t1 = Date.UTC(2017, 09, 11, 00, 00, 00); //北京时间2018-2-13 00:00:00
        var t2 = Date.UTC(todayYear, todayMonth, todayDate, todayHour, todayMinute, todaySecond);
        var diff = t2 - t1;
        var diffYears = Math.floor(diff / years);
        var diffDays = Math.floor((diff / days) - diffYears * 365);
        var diffHours = Math.floor((diff - (diffYears * 365 + diffDays) * days) / hours);
        var diffMinutes = Math.floor((diff - (diffYears * 365 + diffDays) * days - diffHours * hours) / minutes);
        var diffSeconds = Math.floor((diff - (diffYears * 365 + diffDays) * days - diffHours * hours - diffMinutes * minutes) / seconds);
        document.getElementById("sitetime").innerHTML = "本站已运行 " +diffYears+" 年 "+diffDays + " 天 " + diffHours + " 小时 " + diffMinutes + " 分钟 " + diffSeconds + " 秒";
    }/*因为建站时间还没有一年，就将之注释掉了。需要的可以取消*/
    siteTime();
</script>
```
然后在合适的地方（比如`copyright`声明后面）加上下面的代码就行了：
```html
<span id="sitetime"></span>
```

### 2.6 修改不蒜子初始化计数
因为不蒜子至今未开放注册，所以没办法在官网修改初始化，只能自己动手了。和上一条一样，在`/themes/matery/layout/_partial/footer.ejs`文件最后加上：
```js
<script>
    $(document).ready(function () {

        var int = setInterval(fixCount, 50);  // 50ms周期检测函数
        var pvcountOffset = 80000;  // 初始化首次数据
        var uvcountOffset = 20000;

        function fixCount() {
            if (document.getElementById("busuanzi_container_site_pv").style.display != "none") {
                $("#busuanzi_value_site_pv").html(parseInt($("#busuanzi_value_site_pv").html()) + pvcountOffset);
                clearInterval(int);
            }
            if ($("#busuanzi_container_site_pv").css("display") != "none") {
                $("#busuanzi_value_site_uv").html(parseInt($("#busuanzi_value_site_uv").html()) + uvcountOffset); // 加上初始数据 
                clearInterval(int); // 停止检测
            }
        }
    });
</script>
```

然后把上面几行有段代码：

```html
<% if (theme.busuanziStatistics && theme.busuanziStatistics.totalTraffic) { %>
    <span id="busuanzi_container_site_pv">
        <i class="fa fa-heart-o"></i>
        本站总访问量 <span id="busuanzi_value_site_pv" class="white-color"></span>
    </span>
<% } %>
<% if (theme.busuanziStatistics && theme.busuanziStatistics.totalNumberOfvisitors) { %>
    <span id="busuanzi_container_site_uv">
        人次,&nbsp;访客数 <span id="busuanzi_value_site_uv" class="white-color"></span> 人.
    </span>
<% } %>
```

修改为：

```html
<% if (theme.busuanziStatistics && theme.busuanziStatistics.totalTraffic) { %>
    <span id="busuanzi_container_site_pv" style='display:none'>
        <i class="fa fa-heart-o"></i>
        本站总访问量 <span id="busuanzi_value_site_pv" class="white-color"></span>
    </span>
<% } %>
<% if (theme.busuanziStatistics && theme.busuanziStatistics.totalNumberOfvisitors) { %>
    <span id="busuanzi_container_site_uv" style='display:none'>
        人次,&nbsp;访客数 <span id="busuanzi_value_site_uv" class="white-color"></span> 人.
    </span>
<% } %>
```
其实就是增加了两个`style='display:none'`而已。

### 2.7 添加动漫人物
其实三步就行了，不用像网上有些教程那么复杂。

**第一步：**
```bash
npm install --save hexo-helper-live2d
```
**第二步：**
```bash
npm install live2d-widget-model-shizuku
```
**第三步：**
在根目录配置文件中添加如下代码：
```yml
live2d:
    enable: true
    scriptFrom: local
    pluginRootPath: live2dw/
    pluginJsPath: lib/
    pluginModelPath: assets/
    tagMode: false
    log: false
    model:
        use: live2d-widget-model-shizuku
    display:
        position: right
        width: 150
        height: 300
    mobile:
        show: true
    react:
        opacity: 0.7
```
然后`hexo g`再`hexo s`就能预览出效果了，但是有个注意的地方，**这个动漫人物最好不要和不蒜子同时使用**，不然不蒜子会显示不出来。至于解决办法后续更新。

> ***解决动漫人物和不蒜子不能同时使用的`bug`（2019.08.11）：

打开`themes\matery\layout\_partial`中的`footer.ejs`，将本站总访问量和访客数的代码改为如下：

```js
<% if (theme.busuanziStatistics && theme.busuanziStatistics.totalTraffic) { %>      
    <span id="busuanzi_container_site_pv" style='display:none'></span>
        <i class="fa fa-heart-o"></i>
        本站总访问量 <span id="busuanzi_value_site_pv" class="white-color"></span>

<% } %>

<% if (theme.busuanziStatistics && theme.busuanziStatistics.totalNumberOfvisitors) { %>
    <span id="busuanzi_container_site_uv" style='display:none'></span>
        人次,&nbsp;访客数 <span id="busuanzi_value_site_uv" class="white-color"></span> 人.
    
<% } %>
```
变化就在下面两句，将源代码对应字段后面的`＜/span＞`写在前面了。

```js
<span id="busuanzi_container_site_pv" style='display:none'></span>
<span id="busuanzi_container_site_uv" style='display:none'></span>
```
> ***发现按照上面改了过后，又出现一个新`bug`：文章头部的阅读次数不显示了，解决办法：（2019.08.11）：

打开`themes\matery\layout\_partial`中的`post-detail.ejs`，找到对应代码字段：
```js
<% if (theme.busuanziStatistics && theme.busuanziStatistics.enable) { %>
    <div id="busuanzi_container_page_pv" class="info-break-policy">
        <i class="fa fa-eye fa-fw"></i><%- __('readCount') %>:&nbsp;&nbsp;
        <span id="busuanzi_value_page_pv" ></span>
    </div>

<% } %>
```
修改为下面的就可以了：
```js
<% if (theme.busuanziStatistics && theme.busuanziStatistics.enable) { %>
        <span id="busuanzi_container_site_pv" style='display:none'></span>
        <i class="fa fa-eye fa-fw"></i><%- __('readCount') %>:&nbsp;&nbsp;
        <span id="busuanzi_value_page_pv" ></span>

<% } %>
```

### 2.8 添加评论插件
---
由于这个主题自带了`gittalk`、`gitment`、`valine`等评论插件，所以我们只需要对应插件参数就行了，这个博客用的是`gittalk`，如下：![](13.png)
当然也可以用其他评论插件，只需要配置对应项就是了，不是自带的可以照着网上的教程自己弄一个，类似的文章有很多，可以搜索关键字就行了。


### 2.9 添加网易云音乐BGM
---
写文章的时候，想插入一段`BGM`怎么办？

其实我们可以借助一些在线音乐的外链播放方式，首先打开网易云网页版，找到想听的歌曲，然后点击生成外链：
![](14.png)

可能你会遇到问题，比如点击生成外链会提示你由于版权原因，不能生成，那么可以用下面办法(目前还有效，不知道后面会不会失效)
1. (以 `Chrome `为例，其他浏览器类似) 打开歌单页面，在“生成外链播放器”上右击，点击审查元素（检查）ctrl+shift+i；
2. 接着找到生成外链播放器这段文字直接双击复制前面的`/outchain/2/20707408/` ![](15.png)
3. 然后在浏览器地址栏修改歌单链接，示例：http://music.163.com/#//outchain/2/20707408/
4. 然后就转到外链设置页面了。

复制如下代码：
![](16.png)

粘贴到文章对应位置就行了，为了美观，设置一下居中，具体代码如下：
```html
<div align="middle">这里粘贴刚刚复制的代码</div>
```
# 第三部分 优化
---
`hexo`添加各种优化功能，比如`SEO`优化等。
待续......
## 1. 优化代码块样式
---
由于代码高亮插件prism_plugin的样式没有行号显示和代码块整体复制功能，不是很方便，为了优化观感和易用性，我们可以对其进行修改：



## 2. 网站SEO优化
---
网站推广是一个比较烦人的事情，特别是对于专心搞技术的来说，可能就不是很擅长，那么怎么才能让别人知道我们网站呢？也就是说我们需要想办法让别人通过搜索就可以搜索到博客的内容，给我们带来自然流量，这就需要`seo`优化,让我们的站点变得对搜索引擎友好
> `SEO`是由英文`Search Engine Optimization`缩写而来， 中文意译为“搜索引擎优化”。`SEO`是指通过站内优化比如网站结构调整、网站内容建设、网站代码优化等以及站外优化。

### 让百度收录你的站点
---
首先要做的就是让各大搜索引擎收录你的站点，我们在刚建站的时候各个搜索引擎是没有收录我们网站的，在搜索引擎中输入`site:<域名>`,如果如下图所示就是说明我们的网站并没有被百度收录。我们可以直接点击下面的“网址提交”来提交我们的网站![查看站点是否被百度收录](18.png)

### 验证网站所有权
---
登录百度站长平台：http://zhanzhang.baidu.com,只要有百度旗下的账号就可以登录，登录成功之后在站点管理中点击[添加网站](http://zhanzhang.baidu.com/site/siteadd)然后输入你的站点地址。
> 注意，这里需要输入我们自己购买的域名,不能使用`xxx.github.io`之类域名.因为`github`是不允许百度的`spider`（蜘蛛）爬取`github`上的内容的，所以如果想让你的站点被百度收录，只能使用自己购买的域名![向百度站长添加网站](21.png)

在填完网址选择完网站的类型之后需要验证网站的所有权，验证网站所有权的方式有三种：
- 文件验证。
- `html`标签验证
- `CNAME`解析验证（**推荐使用**）

![验证网站所有权](23.png)

其实使用哪一种方式都可以，都是比较简单的。
> **但是一定要注意，使用文件验证文件存放的位置需要放在source文件夹下，如果是html文件那么hexo就会将其编译，所以必须要加上的`layout:false`，这样就不会被hexo编译。（如果验证文件是txt格式的就不需要）**

其他两种方式也是很简单的，我个人推荐`文件验证`和`CNAME`验证，`CNAME`验证最为简单，只需加一条解析就好~![添加云解析](23.png)


### 生成网站地图
---
我们需要使用`npm`自动生成网站的`sitemap`，然后将生成的`sitemap`提交到百度和其他搜索引擎
#### 安装sitemap插件
---
```bash
npm install hexo-generator-sitemap --save     
npm install hexo-generator-baidu-sitemap --save
```
#### 修改博客配置文件
---
在根目录配置文件`.yml`中修改`url`为你的站点地址
```yml
# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
# url: https://shw2018.github.io/
url: https://sunhwee.com
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:
```
**执行完`hexo g`命令之后就会在网站根目录生成`sitemap.xml`文件和`baidusitemap.xml文件`**，可以通过https://www.sunhwee.com/baidusitemap.xml，查看该文件是否生成，其中`sitemap.xml`文件是搜索引擎通用的文件，`baidusitemap.xml`是百度专用的`sitemap`文件。

### 向百度提交链接
---
然后我们就可以将我们生成的sitemap文件提交给百度，还是在百度站长平台，找到链接提交，这里我们可以看到有两种提交方式，自动提交和手动提交，自动提交又分为主动推送、自动推送和sitemap
> 如何选择链接提交方式
> 1. 主动推送：最为快速的提交方式，推荐您将站点当天新产出链接立即通过此方式推送给百度，以保证新链接可以及时被百度收录。
> 2. 自动推送：最为便捷的提交方式，请将自动推送的JS代码部署在站点的每一个页面源代码中，部署代码的页面在每次被浏览时，链接会被自动推送给百度。可以与主动推送配合使用。
> 3. sitemap：您可以定期将网站链接放到sitemap中，然后将sitemap提交给百度。百度会周期性的抓取检查您提交的sitemap，对其中的链接进行处理，但收录速度慢于主动推送。
> 4. 手动提交：一次性提交链接给百度，可以使用此种方式。

一般主动提交比手动提交效果好，这里介绍主动提交的三种方法
从效率上来说：
> **主动推送>自动推送>sitemap**
![连接提交](27.png)

#### 主动推送方式
安装插件`hexo-baidu-url-submit`
```bash
npm install hexo-baidu-url-submit --save
```
然后再根目录的配置文件中新增字段
```yml
baidu_url_submit:
  count: 80      # 提交最新的一个链接
  host: www.sunhwee.com    # 在百度站长平台中注册的域名
  token: xxxxxxxxxxxxxxxxx    # 请注意这是您的秘钥， 所以请不要把博客源代码发布在公众仓库里!
  path: baidu_urls.txt     # 文本文档的地址， 新链接会保存在此文本文档里
```
在加入新的deploy
```yml
deploy:
 - type: baidu_url_submitter
```

> 注意,这里多个 `type` 的写法应该这么写,前面那个 `type` 是我推送到 `Github` 与 `Coding `的`page`页面的配置,后面再讲这个.

 这样执行`hexo deploy`的时候，新的链接就会被推送了


#### 设置自动推送
在主题配置文件下设置,将baidu_push设置为true：
```
# Enable baidu push so that the blog will push the url to baidu automatically which is very helpful for SEO
baidu_push: true
```
然后就会将一下代码自动推送到百度，位置是themes\next\layout\_scripts\baidu_push.swig,这样每次访问博客中的页面就会自动向百度提交sitemap
```
{% if theme.baidu_push %}
<script>
(function(){
    var bp = document.createElement('script');
    var curProtocol = window.location.protocol.split(':')[0];
    if (curProtocol === 'https') {
        bp.src = 'https://zz.bdstatic.com/linksubmit/push.js';        
    }
    else {
        bp.src = 'http://push.zhanzhang.baidu.com/push.js';
    }
    var s = document.getElementsByTagName("script")[0];
    s.parentNode.insertBefore(bp, s);
})();
</script>
{% endif %}
```
#### sitemap
将我们上一步生成的sitemap文件提交到百度就可以了~
![将sitemap提交到百度](http://img.blog.csdn.net/20170504211420159?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvc3Vuc2hpbmU5NDAzMjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
我记得被百度收录过程还是蛮久的，一度让我以为我的方法有问题，提交链接在站长工具中有显示大概是有两天的时候，站点被百度收录大概花了半个月= =，让大家看一下现在的成果
在百度搜索`site:cherryblog.site`已经可以搜索到结果
![站点已被百度收录](http://img.blog.csdn.net/20170504212208725?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvc3Vuc2hpbmU5NDAzMjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
在搜索框输入域名也可以找到站点
![站点已被百度收录](http://img.blog.csdn.net/20170504212800850?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvc3Vuc2hpbmU5NDAzMjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
输入关键字的名字也可以在第二页就找到呢，好开森~
![站点已被百度收录](http://img.blog.csdn.net/20170504213218169?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvc3Vuc2hpbmU5NDAzMjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
## 让google收录你的站点
相比于百度，google的效率实在不能更快，貌似十分钟左右站点就被收录了，其实方法是和百度是一样的，都是先验证你的站点所有权，然后提交sitemap
google站点平台：https://www.google.com/webmasters/，然后就是注册账号、验证站点、提交sitemap，一步一步来就好，过不了过久就可以被google收录了
![站点已被google收录](http://img.blog.csdn.net/20170504221124520?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvc3Vuc2hpbmU5NDAzMjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
![站点已被google收录](http://img.blog.csdn.net/20170504221145864?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvc3Vuc2hpbmU5NDAzMjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
![站点已被google收录](http://img.blog.csdn.net/20170504221202442?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvc3Vuc2hpbmU5NDAzMjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
## 让其他搜索引擎收录你的站点
除了百度和google两大搜索引擎，还有搜狗、360等其他的搜索引擎，流程都是一样的
 ，大家就自行选择添加哈，这里就不再赘述了~
## 优化你的url
seo搜索引擎优化认为，网站的最佳结构是**用户从首页点击三次就可以到达任何一个页面**，但是我们使用hexo编译的站点打开文章的url是：sitename/year/mounth/day/title四层的结构，这样的url结构很不利于seo，爬虫就会经常爬不到我们的文章，于是，我们可以将url直接改成sitename/title的形式，并且title最好是用英文，在根目录的配置文件下修改permalink如下：
```
url: http://cherryblog.site
root: /
permalink: :title.html
permalink_defaults:
```
## 其他seo优化
seo优化应该说是一个收益延迟的行为，可能你做的优化短期内看不到什么效果，但是一定要坚持，seo优化也是有很深的可以研究的东西，从我们最初的网站设计，和最基础的标签的选择都有很大的关系，网站设计就如我们刚刚说的，要让用户点击三次可以到达网站的任何一个页面，要增加高质量的外链，增加相关推荐（比如说我们经常见到右侧本站的最高阅读的排名列表），然后就是给每一个页面加上keyword和描述
在代码中，我们应该写出能让浏览器识别的语义化HTML，这样有助于爬虫抓取更多的有效信息：爬虫依赖于标签来确定上下文和各个关键字的权重；并且对外链设置nofollow标签，避免spider爬着爬着就爬出去了（减少网站的跳出率），并且我们要尽量在一些比较大的网站增加我们站点的曝光率，因为spider会经常访问大站，比如我们在掘金等技术社区发表文章中带有我们的站点，这样spider是很有可能爬到我们中的站点的，so....
 - 网站**外链**的推广度、数量和质量
 - 网站的**内链**足够强大
 - 网站的**原创**质量
 - 网站的**年龄**时间
 - 网站的**更新频率**（更新次数越多越好）
 - 网站的**服务器**
 - 网站的**流量**：流量越高网站的权重越高
 - 网站的**关键词排名**：关键词排名越靠前，网站的权重越高
 - 网站的**收录**数量：网站百度收录数量越多，网站百度权重越高
 - 网站的浏览量及深度：**用户体验**越好，网站的百度权重越高




## 2. 网站SEO优化
---
网站 SEO 优化
关于网站 SEO 这一块我主要参考了这位小姐姐的这篇文章,但是有些发现她有些地方写的不是很清楚,自己也在这一块设置时也摸索了半天,所以直接像大家分享一下我的踩坑经验.
让百度收录你的站点
我们直接在百度中搜索site:你的域名就可以查看百度是否已经收录你的网站,如果没有收录的话,你就要去去登录百度站长平台在站点管理中点击添加网站,然后输入你的站点地址, 注意,这里需要输入我们自己购买的域名,不能使用xxx.github.io之类域名.

步骤如下:

输入网站: 添加域名时建议是带上www的前缀
站点属性: 选择自己网站类型
验证网站: 验证网站的所有权,这里主要有以下三种

文件验证: 文件验证文件存放的位置需要放在source文件夹下,txt 格式的不会被 hexo 预编译,其他格式要在头部加上layout: false

HTML 标签验证: 将他给你的代码添加到网站首页的 head 标签内
CNAME 验证: 推荐使用,将对应的 CNAME 文件放在你的 source 文件夹中即可,只要在其中写上你的域名地址就行;除此之外还会要求你到自己的域名提供商(我的是万网)上添加 CNAME 的解析(会面在国内外分流这一块会与更详细的解析说明);

生成网站地图 --- sitemap
这里需要我们安装下面两个插件,先执行下面命令
npm i hexo-generator-sitemap hexo-generator-baidu-sitemap -S

再在你的站点配置文件中修改 URL 为你的站点地址


当你在 hexo g 时,会在public文件夹中生成sitemap.xml 和baidusitemap.xml 两个文件,如果你已经提前将你的 hexo 部署到网上,这是可以直接打开http://yoururl/sitemap.xml和http://yoururl/baidusitemap.xml来查看.(这两者的区别在于 baidusitemap.xml 是百度搜索引擎的专用文件,另一个是通用).
向百度提交链接

如何选择链接提交方式
1、主动推送：最为快速的提交方式，推荐您将站点当天新产出链接立即通过此方式推送给百度，以保证新链接可以及时被百度收录。
2、自动推送：最为便捷的提交方式，请将自动推送的JS代码部署在站点的每一个页面源代码中，部署代码的页面在每次被浏览时，链接会被自动推送给百度。可以与主动推送配合使用。
3、sitemap：您可以定期将网站链接放到sitemap中，然后将sitemap提交给百度。百度会周期性的抓取检查您提交的sitemap，对其中的链接进行处理，但收录速度慢于主动推送。
4、手动提交：一次性提交链接给百度，可以使用此种方式。

这里我推荐大家使用主动推送,当你主动推送时,可以缩短百度爬虫发现您站点新链接的时间,使新发布的页面可以在第一时间被百度收录;对于网站的最新原创内容，使用主动推送功能可以快速通知到百度，使内容可以在转发之前被百度发现.
使用主动推送

需要先安装插件npm i hexo-baidu-url-submit -S

然后再在站点配置文件中按如下方式新增字段

baidu_url_submit:
  count: 10 # 提交最新的链接数
  host: crowncj.com # 在百度站长平台中注册的域名,虽然官方推荐要带有 www, 但可以不带.
  token:  XXXXX # 你的秘钥,每个人都不一样,获取方法在下面
  path: baidu_urls.txt # 文本文档的地址,新链接会保存在此文本文档里


然后加入新的 deploy

deploy:
 - type:baidu_url_submitter

注意,这里多个 type 的写法应该这么写,前面那个 type 是我推送到 Gitub 与 Coding 的page页面的配置,后面再讲这个.







密钥的获取位置在网页抓取中的链接提交这一块,如下所示:








最后当你执行hexo d时新的连接就会被推送上去.
推送成功时,会有如下终端提示,各种不同的推送反馈字段说明在这里查看,一般来说,推送失败都是地址不相符造成的,我们只需对比baidu_url_submit在public中生成的baidu_urls.txt的地址,与自己填写在host字段中是否一样即可,这里需要注意的是,多加www会导致上传失败(血的教训...)








让 Google 收录你的网站

登录 Google 网络站长,点击添加属性按要求添加你的网站


验证你的网站所有权,我推荐使用 HTML 文件上传的方式,将他给你的html 文件放入 sources  文件夹下,但 html 文件默认会被 hexo 预编译,所以这里,我们要手动设置让 hexo 不要编译该文件,在文件开始添加layout:false即可.










添加 sitemap : 进入 Google Search Console - 抓取 - 站点地图,点击「添加/测试站点地图」,输入你的博客网址. 若无报错则站点地图提交成功
提交 robots.txt:


robots.txt 是一种存放于网站根目录下的 ASCII 编码的文本文件，它的作用是告诉搜索引擎此网站中哪些内容是可以被爬取的，哪些是禁止爬取的。robots.txt 放在博客目录下的 source 文件夹中，博客生成后在站点目录 /public/ 下。

我的 robots.txt 文件内容如下：
User-agent: *
Allow: /
Allow: /archives/
Allow: /categories/
Allow: /about/
Disallow: /vendors/
Disallow: /js/
Disallow: /css/
Disallow: /fonts/
Disallow: /vendors/
Disallow: /fancybox/

robots.txt 文件更新至网站后可进入 Google Search Console - 抓取 - robots.txt 测试工具进行测试。

这里部分参考自Hexo 博客搜索 SEO 优化 -- 谷歌篇

优化你的 URL

这段话参考自上面那个小姐姐的文章,写的很好,这里我直接拿来用下
seo搜索引擎优化认为，网站的最佳结构是用户从首页点击三次就可以到达任何一个页面，但是我们使用hexo编译的站点打开文章的url是：sitename/year/mounth/day/title四层的结构，这样的url结构很不利于seo，爬虫就会经常爬不到我们的文章，所以我们可以将url直接改成sitename/title的形式，并且title最好是用英文，在根目录的配置文件下修改permalink如下：








将你的网站同时托管到 Github 和 Coding 上,国内外分流
Coding 类似于中国的 Github 一样,也提供了 Pages 服务,但对我们而言,跟 Github 不同的地方在于免费用户能拥有五个私人仓库,这个可以用来部署自己的一些私人代码,而且配合 Github 可以做到国内IP 访问 Coding 的 Pages 页面,国外访问 Github 上面的 Pages 页面.大致配置过程如下:

在 Coding 上创建仓库: 这里注意要去创建一个公有的仓库,私有仓库是没有 pages 服务的.
将你的公钥传上去.这里网上关于自己公钥的相关教程很多,我就不多叙述了.
修改 hexo 的站点配置文件中的 deploy 选项,配置你的 Github 与 Coding 仓库,需要注意的是其中 Github 的仓库名xxx.github.io必须跟你的 Github 名称一样:










每次上传的时候都需要输入你的账号密码之类的信息,可以直接将你账号密码写在上传地址中,这样就不用每次更新都输入你的账号密码了

例如你的账号为:crown3,密码为 BBB;
那你的repo填写为下面这样即可
github: https://crown3:BBB@github.com/crown3/crown3.github.io.git
coding: https://crown3:BBB@git.coding.net/crown3/仓库名.git


设置 coding 的 pages 服务:在pages页面将部署来源选择为master分支，然后将自定义域名填写自己购买的域名就可以了

设置域名解析: 在你的域名提供商那里修改你的域名解析就行,例如我的是万网,按照下图所示,添加这五条解析即可做到国内外访问分流.




将自己的代码托管到私有仓库
当我们将自己的代码托管到私有仓库后,就可以在任何一台电脑上将你的 hexo 部署代码下载下来进行编辑,而且可以将你的一些个人密钥什么的直接推送到你的代码仓库去,这样更便利于我们的管理维护.
在上文我已经说过了,国内 Coding 的免费用户可以创建五个私有仓库,这是可以直接拿来使用,但是如果你对国内的私有仓库安全性存有怀疑,也可以去使用国外专门做私有仓库托管的bitbucket,在这里私有仓库是可以免费使用的.具体上传之类的使用方法我就不再细述了,都是基于 git 做的代码管理,使用方法都大同小异.
使用 Gulp 压缩你的代码
代码压缩可以明显减小我们的文件大小,加载速度,这里我会直接提供我使用的脚本,大家可以直接拿来使用,有需要了解相关知识的可以去gulp官网去做相关了解.

先安装Gulp以及我们需要使用的一系列插件:

npm i gulp gulp-clean-css gulp-htmlclean gulp-htmlmin gulp-imagemin gulp-uglify -S


接着创建gulpfile.js: 在你的博客根目录(跟你站点配置文件同一层)下创建gulpfile.js这个文件,然后在里面填入如下脚本即可,里面有相关注释,感兴趣的可以去了解一下.

var gulp = require('gulp');
var minifycss = require('gulp-clean-css');
var uglify = require('gulp-uglify');
var htmlmin = require('gulp-htmlmin');
var htmlclean = require('gulp-htmlclean');
var imagemin = require('gulp-imagemin');
var del = require('del');
var runSequence = require('run-sequence');
var Hexo = require('hexo');
// 清除public文件夹
gulp.task('clean', function() {
    return del(['public/**/*']);
});
// 利用Hexo API 来生成博客内容， 效果和在命令行运行： hexo g 一样
// generate html with 'hexo generate'
var hexo = new Hexo(process.cwd(), {});
gulp.task('generate', function(cb) {
    hexo.init().then(function() {
        return hexo.call('generate', {
            watch: false
        });
    }).then(function() {
        return hexo.exit();
    }).then(function() {
        return cb()
    }).catch(function(err) {
        console.log(err);
        hexo.exit(err);
        return cb(err);
    })
})
// 压缩public目录下的所有css
gulp.task('minify-css', function() {
    return gulp.src('./public/**/*.css')
        .pipe(minifycss({
            compatibility: 'ie8'
        }))
        .pipe(gulp.dest('./public'));
});
// 压缩public目录下的所有html
gulp.task('minify-html', function() {
    return gulp.src('./public/**/*.html')
        .pipe(htmlclean())
        .pipe(htmlmin({
            removeComments: true,
            minifyJS: true,
            minifyCSS: true,
            minifyURLs: true,
        }))
        .pipe(gulp.dest('./public'))
});
// 压缩public目录下的所有js
gulp.task('minify-js', function() {
    return gulp.src('./public/**/*.js')
        .pipe(uglify())
        .pipe(gulp.dest('./public'));
});
// 压缩public目录下的所有img： 这个采用默认配置
gulp.task('minify-img', function() {
    return gulp.src('./public/images/**/*.*')
        .pipe(imagemin())
        .pipe(gulp.dest('./public/images'))
})
// 同上，压缩图片，这里采用了： 最大化压缩效果。
gulp.task('minify-img-aggressive', function() {
    return gulp.src('./public/images/**/*.*')
        .pipe(imagemin(
        [imagemin.gifsicle({'optimizationLevel': 3}), 
        imagemin.jpegtran({'progressive': true}), 
        imagemin.optipng({'optimizationLevel': 7}), 
        imagemin.svgo()],
        {'verbose': true}))
        .pipe(gulp.dest('./public/images'))
})
// 用run-sequence并发执行，同时处理html，css，js，img
gulp.task('compress', function(cb) {
    runSequence(['minify-html', 'minify-css', 'minify-js', 'minify-img-aggressive'], cb);
});
// 执行顺序： 清除public目录 -> 产生原始博客内容 -> 执行压缩混淆
gulp.task('build', function(cb) {
    runSequence('clean', 'generate', 'compress', cb)
});
gulp.task('default', ['build'])


执行gulp: 在命令行中输入gulp build即可


这里要说明的是,这里利用Hexo API 来生成博客内容,效果和在命令行运行： hexo g 一样,所以当我们在执行gulp build时,会根据我们的相关博文来直接生成相应的public文件夹中的内容,并直接进行压缩,接下来我们运行hexo d上传上去的代码会是已经进行相应压缩了的.

作者：crown3
链接：https://www.jianshu.com/p/efaf72aab32e
来源：简书
简书著作权归作者所有，任何形式的转载都请联系作者获得授权并注明出处。

##  一些注意事项
---
首先解释一下文章开头的配置，如下图所示：
```yml
title: 文章标题
catalog: 是否显示段落目录
date: 文章日期
subtitle: 子标题
header-img: 顶部背景图片
top: 是否置顶
tags: 标签
categories: 分类
```

### 备份博客源文件
---
有时候我们想换一台电脑继续写博客，最简单的方法就是把博客整个目录拷贝过去，就是这么暴力。不过，这种方法有个问题就是要是那天电脑崩了，本地源文件丢失了，比较麻烦，所以这时候就可以将博客目录下的所有源文件都上传到`github`上面。

首先在`github`博客仓库下新建一个分支`hexo`，然后`git clone`到本地，把`.git`文件夹拿出来，放在博客根目录下。

然后`git branch -b hexo`切换到`hexo`分支，然后`git add .`，然后`git commit -m "xxx"`，最后`git push origin hexo`提交就行了。

具体效果可以看我的博客源文件仓库：[传送门](https://github.com/shw2018/shw2018.github.io)。

大家也可以先用下文hexo安装方法安装完hexo，然后直接`git clone -b hexo https://github.com/shw2018/shw2018.github.io.git`克隆我的所有源文件，这是我目前修改完的基本没bug的定制化的博客，可以直接拿来用。

**其他还有什么问题的话等我想起来了再继续添加，如果遇到问题欢迎联系我。**

参考：

* [Blinkfox](https://blinkfox.github.io/)
* [godweiyang](https://godweiyang.com/)