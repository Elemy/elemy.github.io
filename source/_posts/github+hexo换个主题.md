---
title: github+hexo换个主题
date: 2018-03-19
categories: 博客
tags: [Hexo,Next,博客]
keywords:  Hexo,Next,博客
---
看到网上很多胖友推荐next，在Github上Star也是最高的Hexo主题，所以想要体验一下。下面是记录的安装步骤。

### 找到本地博客目录

cmd进入本地博客目录，我用的是git bash直接在该文件下打开。

### 下载主题包

在cmd中输入以下命令，下载next主题包，下载完成后的主题包在theme文件夹下。
```
$ git clone https://github.com/iissnan/hexo-theme-next themes/next
```
### 修改站点配置文件

修改博客的配置文件（目录：根目录下的_config.yml，称为“站点配置文件”）。打开文件修改theme的值为next，**注意！冒号后面有一个空格**。

```
theme: next
```

### 浏览器中查看主题

在命令行中输入以下命令，就可以查看看更改后的的主题了，很简约的一个主题。

```
$ hexo s --debug
```

一大串代码之后，直到看见“ http://localhost:XXXX”为止，这里XXXX表示端口号，默认是4000，将这一串地址输入到浏览器中，即可查看主题。

### 切换风格

这个主题还有其他几种风格，找到theme/next/_config.yml（称为主题配置文件）,在scheme字段前删除/添加“#”，刷新浏览器，即可查看切换后的主题。


### 上传代码

更新github上的代码，依次：

```
$ hexo g #完整命令为hexo generate，用于生成静态文件
$ hexo s #完整命令为hexo server，用于启动服务器，主要用来本地预览
$ hexo d #完整命令为hexo deploy，用于将本地文件发布到github上
```


### 补充

在执行hexo d时，可能会抛出

```
ERROR Deployer not found: git
```
解决办法：

1、deploy的type 的github需要改成git

2、
```
$ npm install hexo-deployer-git –save
```
也可能会抛出

```
bash: /dev/tty: No such device or address
error: failed to execute prompt script (exit code 1)
fatal: could not read Username for 'https://github.com': No error
FATAL Something's wrong. Maybe you can find the solution here: http://hexo.io/docs/troubleshooting.html
Error: bash: /dev/tty: No such device or address
error: failed to execute prompt script (exit code 1)
fatal: could not read Username for 'https://github.com': No error
```
解决办法：

把_config.yml文件中repository/repo:https://github.com/Elemy/elemy.github.io.git 这个地址改为 git@github.com:Elemy/elemy.github.io.git
