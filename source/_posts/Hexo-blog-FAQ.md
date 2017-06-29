---
title: Hexo blog FAQ
date: 2017-06-21 01:39:21
tags: [Hexo, blog, GitHub]
categories: 写码 
toc: true
---

用Hexo和GitHub pages搭建个人独立博客遇到的坑。

<!-- more -->

### Q: 怎么设置我的独立域名博客 ###

1) 注册一个你喜欢的域名，比如我在阿里云（万网）上注册了cookcode.me的域名

2) 注册一个GitHub账号，创建一个专门用来作博客的repository，比如:

   ```
   GitHub账号: cookcodeblog
   
   博客repository: cookcodeblog.github.io
   ```
   
3) 在阿里云（万网）上设置域名解析:
   
   ```
   A 
        192.30.252.154
        192.30.252.153

   CNAME
        www
            cookcodeblog.github.io
	```
   
4) 在GitHub上点击`repository` -> `settings`, 拉到 GitHub Pages的地方可以在custom domain中输入域名。
   
   **坑： 这个设置只对本地浏览器有用，清除浏览器数据后，这个设置就不起作用了！！** 
   
5) 正确的做法是在hexo的`source`目录创建一个CNAME文件，输入域名，比如：
   ```
   cookcode.me
   ```
   
   在运行`hexo generate`后，这个CNAME文件会被生成到`public`目录，在运行`hexo deploy`后，这个	CNAME文件会被部署到博客repository的`master`的根目录，并且永久生效。
   
 



