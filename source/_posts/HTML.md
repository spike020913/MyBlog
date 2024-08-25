---
title: HTML
date: 2024-08-17 16:26:10
tags:
categories:
- HTML
---
# HTML知识点汇总

## HTML基础

1. 标题通过`<h1>` - `<h6>`标签定义，h1最大，h6最小
2. 段落通过标签 `<p>` 定义。
3. 链接通过标签 `<a>` 定义。
   `href`：指定链接目标的URL，可以是另一个网页的URL、文件的URL或其他资源的URL。
   `target`：指定链接在当前页面打开(_self)，还是新页面打开(_blank)。
   `title`：鼠标悬停时提供链接的额外信息。
4. 图像通过标签 `<img>` 定义。
5. 换行用`<br>`

## HTML属性

* **`id`**: 给元素一个唯一的标识符，可以用于 CSS 选择器或 JavaScript 操作。
  ```
  <div id="header">This is a header</div>
  ```
* **`class`**: 给元素指定一个或多个类名，方便通过 CSS 或 JavaScript 操作。
  ```
  <p class="text-muted">This is a paragraph.</p>
  ```
* **`style`**: 直接为元素定义 CSS 样式。
  ```
  <span style="color: red;">This text is red.</span>
  ```
* **`href`**: 用于 `<a>` 标签，指定链接目标。
  ```
  <a href="https://www.example.com">Visit Example</a>
  ```
* **`src`**: 用于 `<img>` 和 `<script>` 标签，指定资源的路径。
  ```
  <img src="image.jpg" alt="Description">
  ```
* **`alt`**: 用于 `<img>` 标签，提供图片的替代文本。
  ```
  <img src="logo.png" alt="Company Logo">
  ```
* **`title`**: 提供关于元素的额外信息，通常在鼠标悬停时显示。
  ```
  <button title="Click me">Submit</button>
  ```
* **`name`**: 在 `<input>`, `<form>`, `<select>` 等表单元素中使用，定义元素的名称。
  ```
  <input type="text" name="username">
  ```
* **`value`**: 定义表单元素的值。
  ```
  <input type="text" value="Default text">
  ```
* **`target`**: 用于 `<a>` 标签，指定链接的打开方式（如 `_blank` 在新窗口中打开）。
  ```
  <a href="https://www.example.com" target="_blank" rel="noopener">Open in new tab</a>
  ```
* **`type`**: 指定表单元素的类型（如 `text`, `password`, `submit`）。
  ```
  <input type="password" name="password">
  ```

## HTML头部

`<head>`元素包含了所有的头部标签元素。在 <head>元素中你可以插入脚本（scripts）, 样式文件（CSS），及各种meta信息。

可以添加在头部区域的元素标签为: `<title>, <style>, <meta>, <link>, <script>, <noscript>, <base>`

* `<title>`在 HTML/XHTML 文档中是必需的，定义了网页的标题。
* `<base>`描述了基本的链接地址/链接目标，该标签作为HTML文档中所有的链接标签的默认链接
* `<link>`用于链接到CSS样式表
* `<style>`定义了HTML文档的样式文件引用地址，也可以直接更改样式
* `<script>`用于加载脚本文件，如JavaScript

## HTML与CSS

* 内联样式
  `<p style="color:blue; margin-left:20px;">这是一个段落。</p>`
* 内部样式
  ```javascript
  <style type="text/css"> 
      body { background-color: yellow; } 
      p { color: blue; } 
  </style>
  ```
* 外部样式
  在`<head>`中加入`<link rel="stylesheet" href="mystyle.css">`

## HTML表格

* `<tr>`：table row，表示表格的一行。
* `<td>`：table data，表示表格的数据单元格。
* `<th>`：table header，表示表格的表头单元格。
* `<thead>`：thead，表格头
* `<>`：tbody，表格主题

## HTML列表

* `<ol>`有序列表
* `<ul>`无序列表
* `<li>` List item 列表item
* `<dl>` definition list 自定义列表
* `<dt>` definition term 自定义列表item
* `<dd>` definition description 自定列表item的描述

## HTML表单

* `<form>` 元素用于创建表单，`action` 属性定义了表单数据提交的目标 URL，`method` 属性定义了提交数据的 HTTP 方法
* `<label>` 元素用于为表单元素添加标签，提高可访问性。
* `<input>` 元素是最常用的表单元素之一，它可以创建文本输入框、密码框、单选按钮、复选框等。`type` 属性定义了输入框的类型，`id` 属性用于关联 `<label>` 元素，`name` 属性用于标识表单字段。
* `<select>` 元素用于创建下拉列表，而 `<option>` 元素用于定义下拉列表中的选项。

例子：

```html
<form action="/" method="post">
    <!-- 文本输入框 -->
    <label for="name">用户名:</label>
    <input type="text" id="name" name="name" required>

    <br>

    <!-- 密码输入框 -->
    <label for="password">密码:</label>
    <input type="password" id="password" name="password" required>

    <br>

    <!-- 单选按钮 -->
    <label>性别:</label>
    <input type="radio" id="male" name="gender" value="male" checked>
    <label for="male">男</label>
    <input type="radio" id="female" name="gender" value="female">
    <label for="female">女</label>

    <br>

    <!-- 复选框 -->
    <input type="checkbox" id="subscribe" name="subscribe" checked>
    <label for="subscribe">订阅推送信息</label>

    <br>

    <!-- 下拉列表 -->
    <label for="country">国家:</label>
    <select id="country" name="country">
        <option value="cn">CN</option>
        <option value="usa">USA</option>
        <option value="uk">UK</option>
    </select>

    <br>

    <!-- 提交按钮 -->
    <input type="submit" value="提交">
</form>
```

## HTML的`div`和`span`

**块级元素 vs. 行内元素：**

* `<div>,  <h1>, <p>, <ul>, <table>`等是块级元素，它独占一行，可以设置宽度、高度以及边距等样式属性。它适合用于创建页面的大块结构，例如页面的主体区域、容器、布局等。
* `<span>， <b>, <td>, <a>, <img>`是行内元素，它不会独占一行，宽度默认由其内容决定。它适合用于对文本或其他行内元素进行样式化、标记或包裹。

**默认样式和布局：**

* `<div>`元素的默认样式为块级显示，会以块的形式占据可用空间。
* `<span>`元素的默认样式为行内显示，它不会独占一行，只占据其内容的宽度。

**嵌套关系：**

* `<div>` 可以容纳其他块级元素和行内元素，包括其他的 <div> 和 <span> 元素。
* `<span>`通常被用来包裹文本或其他行内元素，比如用来设置特定文本的样式。

`<div>`用于创建页面结构和布局，而 `<span>`用于对文本或行内元素进行样式化或包裹。


## 快速生成HTML方法

- 生成标签 直接输入标签名 按tab键即可   比如  div   然后tab 键， 就可以生成 <div></div>
- 如果想要生成多个相同标签  加上 * 就可以了 比如   div*3  就可以快速生成3个div
- 如果有父子级关系的标签，可以用 >  比如   ul > li就可以了
- 如果有兄弟关系的标签，用  +  就可以了 比如 div+p
- 如果生成带有类名或者id名字的，  直接写  .demo  或者  #two   tab 键就可以了
- 如果生成的div 类名是有顺序的， 可以用 自增符号  $
- 如果想要在生成的标签内部写内容可以用  { }  表示

## 总结

HTML 是一种在 Web 上使用的通用标记语言。HTML 允许你格式化文本，添加图片，创建链接、输入表单、框架和表格等等，并可将之存为文本文件，浏览器即可读取和显示。
