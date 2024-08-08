---
title: JavaScript中的DOM
date: 2024-07-31 12:22:21
tags: [JavaScript]
---
### DOM是什么？

是一种可以改变网页结构样式布局的一种

### 获取元素

1. getElementByID() --- 获取一个
2. getElementByTagName() --- 返回带有指定tag的集合

   ```
   <li>1<li>
   <li>2<li>
   <li>3<li>
   var lis = document.getElementByTagName('li')
   lis = 3个li
   ```
3. getElementsByClassName()
4. querySelector(), querySelectorAll() --- 返回指定选择器的第一个对象/全部对象

   ```
   var nav = document.querySelector('.class') --- class 为 class
   var id = document.querySelector('#id') --- id 为 id
   var li = document.querySelector('li') --- block type 为 li
   ```
5. 获取body --- document.body
6. 获取html --- document.documentElement

### 事件基础

1. 事件三要素
   1. 获取事件源
   2. 注册事件类型
   3. 添加事件处理程序

### 操作元素

1. InnerText和InnerHTML的区别:
   InnerText不识别HTML标签，InnerHTML可以识别出HTML标签，通常会用InnerHTML
   都用来更改元素内容

```
innerText: "<strong>TEST<strong>" = "<strong>TEST<strong>"
innerHTML: "<strong>TEST<strong>" = "TEST" (but bigger)
```

2. src,  href, id, title, alt等block中的属性都可以通过这两个修改
3. 在操作元素中定义函数时，this指的是事件函数的调用者，即
   ```
   btn.onclick = function() {
     this.disable = true;
     这里的this指的就是btn
   }
   ```
4. 修改元素的大小，颜色，位置
   ```
   element.style.background = xxx;    --- 样式比较少的更改用style直接改
   element.className = "xx";          --- 样式比较多的建议直接换class
   ```
5. 排他思想 --- 先把其他全部还原，最后改目标元素

### 获取元素

* element.xxx -> 能得到元素本身内置的属性
* element.getAttribute -> 能得到元素本身/自定义属性
* element.setAttribute -> 设置的自定义属性,但必须"data-"开头
* element.dataset -> 能得到元素全部的自定义属性

```
element.setAttribute("data-index", 1)
element.setAttribute("data-name", "Jeff")
element.dataset = {'index': 1, 'name': "Jeff"}
```

### 节点操作

1. 获取父节点/子节点的方式v

   ```
   var a = document.querySelector('a');
   var parent = a.parentNode;
   var child = a.childNodes;
   ```
2. 获取兄弟节点

   ```
   a.nextSibling -> 包含文本+元素节点
   a.nextElementSibling -> 只要元素节点
   ```
3. 创建/删除节点

   ```
   var node = document.createElement("div");
   var xxx = document.createElement("li");
   node.appendChild(xxx); --- 加到末尾
   node.insertBefore(xxx); --- 加到最前
   node.removeChild(xxx); --- 删除节点
   ```
4. 复制节点

   ```
   node.cloneNode() --- 浅拷贝，只拷贝自己
   node.cloneNode(true) --- 深拷贝，拷贝自己和自己的子节点
   ```
