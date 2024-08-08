---
title: jQuery-Event
date: 2024-08-07 14:54:46
tags: [jQuery]
categories: 
- JavaScript
---
## 4种常见的jQuery事件

## jQuery事件的绑定和解绑

#### 单个事件注册

可重复事件注册：`$('div').clickEvent(function() { xxx });`

单次事件注册：`$('div').one(clickEvent, function() { xxx });`

clickEvent: click, mouseenter, mouseleave, etc...

#### 多个事件注册

On的优势1：可以一次性注册多个事件

```
$('div').on({
    click: function() { xxx },
    mouseenter: function() { xxx }
})
```

On的优势2：可以事件委 --- 把原来加给子元素身上的事件绑定在父元素身上

`$('father').on('click', 'son', function() { xxx });`

On的优势3：可以给动态生成的元素进行事件绑定

```
$("ol").on("click", "li", function() {
    alert (11);
})
var li = $("<li>我是后来创建的</li>");
$("ol").append(li);  // 这里的li同样会绑定click function
```

#### 事件解绑

`$('div').off()` --- 解除全部

`$('div').off('click')` --- 解除div上的click

`$('ol').off('click', 'li')` --- 解除 ol 里 li 的 click

## 自动触发事件

`element.click()`

`element.trigger('click')`

`element.triggerHandler('click')` --- 不会触发元素的默认行为

## jQuery的其他方法

#### 对象拷贝

`$.extend([deep], target, object1, [objectN])`

deep：如果设为true为深拷贝,默认为false浅拷贝

target：要拷贝的目标对象

object1：待拷贝到第一个对象的对象

#### 多库共存

其他js库也会使用`$`作为标识符，导致冲突 --- 使用`jQuery`来代替`$`

#### jQuery插件 --- www.jq22.com

懒加载：当页面滑动到可视区域的时候再加载图片

bootstrap
