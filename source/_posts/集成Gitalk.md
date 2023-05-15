---
title: Hexo 经验分享(3) | 评论系统实现
date: 2023-05-12 11:26:28
categories:
- Hexo 教程 
tags:
- Hexo 教程
- 博客教程
- Gitalk
comments: true
copyright: true
---

Gitalk 利用了 GithubAPI 基于 GitHub Issue 和 Preact 开发的评论插件，官方网址： https://gitalk.github.io.
NexT 集成 Gitalk 评论系统，因此实现评论功能非常方便.

<!--more-->


# Gitalk 评论系统
NexT 集成 Gitalk 评论系统，其特性为
* 使用 GitHub 登录
* 支持多语言 [en, zh-CN, zh-TW, es-ES, fr, ru]
* 支持个人或组织
* 无干扰模式（设置 distractionFreeMode 为 true 开启）
* 快捷键提交评论 （cmd|ctrl + enter）

# 注册 Gitalk 应用
打开 https://github.com/settings/applications/new，输入名称，输入描述，输入网站url.
![](1684115875788.png)


# Gitalk 配置
打开**主题配置文件**，修改 `gitalk`字段. 
```
gitalk:
  enable: true
  github_id: livelihao # GitHub repo owner
  repo: livelihao.github.io # Repository name to store issues
  client_id:  # GitHub Application Client ID
  client_secret:  # GitHub Application Client Secret
  admin_user: livelihao # GitHub repo owner and collaborators, only these guys can initialize gitHub issues
  distraction_free_mode: true # Facebook-like distraction free mode
  # When the official proxy is not available, you can change it to your own proxy address
  proxy: https://cors-anywhere.azm.workers.dev/https://github.com/login/oauth/access_token # This is official proxy address
  # Gitalk's display language depends on user's browser or system environment
  # If you want everyone visiting your site to see a uniform language, you can set a force language value
  # Available values: en | es-ES | fr | ru | zh-CN | zh-TW
  language: zh-CN
```
如果不需要评论，在文章头部加入 `comments: flase` 关闭评论.

# 遇到的问题
> 未找到相关的issue进行评论，请联系@XXX初始化创建.
解决办法：出现这总情况是因为博主未给文章评论初始化，博主只需要登录 GitHub 账户即可.

# 参考
[Hexo 集成 Gitalk 评论系统](https://www.jianshu.com/p/02fc71f3633f)
