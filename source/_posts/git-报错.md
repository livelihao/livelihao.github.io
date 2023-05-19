---
title: git clone 报错及解决方案
date: 2023-05-19 10:12:28
categories:
- Git 教程 
tags:
- Git 教程
comments: true
copyright: true
---

# 报错
在使用 `git clone` 命令时，遇到以下错误.
```
fatal: unable to connect to github.com:
github.com[0: 20.205.243.166]: errno=Connection timed out
```
或者
```
fatal: unable to access 'https://github.com/xxx.git/': Encountered end of file
```

<!--more-->
# 解决方案
## 引起错误的原因：
该错误一般情况下是因为网络代理所引起的，因此解决方法可以从取消网络代理，或者使用其他的代理的角度出发.

## 方案 1
取消代理，运行命令如下.
```
git config --global --unset http.proxy 
git config --global --unset https.proxy
```
## 方案 2
将网址中的 `https` 修改为 `http` 或者 `git`，即 `http://github.com/xxx.git/` 或者 `git://github.com/xxx.git/`.

## 方案 3
在网址前面加入代理，例如 `https://ghproxy.com/`，即 `https://ghproxy.com/https://github.com/xxx.git/`.

---

# 总结
这种错误一般情况下都因为网络环境导致的，解决方案也不止上述3种，例如使用科学上网，或者关闭科学上网等都有可能解决. 也可以多种方法尝试，而且还应多试几次，都可能解决.
