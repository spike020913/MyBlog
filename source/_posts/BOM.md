---
title: BOM
date: 2024-08-01 16:33:10
tags: [BOM]
categories: 
- JavaScript
---
## 什么是BOM？

### BOM概念

BOM ( Browser Object Model )即浏览器对象模型，它提供了独立于内容而与浏览器窗口进行交互的对象，其核心对象是 window
BOM由一系列相关的对象构成，并且每个对象都提供了很多方法与属性。
BOM缺乏标准， JavaScript语法的标准化组织是 ECMA , DOM的标准化组织是W3C , BOM最初是Netscape浏览器标准的一部分。

### BOM和DOM的区别

**DOM:**
文档对象模型
DOM就是把「文档」当做一个「对象」来看待
DOM的顶级对象是 document
DOM主要学习的是操作页面元素
DOM 是W3C 标准规范

**BOM:**
浏览器对象模型
把「浏览器」当做一个「对象」来看待
BOM的顶级对象是 window
BOM 学习的是浏览器窗口交互的一些对象
BOM 是浏览器厂商在各自浏览器上定义的，兼容性较差
BOM > DOM, WINDOWS是顶级对象，document是windows的child

## Windows对象的常见事件

1. 窗口加载事件
   ```
   window.onload = function() {
       // TODO
   }
   window.onload 是窗口加载事件,当文档内容完全加载完成会触发该事件（包括图像、脚本文件、CSS文件等），就调用的处理函数。
   注意：
   1.有了window.onload就可以把JS代码写到页面元素的上方,因为onload是等页面内容全部加载完毕,再去执行处理函数。
   2. window.onload传统注册事件方式只能写一次,如果有多个,会以最后一个window.onload为准。
   ```
2. 窗口调整事件 window.resize() --- 常用于响应式布局

## 定时器

1. `setTimeout(回调函数，时间(ms))` --- 等待x秒后执行一次回调函数
2. `window.clearTimeout(name)`
3. `setInterval(回调函数，时间(ms))` --- 等待x秒后一直执行回调函数
4. This指向问题

## JS执行机制

1. **This指向问题**
   全局中this永远指window
   function中谁调用this指谁
   构造函数中this指向构造函数的实例对象
2. **JS的同步和异步**
   同步任务：
   同步任务都在主线程上执行，形成一个执行栈。
   异步任务：
   JS的异步是通过回调函数实现的。一般而言，异步任务有以下三种类型：
   1、普通事件,如 click, resize
   2、资源加载,如 load、 error
   3、定时器,包括setInterval, setTimeout等异步任务相关回调函数添加到任务队列中（任务队列也称为消息队列）。
3. **执行机制**：

   1. 先执行执行栈中的同步任务。
   2. 异步任务(回调函数)放入任务队列中。
   3. 一旦执行栈中的所有同步任务执行完毕,系统就会按次序读取任务队列中的异步任务,于是被读取的异步任务结束等待状态,进入执行栈,开始执行。
      ```
      console.log(1);
      setTimeout(function(){
        console.log(3);
      }, 0)
      console.log(2);
      // 123
      ```

## location对象

1. **什么是location对象？**
   window对象给我们提供了一个location属性，用于获取或设置窗体的URL ，并且可以用于解析URL。
   因为这个属性返回的是一个对象，所以我们将这个属性也称为location对象。
2. **location对象的属性**
   ```
   location.href        获取或者设置整个URL
   location.host        返回主机域名
   location.port        返回端口
   location.pathname    返回路径
   location.search      返回参数
   location.hash        返回片段
   ```
3. **location常见方法**
   ```
   Alocation.assign()      跟href一样,可以跳转页面(也称为重定向页面)
   location.replace()      替换当前页面,因为不记录历史,所以不能后退页面
   location.reload()       重新加载页面,相当于刷新按钮或者 f5 如果参数为true强制刷新 ctrl+f5
   ```

## navigator对象

通常用于判断移动端/pc端/的页面切换

## history对象

window对象给我们提供了一个history对象,与浏览器历史记录进行交互。该对象包含用户（在浏览器窗口中)访问过的 URL。history对象方法：
`back()` --- 后退
`forward()` --- 前进
``go() --- 前进后退功能（参数如果是1前进1个页面，如果是-1后退1个页面）
