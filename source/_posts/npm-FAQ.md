---
title: npm FAQ
tags: [npm, gulp, PhantomJS]
categories: [写码]
date: 2017-06-29 23:02:04
---

整理一些使用npm过程中遇到的**坑**

<!-- more -->

## npm install 401 unauthorized

npm install 401 unauthorized 的错从字面上看是访问npm组件库时没有授权的错误，但是实际的可能性有：

* 如果连接的是公司专门的registry，需要检查`~/.npmrc`有没有按照要求设置了，特别是修改密码后需要同步修改`~/.npmrc`
* 如果是在国内连接公共的npm库，可以考虑用[cnpm](https://npm.taobao.org) 镜像
* 如果只是在项目目录运行`npm install`才会失败，检查一下`package.json`是否有语法错误
* 尝试清一下缓存`npm cache verify`
* 检查一下npm的版本，试着退回到旧版本，或者安装[NodeJs LTS](https://nodejs.org/en/) 版本看看

## npm 重装后找不到 gulp

重新安装npm后，如果找不到gulp，只需要重新安装一下gulp就可以了：

```
npm install -g gulp
```

## npm install PhantomJS failed

如果`npm install phantomjs-prebuilt`失败，需要先安装 [PhantomJS binary](https://nodejs.org/en/)，然后添加PhantomJS到PATH环境变量，再重新运行`npm install phantomjs-prebuilt`。

```bash
export PHANTOMJS_HOME=/Users/cookcode/tools/phantomjs
export PATH=$PHANTOMJS_HOME/bin:$PATH
```

