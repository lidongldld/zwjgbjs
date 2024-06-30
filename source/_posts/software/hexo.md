---
title: hexo 配置学习
date: 2024-06-24 21:52:48
tags: hexo
software: Hexo攻略
---
<!-- # 测试完成 -->
<!-- {% asset_img 2024-06-24T215559.png This is an example image %}-->

学习配置文档：
https://xiamu-ssr.github.io/Hexo/2024/06/19/2024-06-19-12-31-52/
学习视频：
https://www.bilibili.com/video/BV1xTgTemEDU/?spm_id_from=333.337.search-card.all.click&vd_source=0e3ef2750148c322d0673ff338633934

### hexo 语法
```shell
# 创建草稿 
hexo new draft aaa #其中【aaa】就是草稿名
# Hexo提供了一个预览的方法
hexo s --draft
# 正式发布博文
hexo p aaa
# 该命令的原理也不过是将文章从/source/_drafts移动到/source/_posts而已，若日后想将正式文章转为为草稿，只需手动将文章从/source/_posts目录移动到/source/_drafts目录即可
```