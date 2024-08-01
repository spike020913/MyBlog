---
title: DOM & Event in JavaScript
date: 2024-07-31 16:48:44
tags:
---
## 注册事件的两种方式

1. 传统 --- btn.onclick = function()
2. 最新 --- btn.addEventListener(type, listener, useCapture)
   type --- 'click', 'mouseover'等事件性字符串
   listener --- 事件处理函数
   useCapture --- true 对应 在捕获阶段操作 / false 对应在冒泡阶段操作 / 默认为false

## 删除事件的两种方式

1. 传统 --- btn.onclick = null;
2. 最新 --- btn.removeEventListener(type, listener)
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
3. 阻止默认事件：event.preventDefault();
4. 阻止冒泡：event.stopPropagation();

## 案例

## 事件委托原理

不给每个子节点单独设置事件监听器，而是在父节点上设置，然后利用冒泡原理来影响每个子节点

Eg: 一个ul下有很多li，点击li后，会冒泡到ul上，ul上有注册事件，所以会触发事件监听器 -> 只用了一次DOM，大幅提升效率

## 常见鼠标、键盘事件

1. 键盘事件
   ```
   e.onkeyup        某个键盘按键被松开时触发
   e.onkeydown      某个键盘按键被按下时触发
   e.onkeypress     某个键盘按键被按下时 触发 （但是它不识别功能键 比如 ctrl shift 箭头等）
   e.keyCode        按下按键的ASCII值
   ```
2. 鼠标事件
   ```
   event        对象代表事件的状态,跟事件相关的一系列信息的集合。
   e.clientX    返回鼠标相对于浏览器窗口可视区的X 坐标
   e.clientY    返回鼠标相对于浏览器窗口可视区的 Y 坐标
   e.pageX      返回鼠标相对于文档页面的X 坐标 IE9+ 支持
   e.pageY      返回鼠标相对于文档页面的 Y 坐标 IE9+ 支持
   e.screenX    返回鼠标相对于电脑屏幕的 X 坐标
   e.screenY    返回鼠标相对于电脑屏幕的 Y 坐标
   ```
