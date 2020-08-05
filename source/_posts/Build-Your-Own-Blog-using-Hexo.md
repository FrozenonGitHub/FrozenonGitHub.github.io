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

Welcome to my world! This blog will walk you through steps to build your own blog using [Hexo](https://hexo.io/).

I assume that you already have a GitHub account and git installed on your PC.

## Create Your GitHub Repository
Your blog will be available at [https://username.github.io](), supported by GitHub. See [GitHub Pages](https://pages.github.com) for detail. 
- First, we need to create a new repository on GitHub name <username>.github.io, where <username> is your GitHub user name.
- Clone the repository by running the following command:
``` bash
$ git clone https://github.com/<username>/<username>.github.io.git
```

The repository directory will be used as your blog root directory.

## Install Hexo

1. Install Node.js on your computer. [Download](https://nodejs.org/en/download/)
2. Install Hexo via npm:
``` bash
$ npm install -g hexo-cli
```

You might want to use an mirror website to accelerate npm install process. Add the registry param for temporary usage.

``` bash
$ npm install -g hexo-cli --registry https://registry.npm.taobao.org
```

## Local Test

1. Create an empty directory, for temporary use. Enter the directory and let Hexo generate initial files.
```  bash
$ cd <dir_name>
$ hexo init
```

2. Copy the files under <dir_name> to your repository directory. Then run the following commands under your repository directory:
```  bash
$ npm install	# install necessary plugins for Hexo
$ hexo g	# generate static pages
$ hexo s	# start server, open localhost:4000 with your browser
```

Now you can see your blog using default Hexo theme 'landscape'.

![Hexo-theme-landscape](https://alexsixdegrees.github.io/2018/01/24/hexo-theme/landscape.png)

## Deploy on GitHub

1. modify _config.yml under your blog root directory:
```  json
deploy:
  type: git
  repo: https://github.com/<username>/<project>
  branch: master
```

- Note:
  - You can also use SSH for repo address, which requires SSH key match.
  - Your blog will be deployed on branch 'master' as default. If you want to store your source code (e.g. modification to themes, markdown files) in the same repository, you'd better create another branch for such purpose. After deployment, the remote 'master' branch will have different files, which will cause conflict.

2. install hexo-deployer-git plugin via npm:
3. run ```hexo d``` to deploy your blog on GitHub.
4. Check it out for yourself: [https://<username>.github.io]()

## Change Hexo Blog Theme

I'm using Hexo theme Icarus now. See [Icarus](https://github.com/ppoffice/hexo-theme-icarus). More themes [here](https://hexo.io/themes/index.html).

I'm using Hexo version 5.0.0, and currently not all themes support this brand new version. Starting from version 5.0.0, Hexo allows installing themes from npm.

However, the theme I choose need some modification to adapt to Hexo 5.0.0, so I choose to do it the old fashion way. The modifications to be made are listed here: [#github issue](https://github.com/ppoffice/hexo-theme-icarus/issues/771).

- Download & extract or git clone Icarus from GitHub to your blog's theme folder:
``` bash
$ git clone https://github.com/ppoffice/hexo-theme-icarus.git themes/icarus
```

- Carry out the above modifications ([#github issue](https://github.com/ppoffice/hexo-theme-icarus/issues/771)) plus this one:
``` yml
theme: icarus
```

Now you can check it locally (```hexo s```) or online (```hexo d```). 