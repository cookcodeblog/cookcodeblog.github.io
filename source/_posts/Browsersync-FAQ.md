---
title: Browsersync FAQ
tags: [Browsersync, Intellij]
categories: [写码]
date: 2017-06-29 00:00:33
---

Browsersync可以用来监控HTML, JS和CSS的改动，从而触发浏览器自动刷新，来帮助我们调试Web页面，节约时间 （因为每次都要按`F5`很烦）。

但是Browsersync也有一些**坑**需要注意。

<!-- more -->

## 设置默认打开Google Chrome


Windows上默认浏览器是IE，但是Web开发时用的是Google Chrome浏览器，可以通过以下设置Browsersync默认打开Google Chrome浏览器：

```
browser: "chrome"
```

**[坑]** [Browsersync Options](https://www.browsersync.io/docs/options)说明要设置成 `browser: "google chrome"`，但是这样在Windows下会报找不到google chrome的错


## Browsersync 等了很久才重新加载

在Intellij上调试页面时，发现修改HTML文件后，Browersync等了差不多2分钟才reload。

刚开始怀疑需要配置Browsersync时间间隔，后来才明白原来Intellij默认的自动保存的`safe write`模式会先将文件的改动写入到一个临时文件中，再保存到真正要改动的文件中。

而Browsersync只能监控文件的改动（last modified time 或者 cksum），所以在Intellij真正写入到文件之前，Browsersync不会触发reload。

解决方法超级简单：改动后按一下`ctrl` + `s`，让Intellj立即保存改动，就会立即触发Browsersync reload了。

> Reference

* https://www.jetbrains.com/help/idea/saving-and-reverting-changes.html