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

**相关案例： 侧边栏先是绝对定位，然后变成固定定位 --- 页面下滑的时候，通过读取`element.scrollTop` 和 `window.pageYoffset`来确定什么变成固定定位**

## 简单总结offset, client 和 scroll：

{% asset_img 1722589983352.png %}

1. Offset --- 常用于获取元素位置      offsetLeft offsetTop
2. Client --- 常用于获取元素大小      clientWidth clientHeight
3. Scroll --- 常用于获取滚动距离      scrollTop scrollLeft
4. 页面滚动距离通过window.pageYoffset/Xoffset来决定

## 封装动画函数

```
function animate(obj, target) {
    clearInterval(obj.timer)
    obj.timer = setInterval(function() {
         var step = (target - obj.offsetLeft) / 10;
         step = step > 0 ? Math.ceil(step) : Math.floor(step);
         if (obj.offsetLeft == target) clearInterval(obj.timer);
         obj.style.left = obj.offsetLeft + step + 'px';
    }, 15)
}
```

## 网页轮播图案例

1. 无缝滚动 --- 最后一张图后面加上第一张图的复制，到了第一张图的复制哪里如果继续点击next的话会先强制设置left到第一个，然后再正常进行缓动动画跳到第二个.
2. 自动轮播 --- 鼠标离开box，开启定时器，每x秒调用点击事件；鼠标在box上，取消定时器。
3. 节流阀 --- 防止轮播图轮播过快：一个结束，第二个才能开始，设置一个全局变量，之后回调的时候更改
