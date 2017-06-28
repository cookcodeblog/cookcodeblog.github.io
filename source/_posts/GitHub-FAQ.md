---
title: GitHub FAQ
date: 2017-06-22 00:03:29
tags: [GitHub, Git]
categories: 随笔
---

使用GitHub过程中遇到的坑。

<!-- more -->

### Q: 重启电脑后 Permission denied (public key) ###

1) 首先需要检查能不能ssh到GitHub

```
ssh -vT git@github.com
```

2) 如果不能，需要检查GitHub账号上的SSH key是不是已经设置正确

3) 如果本机SSH private key文件名不是默认的id_rsa，需要检查SSH agent中是否已经有了需要用到的私钥

```
ssh-add -l
```

4) 如果没有需要用到的私钥，需要添加指定的私钥

```
ssh-add ~/.ssh/id_rsa_xxx
```

**坑：这一步添加私钥，只在SSH agent当前进程中有效，当电脑重启后，这个设置就失效了!!**

5) 为了避免每次重启电脑后失效，可以采取以下方法：

a. 在本机~/.profile 或 ~/.bash_profile 或 ~/.bashrc (取决于本机用什么bash）中添加以下命令

```
ssh-add ~/.ssh/id_rsa_xxx
```

再运行`source ~/.profile` (取决于本机用什么profile）

但是这个只对terminal起作用，对IDE（比如Intellij）不起作用。

b. 在Mac电脑上运行一下命令 (Windows上我没有测试过）：

```
ssh-add -K ~/.ssh/id_rsa_xxx
```

这个命令将指定的SSH private key添加到KeyChain中, 对terminal和IDE都起作用。


*References:*

[1] https://segmentfault.com/q/1010000000835302

[2] https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/

[3] https://help.github.com/articles/error-permission-denied-publickey/





