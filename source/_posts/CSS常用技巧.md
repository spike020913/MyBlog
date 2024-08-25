---
title: CSS常用技巧
date: 2024-08-24 14:09:55
tags:
categories:
- CSS
---
## 圆角边框

`border-radius: length;`

- 参数值可以为数值或百分比的形式
- 如果是正方形，想要设置为一个圆，把数值修改为高度或者宽度的一半即可，或者直接写为 50%
- 该属性是一个简写属性，可以跟四个值，分别代表左上角、右上角、右下角、左下角
- 分开写：border-top-left-radius、border-top-right-radius、border-bottom-right-radius 和border-bottom-left-radius

## 清除浮动推荐方法

给父元素添加

```css
 .clearfix:before,.clearfix:after {
   content:"";
   display:table; 
 }
 .clearfix:after {
   clear:both;
 }
 .clearfix {
    *zoom:1;
 }   
```

## 垂直居中方法

1. ```javascript
   1
   ```
2. ```javascript
   1
   ```
3. ```javascript
   1
   ```

## 清除所有元素内外边距

```java
* {
    margin: 0;
    padding: 0;
}
```

##
