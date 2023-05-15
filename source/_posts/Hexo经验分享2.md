---
title: Hexo 经验分享(2) | NexT 主题设置
date: 2023-05-12 11:26:28
categories:
- Hexo 教程 
tags:
- Hexo 教程
- 博客教程
comments: true
copyright: true
---
NexT 是一个高质量的主题模板，风格简约，非常符合审美.
在本文中，我将使用 NexT 主题对博客网站进行配置，并个性化设置博客网站.

<!-- more -->

# Hexo 主题
Hexo 主题可以通过 [Hexo themes](https://hexo.io/themes/) 来选择一个合适的主题，本网站是基于 [NexT](https://theme-next.js.org/) 主题设计并搭建.

## NexT 主题下载
`git clone https://github.com/theme-next/hexo-theme-next themes/next`
> 使用 `git` 下载主题文件，存放位置为 `/themes/next`文件夹. 

## NexT 主题启用
打开根目录的 `_config.yml` 文件，修改 `theme` 字段的 `landscape` 为 `next`. 

* 根目录的 `_config.yml` 文件被称为 **站点配置文件**，用于配置 Hexo 本身的站点信息；
* 主题文件夹（`/themes/next` 文件夹）下的 `_config.yml` 文件被称为 **主题配置文件**，用于配置主题相关信息.

执行命令重新生成静态文件，并在浏览器中打开 "http://localhost:4000"，可以预览 Hexo 博客站点使用 NexT 主题的样式，
```
hexo clean  # 清除原有文件
hexo g      # 生成静态文件
hexo s      # 本地启动 Web 服务器
```
# 个性化设置
## NexT Scheme
修改 NexT 主题外观，打开 **主题配置文件**，修改 `scheme` 字段，把要设置的主题取消注释.
```
# scheme: Muse    
# scheme: Mist    
# scheme: Pisces  
# scheme: Gemini  
```

4种 Scheme 官方描述如下；
> * Muse -> Default Scheme, this is the initial version of NexT. Uses black-white tone and mainly looks cleanly.
> * Mist -> A tighter version of Muse with a tidy single-column view.
> * Pisces -> Double-column Scheme, fresh like your neighbor's daughter.
> * Gemini -> Looks like Pisces, but have distinct column blocks with shadow to appear more sensitive to view.

## 修改网站标题、描述

打开 **站点配置文件**，修改下面的字段.
```
title: 自由笔记 # 网站标题
subtitle: ''   
description: 'Believe you can and you are halfway there.' # 网站描述
keywords:
author: Hao Li  # 作者
language: zh-CN # 网站语言
```

## 修改菜单
打开 **主题配置文件**，修改 `menu` 字段. 将要添加的界面取消注释.

```
menu:
  home: / || fa fa-home
  # about: /about/ || fa fa-user
  tags: /tags/ || fa fa-tags
  categories: /categories/ || fa fa-th
  # archives: /archives/ || fa fa-archive
  # schedule: /schedule/ || fa fa-calendar
  # sitemap: /sitemap.xml || fa fa-sitemap
  # commonweal: /404/ || fa fa-heartbeat
```

运行 `hexo new page tags` 添加 Tags 页面，编辑 `Tags/index.md`，加入 `type: "tags"`.
运行 `hexo new page categories` 添加 Categories 页面，编辑 `Categories/index.md`，加入 `type: "categories"`.


# 主题优化

## 配置社交链接

在博客上显示社交链接，例如 GitHub、Twitter 或微博等，可以在 `theme/next/_config.yml` 文件的 `social` 部分配置链接.
```
social:
  GitHub: https://github.com/livelihao || fab fa-github
  E-Mail: mailto:livehao@163.com || fa fa-envelope
```

## 添加版权信息

打开 **主题配置文件**，修改 `creative_commons`字段.
```
creative_commons:
  license: by-nc-sa
  size: small
  sidebar: false
  post: true
```
在文章头部加入 `copyright: true`.

## 修改 tag 图标
允许修改 tag 图标，打开**主题配置文件**，找到 `tag_icon`, 修改为 `true`.
```
tag_icon: true
```

## 添加文章打赏
找到主题配置文件 `_config.yml` 中的 `reward_settings` 和 `Reward` 部分，将其设置为如下.
```
reward_settings:
  enable: true
  animation: false
  comment: 您的认可是我前进的动力

reward:
  wechatpay: /images/wechatpay.png
  alipay: /images/alipay.jpg
```

## 添加字数统计功能
1. 运行命令 `npm install hexo-wordcount --save` 安装插件 `hexo-wordcount`
2. 运行命令 `npm install hexo-symbols-count-time --save` 安装插件 `hexo-symbols-count-time`
3. 修改**主题配置文件**
```
symbols_count_time:
  separated_meta: true     # 是否另起一行（true的话不和发表时间等同一行）
  item_text_post: true     # 首页文章统计数量前是否显示文字描述（本文字数、阅读时长）
  item_text_total: false   # 页面底部统计数量前是否显示文字描述（站点总字数、站点阅读时长）
  awl: 4                   # Average Word Length
  wpm: 275                 # Words Per Minute（每分钟阅读词数）
  suffix: mins.

post_wordcount:
  item_text: true
  wordcount: true         # 单篇 字数统计
  min2read: true          # 单篇 阅读时长
  totalcount: false       # 网站 字数统计
  separated_meta: true
```


# 参考

[NexT 主题设置](https://theme-next.js.org/docs/theme-settings/)
[Hexo 添加字数统计和阅读统计](https://blog.csdn.net/qq_44082148/article/details/105701427)




