---
title: HEXO+Github Build Personal Blog!
date: 2020-06-10 15:27:20
tags:
---
# 开始 Hexo

## 什么是 Hexo？
[Hexo](https://hexo.io/zh-cn/) 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

![Hexo](HEXO.png)

## 安装

### 安装前提
安装 Hexo 相当简单，只需要先安装下列应用程序即可：

* [Node.js](http://nodejs.cn/download/) (Node.js 版本需不低于 8.10，建议使用 Node.js 10.0 及以上版本 **PS: 无法使用Node.js 14.0 以上版本！**)
* [Git](https://git-scm.com/downloads)

### 安装 Hexo

所有必备的应用程序安装完成后，即可使用 npm 安装 Hexo
首先在本地需要建立一个Hexo文件夹用于存储本地文件(做本地文件保存以及测试使用)

在文件内空白处右键，点击Git Bash Here
点击后弹出git命令框，输入此命令下载hexo：

```cmd
npm install -g hexo
```

### 进阶安装和使用

初始化hexo

```cmd
$ hexo init
```

接下来这四步对建站进行了部署，在进行最后一步后访问 http://localhost:4000 就可以查看你的本地hexo访问页面了

```cmd
$ npm install
$ hexo g
$ hexo d
$ hexo server
```
> **hexo g = hexo generate : 生成静态文件**
> **hexo d = hexo deploy : 部署网站**
> **不要在hexo server后还在git命令框按Ctrl C，除非你想停止服务。**
> **如果出现错误，先试试npm install hexo-deployer-git –save命令，还是不行的话就根据报错去查询。**

**若报下面Warning,经查询发现，fsevent是mac系统的，在win或者Linux下使用了，所以会有警告，忽略即可。fsevent的作用是能够检测文件目录的修改，可以记录恶意软件的非法操作，获取恶意软件的完整路径，删除和修改日期。**
```cmd
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN fsevents@1.2.0 had bundled packages that do not match the required version(s). They have been replaced with non-bundled versions.
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.0 (node_modules\fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.0: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})
```

# Github

## 登录（注册）GitHub

点击 [此处](https://github.com/) 注册(Sign up)你的GitHub账户


![注册你的GitHub](GitHubStep1.png)

## 新建 repository

进入已注册页面后，在右上角的“+”中点击New repository按钮

![New repository](GitHubStep2.png)

![New repository](GitHubStep3.png)

新建完成后就可以在你的主页看到你新建的项目了。建完的项目我们先搁置不动，接下来我们去购买属于自己的域名。

# 域名
## 购买域名

点击 [此处](https://wanwang.aliyun.com/domain) 查询并购买你的域名

查询自己的域名后会显示出自己可用的域名（由于我买的是.cn，这里就不会再显示.cn，这里框选.top）

![购买域名](DomainStep1.png)

添加清单后结算清单，我们需要进行实名信息认证，由于我已经验证完毕，过程无法重现（大概就是点击实名认证之后填写一大堆信息，就像开卡似得）

![购买域名](DomainStep2.png)

实在不会可以点击 [这里](https://jingyan.baidu.com/article/11c17a2cd708c2f446e39d02.html) 查询

到了这里就默认你买完啦。

## 解析域名
点击 [此处](https://dns.console.aliyun.com/#/dns/domainList) 来解析你的域名（同样我也已经解析过了，这里只会有解析设置）

![解析域名](DomainStep3.png)

进入页面后点击新手引导设置，它会要求你输入IP

![](DomainStep4.png)

这个IP需要我们打开cmd（win键 + R键），得到窗口后输入

```cmd
ping YosamYang.github.io     \注意YosamYang是我的名字，需要你填入你自己的名字
```

![](DomainStep5.png)

将得到IP输入到Domian页面的弹出框中后开始解析，等待解析完成域名配置完毕。

# 配置hexo以及GitHub

## 配置hexo

在你的新建的 hexo 目录下的 source 文件夹下，新建一个 CNAME.txt 的文本文档；

![CNAME](SetHexoStep1.png)

在文档中输入你的新买的域名（www.yosamstep.cn） ，保存后关闭

![CNAME](SetHexoStep2.png)

重命名你的 .txt 文件，将 .txt 文件的后缀去掉（文件会提示不可用，确定即可）

![CNAME](SetHexoStep3.png)

## 修改_config.yml

打开你的GitHub项目的主页，找到 clone 按钮，点击按钮以复制你的 repository Url

![repository Url](SetHexoStep4.png)

在你新建的 hexo 目录下找到 _config.yml，打开，在最下面的 deploy 部分内容修改：
```
deploy:
 type: git      \**注意每一列value前都要有一个空格 （KEY前也有！）**
 repository: https://github.com/YosamYang/YosamYang.github.io.git     \注意YosamYang是我的名字，需要你填入你自己的名字
 branch: master
```

## Git部署

在你的GitHub页面点击进入你新建的项目，点击Settings进入设置页面

![Github](SetGitHubStep1.png)

在GitHub Pages设置部分找到Custom domain，并在这里输入你购买的域名

![Github](SetGitHubStep2.png)

使用git部署，在你新建的hexo目录下空白处右键，点击Git Bash Here

```cmd
npm install hexo-deployer-git --save
```

执行之前的步骤:(hexo clean –> hexo generate –>hexo deploy)
```cmd
hexo clean
hexo g
hexo d
```

你就可以看到你的博客了

记住，每次修改配置信息或者其他必须要执行上面的步骤(g、d)，才可以使得配置信息生效。


# 更换主题

创建 Hexo 主题非常容易，一般我们都会从 [主题市场](https://hexo.io/themes/)  去 down 自己喜欢的主题， 并修改 _config.yml 内的 theme 设定就可以了。

![Themes](Themes1.png)


接下来我会以 [Butterfly](https://github.com/jerryc127/hexo-theme-butterfly) 为例，去修改我们的博客界面。

![Butterfly](hexo-theme-butterfly-doc-cover.jpg)

## A Hexo Theme: Butterfly

***[hexo-theme-butterfly](https://github.com/jerryc127/hexo-theme-butterfly)*** 是基于 [Molunerfinn](https://github.com/Molunerfinn) 的 [hexo-theme-melody](https://github.com/Molunerfinn/hexo-theme-melody) 的基础上进行开发的。


## 主题安装和升级

### 安装

在你的hexo根目录下空白处右键，点击Git Bash Here

```cmd
git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/Butterfly
```

如果想要安装比较新的 dev 分支，可以

```cmd
git clone -b dev https://github.com/jerryc127/hexo-theme-butterfly.git themes/Butterfly
```

### 应用主题

修改站点配置文件_config.yml，把主题改为 Butterfly

```cmd
theme: Butterfly
```

如果你没有 pug 以及 stylus 的渲染器，请下载安装： **npm install hexo-renderer-pug hexo-renderer-stylus --save** or **yarn add hexo-renderer-pug hexo-renderer-stylus**

### 平滑升级

为了主题的平滑升级，Butterfly 使用了 data files 特性。

推荐把主题默认的配置文件_config.yml 复製到 Hexo 工作目录下的 source/_data/butterfly.yml，如果 source/_data 的目录不存在那就创建一个。

![Themes](Themes2.png)

注意，如果你创建了 butterfly.yml, 它将会替换主题默认配置文件_config.yml 里的配置项 (不是合併而是替换), 之后你就只需要通过 git pull 的方式就可以平滑地升级 theme-butterfly 了。


**更多主题配置详情请访问(https://jerryc.me/)**


> 作者： JerryC
> 来源：   [原文出处](https://jerryc.me/posts/21cfbf15/#%E4%B8%BB%E9%A1%8C%E5%AE%89%E8%A3%9D%E5%92%8C%E5%8D%87%E7%B4%9A)

# HEXO 图片

当我们新建一篇 Blog 的时候，往往最需要的是向文章内部插入图片


同样的，hexo根目录下空白处右键，点击Git Bash Here

```cmd
npm install hexo-asset-image --save
```

在 _config.yml(如果你创建了source/_data/butterfly.yml，则在butterfly.yml中修改) 配置文件中，找到并修改: 

```
post_asset_folder: true，
url: https://YosamYang.github.io   \注意YosamYang是我的名字，需要你填入你自己的名字
```

然后新建一篇文章来 test

```cmd
hexo g
hexo new post "test"
```

这时 /source/_posts 文件夹内除了 test.md 文件还有一个同名的文件夹

![test](test.png)

最后在 test.md 中想引入图片时，先把图片复制到 test 这个文件夹中，然后只需要在 test.md 中按照 markdown 的格式引入图片就可以了

```markdown
![图片描述](图片名.jpg)
```

# Live 2D


检查 hexo 根目录下的 package.json 是否有 "hexo-helper-live2d": "^3.0.3", 依赖：

![](Live2D1.png)

如果有先卸载：

```cmd
npm uninstall hexo-helper-live2d
```

## 安装依赖

安装依赖

```cmd
npm install --save hexo-helper-live2d
```

成功了之后可以看到当前目录的 node_modules/ 下有个 live2d-widget 目录，这是动画的主配置：

![](Live2D2.png)

这个时候是没有模型文件的，所以下一步是下载模型文件

## 下载model文件

下载模型文件：

模型文件可直接用npm安装：如下

```cmd
npm install live2d-widget-model-epsilon2_1
```

model名字可在 [live2d-widget-models](https://github.com/xiazeyu/live2d-widget-models) 中找到，也可点击 [live2d](https://huaji8.top/post/live2d-plugin-2.0/) 看板娘模型预览来选择你喜欢的模型进行安装。

安装完成可以在 node_modules/ 下看到 live2d-widget-model-epsilon2_1 文件夹

![](Live2D3.png)

## 添加live2d看板娘到hexo

配置Hexo的主_config.yml(如果你创建了source/_data/butterfly.yml，则在butterfly.yml中修改)

添加以下代码到配置文件中：
```
## Live2D看板娘
live2d:
  enable: true
  pluginModelPath: assets/
  model:
    #模板目录，在node_modules里
    use: live2d-widget-model-epsilon2_1  
  display:
    position: right
    width: 300 
    height: 600
  mobile:
    # 在手机端显示
    show: false   
  rect:
    opacity:0.7
```

使用hexo g生成文件，使用hexo server即可在本地查看效果：

打开浏览器访问：http://localhost:4000即可看到效果


























