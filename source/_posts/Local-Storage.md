---
title: Local Storage
date: 2024-08-05 17:45:37
tags:
---
## sesstionStorage

1. 生命周期为关闭浏览器窗口
2. 在同一个页面下数据共享
3. 以key - value 方式存储
4. 修改数据的方式为
   `sessionStorage.setItem(key, value)`,
   `removeItem(key)`,
   `getItem(key)`,
   `clear()`

## localStorage

1. 永久生效
2. 多窗口共享，同一浏览器可以共享
3. 修改数据方式与sessionStorage相同

## 二者之间唯一区别就是共享方式的区别
