---
title: PC端常见网页特效
date: 2024-08-02 14:00:58
tags:
---
## offset属性

1. **offset常用方法**
   {% asset_img 1722578573515.png %}
2. **offset和style的区别**
   {% asset_img 1722579532992.png %}
   **案例为京东/淘宝预览图得预览框**

## client属性

{% asset_img 1722587548341.png %}

## scroll属性

{% asset_img 1722589391368.png %}

**相关案例： 侧边栏先是绝对定位，然后变成固定定位 --- 页面下滑的时候，通过读取element.scrollTop 和 window.pageYoffset来确定什么变成固定定位**

## 简单总结offset, client 和 scroll：

{% asset_img 1722589983352.png %}

1. Offset --- 常用于获取元素位置      offsetLeft offsetTop
2. Client --- 常用于获取元素大小      clientWidth clientHeight
3. Scroll --- 常用于获取滚动距离      scrollTop scrollLeft
4. 页面滚动距离通过window.pageYoffset/Xoffset来决定

## 封装动画函数

## 网页轮播图案例
