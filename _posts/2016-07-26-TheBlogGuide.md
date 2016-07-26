---
layout: post
title: 本博客模板使用手册
tags: 教程
---

## 获取模板
```git
git clone https://github.com/Robinyao/Robinyao.github.io
```

## 初始化博客

* 修改网站配置文件
> 修改 `_config.yml` 内容
```yml
name: 博客名称
description: 博客描述
url: 博客地址
avatar: 头像地址
```

* 清空博客文章
> 删除 `_posts/` 目录下的所有文件

* 修改评论框
> 在 `_includes/commentbox` 中填入评论框代码（建议使用[多说](http://duoshuo.com)）

## 自定义

* 在 `_includes/blog-stat` 中填入网站统计代码

* 在 links.md 中增加一条友情链接：
```liquid
{% include link name="" link="url" desc="" %}
```

* 链接到指定的友情链接：
```liquid
{% include friend name="" %}
```

* 增加一张 Github Card：
```liquid
{% include github-card repo="owner/repo-name" %}
```
