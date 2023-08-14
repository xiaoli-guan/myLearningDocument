---
title: CSS、CSS3学习文档
date: 2023-7-26
tags:
 - CSS CSS3
categories:
 - CSS CSS3
---
<h1><center>CSS和CSS3</center></h1>

[TOC]

# 一、CSS概述

CSS（层叠样式表）是一种用来表现HTML（标准通用标记语言的一个应用）或XML（标准通用标记语言的一个子集）等文件样式的计算机语言。CSS 不仅可以静态地修饰网页，还可以配合各种脚本语言动态地对网页各元素进行格式化。

CSS 能够对网页中元素位置的排版进行像素级精确控制，支持几乎所有的字体字号样式，拥有对网页对象和模型样式编辑的能力。

CSS 定义如何显示 HTML 元素，就像 HTML 中的字体标签和颜色属性所起的作用那样。样式通常保存在外部的 .css 文件中，我们只需要编辑一个简单的 CSS 文档然后引用该文档就可以改变所有页面的布局和外观。

## 1.1、**语法：**

![image-20230719130401204](.\Image\image-20230719130401204.png)

例如，要让p标签内的文本都是红色，字体居中，我们就可以这么来写

```css
p {
    color: red;
    text-align: center;
}
```

>  **CSS注释以 /\* 开始, 以 */ 结束**

## 1.2、样式引入

| 外联式     | \<link rel="stylesheet" href="main.css"\>               |
| ---------- | ------------------------------------------------------- |
| **内联式** | **\<style> p { color: red; }\</style>**                 |
| **行内式** | **\<p style="color: red;text-align: center">样式\</p>** |

**三种样式引入的优先级：**

- 三种引入方式内容属性不冲突：三种方式会同时起作用。
- 三种引入方式内容属性会冲突：
    - 内联式和外联式冲突，后面的会覆盖前面的。
    - 其他冲突，以行内式为准。

> **注意：当属性值内存在“!important ”关键字的时候，优先使用该类方式导入属性值。**

# 二、常用的CSS选择器

## 2.1、id选择器

id 选择器可以为标有特定 id 的 HTML 元素指定特定的样式，一般来说，一个页面中标签的id的名称，必须唯一且不能重复。

```html
<p id="part1">段落1</p>
<p id="part2">段落2</p>
```

```css
#part1 {
    color: red;
}
```

## 2.2、class选择器

class 选择器可以为标有特定 class 的 HTML 元素指定特定的样式，一般来说，一个页面中标签的class的名称，可以不唯一且可以重复。

```html
<p class="green">段落1</p>
<p class="bold">段落2</p>
<p class="green bold">段落3</p>
```

```css
.green {
    color: green;
}

.bold {
    font-weight: bold;
}
```

## 2.3、标签选择器

除了使用id选择器和class选择器，我们也可以直接使用标签选择器。

```html
<p>段落1</p>
<p>段落2</p>
<p>段落3</p>
<a href="https://www.baidu.com/">打开百度，你就知道！</a>
```

```css
p {
    color: yellow;
}

a {
    color: red;
}
```

## 2.4、子代选择器

子代选择器可以选择当前元素的所有儿子元素。定义的时候用 > 隔开。

**需求描述** ：为div标签下所有h1儿子节点设置为红色文本样式

```html
<div>
    <h1>儿子标题</h1>
    <span><h1>孙子标题</h1></span>
    <h1>儿子标题</h1>
</div>
```

```css
div>h1{
    color: red;
}
```

## 2.5、后代选择器

标签元素除了并列书写还可以嵌套书写，后代选择器就是用于选择嵌套标签元素的一种选择器。定义的时候用 空格 隔开。

**需求描述** ：为所有段落标签中的超链接标签添加红色文本

```html
<p class="part">
    <a href="http://www.baidu.com/">打开百度，你就知道！</a>
</p>
<a href="http://www.baidu.com/">打开百度，你就知道！</a>
```

```css
.part a {
    color: red;
}
```

## 2.6、相邻兄弟选择器

相邻兄弟选择器（Adjacent sibling selector）可选择紧接在另一元素后的元素，且二者有相同父元素。如果需要选择紧接在另一个元素后的元素，而且二者有相同的父元素，可以使用相邻兄弟选择器（Adjacent sibling selector）。定义的时候用 + 隔开。
**需求描述** ：为div之后的第一个p标签元素设置为黄色文本样式

```html
<div>
    <p>DIV 内部段落。</p>
</div>
<p>DIV 之后的第一个 P 元素。</p>
<p>DIV 之后的第二个 P 元素。</p>
```

```css
div + p {
    background-color: yellow;
}
```

## 2.7、后续兄弟选择器

后续兄弟选择器选取所有指定元素之后的相邻兄弟元素。定义的时候用 ~ 隔开。

**需求描述** ：为div之后的所有p标签元素设置为黄色文本样式

```html
<div>
    <p>DIV 内部段落。</p>
</div>
<p>DIV 之后的第一个 P 元素。</p>
<p>DIV 之后的第二个 P 元素。</p>
```

```css
div ~ p {
    background-color: yellow;
}
```

## 2.8、交集选择器

选择的元素必须同时满足多个条件才可以被选择，交集选择器就是干这个的。定义的时候用 标签名.ID名/类名 。

**需求描述** ：为所有p标签且class为part的段落添加绿色文本样式

```html
<p class="part">段落</p>
<h1 class="part">标题</h1>
```

```css
p.part {
    color: red;
}
```

## 2.9、并集选择器

多种元素共享某种属性，这时候就可以使用并集选择器。定义的时候用 逗号 隔开。

**需求描述** ：为p标签、h1标签、class=‘link’、id='click’的这几种元素添加红色文本样式

```html
<p>段落</p>
<h1>标题</h1>
<a href="https://www.baidu.com/" class="link">打开百度，你就知道！</a>
<button id="click">我是按钮</button>
```

```css
p, h1, .link, #click {
    color: red;
}
```

## 2.10、通配符选择器

通配符选择器可以匹配任何标签，我们常用于统一页面样式。

**需求描述** ：将页面所有元素的字体设置为红色文本样式

```html
<div>DIV文本</div>
<p>P文本</p>
<a href="https://www.baidu.com">打开百度，你就知道！</a
```

```css
* {
    color: red;
}
```

## 2.11、伪类选择器

CSS伪类是用来添加一些选择器的特殊效果。

**anchor伪类：**

```html
<a href="https://www.baidu.com/">打开百度，你就知道！</a>
```

```css
a:link {color:#FF0000;} /* 未访问的链接样式 */
a:visited {color:#00FF00;} /* 已访问的链接样式 */
a:hover {color:#FF00FF;} /* 鼠标划过链接样式 */
a:active {color:#0000FF;} /* 已选中的链接样式 */
```

> 注意：推荐使用顺序为link、visited、hover、active

**input伪类：**

