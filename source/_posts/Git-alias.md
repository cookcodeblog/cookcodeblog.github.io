---
title: Git alias
tags: [Git]
categories: [写码]
date: 2017-06-28 23:48:02
---

写码时，在Intellij里把Terminal设置成Git bash （Mac上不需要设置，所以说Mac用来写码就是happy），然后就可以在Terminal里面愉快的敲Git命令了。

可以将常用的Git命令作为alias保存在`~/.profile` (取决于你用什么bash，比如我在Mac上用的是`zsh`，那么我的profile其实是`.zshrc`)，这样每次敲入命令时就可以少打点字，也可以作为一个备忘。

> 懒惰是程序员的美德

下面是我常用到的Git命令的alias：

```bash
# git alias
alias gs='git status'
alias ga='git add'
alias gc='git commit -m'
alias gp='git push origin'
alias gd='git diff'
# switch to an existing branch
alias go='git checkout'
# switch to a new branch
alias gob='git checkout -b'
alias gl='git log --graph --decorate --oneline'
# replace local file
alias gr='git checkout --'
```

保存到profile文件后，记得运行`source ~/.profile` 来让设置在当前Terminal生效，或者重新开一下Terminal也可以。


