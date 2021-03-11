---
title: 个人博客搭建（Hexo + Github）
date: 2021-03-10 17:40:41
tags:
---

**目录结构**

- 准备
  - Node.js, Git, Github
- 安装Hexo
- 连接Github与本地
- 写文章、发布文章

准备

搭建参考了知乎教程 https://zhuanlan.zhihu.com/p/35668237 https://ismartinmeng.com/2020/05/25/Deploy-you-personal-blog-in-10-min-with-Hexo-AWS-Route53-GithubPage-05-2020/

### Github创建仓库与Github Page

1. Github新建一个项目，Repository name项目名必须以你的**用户名**.github.io命名，如果不是用户名.github.io的格式url格式会变 从而导致链接你的自定义域名失败。
2. 点击仓库的Setting页面，向下拉到最后有个`GitHub Pages`，点击`Choose a theme`选择一个主题。然后等一会儿，再回到`GitHub Pages` 。稍等一会儿等到链接处告诉你ready变绿，在显示your site is ready is already published at那里点击链接，便会出现自己的网页。

### Hexo创建本地项目

在合适的地方新建一个文件夹，用来存放自己的博客文件，比如我会存在documents\codeprogram\blog目录下。

打开terminal，定位到该目录下，输入`sudo npm i hexo-cli -g`安装Hexo。

安装完后输入`hexo -v`验证是否安装成功。

然后就要初始化我们的网站，输入`hexo init`初始化文件夹，接着输入`npm install`安装npm的依赖包。

这样本地的网站配置也弄好，输入`hexo g`生成静态网页（注：这个命令每次要生成新post后都会需要），然后输入`hexo s`启动本地服务器，然后浏览器打开[http://localhost:4000/](https://link.zhihu.com/?target=http%3A//localhost%3A4000/)，就可以看到我们的博客，按`ctrl+c`关闭本地服务器。



## 连接Github与本地

打开博客根目录下的`_config.yml`文件，这是博客的配置文件，在这里你可以修改与博客相关的各种信息。

修改最后一行的配置：

```bash
deploy:
  type: git
  repository: https://github.com/Kexin34/kexinwen.github.io
  branch: main
```

repository修改为你自己的github项目地址。



## 写文章、发布文章

首先在博客根目录下右键打开git bash，安装一个扩展`npm i hexo-deployer-git`。

然后输入`hexo new post "article title"`，新建一篇文章。

然后打开`D:\study\program\blog\source\_posts`的目录，可以发现下面多了一个文件夹和一个`.md`文件，一个用来存放你的图片等数据，另一个就是你的文章文件啦。

编写完markdown文件后，根目录下输入`hexo g`生成静态网页，然后输入`hexo s`可以本地预览效果，最后输入`hexo d`上传到github上。这时打开你的github.io主页就能看到发布的文章啦。



### 链接Github仓库与本地Hexo repo

**有git基础的同学可略过本部分**
**(1) 在本地的刚建好的hexo文件目录下初始git**
`git init` `git add .` `git commit -m "init"`

**(2) 然后链接远程仓库**
`git remote add orign` + 你的仓库url 

**(3)之后拉取并处理冲突**
如果选择主题则需要在pull加上–allow-unrelated-histories
`git pull origin master --allow-unrelated-histories`
如果之前没选择应该直接
`git pull origin master`
就可以

然后再提交本地hexo代码到github
`git init` `git add .` `git commit -m "init"`
此时稍等一下再打开你的username.github.io应该能看到本地hexo的页面部署到了云端！