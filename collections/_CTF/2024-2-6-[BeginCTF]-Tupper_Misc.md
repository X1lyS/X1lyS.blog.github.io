---
title: BeginCTF-Tupper
category: CTF-Misc
date: 2024-2-6
---


> source:[BeginCTF]Tupper

## Learn

Tupper’s self-referential formula（茶泊尔的自指公式）是一个以计算机图像形式呈现出自身的数学公式。这个公式是由Jeff Tupper在2001年提出的。公式描述了在二维平面上的一个巨大的矩形区域，其中的每个像素点根据公式的计算结果来决定其颜色。公式本身定义了一个特定的函数，该函数会将坐标(x, y)的像素点映射为0或1。当这个函数的图像在指定的矩形范围内显示出来时，它会精确地呈现出自身的数学表达式。

## Info

672个txt文件，内容是少许数字与字母，最后一个txt中发现了=，文件个数为4的倍数，推测是base64编码

## EXP

- 合并672个txt文件为一个可写脚本，或[在线合并文件工具](https://uutool.cn/txt-merge/)
- base64解码
- 得到一串数字
- [在线Tupper绘图](https://tuppers-formula.ovh/)

## Summary

```cpp
base64编码的特性
1.Base64使用一组基于ASCII字符的字符集进行编码。它仅支持64个字符（A-Z、a-z、0-9和+ /）
因此它的编码结果是大小写敏感的并且特殊字符有时会导致问题。
2.四个一组
3.结尾可能会有=
  
文件合并
  
Tupper
可以理解成一种计算机绘图公式,输入对应的数值可以计算得到目的图像，进行图像与数值之间的转换
```
