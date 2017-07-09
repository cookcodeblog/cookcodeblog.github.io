---
title: Bower FAQ
tags: [Bower]
categories: [写码]
date: 2017-07-02 16:57:32
---

## 5分钟Bower入门

[使用Bower管理客户端依赖](https://segmentfault.com/a/1190000000349555)

## bower.json and .bower.json

Bower的客户端依赖都放在`bower_components`目录中。

在每个component下面都有一个`bower.json`和`.bower.json`，这两者有什么区别？

简单的来讲：

### `bower.json` 是compoent的内部开发者来维护的依赖关系

比如我们项目开发时，会在项目根目录下的`bower.json`中维护客户端依赖关系。

### `.bower.json` 是component的外部使用者可以来修改的依赖关系

比如使用gulp集成bower来inject依赖的js文件到index.html时，gulp的`main-bower-file`插件读取的就是component的`.bower.json`。如果发现js文件的inject顺序不对时，需要修改component的`.bower.json`中的`dependencies`。



