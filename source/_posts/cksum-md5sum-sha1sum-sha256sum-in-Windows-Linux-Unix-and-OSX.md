---
title: 'cksum md5sum sha1sum sha256sum in Windows, Linux, Unix and OSX'
tags: [cksum, md5sum, sha1sum, sha256sum]
categories: [写码]
date: 2017-07-09 08:21:37
---

在下载文件，或者上传文件时需要检查文件的`sum`来确保文件的完整性。

## Windows

在Windows上可以通过Windows内置的`certutil`命令来计算：

```bat
certutil -hashfile file1 MD5
certutil -hashfile file1 SHA1
certutil -hashfile file1 SHA256
```
但是`certutil`命令不支持计算`cksum`，如果Windows上安装了Git，则可以用Git Bash来执行`cksum file1`。

## Linux/Unix

Linux/Unix 提供了各种`sum`的命令来计算：

```bash
cksum file1
md5sum file1
sha1sum file1
sha256sum file1
```

如果Windows上安装了Git，也可以用Git Bash来执行上述命令。

## Mac OS X

在 Mac OS X上，`cksum`和`md5`是单独的命令，`shasum`则可以用来计算各种`sha`算法的`sum`:

```bash
cksum file1
md5 file1
shasum -a 1 file1
shasum -a 256 file1
```

## OpenSSL

如果在Linux／Unix，或Mac OS X上安装了`openssl`，可以用`openssl`来计算`md5`和各种`sha`的`sum`:

```bash
openssl dgst -MD5 file1
openssl dgst -SHA1 file1
openssl dgst -SHA256 file1
```