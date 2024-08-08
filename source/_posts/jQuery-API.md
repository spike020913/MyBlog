---
title: jQuery API
date: 2024-08-06 14:17:49
tags: [jQuery]
categories: 
- JavaScript
---
## 选择器

#### 基本和层级选择器

{% asset_img 1722926196092.png %}

jQuery有隐式迭代：把匹配的所有元素内部进行遍历循环，并给每一个元素添加css

#### 筛选选择器

{% asset_img 1722926957273.png %}

```
$(function() {
     $("ul li:first").css("color", "red");
     $("ul li:eq(2)").css("color", "blue");
     $("ol li:odd").css("color", "skyblue");
     $("ol li:even").css("color", "pink");
 })
```

#### 筛选方法

{% asset_img 1722927858101.png %}

```
<script>
        // 注意一下都是方法 带括号
        $(function() {
            // 1. 兄弟元素siblings 除了自身元素之外的所有亲兄弟
            $("ol .item").siblings("li").css("color", "red");


            // 2. 第n个元素
            var index = 2;
            // (1) 我们可以利用选择器的方式选择
            $("ul li:eq(2)").css("color", "blue");
            $("ul li:eq("+index+")").css("color", "blue");


            // (2) 我们可以利用选择方法的方式选择 更推荐这种写法
            $("ul li").eq(2).css("color", "blue");
            $("ul li").eq(index).css("color", "blue");

  
            // 3. 判断是否有某个类名
            console.log($("div:first").hasClass("current"));
            console.log($("div:last").hasClass("current"));
        });
    </script>
```

## 样式操作

#### 1. 操作css

{% asset_img 1722932175404.png %}

#### 2. 操作class

添加类：`$( "div" ).addClass("'current");`
移除类：`$( "div" ).removeClass("'current");`
切换类： `$( "div" ).toggleClass("current");`

#### jQuery里的class操作不会影响className

## 属性操作

#### 获取属性

元素自带：`prop.("属性")`

自定义：`attr.("属性")`

#### 设置属性

元素自带：`prop.("属性", "val")`

自定义：`attr.("属性", "val")`

#### data()

使用data可以在指定元素上缓存一段数据，但是刷新页面后数据就会消失

设置：`data("name", "Jeff")`

获取：`data("name")`

## 文本属性值

`html() / html("changed html")` --- 原生innerHTML

`text() / text("changed text")` --- 原生innerText

`val() / val("changed 表单 val")` --- 原生value

## 元素操作 --- 元素的增查删改

#### 遍历

由于jQuery有隐式迭代，当我们需要对同类元素做不同操作的时候就需要用到`element.each() / .each()`

`$("div").each(function (index, domEle) { xxx; })`

用于遍历所有div，但需要手动将domEle转换为jQuery对象

`$.each(object, function (index, element) { xxx; })`

## 尺寸，位置操作

#### jQuery尺寸

{%asset_img 1723008506020.png%}

#### jQuery位置

主要分为`offset()`, `position()`, `scrollTop()/scrollLeft()` 三个部分

* offset() --- 设置或返回被选元素相对于**文档**的偏移坐标
  有两个属性 `offset().top` 和 `offset().left`
  设置方法为 `offset({top:10, left: 10})`
* position() --- 设置或返回被选元素相对于**带有定位的父亲**的偏移坐标
* scrollTop() --- 设置或返回被选元素**被卷去的头部**

## 效果

#### 常见的动画效果

1. hide, show, toggle
2. slideDown, slideUp, slideToggle
3. fadeIn, fadeOut, fadeToggle
4. custom animation
5. hover = mouseEnter + mouseLeave

#### 动画队列 & 如何停止动画排队

动画一但触发，就会执行，快速多次触发多个动画排队执行，导致一些不希望的效果。

解决方法：`stop()` --- 结束上一次的动画
