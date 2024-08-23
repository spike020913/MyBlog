---
title: DOM
date: 2024-07-31 12:22:21
tags: [DOM]
categories: 
- JavaScript
---
## DOM是什么？

文档对象模型（DOM）是一个网络文档的编程接口。它代表页面，以便程序可以改变文档的结构、风格和内容。DOM 将文档表示为节点和对象 --- 这样，编程语言就可以与页面交互，但DOM 不是 JavaScript 语言的一部分，是用于建立网站的 WebAPI。

网页是一个既可以在浏览器窗口中显示，也可以作为 HTML 源代码的文档。在这两种情况下，它都是同一个文档，但文档对象模型（DOM）的表示方式使它可以被操作。作为一个面向对象的网页表示，它可以用脚本语言（如 JavaScript）进行修改。

## DOM的数据类型

* Document: 当一个成员返回 `document` 对象（例如，元素的 `ownerDocument` 属性返回它所属的 `document`），这个对象就是 root `document` 对象本身。
* Node: 位于文档中的每个对象都是某种类型的节点。在一个 HTML 文档中，一个对象可以是一个元素节点，也可以是一个文本节点或属性节点。
* Element: `element` 类型是基于 `node` 的。它指的是一个元素或一个由 DOM API 的成员返回的 `element` 类型的节点。例如，我们不说 [`document.createElement()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/createElement) 方法返回一个 `node` 的对象引用，而只是说这个方法返回刚刚在 DOM 中创建的 `element`。
* nodeList: `nodeList` 是由元素组成的数组，如同 `document.querySelectorAll()` 等方法返回的类型。`nodeList` 中的条目通过索引有两种方式进行访问： `list.item(1)` / `list[1]`由元素组成的数组。
* Attr: 当 `attribute` 通过成员函数（例如通过 `createAttribute()` 方法）返回时，它是一个为属性暴露出专门接口的对象引用。

## DOM的核心接口

* [`document.querySelector()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/querySelector)
* [`document.querySelectorAll()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/querySelectorAll)
* [`document.createElement()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/createElement)
* [`Element.innerHTML`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/innerHTML)
* [`Element.setAttribute()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/setAttribute)
* [`Element.getAttribute()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/getAttribute)
* [`EventTarget.addEventListener()`](https://developer.mozilla.org/zh-CN/docs/Web/API/EventTarget/addEventListener)
* [`HTMLElement.style`](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLElement/style)
* [`Node.appendChild()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Node/appendChild)
* [`window.onload`](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/load_event "window.onload")
* [`window.scrollTo()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/scrollTo)

## 注册事件的两种方式

1. 传统 --- `btn.onclick = function()`
2. 最新 --- `btn.addEventListener(type, listener, useCapture)`
   type --- 'click', 'mouseover'等事件性字符串
   listener --- 事件处理函数
   useCapture --- true 对应 在捕获阶段操作 / false 对应在冒泡阶段操作 / 默认为false

## 删除事件的两种方式

1. 传统 --- `btn.onclick = null;`
2. 最新 --- `btn.removeEventListener(type, listener)`
   ```点一次就消失
   btn.addEventListener('click', fn)

   function fn() = {
     alert(!);
     btn.removeEventListener('click', fn);
   }
   ```

## DOM事件流的三个阶段

1. 事件流描述的是页面中接受事件的顺序。
2. 而事件发生时会在元素节点之间按照特定的顺序传播，这个传播的过程就是**DOM事件流**
3. 三个阶段分别为：
   捕获: document -> html -> body -> div -> xxx
   当前: xxx -> target
   冒泡 target -> xxx -> div -> body -> html -> document

## 事件对象

1. 什么是事件对象？

   ```
   div.addEventListener('click', function(e) {
       console.log(e)
   })

   // 1. event 就是一个事件对象，写到侦听函数的小括号里面，当形参来看
   // 2. 事件对象只有有了事件才会存在，它是系统给我们自动创建的，不需要我们传递参数
   // 3. 事件对象是我们事件的一系列相关数据的集合跟事件相关的，如鼠标点击里面就包含了鼠标的相关信息，鼠标坐标啊，如果是键盘事件里面就包含的键盘事件的信息
   // 4. 这个事件对象我们可以自己命名 比如 event 、 evt、 e

   ```
2. event.target 和 this的区别:

   ```
   var ul = document.querySelector('ul');
   ul.addEventListener('click', function(e) {
       // 我们给ul 绑定了事件 那么this 就指向ul
       console.log(this);
       // e.target 指向我们点击的那个对象 谁触发了这个事件 我们点击的是li e.target 指向的就是li
       console.log(e.target);
   })
   ```
3. 阻止默认事件：`event.preventDefault();`
4. 阻止冒泡：`event.stopPropagation();`

## 事件委托原理

不给每个子节点单独设置事件监听器，而是在父节点上设置，然后利用冒泡原理来影响每个子节点

Eg: 一个ul下有很多li，点击li后，会冒泡到ul上，ul上有注册事件，所以会触发事件监听器 -> 只用了一次DOM，大幅提升效率

### 获取元素

1. `getElementByID()` --- 获取一个
2. `getElementByTagName()` --- 返回带有指定tag的集合

   ```
   <li>1<li>
   <li>2<li>
   <li>3<li>
   var lis = document.getElementByTagName('li')
   lis = 3个li
   ```
3. `getElementsByClassName()`
4. `querySelector()`, `querySelectorAll()` --- 返回指定选择器的第一个对象/全部对象

   ```
   var nav = document.querySelector('.class') --- class 为 class
   var id = document.querySelector('#id') --- id 为 id
   var li = document.querySelector('li') --- block type 为 li
   ```
5. 获取body --- `document.body`
6. 获取html --- `document.documentElement`

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

* `element.xxx` -> 能得到元素本身内置的属性xxx
* `element.getAttribute` -> 能得到元素本身/自定义属性
* `element.setAttribute` -> 设置的自定义属性,但必须"data-"开头
* `element.dataset` -> 能得到元素全部的自定义属性

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
