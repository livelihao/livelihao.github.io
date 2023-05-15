---
title: Hexo 经验分享(4) | Hexo 数学公式渲染
date: 2023-05-15 11:19:03
categories:
- Hexo 教程 
tags:
- Hexo 教程
- 博客教程
- kramed 
comments: true
copyright: true
---


在使用 `markdown` 编写文章时，有些公式并不能正确显示. 在配置网站时，这个问题困扰了好久，解决方法和网上有些不同，
遇到的问题是，本地的 `markdown` 公式在本地正确地显示，在网站上行间公式既不显示，也不渲染.

<!--more-->

结合网上的一些办法，做了以下操作
# 更换渲染引擎
```
npm uninstall hexo-renderer-marked --save
npm install hexo-renderer-kramed --save
```
# 渲染避免冲突
进入 `kramed` 目录，修改 `\node_modules\kramed\lib\rules\inline.js`.
修改下列两行
```
//  escape: /^\\([\\`*{}\[\]()#$+\-.!_>])/,
  escape: /^\\([`*\[\]()#$+\-.!_>])/
```
```
//  em: /^\b_((?:__|[\s\S])+?)_\b|^\*((?:\*\*|[\s\S])+?)\*(?!\*)/,
  em: /^\*((?:\*\*|[\s\S])+?)\*(?!\*)/
```
# 配置文件开启 MathJax
```
math:
  # Default (false) will load mathjax / katex script on demand.
  # That is it only render those page which has `mathjax: true` in front-matter.
  # If you set it to true, it will load mathjax / katex script EVERY PAGE.
  enable: true
  every_page: true

  mathjax:
    enable: true
    # Available values: none | ams | all
    tags: none
    per_page: true

  katex:
    enable: true
    # See: https://github.com/KaTeX/KaTeX/tree/master/contrib/copy-tex
    copy_tex: true
```
# 行间公式修改
` $$ a + b = c $$` 修改为 ` \$$ a + b = c \$$`.
至此，行间公式就可以正常显示了.

# 参考

* [Hexo 中渲染 MathJax 数学公式](https://blog.csdn.net/qq_44846324/article/details/114582328)