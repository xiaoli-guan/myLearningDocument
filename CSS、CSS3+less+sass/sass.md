---
title: Sass学习文档
date: 2023-7-26
tags:
 - sass
categories:
 - sass
---

<h1><center>Sass学习文档</center></h1>

[TOC]

 # 一、Sass介绍

## 1.1、介绍

[Sass中文网](https://www.sass.hk/)

Sass(Syntactically Awesome Stylesheets)是一个 CSS 预处理器，是 CSS 扩展语言，可以帮助我们减少 CSS 重复的代码，节省开发时间。

1.  它能够帮我们更快更高效的编写更好维护的 css；
2.  Sass 引入合理的样式复用机制，可以节约很多时间来重复。

## 1.2、less和sass的区别

**1、Less在JS上运行，Sass在Ruby上使用。**

**2、编写变量的方式不同。**

Sass使用$，而Less使用@

**3、在Less中，仅允许循环数值。**

在Sass中，我们可以遍历任何类型的数据。但在Less中，我们只能使用递归函数循环数值。

**4、输出格式不一样**

Less无输出格式，Sass可以使用特定的输出格式

- nested：嵌套缩进的css代码
- expanded：展开的多行css代码
- compact：简洁格式的css代码
- compressed：压缩后的css代码

# 二、Sass安装引入

请点击下方链接进行Sass的安装

[Sass安装带图博客](https://blog.csdn.net/Sunsun1114/article/details/122757906?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522169033781516800180648683%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=169033781516800180648683&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~hot_rank-14-122757906-null-null.142^v91^koosearch_v1,239^v3^control&utm_term=Rudy%E5%AE%89%E8%A3%85&spm=1018.2226.3001.4187)

# 三、Sass语法

## 3.1、变量

> 变量可以存储样式信息，以便后面使用。  
> 比如一个样式在页面的多个地方使用，就可以先将该样式的值赋给一个变量，后面直接使用变量即可。

**语法：** $变量名：样式值；  
**使用：** $变量名；  
**注意点**：

1.  以$符号开头，后跟变量名
2.  多个单词，变量名以-分割，如：$theme-color
3.  变量写在#{}中以镶嵌入字符串

**示例如下：**

```scss
// .scss文件  Sass后缀名为scss
$dark: #000;
$side: left;
.box {
	color: $dark;
}

.box2 {
	background: $dark;
	border-#{$side}-radius: 5px;
}

--------------------------------------

// 生成的css代码
.box1 {
  color: #000;
}

.box2 {
  background: #000;
  border-left-radius: 5px;
}
```


## 3.2、嵌套

### 3.2.1、选择器嵌套

> 子元素在父元素样式的一对大括号{}内 如：ul { li { } }

**语法：**

    爷爷 {
    	爸爸 {
    		儿子 {
    			孙子 {
    			
    			}
    		}
    	}
    }


**示例如下:**

```scss
// html结构
<div class="grandpa">
	<div class="father">
		<div class="son"></div>
	</div>
</div>
// .scss文件
.grandpa {
    width: 200px;
    height: 200px;
    
    .father {
        width: 100px;
        height: 100px;

        .son {
            width: 50px;
            height: 50px;
        }
    }
}

--------------------------------------

// 生成的css代码
.grandpa {
  width: 200px;
  height: 200px;
}

.grandpa .father {
  width: 100px;
  height: 100px;
}

.grandpa .father .son {
  width: 50px;
  height: 50px;
}
```


### 3.2.2、伪类嵌套

> 从上面我们可以看出，选择器嵌套得出的css样式相当于后代选择器一样，中间都有一个空格分隔，那如果想给一个元素添加:hover要怎么做呢?

&符就是来解决这个问题的。  
**语法:** &:hover { }  
**示例如下：**

```scss
// html结构
<div class="box">
	<a href="javascript:;">hello</a>
</div>
// .scss文件
// 这里我们希望鼠标悬停a的文本颜色改变
.box {
	a {
		&:hover {
			color: red;
		}
	}
}
--------------------------------------

// 生成的css代码
.box a:hover {
  color: red;
}
```


这里&就表示直接调用父选择器，拿上边的例子你可以把&理解为它是&外面的所有父选择器，& =\> .box a。

## 3.3、混合 mixin

> mixin相当于已经定义好了一类样式，可以在任何地方重复的使用它，就跟js中的函数一样。

**语法1-不含参数：**

    @mixin name {
    	css样式
    }


**使用:** @include name；  
**示例如下:**

```scss
// .scss文件
// 定义一个mixin
@mixin box-style {
	width: 200px;
	height: 200px;
	background: #000;
}
// 使用
.box {
	@include box-style;
	// 当然也可以继续在这里添加样式
	border-radius: 5px;
}
--------------------------------------

// 生成的css代码
.box {
  width: 200px;
  height: 200px;
  background: #000;
  border-radius: 5px;
}
```


**语法2-含参数:**

    @mixin name ($param1，$param2， ...) {
    	css样式
    }

**使用:** @include name(样式1，样式2，…)；  

> **注意：**  定义的时候参数要以$符开头，和变量命名是一样的  

**示例如下:**

```scss
// .scss文件
$box-width: 200px;
$box-height: 200px;

// 定义一个mixin
@mixin box ($width, $height) {
	width: $width;
	height: $height;
}
// 使用
.box {
	// 1. 第一种用法, 直接将css样式写入
	@include box(200px, 200px);

	// 2. 第二种, 将定义好的变量写入
	@include box($box-width, $box-height);
}

--------------------------------------

// 生成的css代码
.box {
  width: 200px;
  height: 200px;
}
```


## 3.4、继承 extend

> 如果一个元素的样式和另一个元素的样式完全一样，这个元素无需再写一遍重复的样式，只需要使用@extend 就可以把另一个元素的所有样式全部继承过来。

**语法:** @extend 元素选择器；  
**示例如下：**

```scss
// .scss文件
.box1 {
	width: 200px;
	height: 200px;
}

// box2 继承 box1的样式
.box2 {
	@extend .box1;
}
--------------------------------------

// 生成的css代码
.box1, .box2 {
  width: 200px;
  height: 200px;
}
```


不过继承要慎用，被继承相关的元素的样式也会继承过去，您看下面的例子：

```scss
// .scss文件
.box1 {
	width: 200px;
	height: 200px;
}
.box1 div {
	width: 100px;
}

// box2 继承 box1的样式
.box2 {
	@extend .box1;
}
--------------------------------------

// 生成的css代码
.box1, .box2 {
  width: 200px;
  height: 200px;
}

.box1 div, .box2 div {
  width: 100px;
}
```


如果不想与被继承元素的相关元素牵扯，还是注意选择器的书写。

## 3.5、导入 import

> 如果一个页面需要使用其他页面的样式，sass可以导入其他的scss文件，scss会把他们编译成一个css文件。  
> 这样在开发中可以把一个页面的样式分割成多个scss文件，然后在页面的scss文件中导入其他scss，可以实现css的模块化开发。

**语法：** @import “文件名”  

**示例如下：**

```scss
// 这里假设同级目录下有一个box1.scss
div {
	width: 200px;
}
// 在box2.scss文件里引入box1.scss
@import "box1"
--------------------------------------

// 生成的css代码
div {
	width: 200px;
}
```


## 3.6、注释

1.  单行注释： / / css文件里不会显示 压缩方式的css不会显示
2.  多行注释： /**/ css文件里会显示 压缩方式的css不会显示
3.  强制注释：/\* ! */ css文件里会显示 压缩方式的css会显示

## 3.7、数学运算

> 包含+、-、*、/(加减乘除)

**示例如下:**

```scss
// .scss文件
.box {
	width: 50px + 50px;
	height: 100px - 50px;
	// 这里不能两个都带单位，否则是100px*px这种不合法的值
	margin-top: 10px * 10; 
	// css会将/认为是合法的，所以需要加括号
	padding-top: (100px / 2) ;
}
--------------------------------------

// 生成的css代码
.box {
  width: 100px;
  height: 50px;
  margin-top: 100px;
  padding-top: 50px;
}
```


## 3.8、if条件语句

> Sass可以根据条件判断给出特定的样式

**语法:**

    @if 条件语句 {
    } @ else if 条件语句 {
    } @else


**示例如下：**

```scss
// .scss文件
.box {
	@if 1+1 == 2 {
		color: red;
	} @else if 1+1 == 3 {
		color: blud;
	} @else {
		color: pink;
	}
}
--------------------------------------

// 生成的css代码
.box {
  color: red;
}
```


## 3.9、for循环

> Sass也支持for循环，有两种语法。

**语法1：**

    @for $index from 开始值 through 结束值 {
    }
    从开始值开始，到结束值结束，包含结束值  index表示 1， 2，...结束值


**示例如下:**

```scss
// .scss文件
@for $i from 1 through 5 {
	.col-#{$i} {
		width: 50px * $i;
	}
}
--------------------------------------

// 生成的css代码
.col-1 {
  width: 50px;
}

.col-2 {
  width: 100px;
}

.col-3 {
  width: 150px;
}

.col-4 {
  width: 200px;
}

.col-5 {
  width: 250px;
}
```

**语法2：**

    @for $index from 开始值 to 结束值 {
    }
    从开始值开始，到结束值结束，不包含结束值  index表示 1， 2，...结束值-1


**示例如下:**

```scss
// .scss文件
@for $i from 1 to 5 {
	.col-#{$i} {
		width: 50px * $i;
	}
}
--------------------------------------

// 生成的css代码
.col-1 {
  width: 50px;
}

.col-2 {
  width: 100px;
}

.col-3 {
  width: 150px;
}

.col-4 {
  width: 200px;
}
```


## 3.10、each循环

> 遍历一个列表，然后从列表中取出对应值。  
> 像border: 1px solied red； 1px solid red 这种用空格隔开的复合属性便是列表。

**语法：**

    @each $index in $list {
    }


**示例如下：**

```scss
// .scss文件
$icons: success fail warning;
@each $i in $icons {
	.icon-#{$i} {
		background-image: url(../images/icons/#{$icon}.png);
	}
}
--------------------------------------

// 生成的css代码
.icon-success {
  background-image: url(../images/icons/success.png);
}

.icon-error {
  background-image: url(../images/icons/error.png);
}

.icon-warning {
  background-image: url(../images/icons/warning.png);
}
```


## 3.11、while循环

> 只要条件为真，就执行语句体。

**语法：**

    @while 条件 {
    }


**示例如下：**

```scss
// .scss文件
$index: 6;
@while $index> 0 {
    .box-#{$index} {
        width: 5px * $index;
    }

    $index: $index - 2;
}
--------------------------------------

// 生成的css代码
.box-6 {
  width: 30px;
}

.box-4 {
  width: 20px;
}

.box-2 {
  width: 10px;
}
```


## 3.12、用户自定义函数

**语法：**

    @function name($param1，$param2，...) {
    }


**示例如下：**

```scss
// .scss文件
$index: 6;
@function get-color($key) {
	@if $key > 5 {
		@return #000;
	} @else {
		@return #fff;
	}
}

body {
	background: get-color($index);
}
--------------------------------------

// 生成的css代码
body {
  background: #000;
}
```