| 选择器                                                       | 示例               | 示例说明                     |
| ------------------------------------------------------------ | ------------------ | ---------------------------- |
| [:focus](https://www.runoob.com/cssref/sel-focus.html)       | input:focus        | 选择元素输入后具有焦点       |
| [:checked](https://www.runoob.com/cssref/sel-checked.html)   | input:checked      | 选择所有选中的表单元素       |
| [:disabled](https://www.runoob.com/css/cssref/sel-disabled.html) | input:disabled     | 选择所有禁用的表单元素       |
| [:enabled](https://www.runoob.com/cssref/sel-enable.html)    | input:enabled      | 选择所有启用的表单元素       |
| [:in-range](https://www.runoob.com/cssref/sel-in-range.html) | input:in-range     | 选择元素指定范围内的值       |
| [:out-of-range](https://www.runoob.com/cssref/sel-out-of-range.html) | input:out-of-range | 选择元素指定范围外的值       |
| [:invalid](https://www.runoob.com/cssref/sel-invalid.html)   | input:invalid      | 选择所有无效值的元素         |
| [:valid](https://www.runoob.com/cssref/sel-valid.html)       | input:valid        | 选择所有有效值的元素         |
| [:optional](https://www.runoob.com/cssref/sel-optional.html) | input:optional     | 选择没有"required"属性的元素 |
| [:required](https://www.runoob.com/cssref/sel-required.html) | input:required     | 选择含有"required"属性的元素 |
| [:read-only](https://www.runoob.com/cssref/sel-read-only.html) | input:read-only    | 选择只读属性的元素           |
| [:read-write](https://www.runoob.com/cssref/sel-read-write.html) | input:read-write   | 选择可写属性的元素           |

**other伪类：**

| 选择器                                                       | 示例                  | 示例说明                                |
| ------------------------------------------------------------ | --------------------- | --------------------------------------- |
| [:not(selector)](https://www.runoob.com/cssref/sel-not.html) | :not§                 | 选择所有p元素以外的元素                 |
| [:empty](https://www.runoob.com/cssref/sel-empty.html)       | p:empty               | 选择所有没有子元素的p元素               |
| [:first-child](https://www.runoob.com/cssref/sel-firstchild.html) | p:first-child         | 选择所有p元素的第一个子元素             |
| [:first-of-type](https://www.runoob.com/cssref/sel-first-of-type.html) | p:first-of-type       | 选择的每个p元素是其父元素的第一个p元素  |
| [:last-child](https://www.runoob.com/cssref/sel-last-child.html) | p:last-child          | 选择所有p元素的最后一个子元素           |
| [:last-of-type](https://www.runoob.com/cssref/sel-last-of-type.html) | p:last-of-type        | 选择每个p元素是其父元素的最后一个p元素  |
| [:nth-child(n)](https://www.runoob.com/cssref/sel-nth-child.html) | p:nth-child(2)        | 选择所有p元素的父元素的正数第二个子元素 |
| [:nth-of-type(n)](https://www.runoob.com/cssref/sel-nth-of-type.html) | p:nth-of-type(2)      | 选择所有p元素正数的第二个为p的子元素    |
| [:nth-last-child(n)](https://www.runoob.com/cssref/sel-nth-last-child.html) | p:nth-last-child(2)   | 选择所有p元素的父元素的倒数第二个子元素 |
| [:nth-last-of-type(n)](https://www.runoob.com/cssref/sel-nth-last-of-type.html) | p:nth-last-of-type(2) | 选择所有p元素倒数的第二个为p的子元素    |
| [:only-child](https://www.runoob.com/cssref/sel-only-child.html) | p:only-child          | 选择所有仅有一个子元素的p元素           |
| [:only-of-type](https://www.runoob.com/cssref/sel-only-of-type.html) | p:only-of-type        | 选择所有仅有一个子元素为p的元素         |
| [:first-letter](https://www.runoob.com/cssref/sel-firstletter.html) | p:first-letter        | 选择每个p元素的第一个字母               |
| [:first-line](https://www.runoob.com/cssref/sel-firstline.html) | p:first-line          | 选择每个p元素的第一行                   |
| [:before](https://www.runoob.com/cssref/sel-before.html)     | p:before              | 在每个p元素之前插入内容                 |
| [:after](https://www.runoob.com/cssref/sel-after.html)       | p:after               | 在每个p元素之后插入内容                 |

## 2.12、属性选择器

属性选择器可以根据元素的属性及属性值来选择元素。

**需求描述** ：为类型为text和button的input标签设置一下样式

```html
<input type="text" value="文本框">
<input type="button" value="按钮">
```

```css
input[type="text"] {
    width: 150px;
    display: block;
    margin-bottom: 10px;
    background-color: yellow;
}

input[type="button"] {
    width: 120px;
    margin-left: 35px;
    display: block;
}
```

## 2.13、子串匹配属性选择器

按照一定的匹配规则指向符合的属性值，请看例子。

| 类型         | 描述                                       |
| ------------ | ------------------------------------------ |
| [abc^=“def”] | 选择 abc 属性值以 “def” 开头的所有元素     |
| [abc$=“def”] | 选择 abc 属性值以 “def” 结尾的所有元素     |
| [abc*=“def”] | 选择 abc 属性值中包含子串 “def” 的所有元素 |

如果希望对指向 baidu 的所有链接应用样式，不必为所有这些链接指定 class，再根据这个类编写样式，而只需编写以下规则：

```css
a[href*="baidu.com"] {
    color: red;
}
```

## 2.14、选择器权重计算及优先级

选择器的权重是以 `(a, b, c)` 的格式表示的，从左往右逐位开始比较数字大小，数字更大则该选择器优先级就更高，相同则继续比较下一位，所有位相同时则按照后来者居上原则判断样式优先级。

权重的表示格式通常为 `(a, b, c)` ，各字母的含义是：

- `a` ：**ID选择器**的个数；
- `b` ：**类**、**伪类**、**属性**选择器的个数；
- `c` ：**元素**、**伪元素**选择器的个数。

比如 `.calendar .header .text > span` 是 `(0, 3, 1)` ，它的优先级就没有 `[data-theme="feb"] .row .cell.active span` 的 `(0, 4, 1)` 高。

> 带有 `!important`的样式权重最高

| 选择器       | 权重  |
| ------------ | ----- |
| ！important  | 10000 |
| 内联选择器   | 1000  |
| ID选择器     | 100   |
| 类别选择器   | 10    |
| 属性选择器   | 10    |
| 伪类         | 10    |
| 元素选择器   | 1     |
| 通配符选择器 | 0     |
| 继承选择器   | 无    |

# 三、CSS常见样式

## 3.1、背景样式

CSS 文本属性用于定义HTML文本内容的样式。

| 属性                                                         | 描述                                         |
| ------------------------------------------------------------ | -------------------------------------------- |
| [background](https://www.runoob.com/cssref/css3-pr-background.html) | 简写属性，作用是将背景属性设置在一个声明中。 |
| [background-attachment](https://www.runoob.com/cssref/pr-background-attachment.html) | 背景图像是否固定或者随着页面的其余部分滚动。 |
| [background-color](https://www.runoob.com/cssref/pr-background-color.html) | 设置元素的背景颜色。                         |
| [background-image](https://www.runoob.com/cssref/pr-background-image.html) | 把图像设置为背景。                           |
| [background-position](https://www.runoob.com/cssref/pr-background-position.html) | 设置背景图像的起始位置。                     |
| [background-repeat](https://www.runoob.com/cssref/pr-background-repeat.html) | 设置背景图像是否及如何重复。                 |

**1、background-image设置背景图**

​		语法：`background-image:url("imgs/main_bg.jpg")`

**2、background-repeat背景图重复**

默认情况下，背景图会铺满整个页面，背景图大小不够铺满整个页面时，背景图会在横坐标和纵坐标中进行重复；

| 属性值    | 描述                     |
| --------- | ------------------------ |
| repeat    | 横、纵坐标重复（默认值） |
| no-repeat | 不重复                   |
| repeat-x  | 只在x轴重复、y也一样     |

**4、background-size设置背景图的尺寸**

| 属性值    | 描述                                                         |
| --------- | ------------------------------------------------------------ |
| contain   | 图片要完整的显示在指定的区域，不能改变图片的比例,可能有部分空白区域 |
| cover     | 图片撑满整个指定区域，而且比例不变，可能会溢出               |
| 100%      | 横向撑满，纵向按比例缩放                                     |
| 100% 100% | 横、纵向撑满，图片比例可能会发生变化                         |
| x y       | 可以设置数值代表横、纵向的像素尺寸                           |

**5.、background-position设置背景图位置**

| 属性值        | 描述               |
| ------------- | ------------------ |
| center        | 背景图横、纵向居中 |
| center top    | 横向居中，纵向靠上 |
| center bottom | 横向居中，纵向靠下 |
| left center   | 横向靠左，纵向居中 |

也可以用**数值或百分比**如background-position：10% 10px 表示横、纵坐标离左边、上边边框的距离；

**6、background-attachment设置为是否固定**

| 属性值 | 描述             |
| ------ | ---------------- |
| fixed  | 背景图相对于视口 |
| scroll | 不固定（默认值） |

## 3.2、文本样式

CSS 文本属性用于定义HTML文本内容的样式。

| 属性                                                         | 描述                       |
| ------------------------------------------------------------ | -------------------------- |
| [color](https://www.runoob.com/cssref/pr-text-color.html)    | 设置文本颜色。             |
| [direction](https://www.runoob.com/cssref/pr-text-direction.html) | 设置文本方向。             |
| [letter-spacing](https://www.runoob.com/cssref/pr-text-letter-spacing.html) | 设置字符间距。             |
| [line-height](https://www.runoob.com/cssref/pr-dim-line-height.html) | 设置行高。                 |
| [text-align](https://www.runoob.com/cssref/pr-text-text-align.html) | 对齐元素中的文本。         |
| [text-decoration](https://www.runoob.com/cssref/pr-text-text-decoration.html) | 向文本添加修饰。           |
| [text-indent](https://www.runoob.com/cssref/pr-text-text-indent.html) | 缩进元素中文本的首行。     |
| [text-shadow](https://www.runoob.com/cssref/css3-pr-text-shadow.html) | 设置文本阴影。             |
| [text-transform](https://www.runoob.com/cssref/pr-text-text-transform.html) | 控制元素中的字母。         |
| [unicode-bidi](https://www.runoob.com/cssref/pr-text-unicode-bidi.html) | 设置或返回文本是否被重写。 |
| [vertical-align](https://www.runoob.com/cssref/pr-pos-vertical-align.html) | 设置元素的垂直对齐。       |
| [white-space](https://www.runoob.com/cssref/pr-text-white-space.html) | 设置元素中空白的处理方式。 |
| [word-spacing](https://www.runoob.com/cssref/pr-text-word-spacing.html) | 设置字间距。               |



## 3.3、字体样式

CSS 字体属性用于定义HTML内容字体的样式。

| 属性                                                         | 描述                                 |
| ------------------------------------------------------------ | ------------------------------------ |
| [font](https://www.runoob.com/cssref/pr-font-font.html)      | 在一个声明中设置所有的字体属性。     |
| [font-family](https://www.runoob.com/cssref/pr-font-font-family.html) | 指定文本的字体系列。                 |
| [font-size](https://www.runoob.com/cssref/pr-font-font-size.html) | 指定文本的字体大小。                 |
| [font-style](https://www.runoob.com/cssref/pr-font-font-style.html) | 指定文本的字体样式。                 |
| [font-variant](https://www.runoob.com/cssref/pr-font-font-variant.html) | 以小型大写字体或者正常字体显示文本。 |
| [font-weight](https://www.runoob.com/cssref/pr-font-weight.html) | 指定字体的粗细。                     |



## 3.4、列表样式

CSS 列表属性用于定义HTML常见列表的样式。

| 属性                                                         | 描述                                                 |
| ------------------------------------------------------------ | ---------------------------------------------------- |
| [list-style](https://www.runoob.com/cssref/pr-list-style.html) | 简写属性，用于把所有用于列表的属性设置于一个声明中。 |
| [list-style-image](https://www.runoob.com/cssref/pr-list-style-image.html) | 将图像设置为列表项标志。                             |
| [list-style-position](https://www.runoob.com/cssref/pr-list-style-position.html) | 设置列表中列表项标志的位置。                         |
| [list-style-type](https://www.runoob.com/cssref/pr-list-style-type.html) | 设置列表项标志的类型。                               |



## 3.5、表格样式

CSS 表格属性用于定义HTML表格的样式。

| 属性                                                         | 描述                                 |
| ------------------------------------------------------------ | ------------------------------------ |
| [border-collapse](https://www.w3school.com.cn/cssref/pr_tab_border-collapse.asp) | 设置是否把表格边框合并为单一的边框。 |
| [border-spacing](https://www.w3school.com.cn/cssref/pr_tab_border-spacing.asp) | 设置分隔单元格边框的距离。           |
| [caption-side](https://www.w3school.com.cn/cssref/pr_tab_caption-side.asp) | 设置表格标题的位置。                 |
| [empty-cells](https://www.w3school.com.cn/cssref/pr_tab_empty-cells.asp) | 设置是否显示表格中的空单元格。       |
| [table-layout](https://www.w3school.com.cn/cssref/pr_tab_table-layout.asp) | 设置显示单元、行和列的算法。         |



## 3.6、轮廓样式

轮廓（outline）是绘制于元素周围的一条线，位于边框边缘的外围，可起到突出元素的作用。

| 属性                                                         | 描述                             |
| ------------------------------------------------------------ | -------------------------------- |
| [outline](https://www.w3school.com.cn/cssref/pr_outline.asp) | 在一个声明中设置所有的轮廓属性。 |
| [outline-color](https://www.w3school.com.cn/cssref/pr_outline-color.asp) | 设置轮廓的颜色。                 |
| [outline-style](https://www.w3school.com.cn/cssref/pr_outline-style.asp) | 设置轮廓的样式。                 |
| [outline-width](https://www.w3school.com.cn/cssref/pr_outline-width.asp) | 设置轮廓的宽度。                 |



# 四、CSS盒子模型

## 4.1、概述

所有HTML元素可以看作盒子，在CSS中，"box model"这一术语是用来设计和布局时使用。

CSS盒模型本质上是一个盒子，封装周围的HTML元素，它包括：边距，边框，填充，和实际内容。

盒模型允许我们在其它元素和周围元素边框之间的空间放置元素。

下面的图片说明了盒子模型(Box Model)：
![image-20230719135340056](.\Image\image-20230719135340056.png)

- **Margin(外边距)** - 清除边框外的区域，外边距是透明的。
- **Border(边框)** - 围绕在内边距和内容外的边框。
- **Padding(内边距)** - 清除内容周围的区域，内边距是透明的。
- **Content(内容)** - 盒子的内容，显示文本和图像。

当您指定一个 CSS 元素的宽度和高度属性时，你只是设置内容区域的宽度和高度。要知道，完整大小的元素，你还必须添加内边距、边框和外边距。

## 4.2、内边距(padding)

![image-20230719140226151](.\Image\image-20230719140226151.png)

常用的属性：

| 属性                                                         | 描述                                                 |
| ------------------------------------------------------------ | ---------------------------------------------------- |
| [padding](https://www.w3school.com.cn/cssref/pr_padding.asp) | 简写属性。作用是在一个声明中设置元素的所内边距属性。 |
| [padding-bottom](https://www.w3school.com.cn/cssref/pr_padding-bottom.asp) | 设置元素的下内边距。                                 |
| [padding-left](https://www.w3school.com.cn/cssref/pr_padding-left.asp) | 设置元素的左内边距。                                 |
| [padding-right](https://www.w3school.com.cn/cssref/pr_padding-right.asp) | 设置元素的右内边距。                                 |
| [padding-top](https://www.w3school.com.cn/cssref/pr_padding-top.asp) | 设置元素的上内边距。                                 |

## 4.3、边框(border)

元素的边框 (border) 是围绕元素内容和内边距的一条或多条线，CSS边框属性允许你指定一个元素边框的样式和颜色。

常用的属性：

| 属性                                                         | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [border](https://www.w3school.com.cn/cssref/pr_border.asp)   | 简写属性，用于把针对四个边的属性设置在一个声明。             |
| [border-style](https://www.w3school.com.cn/cssref/pr_border-style.asp) | 用于设置元素所有边框的样式，或者单独地为各边设置边框样式。   |
| [border-width](https://www.w3school.com.cn/cssref/pr_border-width.asp) | 简写属性，用于为元素的所有边框设置宽度，或者单独地为各边边框设置宽度。 |
| [border-color](https://www.w3school.com.cn/cssref/pr_border-color.asp) | 简写属性，设置元素的所有边框中可见部分的颜色，或为 4 个边分别设置颜色。 |
| [border-bottom](https://www.w3school.com.cn/cssref/pr_border-bottom.asp) | 简写属性，用于把下边框的所有属性设置到一个声明中。           |
| [border-bottom-color](https://www.w3school.com.cn/cssref/pr_border-bottom_color.asp) | 设置元素的下边框的颜色。                                     |
| [border-bottom-style](https://www.w3school.com.cn/cssref/pr_border-bottom_style.asp) | 设置元素的下边框的样式。                                     |
| [border-bottom-width](https://www.w3school.com.cn/cssref/pr_border-bottom_width.asp) | 设置元素的下边框的宽度。                                     |
| [border-left](https://www.w3school.com.cn/cssref/pr_border-left.asp) | 简写属性，用于把左边框的所有属性设置到一个声明中。           |
| [border-left-color](https://www.w3school.com.cn/cssref/pr_border-left_color.asp) | 设置元素的左边框的颜色。                                     |
| [border-left-style](https://www.w3school.com.cn/cssref/pr_border-left_style.asp) | 设置元素的左边框的样式。                                     |
| [border-left-width](https://www.w3school.com.cn/cssref/pr_border-left_width.asp) | 设置元素的左边框的宽度。                                     |
| [border-right](https://www.w3school.com.cn/cssref/pr_border-right.asp) | 简写属性，用于把右边框的所有属性设置到一个声明中。           |
| [border-right-color](https://www.w3school.com.cn/cssref/pr_border-right_color.asp) | 设置元素的右边框的颜色。                                     |
| [border-right-style](https://www.w3school.com.cn/cssref/pr_border-right_style.asp) | 设置元素的右边框的样式。                                     |
| [border-right-width](https://www.w3school.com.cn/cssref/pr_border-right_width.asp) | 设置元素的右边框的宽度。                                     |
| [border-top](https://www.w3school.com.cn/cssref/pr_border-top.asp) | 简写属性，用于把上边框的所有属性设置到一个声明中。           |
| [border-top-color](https://www.w3school.com.cn/cssref/pr_border-top_color.asp) | 设置元素的上边框的颜色。                                     |
| [border-top-style](https://www.w3school.com.cn/cssref/pr_border-top_style.asp) | 设置元素的上边框的样式。                                     |
| [border-top-width](https://www.w3school.com.cn/cssref/pr_border-top_width.asp) | 设置元素的上边框的宽度。                                     |

## 4.4、外边距(margin)

margin 清除周围的（外边距）元素区域，margin 没有背景颜色，是完全透明的。margin 可以单独改变元素的上，下，左，右边距，也可以一次改变所有的属性。

![image-20230719140226151](.\Image\image-20230719140226151.png)

常用的属性：

| 属性                                                         | 描述                                       |
| ------------------------------------------------------------ | ------------------------------------------ |
| [margin](https://www.w3school.com.cn/cssref/pr_margin.asp)   | 简写属性。在一个声明中设置所有外边距属性。 |
| [margin-bottom](https://www.w3school.com.cn/cssref/pr_margin-bottom.asp) | 设置元素的下外边距。                       |
| [margin-left](https://www.w3school.com.cn/cssref/pr_margin-left.asp) | 设置元素的左外边距。                       |
| [margin-right](https://www.w3school.com.cn/cssref/pr_margin-right.asp) | 设置元素的右外边距。                       |
| [margin-top](https://www.w3school.com.cn/cssref/pr_margin-top.asp) | 设置元素的上外边距。                       |

## 4.5、外边距合并（崩塌）

外边距合并指的是，当两个垂直外边距相遇时，它们将形成一个外边距。合并后的外边距的高度等于两个发生合并的外边距的高度中的较大者。外边距合并（叠加）是一个相当简单的概念。但是，在实践中对网页进行布局时，它会造成许多混淆。

比如当一个元素出现在另一个元素上面时，第一个元素的下外边距与第二个元素的上外边距会发生合并。

![image-20230719140713044](https://img-blog.csdnimg.cn/img_convert/97915617128dfe52cc82a3d54bd440d5.png)

当一个元素包含在另一个元素中时（假设没有内边距或边框把外边距分隔开），它们的上和/或下外边距也会发生合并。请看下图：

![image-20230725112820468](https://img-blog.csdnimg.cn/img_convert/7dfd27a5b55329283f95303e2105d0be.png)

尽管看上去有些奇怪，但是外边距甚至可以与自身发生合并。假设有一个空元素，它有外边距，但是没有边框或填充。在这种情况下，上外边距与下外边距就碰到了一起，它们会发生合并：

![image-20230725112838438](https://img-blog.csdnimg.cn/img_convert/bc4c73c3db84118acce8191bf1529cd1.png)

如果这个外边距遇到另一个元素的外边距，它还会发生合并：

![image-20230725112854236](https://img-blog.csdnimg.cn/img_convert/00fbaa255684dc39e46b8e131b85d32a.png)

这就是一系列的段落元素占用空间非常小的原因，因为它们的所有外边距都合并到一起，形成了一个小的外边距。

> 注意：只有普通文档流中块框的垂直外边距才会发生外边距合并。行内框、浮动框或绝对定位之间的外边距不会合并。

# 五、CSS显示特性

## 5.1、块级元素

**块级元素(block)特性：**

* 总是独占一行，表现为另起一行开始，而且其后的元素也必须另起一行显示

* 宽度(width)、高度(height)、内边距(padding)和外边距(margin)都可控制

**块级元素主要有：**

**address , blockquote , center , dir , div , dl , fieldset , form , h1 , h2 , h3 , h4 , h5 , h6 , hr , isindex , menu , noframes , noscript , ol , p , pre , table , ul , li**

## 5.2、内联元素

**内联元素(inline)特性：**

* 和相邻的内联元素在同一行
* 宽度(width)、高度(height)、内边距的top/bottom(padding-top/padding-bottom)和外边距的top/bottom(margin-top/margin-bottom)都不可改变，就是里面文字或图片的大小

**内联元素主要有：**

**a , abbr , acronym , b , bdo , big , br , cite , code , dfn , em , font , i , img , input , kbd , label , q , s , samp , select , small , span , strike , strong , sub , sup ,textarea , tt , u , var**

## 5.3、可变元素

**可变元素：根据上下文关系确定该元素是块元素还是内联元素**

**applet ,button ,del ,iframe , ins ,map ,object , script**

## 5.4、类别修改

利用CSS我们可以摆脱上面表格里HTML标签归类的限制，自由地在不同标签/元素上应用我们需要的属性。

主要用的CSS样式有以下三个：

* display:block – 显示为块级元素

* display:inline – 显示为内联元素

* display:inline-block – 显示为内联块元素，表现为同行显示并可修改宽高内外边距等属性

> 我们常将所有\<li>元素加上display:inline-block样式，原本垂直的列表就可以水平显示了。

## 5.5、元素隐藏
隐藏一个元素可以通过把display属性设置为"none"，或把visibility属性设置为"hidden"。但是请注意，这两种方法会产生不同的结果。

但两者的区别在于：

* **display:none** ：使元素在网页上不可见，元素不再占用空间。
* **visibility: hidden** ：使元素在网页上不可见，元素仍会占用空间。

# 六、CSS定位

## 6.1、概述

**CSS 定位和浮动**

CSS 定位 (Positioning) 属性允许你对元素进行定位。

CSS 为定位和浮动提供了一些属性，利用这些属性，可以建立列式布局，将布局的一部分与另一部分重叠，还可以完成多年来通常需要使用多个表格才能完成的任务。

定位的基本思想很简单，它允许你定义元素框相对于其正常位置应该出现的位置，或者相对于父元素、另一个元素甚至浏览器窗口本身的位置。显然，这个功能非常强大，也很让人吃惊。要知道，用户代理对 CSS2 中定位的支持远胜于对其它方面的支持，对此不应感到奇怪。

另一方面，CSS1 中首次提出了浮动，它以 Netscape 在 Web 发展初期增加的一个功能为基础。浮动不完全是定位，不过，它当然也不是正常流布局。我们会在后面的章节中明确浮动的含义。

**CSS 定位机制**

CSS 有三种基本的定位机制：**普通流（相对定位）、绝对定位和浮动定位。**

除非专门指定，否则所有框都在普通流中定位。也就是说，普通流中的元素的位置由元素在 HTML 中的位置决定。

块级框从上到下一个接一个地排列，框之间的垂直距离是由框的垂直外边距计算出来。

行内框在一行中水平布置。可以使用水平内边距、边框和外边距调整它们的间距。但是，垂直内边距、边框和外边距不影响行内框的高度。由一行形成的水平框称为行框（Line Box），行框的高度总是足以容纳它包含的所有行内框。不过，设置行高可以增加这个框的高度。

**CSS 定位属性**

通过使用 position 属性，我们可以选择 4 种不同类型的定位，这会影响元素框生成的方式。

| 值       | 描述                                                         |
| -------- | ------------------------------------------------------------ |
| absolute | 生成绝对定位的元素，**相对于 static 定位以外的第一个父元素进行定位。**元素的位置通过 “left”, “top”, “right” 以及 “bottom” 属性进行规定。 |
| fixed    | 生成绝对定位的元素，**相对于浏览器窗口进行定位。**元素的位置通过 “left”, “top”, “right” 以及 “bottom” 属性进行规定。 |
| relative | 生成相对定位的元素，**相对于其正常位置进行定位。**因此，“left: 20” 会向元素的 left 位置添加 20 像素。 |
| static   | 默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right 或者 z-index 声明）。 |
| inherit  | 规定应该从父元素继承 position 属性的值。                     |

> 注意：相对定位实际上被看作普通流定位模型的一部分，因为元素的位置相对于它在普通流中的位置。

##  6.1、相对定位

**相对于其正常位置(未添加定位时的位置)进行定位**

如果对一个元素进行相对定位，它将出现在它所在的位置上。然后，可以通过设置垂直或水平位置，让这个元素“相对于”它的起点进行移动。

如果将 top 设置为 20px，那么框将在原位置顶部下面 20 像素的地方。如果 left 设置为 30 像素，那么会在元素左边创建 30 像素的空间，也就是将元素向右移动。

![image-20230719143639611](.\Image\image-20230719143639611.png)

> **注意：在使用相对定位时，无论是否进行移动，元素仍然占据原来的空间。因此，移动元素会导致它覆盖其它框。**

## 6.3、绝对定位

**绝对定位的元素的位置相对于最近的已定位祖先元素，如果元素没有已定位的祖先元素，那么它的位置相对于最初的包含块。**

绝对定位使元素的位置与文档流无关，因此不占据空间。这一点与相对定位不同，相对定位实际上被看作普通流定位模型的一部分，因为元素的位置相对于它在普通流中的位置。

普通流中其它元素的布局就像绝对定位的元素不存在一样：

```css
#box_relative {
    position: absolute;
    left: 30px;
    top: 20px;
}
```

![image-20230719143759631](.\Image\image-20230719143759631.png)

> **注意：根据用户代理的不同，最初的包含块可能是画布或 HTML 元素。因为绝对定位的框与文档流无关，所以它们可以覆盖页面上的其它元素。可以通过设置 z-index 属性来控制这些框的堆放次序。**

## 6.4、浮动定位

浮动的框可以向左或向右移动，直到它的外边缘碰到包含框或另一个浮动框的边框为止。

由于浮动框不在文档的普通流中，所以文档的普通流中的块框表现得就像浮动框不存在一样。

请看下图，当把框 1 向右浮动时，它脱离文档流并且向右移动，直到它的右边缘碰到包含框的右边缘：

![image-20230719144854826](.\Image\image-20230719144854826.png)

再请看下图，当框 1 向左浮动时，它脱离文档流并且向左移动，直到它的左边缘碰到包含框的左边缘。因为它不再处于文档流中，所以它不占据空间，实际上覆盖住了框 2，使框 2 从视图中消失。

如果把所有三个框都向左移动，那么框 1 向左浮动直到碰到包含框，另外两个框向左浮动直到碰到前一个浮动框。

![image-20230719144907714](.\Image\image-20230719144907714.png)

如下图所示，如果包含框太窄，无法容纳水平排列的三个浮动元素，那么其它浮动块向下移动，直到有足够的空间。如果浮动元素的高度不同，那么当它们向下移动时可能被其它浮动元素“卡住”：

![image-20230719144918506](.\Image\image-20230719144918506.png)

**CSS 浮动属性**

在 CSS 中，我们通过 float 属性实现元素的浮动。

| 值      | 描述                                                 |
| ------- | ---------------------------------------------------- |
| left    | 元素向左浮动。                                       |
| right   | 元素向右浮动。                                       |
| none    | 默认值。元素不浮动，并会显示在其在文本中出现的位置。 |
| inherit | 规定应该从父元素继承 float 属性的值。                |

**行框和清理**

浮动框旁边的行框被缩短，从而给浮动框留出空间，行框围绕浮动框。因此，创建浮动框可以使文本围绕图像：

![行框围绕浮动框](https://img-blog.csdnimg.cn/img_convert/b743de0006db1122205458a010b61556.png)

要想阻止行框围绕浮动框，需要对该框应用 [clear 属性](https://www.w3school.com.cn/cssref/pr_class_clear.asp)。clear 属性的值可以是 left、right、both 或 none，它表示框的哪些边不应该挨着浮动框。为了实现这种效果，在被清理的元素的上外边距上添加足够的空间，使元素的顶边缘垂直下降到浮动框下面：

![clear 属性实例 - 对行框应用 clear](https://img-blog.csdnimg.cn/img_convert/af3a405b92b47f4b3cec50d9dfffc283.png)

这是一个有用的工具，它让周围的元素为浮动元素留出空间。

让我们更详细地看看浮动和清理。假设希望让一个图片浮动到文本块的左边，并且希望这幅图片和文本包含在另一个具有背景颜色和边框的元素中。您可能编写下面的代码：

```css
.news {
    background-color: gray;
    border: solid 1px black;
}

.news img {
    float: left;
}

.news p {
    float: right;
}

<div class="news">
<img src="news-pic.jpg" />
<p>some text</p>
</div>
```


这种情况下，出现了一个问题。因为浮动元素脱离了文档流，所以包围图片和文本的 div 不占据空间。

如何让包围元素在视觉上包围浮动元素呢？需要在这个元素中的某个地方应用 clear：

![clear 属性实例 - 对空元素应用清理](https://img-blog.csdnimg.cn/img_convert/12190724a595fff5632b0e0876cb2248.png)

不幸的是出现了一个新的问题，由于没有现有的元素可以应用清理，所以我们只能添加一个空元素并且清理它。

```css
.news {
    background-color: gray;
    border: solid 1px black;
}

.news img {
    float: left;
}

.news p {
    float: right;
}

.clear {
    clear: both;
}

<div class="news">
<img src="news-pic.jpg" />
<p>some text</p>
<div class="clear"></div>
</div>
```


这样可以实现我们希望的效果，但是需要添加多余的代码。常常有元素可以应用 clear，但是有时候不得不为了进行布局而添加无意义的标记。不过我们还有另一种办法，那就是对容器 div 进行浮动：

```css
.news {
    background-color: gray;
    border: solid 1px black;
    float: left;
}

.news img {
    float: left;
}

.news p {
    float: right;
}

<div class="news">
<img src="news-pic.jpg" />
<p>some text</p>
</div>
```


这样会得到我们希望的效果。不幸的是，下一个元素会受到这个浮动元素的影响。为了解决这个问题，有些人选择对布局中的所有东西进行浮动，然后使用适当的有意义的元素（常常是站点的页脚）对这些浮动进行清理，这有助于减少或消除不必要的标记。

# 第七章、CSS3新增属性

## 7.1、CSS3边框

通过 CSS3能创建圆角边框，向矩形添加阴影，使用图片来绘制边框，并且不需使用设计软件，比如 PhotoShop。

| 属性                                                         | 说明                                           |
| ------------------------------------------------------------ | ---------------------------------------------- |
| [border-image](https://www.runoob.com/cssref/css3-pr-border-image.html) | 设置所有边框图像的速记属性。                   |
| [border-radius](https://www.runoob.com/cssref/css3-pr-border-radius.html) | 一个用于设置所有四个边框- *-半径属性的速记属性 |
| [box-shadow](https://www.runoob.com/cssref/css3-pr-box-shadow.html) | 附加一个或多个下拉框的阴影                     |

## 7.2、CSS3圆角

使用 CSS3 border-radius 属性，你可以给任何元素制作 “圆角”。

| 属性                                                         | 描述                                    |
| ------------------------------------------------------------ | --------------------------------------- |
| [border-radius](https://www.runoob.com/cssref/css3-pr-border-radius.html) | 所有四个边角 border-radius 属性的缩写。 |
| [border-top-left-radius](https://www.runoob.com/cssref/css3-pr-border-top-left-radius.html) | 定义了左上角的弧度。                    |
| [border-top-right-radius](https://www.runoob.com/cssref/css3-pr-border-top-right-radius.html) | 定义了右上角的弧度。                    |
| [border-bottom-right-radius](https://www.runoob.com/cssref/css3-pr-border-bottom-right-radius.html) | 定义了右下角的弧度。                    |
| [border-bottom-left-radius](https://www.runoob.com/cssref/css3-pr-border-bottom-left-radius.html) | 定义了左下角的弧度。                    |

## 7.3、CSS3背景

CSS3 中包含几个新的背景属性，提供更大背景元素控制。

| 属性                                                         | 描述                     |
| ------------------------------------------------------------ | ------------------------ |
| [background-clip](https://www.runoob.com/cssref/css3-pr-background-clip.html) | 规定背景的绘制区域。     |
| [background-origin](https://www.runoob.com/cssref/css3-pr-background-origin.html) | 规定背景图片的定位区域。 |
| [background-size](https://www.runoob.com/cssref/css3-pr-background-size.html) | 规定背景图片的尺寸。     |

## 7.4、CSS3渐变

CSS3 渐变（gradients）可以让你在两个或多个指定的颜色之间显示平稳的过渡。

以前，你必须使用图像来实现这些效果。但是，通过使用 CSS3 渐变（gradients），你可以减少下载的时间和宽带的使用。此外，渐变效果的元素在放大时看起来效果更好，因为渐变（gradient）是由浏览器生成的。

CSS3 定义了两种类型的渐变（gradients）：

* **线性渐变（Linear Gradients）- 向下/向上/向左/向右/对角方向**
* **径向渐变（Radial Gradients）- 由它们的中心定义**

### 7.4.1、线性渐变

为了创建一个线性渐变，你必须至少定义两种颜色节点。颜色节点即你想要呈现平稳过渡的颜色。同时，你也可以设置一个起点和一个方向（或一个角度）。

**线性渐变 - 从上到下（默认情况下）**

```css
#grad {
    background-image: linear-gradient(#e66465, #9198e5);
}
```

**线性渐变 - 从左到右**

```css
#grad {
    background-image: linear-gradient(to right, red, yellow);
}
```

**线性渐变 - 对角变化**

```css
#grad {
    background-image: linear-gradient(to bottom right, red, yellow);
}
```

如果你想要在渐变的方向上做更多的控制，你可以定义一个角度，而不用预定义方向（to bottom、to top、to right、to left、to bottom right，等等）。语法如下：

```css
background-image: linear-gradient(angle, color-stop1, color-stop2);
```

角度是指水平线和渐变线之间的角度，逆时针方向计算。换句话说，0deg 将创建一个从下到上的渐变，90deg 将创建一个从左到右的渐变。

![image-20230719152643438](.\Image\image-20230719152643438.png)

```css
/*在线性渐变上使用角度*/
#grad {
    background-image: linear-gradient(-90deg, red, yellow);
}
```

> 但是，请注意很多浏览器（Chrome、Safari、firefox等）的使用了旧的标准，即 0deg 将创建一个从左到右的渐变，90deg 将创建一个从下到上的渐变。换算公式 **90 - x = y** 其中 x 为标准角度，y为非标准角度。

### 7.4.2、径向渐变

径向渐变由它的中心定义。为了创建一个径向渐变，你也必须至少定义两种颜色节点。颜色节点即你想要呈现平稳过渡的颜色。同时，你也可以指定渐变的中心、形状（圆形或椭圆形）、大小。默认情况下，渐变的中心是 center（表示在中心点），渐变的形状是 ellipse（表示椭圆形），渐变的大小是 farthest-corner（表示到最远的角落）。

**径向渐变 - 颜色节点均匀分布（默认情况下）**

```css
#grad {
    background-image: radial-gradient(red, yellow, green);
}
```

**径向渐变 - 颜色节点不均匀分布**

```css
#grad {
    background-image: radial-gradient(red 5%, yellow 15%, green 60%);
}
```

**设置形状**

shape 参数定义了形状。它可以是值 circle 或 ellipse。其中，circle 表示圆形，ellipse 表示椭圆形。默认值是 ellipse。

形状为圆形的径向渐变：

```css
#grad {
    background-image: radial-gradient(circle, red, yellow, green);
}
```

**不同尺寸大小关键字的使用**

size 参数定义了渐变的大小。它可以是以下四个值：

- **closest-side**
- **farthest-side**
- **closest-corner**
- **farthest-corner**

带有不同尺寸大小关键字的径向渐变：

```css
#grad1 {
    background-image: radial-gradient(closest-side at 60% 55%, red, yellow, black);
}

#grad2 {
    background-image: radial-gradient(farthest-side at 60% 55%, red, yellow, black);
}
```

**重复的径向渐变**

repeating-radial-gradient() 函数用于重复径向渐变：

```cs
#grad {
    background-image: repeating-radial-gradient(red, yellow 10%, green 15%);
}
```

## 7.5、CSS3文本效果

CSS3中包含几个新的文本特征。

| 属性                                                         | 描述                                                    |
| ------------------------------------------------------------ | ------------------------------------------------------- |
| [hanging-punctuation](https://www.runoob.com/cssref/css3-pr-hanging-punctuation.html) | 规定标点字符是否位于线框之外。                          |
| [punctuation-trim](https://www.runoob.com/cssref/css3-pr-punctuation-trim.html) | 规定是否对标点字符进行修剪。                            |
| [text-align-last](https://www.runoob.com/cssref/css3-pr-text-align-last.html) | 设置如何对齐最后一行或紧挨着强制换行符之前的行。        |
| [text-emphasis](https://www.runoob.com/css3/css3-pr-text-emphasis.html) | 向元素的文本应用重点标记以及重点标记的前景色。          |
| [text-justify](https://www.runoob.com/cssref/css3-pr-text-justify.html) | 规定当 text-align 设置为 “justify” 时所使用的对齐方法。 |
| [text-outline](https://www.runoob.com/cssref/css3-pr-text-outline.html) | 规定文本的轮廓。                                        |
| [text-overflow](https://www.runoob.com/cssref/css3-pr-text-overflow.html) | 规定当文本溢出包含元素时发生的事情。                    |
| [text-shadow](https://www.runoob.com/cssref/css3-pr-text-shadow.html) | 向文本添加阴影。                                        |
| [text-wrap](https://www.runoob.com/cssref/css3-pr-text-wrap.html) | 规定文本的换行规则。                                    |
| [word-break](https://www.runoob.com/cssref/css3-pr-word-break.html) | 规定非中日韩文本的换行规则。                            |
| [word-wrap](https://www.runoob.com/cssref/css3-pr-word-wrap.html) | 允许对长的不可分割的单词进行分割并换行到下一行。        |

**例子：设置内容超出显示省略号**

**需要先使用 “overflow:hidden;” 来把超出的部分隐藏，然后使用“text-overflow:ellipsis;”当文本超出时显示为省略号。**

* overflow：hidden; 不显示超过对象尺寸的内容，就是把超出的部分隐藏了；
* text-overflow：ellipsis; 当文本对象溢出是显示…，当然也可是设置属性为 clip 不显示点点点；

```css
.text-ellipsis{
  overflow:hidden;/*超出内容隐藏*/
  white-space: nowrap;/*不换行*/
  text-overflow: ellipsis;/*设置...号*/
  -o-text-overflow: ellipsis;/*opera浏览器hack*/
}
```

## 7.6、CSS3字体

使用以前 CSS 的版本，网页设计师不得不使用用户计算机上已经安装的字体。

使用 CSS3，网页设计师可以使用它/她喜欢的任何字体。

当你发现您要使用的字体文件时，只需简单的将字体文件包含在网站中，它会自动下载给需要的用户。

您所选择的字体在新的 CSS3 版本有关于 @font-face 规则描述。

您"自己的"的字体是在 CSS3 @font-face 规则中定义的。

如需为 HTML 元素使用字体，请通过 font-family 属性来引用字体的名称 (myFirstFont)：

```css
<style>
    @font-face {
        font-family: myFirstFont;
        src: url(sansation_light.woff);
    }

    div {
        font-family: myFirstFont;
    }
</style>
```

下表列出了所有的字体描述和里面的@font-face规则定义：

| 描述符        | 值                                                           | **描述**                                                     |
| ------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| font-family   | name                                                         | 必需。规定字体的名称。                                       |
| src           | URL                                                          | 必需。定义字体文件的 URL。                                   |
| font-stretch  | normal<br/>condensed<br/>ultra-condensed<br/>extra-condensed<br/>semi-condensed<br/>expanded<br/>semi-expanded<br/>extra-expanded<br/>ultra-expanded | 可选。定义如何拉伸字体。默认是 “normal”。                    |
| font-style    | normal<br/>italic<br/>oblique                                | 可选。定义字体的样式。默认是 “normal”。                      |
| font-weight   | normal<br/>bold<br/>100<br/>200<br/>300<br/>400<br/>500<br/>600<br/>700<br/>800<br/>900 | 可选。定义字体的粗细。默认是 “normal”。                      |
| unicode-range | unicode-range                                                | 可选。定义字体支持的 UNICODE 字符范围。默认是 “U+0-10FFFF”。 |



# 八、CSS3 2D 转换

CSS3 转换可以对元素进行移动、缩放、转动、拉长或拉伸。

## 8.1、translate() 方法

![image-20230719155433598](.\Image\image-20230719155433598.png)

translate()方法，根据左(X轴)和顶部(Y轴)位置给定的参数，从当前元素位置移动。

translate(50px, 100px)是从左边元素移动50个像素，并从顶部移动100像素。

```css
div {
    -webkit-transform: translate(50px, 100px);/*Safari/Chrome浏览器支持*/
    -moz-transform: translate(50px, 100px);/*Firefox浏览器支持*/
    -ms-transform: translate(50px, 100px);/*IE浏览器支持*/
    -o-transform: translate(50px, 100px);/*Opera浏览器支持*/
    transform: translate(50px, 100px);
}
```

## 8.2、rotate() 方法

![image-20230719155555563](.\Image\image-20230719155555563.png)

rotate()方法，在一个给定度数顺时针旋转的元素。负值是允许的，这样是元素逆时针旋转。

rotate(30deg)代表元素顺时针旋转30度。

```css
div {
    -webkit-transform: rotate(30deg);
    -moz-transform: rotate(30deg);
    -ms-transform: rotate(30deg);
    -o-transform: rotate(30deg);
    transform: rotate(30deg);
}
```

## 8.3、scale() 方法

scale()方法，该元素增加或减少的大小，取决于宽度（X轴）和高度（Y轴）的参数。

scale(2, 3)转变宽度为原来的大小的2倍，和其原始大小3倍的高度。

```css
div {
    -webkit-transform: scale(2, 3);
    -moz-transform: scale(2, 3);
    -ms-transform: scale(2, 3);
    -o-transform: scale(2, 3);
    transform: scale(2, 3);
}
```



## 8.4、skew() 方法

skew() 方法包含两个参数值，分别表示X轴和Y轴倾斜的角度，如果第二个参数为空，则默认为0，参数为负表示向相反方向倾斜。

skew(30deg, 20deg)元素在X轴和Y轴上倾斜20度30度。

```css
div {
    -webkit-transform: skew(30deg, 20deg);
    -moz-transform: skew(30deg, 20deg);
    -ms-transform: skew(30deg, 20deg);
    -o-transform: skew(30deg, 20deg);
    transform: skew(30deg, 20deg);
}
```

## 8.5、matrix() 方法

![](https://img-blog.csdnimg.cn/img_convert/4c03a766ea910d8da8e1d86f26685211.png)

matrix()方法和2D变换方法合并成一个。

matrix 方法有六个参数，包含旋转，缩放，移动（平移）和倾斜功能。

```css
div {
    -webkit-transform: matrix(0.866, 0.5, -0.5, 0.866, 0, 0);
    -moz-transform: matrix(0.866, 0.5, -0.5, 0.866, 0, 0);
    -ms-transform: matrix(0.866, 0.5, -0.5, 0.866, 0, 0);
    -o-transform: matrix(0.866, 0.5, -0.5, 0.866, 0, 0);
    transform: matrix(0.866, 0.5, -0.5, 0.866, 0, 0);
}
```

**2D 转换属性**

| 属性                                                         | 描述                   |
| ------------------------------------------------------------ | ---------------------- |
| [transform](https://www.runoob.com/cssref/css3-pr-transform.html) | 适用于2D或3D转换的元素 |
| [transform-origin](https://www.runoob.com/cssref/css3-pr-transform-origin.html) | 允许您更改转化元素位置 |

**2D 转换方法**

| 函数                            | 描述                                     |
| ------------------------------- | ---------------------------------------- |
| matrix(*n*,*n*,*n*,*n*,*n*,*n*) | 定义 2D 转换，使用六个值的矩阵。         |
| translate(*x*,*y*)              | 定义 2D 转换，沿着 X 和 Y 轴移动元素。   |
| translateX(*n*)                 | 定义 2D 转换，沿着 X 轴移动元素。        |
| translateY(*n*)                 | 定义 2D 转换，沿着 Y 轴移动元素。        |
| scale(*x*,*y*)                  | 定义 2D 缩放转换，改变元素的宽度和高度。 |
| scaleX(*n*)                     | 定义 2D 缩放转换，改变元素的宽度。       |
| scaleY(*n*)                     | 定义 2D 缩放转换，改变元素的高度。       |
| rotate(*angle*)                 | 定义 2D 旋转，在参数中规定角度。         |
| skew(*x-angle*,*y-angle*)       | 定义 2D 倾斜转换，沿着 X 和 Y 轴。       |
| skewX(*angle*)                  | 定义 2D 倾斜转换，沿着 X 轴。            |
| skewY(*angle*)                  | 定义 2D 倾斜转换，沿着 Y 轴。            |

# 九、CSS3 3D 转换

CSS3 允许您使用 3D 转换来对元素进行格式化。

## 9.1、rotateX() 方法

![](https://img-blog.csdnimg.cn/img_convert/d28a192433770dff5316574375440970.png)

rotateX()方法，围绕其在一个给定度数X轴旋转的元素。

```css
div {
    -webkit-transform: rotateX(120deg);
    -moz-transform: rotateX(120deg);
    -ms-transform: rotateX(120deg);
    -o-transform: rotateX(120deg);
    transform: rotateX(120deg);
}
```

## 9.2、rotateY() 方法

![](https://img-blog.csdnimg.cn/img_convert/364130d125e3cac994a2a19b8f5b1d7c.png)

rotateY()方法，围绕其在一个给定度数Y轴旋转的元素。

```css
div {
    -webkit-transform: rotateY(120deg);
    -moz-transform: rotateY(120deg);
    -ms-transform: rotateY(120deg);
    -o-transform: rotateY(120deg);
    transform: rotateY(120deg);
}
```

**3D 转换属性**

| 属性                                                         | 描述                             |
| ------------------------------------------------------------ | -------------------------------- |
| [transform](https://www.runoob.com/cssref/css3-pr-transform.html) | 向元素应用 2D 或 3D 转换。       |
| [transform-origin](https://www.runoob.com/cssref/css3-pr-transform-origin.html) | 允许你改变被转换元素的位置。     |
| [perspective](https://www.runoob.com/cssref/css3-pr-perspective.html) | 规定 3D 元素的透视效果。         |
| [perspective-origin](https://www.runoob.com/cssref/css3-pr-perspective-origin.html) | 规定 3D 元素的底部位置。         |
| [backface-visibility](https://www.runoob.com/cssref/css3-pr-backface-visibility.html) | 定义元素在不面对屏幕时是否可见。 |

**3D 转换方法**

| 函数                                                         | 描述                                      |
| ------------------------------------------------------------ | ----------------------------------------- |
| matrix3d(*n*,*n*,*n*,*n*,*n*,*n*, *n*,*n*,*n*,*n*,*n*,*n*,*n*,*n*,*n*,*n*) | 定义 3D 转换，使用 16 个值的 4x4 矩阵。   |
| translate3d(*x*,*y*,*z*)                                     | 定义 3D 转化。                            |
| translateX(*x*)                                              | 定义 3D 转化，仅使用用于 X 轴的值。       |
| translateY(*y*)                                              | 定义 3D 转化，仅使用用于 Y 轴的值。       |
| translateZ(*z*)                                              | 定义 3D 转化，仅使用用于 Z 轴的值。       |
| scale3d(*x*,*y*,*z*)                                         | 定义 3D 缩放转换。                        |
| scaleX(*x*)                                                  | 定义 3D 缩放转换，通过给定一个 X 轴的值。 |
| scaleY(*y*)                                                  | 定义 3D 缩放转换，通过给定一个 Y 轴的值。 |
| scaleZ(*z*)                                                  | 定义 3D 缩放转换，通过给定一个 Z 轴的值。 |
| rotate3d(*x*,*y*,*z*,*angle*)                                | 定义 3D 旋转。                            |
| rotateX(*angle*)                                             | 定义沿 X 轴的 3D 旋转。                   |
| rotateY(*angle*)                                             | 定义沿 Y 轴的 3D 旋转。                   |
| rotateZ(*angle*)                                             | 定义沿 Z 轴的 3D 旋转。                   |
| perspective(*n*)                                             | 定义 3D 转换元素的透视视图。              |

# 十、CSS3过渡

CSS3中，我们为了添加某种效果可以从一种样式转变到另一个的时候，无需使用Flash动画或JavaScript。

CSS3 过渡是元素从一种样式逐渐改变为另一种的效果。

要实现这一点，必须规定两项内容：

* 指定要添加效果的CSS属性

* 指定效果的持续时间

应用于宽度属性的过渡效果，时长为 2 秒：

```css
div {
    width: 100px;
    height: 100px;
    background: red;
    
    -webkit-transition: width 2s;
    -moz-transition: width 2s;
    -ms-transition: width 2s;
    -o-transition: width 2s;
    transition: width 2s;
}
```

> **注意：如果未指定的期限，transition将没有任何效果，因为默认值是0。**

**过渡属性**

| 属性                                                         | 描述                                         |
| ------------------------------------------------------------ | -------------------------------------------- |
| [transition](https://www.runoob.com/cssref/css3-pr-transition.html) | 简写属性，用于在一个属性中设置四个过渡属性。 |
| [transition-property](https://www.runoob.com/cssref/css3-pr-transition-property.html) | 规定应用过渡的 CSS 属性的名称。              |
| [transition-duration](https://www.runoob.com/cssref/css3-pr-transition-duration.html) | 定义过渡效果花费的时间。默认是 0。           |
| [transition-timing-function](https://www.runoob.com/cssref/css3-pr-transition-timing-function.html) | 规定过渡效果的时间曲线。默认是 “ease”。      |
| [transition-delay](https://www.runoob.com/cssref/css3-pr-transition-delay.html) | 规定过渡效果何时开始。默认是 0。             |



# 十一、CSS3动画

CSS3 可以创建动画，它可以取代许多网页动画图像、Flash 动画和 JavaScript 实现的效果。

要创建 CSS3 动画，你需要了解 @keyframes 规则。

@keyframes 规则是创建动画。

@keyframes 规则内指定一个 CSS 样式和动画将逐步从目前的样式更改为新的样式。

当在 **@keyframes** 创建动画，把它绑定到一个选择器，否则动画不会有任何效果。

指定至少这两个CSS3的动画属性绑定向一个选择器：

* 规定动画的名称
* 规定动画的时长

把 “myfirst” 动画捆绑到 div 元素，时长：5 秒：

```css
@keyframes myfirst {
    0% {background: red;}
    25% {background: yellow;}
    50% {background: blue;}
    100% {background: green;}
}

@-webkit-keyframes myfirst {
    0% {background: red;}
    25% {background: yellow;}
    50% {background: blue;}
    100% {background: green;}
}

@-moz-keyframes myfirst {
    0% {background: red;}
    25% {background: yellow;}
    50% {background: blue;}
    100% {background: green;}
}

@-ms-keyframes myfirst {
    0% {background: red;}
    25% {background: yellow;}
    50% {background: blue;}
    100% {background: green;}
}

@-o-keyframes myfirst {
    0% {background: red;}
    25% {background: yellow;}
    50% {background: blue;}
    100% {background: green;}
}

div {
    width: 300px;
    height: 300px;
    background: black;

    -webkit-animation: myfirst 5s;
    -o-animation: myfirst 5s;
    animation: myfirst 5s;
}
```

请用百分比来规定变化发生的时间，或用关键词 “from” 和 “to”，等同于 0% 和 100%。

0% 是动画的开始，100% 是动画的完成。

为了得到最佳的浏览器支持，您应该始终定义 0% 和 100% 选择器。

**动画属性**

| 属性                                                         | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [@keyframes](https://www.runoob.com/cssref/css3-pr-animation-keyframes.html) | 规定动画。                                                   |
| [animation](https://www.runoob.com/cssref/css3-pr-animation.html) | 所有动画属性的简写属性。                                     |
| [animation-name](https://www.runoob.com/cssref/css3-pr-animation-name.html) | 规定 @keyframes 动画的名称。                                 |
| [animation-duration](https://www.runoob.com/cssref/css3-pr-animation-duration.html) | 规定动画完成一个周期所花费的秒或毫秒。默认是 0。             |
| [animation-timing-function](https://www.runoob.com/cssref/css3-pr-animation-timing-function.html) | 规定动画的速度曲线。默认是 “ease”。                          |
| [animation-fill-mode](https://www.runoob.com/cssref/css3-pr-animation-fill-mode.html) | 规定当动画不播放时（当动画完成时，或当动画有一个延迟未开始播放时），要应用到元素的样式。 |
| [animation-delay](https://www.runoob.com/cssref/css3-pr-animation-delay.html) | 规定动画何时开始。默认是 0。                                 |
| [animation-iteration-count](https://www.runoob.com/cssref/css3-pr-animation-iteration-count.html) | 规定动画被播放的次数。默认是 1。                             |
| [animation-direction](https://www.runoob.com/cssref/css3-pr-animation-direction.html) | 规定动画是否在下一周期逆向地播放。默认是 “normal”。          |
| [animation-play-state](https://www.runoob.com/cssref/css3-pr-animation-play-state.html) | 规定动画是否正在运行或暂停。默认是 “running”。               |



# 十二、CSS3多列

CSS3 可以将文本内容设计成像报纸一样的多列布局，如下实例：

![image-20230719163836512](.\Image\image-20230719163836512.png)

下表列出了所有 CSS3 的多列属性：

| 属性                                                         | 描述                                      |
| ------------------------------------------------------------ | ----------------------------------------- |
| [column-count](https://www.runoob.com/cssref/css3-pr-column-count.html) | 指定元素应该被分割的列数。                |
| [column-fill](https://www.runoob.com/cssref/css3-pr-column-fill.html) | 指定如何填充列。                          |
| [column-gap](https://www.runoob.com/cssref/css3-pr-column-gap.html) | 指定列与列之间的间隙。                    |
| [column-rule](https://www.runoob.com/cssref/css3-pr-column-rule.html) | 所有 column-rule-* 属性的简写。           |
| [column-rule-color](https://www.runoob.com/cssref/css3-pr-column-rule-color.html) | 指定两列间边框的颜色。                    |
| [column-rule-style](https://www.runoob.com/cssref/css3-pr-column-rule-style.html) | 指定两列间边框的样式。                    |
| [column-rule-width](https://www.runoob.com/cssref/css3-pr-column-rule-width.html) | 指定两列间边框的厚度。                    |
| [column-span](https://www.runoob.com/cssref/css3-pr-column-span.html) | 指定元素要跨越多少列。                    |
| [column-width](https://www.runoob.com/cssref/css3-pr-column-width.html) | 指定列的宽度。                            |
| [columns](https://www.runoob.com/cssref/css3-pr-columns.html) | column-width 与 column-count 的简写属性。 |

# 十三、CSS3用户界面

在 CSS3 中, 增加了一些新的用户界面特性来调整元素尺寸，框尺寸和外边框。

| 属性                                                         | 说明                                       |
| ------------------------------------------------------------ | ------------------------------------------ |
| [resize](https://www.runoob.com/cssref/css3-pr-resize.html)  | 指定一个元素是否是由用户调整大小。         |
| [box-sizing](https://www.runoob.com/cssref/css3-pr-box-sizing.html) | 允许你以适应区域而用某种方式定义某些元素。 |
| [outline-offset](https://www.runoob.com/cssref/css3-pr-outline-offset.html) | 外轮廓修饰并绘制超出边框的边缘。           |

## 13.1、调整尺寸(resize)

CSS3中，resize属性指定一个元素是否应该由用户去调整大小。

由用户指定一个div元素尺寸大小：

```css
div {
    width: 300px;
    height: 300px;
    background: red;
    /*div右下角会多出一个小三角*/
    resize: both;
    overflow: auto;
}
```

## 13.2、方框大小调整(box-sizing)

box-sizing 属性允许您以确切的方式定义适应某个区域的具体内容。

规定两个并排的带边框方框：

```css
div {
    width: 300px;
    height: 300px;
    background: red;

    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
}
```

## 13.3、外形修饰(outline-offset)

outline-offset 属性对轮廓进行偏移，并在超出边框边缘的位置绘制轮廓。

轮廓与边框有两点不同：

- 轮廓不占用空间
- 轮廓可能是非矩形

```css
div {
    width: 300px;
    height: 300px;
    background: red;

    border: 2px solid black;
    outline: 2px solid blue;
    outline-offset: 15px;
}
```

# 十四、CSS3弹性盒子

CSS3 弹性盒（ Flexible Box 或 flexbox），是一种当页面需要适应不同的屏幕大小以及设备类型时确保元素拥有恰当的行为的布局方式。引入弹性盒布局模型的目的是提供一种更加有效的方式来对一个容器中的子元素进行排列、对齐和分配空白空间。

弹性盒子由弹性容器(Flex container)和弹性子元素(Flex item)组成。

弹性容器通过设置 display 属性的值为 flex 或 inline-flex将其定义为弹性容器。

弹性容器内包含了一个或多个弹性子元素。

> 注意：弹性容器外及弹性子元素内是正常渲染的，弹性盒子只定义了弹性子元素如何在弹性容器内布局。弹性子元素通常在弹性盒子内一行显示。默认情况每个容器只有一行。

下表列出了在弹性盒子中常用到的属性：

| 属性                                                         | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [display](https://www.runoob.com/cssref/pr-class-display.html) | 指定 HTML 元素盒子类型。                                     |
| [flex-direction](https://www.runoob.com/cssref/css3-pr-flex-direction.html) | 指定了弹性容器中子元素的排列方式。                           |
| [justify-content](https://www.runoob.com/cssref/css3-pr-justify-content.html) | 设置弹性盒子元素在主轴（横轴）方向上的对齐方式。             |
| [align-items](https://www.runoob.com/cssref/css3-pr-align-items.html) | 设置弹性盒子元素在侧轴（纵轴）方向上的对齐方式。             |
| [flex-wrap](https://www.runoob.com/cssref/css3-pr-flex-wrap.html) | 设置弹性盒子的子元素超出父容器时是否换行。                   |
| [align-content](https://www.runoob.com/cssref/css3-pr-align-content.html) | 修改 flex-wrap 属性的行为，类似 align-items, 但不是设置子元素对齐，而是设置行对齐。 |
| [flex-flow](https://www.runoob.com/cssref/css3-pr-flex-flow.html) | flex-direction 和 flex-wrap 的简写。                         |
| [order](https://www.runoob.com/cssref/css3-pr-order.html)    | 设置弹性盒子的子元素排列顺序。                               |
| [align-self](https://www.runoob.com/cssref/css3-pr-align-self.html) | 在弹性子元素上使用。覆盖容器的 align-items 属性。            |
| [flex](https://www.runoob.com/cssref/css3-pr-flex.html)      | 设置弹性盒子的子元素如何分配空间。                           |

# 十五、CSS3多媒体查询

## 15.1、媒体概述

CSS3 的多媒体查询继承了 CSS2 多媒体类型的所有思想： 取代了查找设备的类型，CSS3 根据设置自适应显示。你可以针对不同的媒体类型(包括显示器、便携设备、电视机，等等)设置不同的样式规则。但是这些多媒体类型在很多设备上支持还不够友好。

目前很多针对苹果手机，Android 手机，平板等设备都会使用到多媒体查询。媒体查询可用于检测很多事情，例如：

- viewport(视窗) 的宽度与高度
- 设备的宽度与高度
- 朝向 (智能手机横屏，竖屏) 。
- 分辨率

多媒体查询由多种媒体组成，可以包含一个或多个表达式，表达式根据条件是否成立返回 true 或 false。

```css
@media not|only mediatype and (expressions) {
    CSS 代码...;
}
```

如果指定的多媒体类型匹配设备类型则查询结果返回 true，文档会在匹配的设备上显示指定样式效果。

除非你使用了 not 或 only 操作符，否则所有的样式会适应在所有设备上显示效果。

* **not:** not是用来排除掉某些特定的设备的，比如 @media not print（非打印设备）。
* **only:** 用来定某种特别的媒体类型。对于支持Media Queries的移动设备来说，如果存在only关键字，移动设备的Web浏览器会忽略only关键字并直接根据后面的表达式应用样式文件。对于不支持Media Queries的设备但能够读取Media Type类型的Web浏览器，遇到only关键字时会忽略这个样式文件。
* **all:** 所有设备，这个应该经常看到。

## 15.2、多媒体类型

| 值     | 描述                             |
| ------ | -------------------------------- |
| all    | 用于所有多媒体类型设备           |
| print  | 用于打印机                       |
| screen | 用于电脑屏幕，平板，智能手机等。 |
| speech | 用于屏幕阅读器                   |

## 15.3、多媒体功能

| 值                      | 描述                                                         |
| ----------------------- | ------------------------------------------------------------ |
| aspect-ratio            | 定义输出设备中的页面可见区域宽度与高度的比率                 |
| color                   | 定义输出设备每一组彩色原件的个数。如果不是彩色设备，则值等于0 |
| color-index             | 定义在输出设备的彩色查询表中的条目数。如果没有使用彩色查询表，则值等于0 |
| device-aspect-ratio     | 定义输出设备的屏幕可见宽度与高度的比率。                     |
| device-height           | 定义输出设备的屏幕可见高度。                                 |
| device-width            | 定义输出设备的屏幕可见宽度。                                 |
| grid                    | 用来查询输出设备是否使用栅格或点阵。                         |
| height                  | 定义输出设备中的页面可见区域高度。                           |
| max-aspect-ratio        | 定义输出设备的屏幕可见宽度与高度的最大比率。                 |
| max-color               | 定义输出设备每一组彩色原件的最大个数。                       |
| max-color-index         | 定义在输出设备的彩色查询表中的最大条目数。                   |
| max-device-aspect-ratio | 定义输出设备的屏幕可见宽度与高度的最大比率。                 |
| max-device-height       | 定义输出设备的屏幕可见的最大高度。                           |
| max-device-width        | 定义输出设备的屏幕最大可见宽度。                             |
| max-height              | 定义输出设备中的页面最大可见区域高度。                       |
| max-monochrome          | 定义在一个单色框架缓冲区中每像素包含的最大单色原件个数。     |
| max-resolution          | 定义设备的最大分辨率。                                       |
| max-width               | 定义输出设备中的页面最大可见区域宽度。                       |
| min-aspect-ratio        | 定义输出设备中的页面可见区域宽度与高度的最小比率。           |
| min-color               | 定义输出设备每一组彩色原件的最小个数。                       |
| min-color-index         | 定义在输出设备的彩色查询表中的最小条目数。                   |
| min-device-aspect-ratio | 定义输出设备的屏幕可见宽度与高度的最小比率。                 |
| min-device-width        | 定义输出设备的屏幕最小可见宽度。                             |
| min-device-height       | 定义输出设备的屏幕的最小可见高度。                           |
| min-height              | 定义输出设备中的页面最小可见区域高度。                       |
| min-monochrome          | 定义在一个单色框架缓冲区中每像素包含的最小单色原件个数       |
| min-resolution          | 定义设备的最小分辨率。                                       |
| min-width               | 定义输出设备中的页面最小可见区域宽度。                       |
| monochrome              | 定义在一个单色框架缓冲区中每像素包含的单色原件个数。如果不是单色设备，则值等于0 |
| orientation             | 定义输出设备中的页面可见区域高度是否大于或等于宽度。         |
| resolution              | 定义设备的分辨率。如：96dpi, 300dpi, 118dpcm                 |
| scan                    | 定义电视类设备的扫描工序。                                   |
| width                   | 定义输出设备中的页面可见区域宽度。                           |

## 15.4、多媒体实例

以下实例中在屏幕可视窗口尺寸小于 480 像素的设备上修改背景颜色：

```css
@media screen and (max-width: 480px) {
    body {
        background-color: lightgreen;
    }
}
```

以下实例在屏幕可视窗口尺寸大于 480 像素时将菜单浮动到页面左侧：

```css
@media screen and (min-width: 480px) {
    #leftsidebar {width: 200px; float: left;}
    #main {margin-left:216px;}
}
```

# 十六、CSS3响应式布局

**响应式布局**指的是同一页面在不同屏幕尺寸下有不同的布局。传统的开发方式是PC端开发一套，移动端再开发一套，而使用响应式布局只要开发一套就够。

**优点**：

* 面对不同分辨率设备灵活性强
* 没有横向滚动条。
* 能够快捷解决多设备显示适应问题

**缺点**：

* 仅适用布局、信息、框架并不复杂的部门类型网站
* 兼容各种设备工作量大，效率低下
* 代码累赘，会出现隐藏无用的元素，加载时间加长
* 其实这是一种折中性质的设计解决方案，多方面因素影响而达不到最佳效果
* 一定程度上改变了网站原有的布局结构，会出现用户混淆的情况

**响应式设计与自适应设计的区别：**

| 响应式设计 | 响应式开发一套界面，通过检测视口分辨率，针对不同客户端在客户端做代码处理，来展现不同的布局和内容 |
| ---------- | ------------------------------------------------------------ |
| 自适应设计 | 自适应需要开发多套界面，通过检测视口分辨率，来判断当前访问的设备是pc端、平板、手机，从而请求服务层，返回不同的页面。 |

## 16.1、百分比布局

百分比是相对于 包含块 的计量单位，通过对属性设置百分比来适应不同的屏幕

比如，当浏览器的宽度或者高度发生变化时，通过百分比单位可以使得浏览器中的组件的宽和高随着浏览器的变化而变化，从而实现响应式的效果。

height、width 属性的百分比依托于父标签的宽高。但是 padding、border、margin 等属性的情况又不一样

* 子元素的 top 和 bottom 如果设置百分比，则相对于直接非 static 定位（默认定位）的父元素的高度，同样，子元素的 left 和 right 如果设置百分比，则相对于直接非 static 定位（默认定位的）父元素的宽度。
* 子元素的 padding 和 margin 如果设置百分比，不论是垂直方向或者是水平方向都相对于直接父亲元素的 width，而与父元素的 height 无关。
* border-radius 为百分比，则是相对于自身的宽度

**缺点：**

计算困难，如果我们要定义一个元素的宽度和高度，按照设计稿，必须换算成百分比单位。

## 16.2、rem布局

- rem 是相对于 html 根元素的字体大小的单位。
- 我们通过修改 html 中 font-size 的字体大小来控制 rem 的大小。

```css
html {
 font-size: 10px;
}
.box {
 width: 10rem;/*100px*/
 height: 20rem;/*200px*/
}
```

> 在实际的开发中，我们通常会以 750px 的移动端设计稿来开发。我们在代码写完后，统一会把所有 px 单位全部转成 rem 来实现。

**一般来说，屏幕尺寸与1rem的对应关系如下**

| 屏幕尺寸 | html 中 font-size 大小 （1rem 大小） |
| -------- | ------------------------------------ |
| 750px    | 75px                                 |
| 640px    | 64px                                 |
| 480px    | 48px                                 |
| 375px    | 37.5px                               |
| 320px    | 32px                                 |

**那么，如果控制1rem的大小呢？**

我们可以通过 js 来动态修改不同屏幕尺寸下的 font-size 大小就可以了。

## 16.3、媒体查询

在第十五章已经介绍过媒体查询。通过@media 媒体查询，可以通过给不同屏幕的大小编写不同的样式来实现响应式的布局。

```css
<style>
 .box {
   width: 500px;
   height: 500px;
   background-color: aqua;
}
/*在屏幕可视窗口尺寸小于1280px*/
 @media screen and (max-width: 1280px) {
   .box {
     width: 400px;
     height: 400px;
  }
}
/*在屏幕可视窗口尺寸小于980px*/
 @media screen and (max-width: 980px) {
   .box {
     width: 300px;
     height: 300px;
  }
}
/*在屏幕可视窗口尺寸小于765px*/
 @media screen and (max-width: 765px) {
   .box {
     width: 200px;
     height: 200px;
  }
}
</style>
<body>
 <div class="box"></div>
</body>
```

**缺点：**如果浏览器大小改变时，需要改变的样式太多，那么多套样式代码会很繁琐。

> 在实际开发时，@media 会结合删格系统一起来使用，实现真正意义上的响应式开发。

## 16.4、vw和vh

`vw`表示相对于视图窗口的宽度，`vh`表示相对于视图窗口高度，除了`vw`和`vh`外，还有`vmin`和`vmax`两个相关的单位。各个单位具体的含义如下：

| 单位 | 含义                                                      |
| ---- | --------------------------------------------------------- |
| vw   | 相对于视窗的宽度，1vw 等于视口宽度的1%，即视窗宽度是100vw |
| vh   | 相对于视窗的高度，1vh 等于视口高度的1%，即视窗高度是100vh |
| vmin | vw和vh中的较小值                                          |
| vmax | vw和vh中的较大值                                          |

vw、vh 是自动应视口宽的，所以就达到了响应式开发的效果。

## 16.5、flex布局

弹性布局是一种十分方便的，只需要依赖于 CSS 样式的实现响应式布局的方式，也是最多用到的一种实现响应式的方法。

弹性布局在父、子元素上都有相对应的属性来规范子元素在父元素中的 “ 弹力 ”。

**在父元素上**，我们经常会用到的有关弹性布局的属性主要有 **flex-direction , flex-wrap , justify-content , align-items , align-content** ，这几个属性分别从 主轴的方向、是否换行、项目在主轴上的对齐方式、项目在交叉轴上的对齐方式、项目在多根轴线上的对齐方式来规范了项目在父元素中的弹性。

**在子元素上**，我们经常会用到的有关弹性布局的属性主要有 **order , flex-grow , flex-shrink ,flex-basis , align-self** ，这几个属性分别从 项目的排序、项目放大比例、项目缩小比例、项目占据主轴空间、单个项目在交叉轴上的对齐方式来规范了项目自身的弹性。

# 十七、浏览器兼容问题

Chrome，Frirefox，Safari，Edge，IE6，IE7，IE8，IE9…360安全浏览器，qq浏览器，世界之窗，TT，搜狗，opera，maxthon（傲游）……

不同厂商，甚至同一厂商不同版本，对同一段CSS的解析效果也不一致，这就导致了页面显示效果不统一，也就带来了兼容性问题。

解决浏览器兼容问题，主要包括4个方面，**浏览器CSS样式初始化、浏览器私有属性，CSS hack语法和自动化插件**。

## 17.1、浏览器CSS样式初始化

由于每个浏览器的css默认样式不尽相同，所以最简单有效的方式就是对其进行初始化。

关于浏览器CSS样式初始化，经验不丰富的话，可能也不知道该初始化什么，这里给大家推荐一个库**Normalize.css**

## 17.2、浏览器私有属性

我们经常会在某个CSS的属性前添加一些前缀，比如-webkit-，-moz- ，-ms-，这些就是浏览器的私有属性。

常用的前缀有：

* -moz-代表firefox浏览器私有属性
* -ms-代表IE浏览器私有属性（目前只有 IE 8+ 支持`-ms-`前缀）
* -webkit-代表chrome、safari私有属性
* -o-代表opera私有属性
* -khtml-代表Konqueror 类型的浏览器的私有属性

> 对于私有属性的顺序要注意，把标准写法放到最前，兼容性写法放到后面

```css
 transform:rotate(-3deg);
-webkit-transform:rotate(-3deg); /*为Chrome/Safari*/
 -moz-transform:rotate(-3deg); /*为Firefox*/
 -ms-transform:rotate(-3deg); /*为IE*/
 -o-transform:rotate(-3deg); /*为Opera*/
```

## 17.3、CSS hack

有时我们需要针对不同的浏览器或不同版本写特定的CSS样式，这种针对不同的浏览器/不同版本写相应的CSS code的过程，叫做CSS hack!

CSS hack的写法大致归纳为3种：条件hack、属性级hack、选择符级hack。

**条件hack**

条件hack主要针对IE浏览器进行一些特殊的设置

```css
<!--[if <keywords>? IE <version>?]> 
 代码块，可以是html，css，js 
<![endif]-->
```

| keywords | 解释                           |
| -------- | ------------------------------ |
| gt       | 选择大于指定版本的IE版本       |
| gte      | 选择大于或等于指定版本的IE版本 |
| lt       | 选择小于指定版本的IE版本       |
| lte      | 选择小于或等于指定版本的IE版本 |
| !        | 选择除指定版本外的所有IE版本   |
| (空)     | 指定是否IE或IE某个版本         |

version则是IE浏览器的版本

```css
<!--[if IE]> 
 <p>你在非IE中将看不到我的身影</p> 
<![endif]-->
  
<!--[if IE]> 
<style> 
 .test{color:red;} 
</style> 
<![endif]-->
  
<!--[if lt IE 9]> 
 <script src="//cdn.bootcss.com/html5shiv/3.7.2/html5shiv.min.js"></script> 
 <script src="//cdn.bootcss.com/respond.js/1.4.2/respond.min.js"></script> 
<![endif]-->
```



---

**属性级hack**

属性hack就是在CSS样式属性名前加上一些只有特定浏览器才能识别的hack前缀。

语法：`selector{<hack>?property:value<hack>?;}`

|            | IE6  | IE7  | IE8  | IE9  | IE10 | 现在浏览器 |
| ---------- | ---- | ---- | ---- | ---- | ---- | ---------- |
| *          | true | true |      |      |      |            |
| +          |      | true |      |      |      |            |
| -          | true |      |      |      |      |            |
| !important |      | true | true | true | true | true       |
| \9         | true | true | true | true | true |            |
| \0         |      |      | true | true | true |            |
| \9\0       |      |      |      | true | true |            |

```css
background-color:green;/*所有浏览器*/
+background-color:green;/*IE7浏览器*/
*background-color:green;/*IE6、7浏览器*/
```

**选择器hack**

语法：`<hack> selector{ sRules }`

|        | IE6  | IE7  | IE8  | IE9  | IE10 | 现代浏览器 |
| ------ | ---- | ---- | ---- | ---- | ---- | ---------- |
| *html  | true |      |      |      |      |            |
| *+html |      | true |      |      |      |            |
| :root  |      |      |      | true |      |            |

例如：针对IE9的hack可以这么写

```css
:root .test
{
    background-color:green;
}
```



## 17.4、自动化插件

Autoprefixer是一款自动管理浏览器前缀的插件，它可以解析CSS文件并且添加浏览器前缀到CSS内容里，使用Can I Use（caniuse网站）的数据来决定哪些前缀是需要的。

把Autoprefixer添加到资源构建工具（例如Grunt）后，可以完全忘记有关CSS前缀的东西，只需按照最新的W3C规范来正常书写CSS即可。如果项目需要支持旧版浏览器，可修改browsers参数设置 。

```css
/*我们编写的代码 */
div { 
 transform: rotate(30deg); 
} 
  
/*自动补全的代码，具体补全哪些由要兼容的浏览器版本决定，可以自行设置 */
div { 
 -ms-transform: rotate(30deg); 
 -webkit-transform: rotate(30deg); 
 -o-transform: rotate(30deg); 
 -moz-transform: rotate(30deg); 
 transform: rotate(30deg); 
}
```

# 十八、样式冲突问题

## 18.1、CSS样式覆盖规则

CSS的全称叫做“层叠样式表，“层叠”指的就是样式的覆盖，当一个元素被运用上多种样式，并且出现重名的样式属性时，浏览器必须从中选择一个属性值，这个过程就叫“层叠”。样式覆盖（这种叫法更大众化些）遵循一定的规则：

* 规则一：**由于继承而发生样式冲突时，最近祖先获胜。**
* 规则二：**继承的样式和直接指定的样式冲突时，直接指定的样式获胜。**
* 规则三：**直接指定的样式发生冲突时，样式权值高者获胜。**
* 规则四：**样式权值相同时，后者获胜。**
* 规则五：**!important的样式属性不被覆盖。**

> **由于样式表可以是外部的，也可以是内部的，规则四提醒我们要注意外部样式表引入的顺序（及\<link>元素的顺序），以及外部样式表与内部样式表的出现位置。一般来说，内部样式表出现在所有外部样式表的引入之后，一般是在\</head>之前。**
>
> 引入样式的优先级：内联>内部>外部

> **样式的权值取决于样式的选择器，权值计算请看本文的2.14小节**

## 18.2、外部样式权重高于局部样式时的处理方法

假如外部样式权重高于局部样式时，而我们不想修改全局样式，仅想在单页面覆盖全局样式时，可以采取以下的方法：

* 提高局部样式的权重
* 使用!important

## 18.3、Vue中覆盖第三方样式的问题

在Vue框架中的style标签上，有一个特殊的属性：scoped。

当一个style标签拥有scoped属性时，它的CSS样式就只能作用于当前的组件，通过该属性，可以使得组件之间的样式不互相污染。

引用了第三方组件（比如elementUI）后，需要在组件中局部修改第三方组件的样式，而又不想去除scoped属性造成组件之间的样式污染。此时只能通过特殊的方式，穿透scoped。

**样式穿透的写法有三种：`>>>`、`/deep/`、`::v-deep`**

1、`>>>`

如果项目使用的是css原生样式，那么可以直接使用 `>>>` 穿透修改

```css
/*  用法：  */
div >>> .cla {
	color: red;
}
```

2、`/deep/`

项目中用到了预处理器 scss 、sass、less 操作符 `>>> `可能会因为无法编译而报错 。可以使用 `/deep/`

> 注意：vue-cli3以上版本不可以，仅适用于Vue2.x版本

```css
/*  用法：  */
div /deep/ .cla {
	color: red;
}
```

3、`::v-deep`

Vue3.x的深度作用选择器正式写法

```css
/*  用法：  */
div ::v-deep .cla {
	color: red;
}
```

# 十九、如何隐藏滚动条

当内容溢出时会出现一个丑丑的滚动条，如果使用`overflow:hidden`会将内容截断。

下面我们将介绍如何隐藏这个滚动条而不影响滚动的功能。

## 19.1、使用两层div

思路：创建一个父\<div>和一个子\<div>,然后给父\<div>设置一个高度和内容超出后隐藏的样式，同时给子\<div>设置内容超出后显示滚动条、高度为100%、宽=100%+滚动条的宽。

也就是说，父div能刚好把子div的滚动条个hidden了。具体实现如下：

```css
<div class="outer-container">	
    <div class="inner-container">	
     ......
    </div>
</div>
.outer-container{
     width: 360px;
     height: 200px;
     position: relative;
     overflow: hidden;
}

.inner-container{
     position: absolute;
     left: 0;
     top: 0;
     right: -17px;/*关键点*/
     bottom: 0;
     overflow-x: hidden;
     overflow-y: scroll;

}
```

> 这个代码巧妙的向右移动了17个像素，刚好等于滚动条的宽度。这个值是手动调试得来的。

## 19.2、使用三层div

使用三个容器包围起来，不需要计算滚动条的宽度

将内容限制在盒子里面了。这样子就看不到滚动条同时也可以滚动

```css
<div class="outer-container">
     <div class="inner-container">
        <div class="content">
            ......
        </div>
     </div>
 </div>
.element, .outer-container {
      width: 200px;
      height: 200px;
}

.outer-container {
      border: 5px solid purple;
      position: relative;
      overflow: hidden;
}

.inner-container {
      position: absolute;
      left: 0;
      overflow-x: hidden;
      overflow-y: scroll;
}

.inner-container::-webkit-scrollbar {
      display: none;
}
```

## 19.3、使用伪类选择器`::-webkit-scrollbar`

在只需兼容移动浏览器（Chrome 和 Safari）时可以这么做。

```css
.element::-webkit-scrollbar 
{
    display:none
}
```

