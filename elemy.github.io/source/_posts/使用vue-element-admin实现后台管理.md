---
title: 使用vue-element-admin实现后台管理
date: 2018-03-30
categories: 博客
tags: [vue-element-admin,后台管理系统]
keywords:  vue-element-admin,后台管理系统
---
刚入职，上级推荐使用vue-element-admin来实现一个后台管理。

### vue-element-admin简介

简单介绍一下，vue-element-admin一个后台集成解决方案，它基于 Vue.js 和 element，功能：

```
- 登录/注销
- 权限验证
- 多环境发布
- 动态侧边栏（支持多级路由）
- 动态面包屑
- 国际化多语言
- 多种动态换肤
- 快捷导航(标签页)
- 富文本编辑器
- Markdown编辑器
- JSON编辑器
- Screenfull全屏
- 列表拖拽
- Svg Sprite 图标
- Dashboard
- 本地mock数据
- Echarts 图表
- Clipboard(剪贴复制)
- 401/404错误页面
- 错误日志
- 导出excel
- 导出zip
- 前端可视化excel
- 树形table
- Table example
- 动态table example
- 拖拽table example
- 内联编辑table example
- Form example
- 二步登录
- SplitPane
- Dropzone
- Sticky
- CountTo
- Markdown2html
```
记录一下关于登录及动态权限二次开发。

### 1、vue-element-admin登录及动态权限

(1) 用账号和密码换取token，并将token存入cookie中，并将token设置在请求头中

(2) 使用token获取用户role_id

(3) 通过role_id与前端预先配置好的路由权限进行匹配，得到用户导航（主要使用**router.addRoutes**(routes)和router中的meta属性）

(4) 每次路由切换（初始化），都会先通过导航守卫（router.beforeEach）进行处理
-   判断是否存在token
      1. 存在，判断role_id是否存在，不存在则重新拉取(从后端请求)用户信息，获得role_id，存在，跳转至指定路由
      2. 不存在，重定向至登录页面

### 2、修改登录及动态权限

考虑到用户角色对应的权限会进行更改，用户对应的导航就从后端获取。

(1)使用账号和密码换取token及相关的用户信息（含有role_id），并将token设置在请求头中同时保存在cookie中,将用户信息存在localstorage(不提倡)

(2)根据role_id请求用户导航权限（json对象），将json对象处理成router格式，使用**router.addRoutes**挂载原来路由对象上

(3)每次路由切换（初始化），都会先通过导航守卫进行处理

- 判断是否存在token
    1. 存在，判断localstorage中是否存在用户信息，存在则请求用户导航
    2. 不存在，重定向至登录页面

### 流程缺陷

1. 用户信息直接存localstorage，直接暴露role_id，会有越权问题
2. 用户信息更新不及时。在两台电脑上都登录过，在一台电脑更新了用户信息，使用另一台登录，用户信息不会马上更新。

