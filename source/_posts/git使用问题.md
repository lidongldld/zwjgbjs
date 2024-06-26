---
title: git 使用问题收集
date: 2024-06-27T00:28:59+08:00
tags: git
---

## 1、github 网络连接不上
使用 watt toolkit 加速器即可解决。
<!-- ![2024-06-27T003707](2024-06-27T003707.png) -->
{% asset_img 2024-06-27T003707.png 加速器勾选情况 %}-
## 2、使用了watt toolkit加速器 push总会失败。
### 报错内容如下：
```text
fatal: unable to access 'https://github.com/lidongldld/zwjgbjs.git/': SSL certificate problem: unable to get local issuer certificate
```
### 解决办法：
自签名SSL证书或内部测试证书，可以使用git config命令禁用SSL验证，但这会降低安全性：
```shell
git config --global http.sslVerify false
```