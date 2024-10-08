---
title: CSS
date: 2024-08-18 22:17:57
tags:
categories:
- CSS
---
## CSS 字体属性

* 使用`font-size`来定义字体大小
* 使用`font-weight`来定义字体粗细，`bold, normal`代表加粗，正常
* 使用`font-style`来定义文本风格，`italic，normal`代表斜体，正常
* 使用`font-family`来定义字体
* 使用`color`来定义文字颜色，可以用预定义的颜色，如`red, green, blue`；也可以用16进制表示`##FF0000`；也可以用RBG代码表示，如`rgb(255,0,0)`
* 使用`text-align`来定义文本内容水平对齐的方式，`left， right， center`代表了左对齐，右对齐，居中
* 使用`text-decoration`来修饰字体，`none，underline，overline，line-through`

## CSS 复合选择器

* 后代选择器 --- `ul li { xxx }`，选取ul里的所有li
* 子选择器 --- `ul > li { xxx }` ，其中后面的元素必须是前面元素的子元素，其孙子元素不管
* 并集选择器 --- `ul, ol { xxx }`
* 伪类选择器 --- `a:hover {xxx} / a:active {xxx} / a:visited {xxx} / a:link {xxx}`

## CSS 元素种类

* `<div>, <h1>-<h6>, <p>, <ul>, <ol>, <li>`是block element（块级元素）

  * 一行一个
  * 高，宽可以直接设置
  * 默认宽度是父级元素的100%
* `<span>, <a>`是line element（行内元素）

  * 一行可以显示多个
  * 高，宽直接设置无效
  * 默认宽度是本身宽度
* `<img>, <td>, <input>`是inline block（行内块元素）

  * 一行可以显示多个
  * 高，宽可以直接设置
  * 默认宽度是本身宽度

转换方式`display: block / inline / inline-block`

如果`display: none`，则当前元素直接消失，不占位置

如果`visibility: hidden`，则当前元素消失，但仍然占位置

## CSS 背景

* `background-color`  --- 颜色
* `background-image` --- url
* `background-repeat` --- 背景图片是否平铺平铺 `repeat / no-repeat / repeat-x / repeat-y`
* `background-position`  --- 背景图片在背景中的位置`top / bottom / center / left / right`
* `background-attachment` --- 是否跟随对象内容滚动 `scroll / fixed`

## CSS Box Model 盒子模型

下面的图片说明了盒子模型(Box Model)：

