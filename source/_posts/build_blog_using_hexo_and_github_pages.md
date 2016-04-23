title: "利用Hexo和GitHub Pages搭建个人博客"
date: 2015-04-11 20:08:14
tags: [Hexo, GitHub, Pacman]
categories: 博客搭建与修改
---

网上看了一些利用GitHub Pages配合Hexo搭建个人博客的教程，如 [Zipperary's blog](http://zipperary.com/categories/hexo/) 等。亲自实践了一次，经过一些小挫折，也算是将博客的框架搭建起来了。这里将搭建过程简单的写下，便于以后参考之用。
# 前期准备
+ 安装 [Node.js](https://nodejs.org/)
+ 安装 [git](http://git-scm.com/)
本机环境为WIN8.1，直接选择对应MSI安装包即可，很方便。

# 安装Hexo
因为网络条件的某些限制，使用npm直接安装hexo会出现一些小问题（？）。可以利用 [淘宝NPM镜像](https://npm.taobao.org/)作为registry，下载对应文件，命令为：
```
npm install hexo -g
```

执行此操作之前，需要在 .npmrc配置文件(位于%userprofile%)加上*registry=https://registry.npm.taobao.org*。
为了能够部署到GitHub，还需要安装Hexo-deploy-git。
```
npm install hexo-deploy-git --save
```

# 配置博客

## 创建GitHub Repo

申请用户并创建 username.github.io这样一个Repo，再本地测试一下SSH的连接方式，看是否能够正常Pull和Push。网上资料很多，就不详细说明了。
## Hexo初始化
找到一个想存放博客的目录，如 D:\Blog 之类，启动cmd窗口并输入指令：
```
Hexo init
```

看到成功的提示之后，再输入
```
npm install
```

虽然我用了淘宝NPM镜像，但这一步**始终无法正常进行**。无奈之下，搜了个免费VPN,才把这一步搞定了，囧。此处请允许我感叹一下。
> Across the Great Wall, we can reach every corner in the world.

## 个性定制
其实我就改了个主题，变动不大，其他高级配置大部分可以在 [Hexo](hexo.io/docs)找到，但是我找到了也没看懂，就暂时放一边了^O^。 [Hexo Themes](http://hexo.io/themes/)列出了不少主题。我选的主题是 ~~[Pacman](http://yangjian.me/pacman/)~~[Jacman](https://github.com/wuchong/jacman)，里面也有中文说明，照着做很方便就搞好了,**注意**在分号之后加一个空格。

## 部署到GitHub

+ 在部署之前，得现有静态页面。
```
hexo generate
```

+ 页面效果咋样呢，本地先预览一下：
```
hexo server
```

+ 浏览器输入 http://localhost:4000/ 就可以查看效果了。
+ 配置部署信息 [Hexo Deployment](http://hexo.io/docs/deployment.html)
```
deploy:
	type: git
	repo: git@github.com:username/xxx # repo的SSH地址即可
	branch: master # 据说得用gh-pages(?),不过我直接用master也可以工作
	message: # 我是直接空着了
```

+ 可以发布博客了
```
hexo deploy
```

> 如果此时出现 *hexo cannot find deployer for git*之类信息，重新安装一下 hexo-deploy-git就可以了
```
npm install hexo-deployer-git --save
```

# 开始写博客

写一个新博客```hexo new blogName```。写完之后安装生成页面->预览->修改->部署一路走下去就可以了。**注意命令行输出**，用文本编辑器打开里面的Markdown文件，写想写的内容就好了。Markdown语法可以参见 [Markdown指南](http://zipperary.com/2013/05/22/introduction-to-markdown/)
# 后话
其实还有一部分没有做好，譬如~~页面代码显示异常~~，没有小黄人啥的，等到以后慢慢添加好了。
