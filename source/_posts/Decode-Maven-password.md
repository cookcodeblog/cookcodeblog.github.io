---
title: Decode Maven password
tags: [Maven, Nexus, Hash, Decode]
categories: [写码]
date: 2017-07-11 22:44:25
---

Maven通过`~/.m2`下的`settings.xml`和`settings-security.xml`来存储加密密码，在连接Nexus时，先解密`settings-security.xml`中的master的密码，再用master的明文密码去解密`settings.xml`中的Nexus的用户密码。

Maven使用了`SHA-256`和`AES/CBC/PKCS5Padding`来计算哈希值和加密，从表面上好像很安全，其实不然，因为从理论上讲只要知道了`salt`, `key`和加密程序，就可以把密文解密出来。而`salt`, `key`和加密程序都定义在Maven用到的`org.sonatype.plexus.components.cipher`包中。

Maven自己的官网[Maven Encryption](https://maven.apache.org/guides/mini/guide-encryption.html)上也写了以下提示：

> Also note that the encrypted passwords can be decrypted by someone that has the master password and settings security file. Keep this file secure (or stored separately) if you expect the possibility that the settings.xml file may be retrieved.

只要知道了`settings.xml`和`settings-security.xml`的密文，很容易就可以使用[maven-settings-decoder](https://github.com/jelmerk/maven-settings-decoder)来解密出来。你也可以参考`maven-settings-decoder`开发一个Maven的plugin来专门解密Maven的密码。

扩展阅读：

* [How to encrypt the user password correctly](http://www.infoq.com/cn/articles/how-to-encrypt-the-user-password-correctly)
* [Develop Maven plugin](https://maven.apache.org/guides/plugin/guide-java-plugin-development.html)

