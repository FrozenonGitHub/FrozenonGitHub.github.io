---
title: Build Your Own Blog using Hexo (CN)
date: 2020-08-16 19:17:02
categories:
- Blog
tags:
- Hexo
- Icarus
- Set up
- CN
---
# GitHub+Hexo搭建个人博客

> 本文主要介绍使用GitHub+Hexo搭建个人博客的一些**关键步骤**以及关于**内容创作**的一些想法。

## GitHub+Hexo
![](http://www.iamwr.com/2017/05/17/GitHub-and-Hexo-build-a-personal-website-detailed-tutorial/cover.png)

[GitHub](https://www.github.com/)聚集了世界上最大的开发者社区。开发者在这里发现、分享、开发更好的软件。无论是开源项目还是私有仓库，GitHub为合作开发提供了一个all-in-one平台。

[Hexo](https://hexo.io/)是一个快速、简洁且高效的博客框架。它支持Markdown、支持插件、一键部署等特性以及活跃的Hexo社区使它成为搭建静态博客的不错选择。

> 接下来介绍搭建博客的**主要步骤**

### 1. 创建GitHub Repository

GitHub+Hexo搭建的博客可以使用GitHub提供的免费URL： `https://username.github.io`，详见[GitHub Pages](https://pages.github.com)。你也可以配置使用自己的URL，但可能会增加购买域名开销。

首先，我们需要创建一个名为`username.github.io`的GitHub仓库，`username` 是你的GitHub用户名。将该仓库克隆到本地：
``` bash
$ git clone https://github.com/<username>/<username>.github.io.git
```
仓库所在的本地目录将作为博客本地根目录。

### 2. 安装Hexo

Hexo使用Node.js渲染，首先安装Node.js。[Node.js下载](https://nodejs.org/en/download/)

使用npm安装Hexo：
``` bash
$ npm install -g hexo-cli
```
如果不能科学上网，可以考虑在使用npm安装时，使用镜像源。这里给出一种临时使用镜像的方法：
``` bash
$ npm install -g hexo-cli --registry https://registry.npm.taobao.org
```

### 3. 本地测试

Hexo创建博客的初始文件时，需要在空路径下。因此，新建一个文件夹用于临时容纳初始文件：
```  bash
$ cd <dir_name>
$ hexo init
```
将新建文件夹下的文件复制到之前的GitHub仓库路径下。进行如下操作：
```  bash
$ npm install	# install necessary plugins for Hexo
$ hexo g	# generate static pages
$ hexo s	# start server, open localhost:4000 with your browser
```
现在你可以打开浏览器在localhost:4000看到使用默认的Hexo主题`landscape`的博客了。
![Hexo-theme-landscape](https://alexsixdegrees.github.io/2018/01/24/hexo-theme/landscape.png)

### 4. 部署到GitHub

修改博客根目录下的`_config.yml`文件：
```  json
deploy:
  type: git
  repo: https://github.com/<username>/<project>
  branch: master
```
这里可以将`repo`对应地址改为SSH的。`branch`设置了部署的分支是`master`分支。由于GitHub在部署分支远端只保存静态网页文件，我另建了一个分支用于markdown和前端源码备份。

接下来使用npm安装hexo-deployer-git插件。执行`hexo d`完成部署。打开`https://username.github.io`，即可查看。

### 5. 更换Hexo主题

Hexo在`/themes`路径下管理不同的主题。`_config.yml`在中修改`theme: <theme_name>`进行切换。我选择了支持插件种类较多的 [Icarus](https://github.com/ppoffice/hexo-theme-icarus)主题。选择其他主题：[Hexo主题](https://hexo.io/themes/index.html)。

> 从Hexo version **5.0.0**开始，Hexo支持通过npm安装主题。但目前(**Aug 2020**)，并非所有Hexo主题都更新了对5.0.0版本以及npm渠道的支持。

传统的安装Hexo主题的方法为，从GitHub下载/clone主题仓库到`/themes`文件夹。使用过程中遇到问题可参考GitHub Issue。例如`ICARUS`主题对Hexo 5.0.0不适配的问题，作者在[*github issue*](https://github.com/ppoffice/hexo-theme-icarus/issues/771)给出了解决方案。

每个Hexo主题都有对应的前端、插件代码，可以自行开发新功能后发起Pull Request.

### 6. 博客写作与发布

Hexo的博客markdown文档保存在`/source`路径下。在markdown文件开头加入如下代码段，提供博客的标题、时间、类别、标签等信息：
```
---
title: Build Your Own Blog using Hexo
date: 2020-08-05 23:56:07
categories:
- Blog
tags:
- Hexo
- Icarus
- Set up
---
```
> 如果`hexo d`之后，远端网页没更新，可尝试重新执行`hexo g`生成静态网页文件之后再`hexo d`

## 关于内容创作的一些想法

### 1. one-size-fits-all
对于up主、博主，内容创作与分享的工作应当专注于内容本身而不是为了适应不同的平台不同的格式要求而频繁修改甚至重写作品。markdown具有相对简洁的语法和主流博客平台的支持，因此成为技术类博客写作的合适选择。

GitHub+Hexo相比于支持在线编辑的博客平台，在博客写作方面并没有明显区别，如果不玩前端就不会带来过多的学习成本。作为备用的博客平台，还是值得推荐的。

### 2. pros & cons
- 优势：DIY前端，为GitHub引流，本地远端备份
- 劣势：搜索引擎引流不足，在线更新不便

### 3. 博客定位
写markdown博客还是挺费精力的，需要谋篇布局、遣词造句、绘图上传。我平时习惯于用oneNote写笔记，乱糟糟的，偶尔有空挑一些可公开的内容写成md文档，作为笔记博客还是ok的。至于吸引关注什么的，暂时没什么想法。

Hexo博客先老老实实当我的笔记本吧(TAT)

