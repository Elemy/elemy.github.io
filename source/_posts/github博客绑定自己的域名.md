---
title: github博客绑定自己的域名
date: 2018-04-01
categories: 博客
tags: [github,域名绑定]
keywords:  github,域名绑定
---
#### 准备工作
1. 用github搭建的博客，绑定自己的域名前，可以通过elemy.github.io访问自己的博客
[参考文章：零基础免费搭建个人博客-hexo+github](http://hifor.net/2015/07/01/%E9%9B%B6%E5%9F%BA%E7%A1%80%E5%85%8D%E8%B4%B9%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2-hexo-github/)
2. 准备域名（我的域名为panll.cc）

#### 开始
1. 在博客所在仓库添加一个文件名为CNAME的文件（*注意：大写*）
>在文件中写入域名，如“panll.cc”。
2. 解析域名

>我买的是阿里云的域名，打开控制台找到自己的域名，点击“解析”，然后添加解析,DNS配置如下：


记录类型 | 主机记录 | 解析线路 | 记录值 | MX优先级 | TTL值
---|---|---|---|---|---
A | @ | 默认 | 192.30.252.154 | -- | 600
A | @ | 默认 | 192.30.252.153 | -- | 600
CNAME | www | 默认 |username.github.io | -- | 600

用你自己的 Github 用户名替换表格中的 username

3. 10分钟后访问自己博客
- 通过访问username.github.io(elemy.github.io),可以自动跳转至自己的域名(panll.cc)
- 直接访问panll.cc