![CSS box-model](https://www.runoob.com/images/box-model.gif)

不同部分的说明：

* **Margin(外边距)** - 清除边框外的区域，外边距是透明的。
* **Border(边框)** - 围绕在内边距和内容外的边框。
* **Padding(内边距)** - 清除内容周围的区域，内边距是透明的。
* **Content(内容)** - 盒子的内容，显示文本和图像。
* 提供4个值，设置的顺序是上，右，下，左；
* 提供3个值，是上，左右，下；
* 提供2个值，上下，左右；
* 一个值，全部；

元素总宽度计算公式：

总元素的宽度=宽度+左填充+右填充+左边框+右边框+左边距+右边距

元素总高度最终计算公式：

总元素的高度=高度+顶部填充+底部填充+上边框+下边框+上边距+下边距

## CSS 浮动

### 1、传统网页布局的三种方式

CSS 提供了三种传统布局方式(盒子如何进行排列顺序)：

- 标准流
- 浮动
- 定位

  这三种布局方式都是用来摆放盒子的，盒子摆放到合适位置，布局自然就完成了。

### 2、标准流

标签按照规定好默认方式排列

1. 块级元素会独占一行，从上向下顺序排列。常用元素：`div、hr、p、h1~h6、ul、ol、dl、form、table`
2. 行内元素会按照顺序，从左到右顺序排列，碰到父元素边缘则自动换行。常用元素：`span、a、i、em` 等

### 3、为什么需要浮动？

总结： 有很多的布局效果，标准流没有办法完成，此时就可以利用浮动完成布局。 因为浮动可以改变元素标签默认的排列方式.

浮动最典型的应用：可以让多个块级元素一行内排列显示。

网页布局第一准则：**多个块级元素纵向排列找标准流，多个块级元素横向排列找浮动**。

### 4、什么是浮动？

float 属性用于创建浮动框，将其移动到一边，直到左边缘或右边缘触及包含块或另一个浮动框的边缘。

语法： `选择器 { float: left / right / none; }`

### 5、浮动特性

加了浮动之后的元素,会具有很多特性,需要我们掌握的.

1. 浮动元素会脱离标准流(脱标：浮动的盒子不再保留原先的位置)
2. 浮动的元素会一行内显示并且元素顶部对齐
3. 浮动的元素会具有行内块元素的特性： 浮动元素的大小根据内容来决定，浮动的盒子中间是没有缝隙的

### 6、浮动元素经常和标准流父级搭配使用

为了约束浮动元素位置, 我们网页布局一般采取的策略是: 先用标准流父元素排列上下位置, 之后内部子元素采取浮动排列左右位置。

### 7、浮动布局注意点

1. 浮动和标准流的父盒子搭配：先用标准流的父元素排列上下位置, 之后内部子元素采取浮动排列左右位置
2. 一个元素浮动了，其余的兄弟元素也要浮动。

### 8、清除浮动

由于父级盒子很多情况下，不方便给高度，但是子盒子浮动又不占有位置，最后父级盒子高度为 0 时，就会影响下面的标准流盒子。

### 9、清除浮动本质

清除浮动的本质是清除浮动元素造成的影响：浮动的子标签无法撑开父盒子的高度

注意：

- 如果父盒子本身有高度，则不需要清除浮动
- 清除浮动之后，父级就会根据浮动的子盒子自动检测高度。
- 父级有了高度，就不会影响下面的标准流了

### 10、清除浮动样式

语法：`选择器{clear: left / right / both;}`

### 总结

为什么需要清除浮动？

1. 父级没高度。
2. 子盒子浮动了。
3. 影响下面布局了，我们就应该清除浮动了。

## CSS 定位

定位 = 定位模式 + 偏移

偏移分为4种：Top, Down, Left, Right --- 它们定义元素相对于父级元素边线的距离

定位模式也分为4种：Static, Relative, Absolute, Fixed

在 CSS 中，通过 `position` 属性定义元素的**定位模式**，语法如下：

```css
选择器 { 
    position: 属性值; 
}
```

### 静态定位(static)

- **静态定位**是元素的**默认**定位方式，**无定位的意思**。它相当于 border 里面的none，静态定位static，不要定位的时候用。
- 语法：

  ```
  选择器 { 
      position: static; 
  }
  ```
- 静态定位 按照标准流特性摆放位置，它没有边偏移。

### 相对定位(relative)

- **相对定位**是元素在移动位置的时候，是相对于它自己**原来的位置**来说的（自恋型）。
- 语法：

```
选择器 { 
	position: relative; 
}
```

- 相对定位的特点：（务必记住）

  - 1.它是相对于自己原来的位置来移动的（移动位置的时候参照点是自己原来的位置）。
  - 2.**原来**在标准流的**位置**继续占有，后面的盒子仍然以标准流的方式对待它。

    因此，**相对定位并没有脱标**。它最典型的应用是给绝对定位当爹的

### 绝对定位(absolute)

- **绝对定位**是元素在移动位置的时候，是相对于它**祖先元素**来说的（拼爹型）。
- 语法：

  ```
   选择器 { 
   	position: absolute; 
   }
  ```

1. **完全脱标** —— 完全不占位置；
2. **父元素没有定位**，则以**浏览器**为准定位（Document 文档）。
3. **父元素要有定位**

   * 元素将依据最近的已经定位（绝对、固定或相对定位）的父元素（祖先）进行定位。

- **绝对定位的特点总结**：（务必记住）

  1.如果**没有祖先元素**或者**祖先元素没有定位**，则以浏览器为基准定位（Document 文档）。

  2.如果祖先元素有定位（相对、绝对、固定定位），则以最近一级的有定位祖先元素为参考点移动位置。

  3.绝对定位**不再占有原先的位置**。所以绝对定位是脱离标准流的。（脱标）

### 定位口诀 —— 子绝父相

弄清楚这个口诀，就明白了绝对定位和相对定位的使用场景。

这个**子绝父相**太重要了，是我们学习定位的**口诀**，是定位中最常用的一种方式这句话的意思是：**子级是绝对定位的话，父级要用相对定位。**

因为绝对定位的盒子是拼爹的，所以要和父级搭配一起来使用。

①子级绝对定位，不会占有位置，可以放到父盒子里面的任何一个地方，不会影响其他的兄弟盒子。

②父盒子需要加定位限制子盒子在父盒子内显示。

③父盒子布局时，需要占有位置，因此父亲只能是相对定位。

这就是子绝父相的由来，所以**相对定位经常用来作为绝对定位的父级**。

总结： **因为父级需要占有位置，因此是相对定位， 子盒子不需要占有位置，则是绝对定位**

当然，子绝父相不是永远不变的，如果父元素不需要占有位置，**子绝父绝**也会遇到。

**疑问**：为什么在布局时，**子级元素**使用**绝对定位**时，**父级元素**就要用**相对定位**呢？

观察下图，思考一下在布局时，**左右两个方向的箭头图片**以及**父级盒子**的定位方式。

**分析**：

1. **方向箭头**叠加在其他图片上方，应该使用**绝对定位**，因为**绝对定位完全脱标**，完全不占位置。
2. **父级盒子**应该使用**相对定位**，因为**相对定位不脱标**，后续盒子仍然以标准流的方式对待它。
   * 如果父级盒子也使用**绝对定位**，会完全脱标，那么下方的**广告盒子**会上移，这显然不是我们想要的。

**结论**：**父级要占有位置，子级要任意摆放**，这就是**子绝父相**的由来。

### 固定定位(fixed)

- **固定定位**是元素**固定于浏览器可视区的位置**。（认死理型）   主要使用场景： 可以在浏览器页面滚动时元素的位置不会改变。
- 语法：

  ```
   选择器 { 
   	position: fixed; 
   }
  ```
- 固定定位的特点：（务必记住）：

  1.以浏览器的可视窗口为参照点移动元素。

  - 跟父元素没有任何关系
  - 不随滚动条滚动。

  2.固定定位**不在占有原先的位置**。
- 固定定位也是**脱标**的，其实**固定定位也可以看做是一种特殊的绝对定位**。（认死理型）

  - **完全脱标**—— 完全不占位置；
  - 只认**浏览器的可视窗口** —— `浏览器可视窗口 + 边偏移属性` 来设置元素的位置；
    - 跟父元素没有任何关系；单独使用的
    - 不随滚动条滚动。

### 定位总结


| **定位模式**          | **是否脱标**         | **移动位置**           | **是否常用**                 |
| --------------------- | -------------------- | ---------------------- | ---------------------------- |
| static   静态定位     | 否                   | 不能使用边偏移         | 很少                         |
| **relative 相对定位** | **否 (占有位置)**    | **相对于自身位置移动** | **基本单独使用**             |
| **absolute绝对定位**  | **是（不占有位置）** | **带有定位的父级**     | **要和定位父级元素搭配使用** |
| **fixed 固定定位**    | **是（不占有位置）** | **浏览器可视区**       | **单独使用，不需要父级**     |
|                       |                      |                        |                              |

- 一定记住 相对定位、固定定位、绝对定位 两个大的特点： 1. 是否占有位置（脱标否） 2. 以谁为基准点移动位置。
- 学习定位重点学会子绝父相。
- 注意：

1. **边偏移**需要和**定位模式**联合使用，**单独使用无效**；
2. `top` 和 `bottom` 不要同时使用；
3. `left` 和 `right` 不要同时使用。

## 定位(position)的应用

### 3.1.  固定定位小技巧： 固定在版心左侧位置。

小算法：

1.让固定定位的盒子 left: 50%.  走到浏览器可视区（也可以看做版心） 的一半位置。

2.让固定定位的盒子 margin-left: 版心宽度的一半距离。  多走 版心宽度的一半位置

就可以让固定定位的盒子**贴着版心右侧对齐**了。

```html
<style>
        .w {
            width: 800px;
            height: 1400px;
            background-color: pink;
            margin: 0 auto;
        }
        .fixed {
            position: fixed;
            /* 1. 走浏览器宽度的一半 */
            left: 50%;
            /* 2. 利用margin 走版心盒子宽度的一半距离 */
            margin-left: 405px;
            width: 50px;
            height: 150px;
            background-color: skyblue;
        }
    </style>
</head>
<body>
    <div class="fixed"></div>
    <div class="w">版心盒子 800像素</div>
  
</body>
```

### 3.2. 堆叠顺序（z-index）

- 在使用**定位**布局时，可能会**出现盒子重叠的情况**。此时，可以使用 **z-index** 来控制盒子的前后次序 (z轴)
- 语法：

  ```
  选择器 { 
  	z-index: 1; 
  }
  ```
- `z-index` 的特性如下：

  1. **属性值**：**正整数**、**负整数**或 **0**，默认值是 0，数值越大，盒子越靠上；
  2. 如果**属性值相同**，则按照书写顺序，**后来居上**；
  3. 数字后面**不能加单位**。

  **注意**：`z-index` 只能应用于**相对定位**、**绝对定位**和**固定定位**的元素，其他**标准流**、**浮动**和**静态定位**无效。
- 应用 `z-index` 层叠等级属性可以**调整盒子的堆叠顺序**。如下图所示：

## 定位(position)的拓展

### 4.1 绝对定位的盒子居中

> **注意**：加了**绝对定位/固定定位的盒子**不能通过设置 `margin: auto` 设置**水平居中**。
>
> 但是可以通过以下计算方法实现水平和垂直居中，可以按照下图的方法：

1. `left: 50%;`：让**盒子的左侧**移动到**父级元素的水平中心位置**；
2. `margin-left: -0.5 * width px;`：让盒子**向左**移动**自身宽度的一半**。

### 4.2 定位特殊特性

绝对定位和固定定位也和浮动类似。

1.行内元素添加绝对或者固定定位，可以直接设置高度和宽度。

2.块级元素添加绝对或者固定定位，如果不给宽度或者高度，默认大小是内容的大小。

前面我们讲过， display 是 显示模式， 可以改变显示模式有以下方式:

- 可以用inline-block  转换为行内块
- 可以用浮动 float 默认转换为行内块（类似，并不完全一样，因为浮动是脱标的）
- 绝对定位和固定定位也和浮动类似， 默认转换的特性 转换为行内块。

所以说， 一个行内的盒子，如果加了**浮动**、**固定定位**和**绝对定位**，不用转换，就可以给这个盒子直接设置宽度和高度等。

### 4.3 脱标的盒子不会触发外边距塌陷

浮动元素、**绝对定位(固定定位）**元素的都不会触发外边距合并的问题。 （我们以前是用padding border overflow解决的）

也就是说，我们给盒子改为了浮动或者定位，就不会有垂直**外边距合并的问题**了。

### 4.4 绝对定位（固定定位）会完全压住盒子

浮动元素不同，只会压住它下面标准流的盒子，但是不会压住下面标准流盒子里面的文字（图片）

但是绝对定位（固定定位） 会压住下面标准流所有的内容。

浮动之所以不会压住文字，因为浮动产生的目的最初是为了做文字环绕效果的。 文字会围绕浮动元素。

## 6. 网页布局总结

通过盒子模型，清楚知道大部分html标签是一个盒子。

通过CSS浮动、定位 可以让每个盒子排列成为网页。

一个完整的网页，是标准流、浮动、定位一起完成布局的，每个都有自己的专门用法。

### 6.1. 标准流

可以让盒子上下排列或者左右排列，**垂直的块级盒子显示就用标准流布局**。

### 6.2. 浮动

可以让多个块级元素一行显示或者左右对齐盒子，**多个块级盒子水平显示就用浮动布局**

### 6.3. 定位

定位最大的特点是有层叠的概念，就是可以让多个盒子前后叠压来显示。**如果元素自由在某个盒子内移动就用定位布局。**

## 7. 元素的显示与隐藏

- 目的（本质）

  ```
  让一个元素在页面中消失或者显示出来
  ```
- 场景

  ```
  类似网站广告，当我们点击关闭就不见了，但是我们重新刷新页面，会重新出现！
  ```

### 7.1. display 显示（重点）

- display 设置或检索对象是否及如何显示。

  ```
  display: none 隐藏对象

  display：block 除了转换为块级元素之外，同时还有显示元素的意思。
  ```
- 特点： display 隐藏元素后，**不再占**有原来的位置。

### 7.2. visibility 可见性 （了解）

- visibility 属性用于指定一个元素应可见还是隐藏。

  ```
  visibility：visible ; 　元素可视

  visibility：hidden; 　  元素隐藏
  ```
- 特点：**visibility 隐藏元素后，继续占有原来的位置**。（停职留薪）
- 如果隐藏元素想要原来位置， 就用 visibility：hidden
- 如果隐藏元素不想要原来位置， 就用 display：none  (用处更多 重点）

### 7.3. overflow 溢出（重点）

- overflow 属性指定了如果内容溢出一个元素的框（超过其指定高度及宽度） 时，会发生什么。


| 属性值      | 描述                                       |
| ----------- | ------------------------------------------ |
| **visible** | 不剪切内容也不添加滚动条                   |
| **hidden**  | 不显示超过对象尺寸的内容，超出的部分隐藏掉 |
| **scroll**  | 不管超出内容否，总是显示滚动条             |
| **auto**    | 超出自动显示滚动条，不超出不显示滚动条     |

- 一般情况下，我们都不想让溢出的内容显示出来，因为溢出的部分会影响布局。
- 但是如果有定位的盒子， 请慎用overflow:hidden  因为它会隐藏多余的部分。
- 实际开发场景：

1. 清除浮动
2. 隐藏超出内容，隐藏掉,  不允许内容超过父盒子。

### 7.4. 显示与隐藏总结


| 属性                           | 区别                   | 用途                                                                            |
| ------------------------------ | ---------------------- | ------------------------------------------------------------------------------- |
| **display 显示     （重点）**  | 隐藏对象，不保留位置   | 配合后面js做特效，比如下拉菜单，原先没有，鼠标经过，显示下拉菜单， 应用极为广泛 |
| **visibility 可见性 （了解）** | 隐藏对象，保留位置     | 使用较少                                                                        |
| **overflow 溢出（重点）**      | 只是隐藏超出大小的部分 | 1. 可以清除浮动  2. 保证盒子里面的内容不会超出该盒子范围                        |
