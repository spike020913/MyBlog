---
title: jQuery
date: 2024-08-05 17:47:15
tags: [jQuery]
categories: 
- JavaScript
---
## 什么是jQuery？

1. JavaScript库：即library，是一个封装好的特定的集合(方法和函数)。这个库中，封装了很多预先定义好的函数在里面,比如动画animate，hide，show，比如获取元素等。
2. jQuery是一个快速简洁的js库，简化了DOM操作

## jQuery优点

1. 小，简洁

## jQuery的使用

1. **导入jQuery文件**
2. **'$'是jQuery的别称**
3. **等待页面加载完毕再执行jQuery代码**
   ```
   $(function() {
       // 此时DOM已经加载完毕
       // 正常操作↓
       $('div').hide();
   })
   ```
4. **jQuery和DOM对象的相互转换**
   ```
   <body>
       <video src="mov.mp4" muted></video>
       <script>
           // 1. DOM对象转换为 jQuery对象
           // (1) 我们直接获取视频，得到就是jQuery对象
           $('video');
           // (2) 我们已经使用原生js 获取过来 DOM对象
           var myvideo = document.querySelector('video');


           $(myvideo).play();  jquery里面没有play 这个方法 -- No
           // 2.  jQuery对象转换为DOM对象
           myvideo.play(); --- No
           $('video')[0].play() --- Ok
           $('video').get(0).play()
       </script>
   </body>
   ```

## DOM对象和jQuery的区别

主要区别为其属性和方法

```
<script>
        // 1. DOM 对象：  用原生js获取过来的对象就是DOM对象
        var myDiv = document.querySelector('div'); // myDiv 是DOM对象
        var mySpan = document.querySelector('span'); // mySpan 是DOM对象
        console.dir(myDiv);


        // 2. jQuery对象： 用jquery方式获取过来的对象是jQuery对象。 本质：通过$把DOM元素进行了包装
        $('div'); // $('div')是一个jQuery 对象
        $('span'); // $('span')是一个jQuery 对象
        console.dir($('div'));


        // 3. jQuery 对象只能使用 jQuery 方法，DOM 对象则使用原生的 JavaScirpt 属性和方法
        myDiv.style.display = 'none'; // OK
        myDiv.hide(); // dom对象不能使用jquery里面的hide方法
        $('div').style.display = 'none'; //jQuery对象不能使用原生js的属性和方法
   </script>
```
