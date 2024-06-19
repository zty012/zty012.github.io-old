---
title: 解决Nginx无效证书
date: 2024-06-19 18:10:29
---

首先来看这个证书：

```
-----BEGIN RSA PRIVATE KEY-----\n
MII...SMC\n
-----END RSA PRIVATE KEY-----
```

```
-----BEGIN CERTIFICATE-----\n
MII...FPY\n
-----END CERTIFICATE-----\n
-----BEGIN CERTIFICATE-----\n
MII...0g==\n
-----END CERTIFICATE-----
```

很正常对吧，我们把它放到nginx里面，报错了，报错信息很长这里就不写了，大致内容是无法解析`nginx.conf`

如果用的1panel，会提示`x509: malformed serial number`

why???明明是正常的证书但是用不了，这就涉及到解析时的问题了，具体什么原因我也懒得看nginx源码了，直接给出解决方案：

在秘钥（key文件）最后加一个换行（`\n`）就行了
