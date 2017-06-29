---
title: Enable Node support in Intellij
tags: [Intellij, NodeJS, npm]
categories: [写码]
date: 2017-06-29 23:32:30
---

1. 安装`NodeJS`插件
2. 打开 File / Settings / Languages & Frameworks / Node.js and NPM
3. 在Node Interpreter中选择正确版本的node.exe
4. 在Coding Assistance中`Enable` Node.js Core library

如果第4步Enable Node.js Core library失败，可能是选择的Node版本Intellij还不支持，有一个临时解决方法:

1. 打开 File / Settings / Languages & Frameworks / JavaScript / Libraries
2. 点击`Download`按钮
3. 在TypeScript community stubs下选择node

这个临时解决方法的不好处就是每个project都需要重新设置一遍。