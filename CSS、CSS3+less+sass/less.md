---
title: less学习文档
date: 2023-7-26
tags:
 - less
categories:
 - less
---
<h1><center>less</center</h1>

[TOC]

# 一、介绍与安装

## 1.1、**介绍**

​	 less作为一门CSS扩展语言，也就是说CSS预处理器。（Leaner Style Sheets）简称less，它只不过是为css新增这些的功能，比如说：变量、函数、作用域等等。它的优点是：更具有维护性、扩展性等，可以降低了维护的成本，根据按这样的话，那么less可以让我们写更少的代码做更多的事情。
​	css的语法非常简单，而且对开发者来说要求比较低，比较合适小白者，但是遇到有些问题，比如没有这种变量、函数等等，的确还不如less的扩展性，需要写大量的代码，但是看眼中的确没有逻辑的代码，CSS冗余度是比较高的。不方便维护，不利于复用，而且没有计算的能力。
  	如果对css有基础的话，less很容易上手的。因为css和less区别不大的，反正可以通过编译生成浏览器能识别的css文件。

> less文件保存时会自动编译成css文件

## 1.2、**使用 Less 的两种方式**

**1、在页面中 引入 Less.js**

- 可在[官网](https://link.juejin.cn/?target=http%3A%2F%2Flesscss.org%2F)下载

- 或使用CDN

    ```html
    <----html---->
    <script src="//cdnjs.cloudflare.com/ajax/libs/less.js/2.7.2/less.min.js">
    </script>
    ```

    ```html
    <link rel="stylesheet/less" href="style.less">
    <script src="less.min.js"></script>
    ```

> 需要注意的是，link 标签一定要在 Less.js 之前引入，并且 link 标签的 rel 属性要设置为stylesheet/less。

**2、在命令行 使用npm安装**

```bash
npm install -g less
```

具体使用命令

```bash
lessc styles.less > styles.css
```

假如还有问题，[官网](https://link.juejin.cn/?target=http%3A%2F%2Fless.bootcss.com%2F)已经有了明确的步骤。

如果你也是 Webpack 的使用者，还需要配合 less-loader 进行处理，具体可见这篇文章：[Webpack飞行手册](https://link.juejin.cn/?target=https%3A%2F%2Ftomotoes.com%2Fposts%2F4d6f8cc5%2F)，里面详细说明了 less 的处理方式。

如果你在本地环境，可以使用第一种方式，非常简单；但在生产环境中，性能非常重要，最好使用第二种方式。

## 1.3、**less和sass的区别**

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

# 二、less语法

## 2.1、变量

变量的定义方式为@，可以赋给变量！

>  变量存在作用域。

语法：**@变量名：值**

less:

```less
// 1.普通的变量
@bgColor:white;
@Height:50rpx;
.contain{
    background-color: @bgColor;
 
}
.row{
    height:@Height;
    margin-left:@Height;
} 
```

编译后的CSS

```css
.contain {
  background-color: white;
}
.row {
  height: 50rpx;
  margin-left: 50rpx;
}
```

**变量还可以用在选择器和属性名上**

```less
// 2.作为选择器和属性名
@Mycontain:width;
 
.@{Mycontain}{//选择器
    height:300rpx;
    @{Mycontain}:200rpx;//属性名
}
```

编译后的CSS

```css
.width {
  height: 300rpx;
  width: 200rpx;
}
```

**变量还可以用作URL**

```less
// 3.作为URL
@img-url:"../imgs/idnex";
img{
    background-image: url("@{img-url}/shouye.png");
}
```

编译后的css：

```css
img {
  background-image: url("../imgs/idnex/shouye.png");
}
```

> 变量是延迟加载的，在使用前不一定要预先声明。在后面声明也是可以的

> 变量作用域：重复声明一个变量时，已最后一个为准(就近原则)

## 2.2、混合

混合就是一种将一系列属性从一个规则引入（“混合”）到另一个规则集的方式。**这个意思是在less中定义的选择器类可以直接放入其他选择器类里面，这种重复使用很强。**

```less
//1.普通混合
.bor{
    background-color: aqua;
    width: 32rpx;
}
.poop{
    color:white;
    .bor;
}
 
.boom{
    height:200rpx;
    .bor;
}
```

编译后的css：

```css
.bor {
  background-color: aqua;
  width: 32rpx;
}
.poop {
  color: white;
  background-color: aqua;
  width: 32rpx;
}
.boom {
  height: 200rpx;
  background-color: aqua;
  width: 32rpx;
}
```

**如果想要创建一个混合的类，但是不想让它输出到css的样式并显示。只要类的名字后面加上括号，就可以实现的，这样不会到css样式中显示！**

```less
// 2.不带输出的混合
.mymix{
    color:black;
}
.mymix-echa(){//css样式中不显示
    background-color: white;
 
}
.dad{
    width: 30rpx;
    height:30rpx;
}
```

编译后的css:

```css
.mymix {
  color: black;
}
.dad {
  width: 30rpx;
  height: 30rpx;
}
```

> **在css样式中实现不显示.mymix-echa()类。**

**带选择器的混合**

```less
//3.带选择器的混合
.father(){
    &:hover{
        background-color: white;
        font-size:32px;
    }
}
 
.child{//类名字后面多了:hover
    .father;
}
.son{//类名字后面多了:hover
    .father;
}
```

编译后的css:

```css
.child:hover {
  background-color: white;
  font-size: 32px;
}
.son:hover {
  background-color: white;
  font-size: 32px;
}
```

**带参数的混合**

```less
// 4.带参数的混合
.son(@width){
    width:@width;
}
.dad{
    .son(300px);//需要传一个参数进去
}
```

编译后的css:

```css
.dad {
  width: 300px;
}
```

**带多个参数的混合**

一个组合可以带多个参数，参数之间可以使用分号或者逗号来分割。

> 建议参数之间都使用分号进行分割

形参也可以带默认值，如下：

```less
//6.带多个参数的混合
.mini(@color;@padding:xxx;@margin:2){
    color-1:@color;
    padding-2:@padding;
    margin-3:@margin;
}
.div{
    .mini(1,2,3;something, ele);
}
```

编译后的css：

```css
.div {
  color-1: 1, 2, 3;
  padding-2: something, ele;
  margin-3: 2;
}
```

> 在less的.div{.mini（1,2,3;something,ele）}参数只有两个，那么就会传到形参1和形参2，形参3使用默认值2

**arguments变量**

arguments变量表示可变参数，意思是形参从先到后的顺序。**注意：这个是参数值位置必须是一一对应。**

```less
//7.arguments变量
.son3(@dd1:20px;@dd2:solid;@dd3:white){
    border:@arguments;
}
.div4{
    .son3();
}
```

编译后的css:

```css
.div4 {
  border: 20px solid white;
}
```

## 2.3、匹配模式

当传值的时候定义一个字符，在使用那个一个字符，就调用规则集。

```less
 
// 8.匹配模式
.border(all,@w){
    border-radius: @w;
}
 
.border{
    .border(all,50%);
}
```

编译后的css：

```css
.border {
  border-radius: 50%;
}
```

**得到混合中的变量的返回值**

就像调用函数一样的过程

```less
//9.得到混合中变量的返回值
.ave(@x,@y){
    @ave:(@x+@y);
}
.son{
    .ave(20px,40px);
    width:@ave;
}
```

编译后的css：

```css
.son {
  width: 60px;
}
```

> .less中第六行调用了.ave,而.ave只声明了一个变量，实际相当于在.son中声明了变量@ave,所以变量ave的作用域在.son中

## 2.4、嵌套规则

为了提高代码复用率，可以使用嵌套规则。

```less
//10.嵌套规则
.contain{
  .dad{
      width:30px;
      background-color: #fff;
      .son{
          border-radius: 40px;
      }
  }  
  .dad1{
      height:300px;
      background-color: black;
  }
}
```

编译后的css：

```css
.contain .dad {
  width: 30px;
  background-color: #fff;
}
.contain .dad .son {
  border-radius: 40px;
}
.contain .dad1 {
  height: 300px;
  background-color: black;
}
```

**父元素选择器&**

表示当前选择器的所有父选择器，使用&符引用选择器的名。

```less
//11.父元素选择器&
.bgcolor{
    background: black;
    a{
        color:#fff;
        &:hover{
            color:blue;
        }
    }
}
```

编译后的css：

```css
.bgcolor {
  background: black;
}
.bgcolor a {
  color: #fff;
}
.bgcolor a:hover {
  color: blue;
}
```

**改变选择器的顺序&**

如果将当前的选择器名字后面放在&，就会当前的选择器提到父级。

```less
// 12.改变选择器的顺序&
.contain{
    h1&{
        width:200px;
        height:300px;
    }
}
 
#son{
    ul{
        li{
            .contain&{
                height:100px;
                background-color: #fff;
            }
        }
    }
}
```

编译后的css：

```css
h1.contain {
  width: 200px;
  height: 300px;
}
.contain#son ul li {
  height: 100px;
  background-color: #fff;
}
```

## 2.5、运算

任何数值，颜色和变量都可以计算的，less当然会自动推断数值的单位，所以不必每一个值都加上单位，有一个值带单位即可。

```less
// 13.运算
.contain{
    font-size:300px+200*2;
}
```

编译后的css：

```css
.contain {
  font-size: 700px;
}
```

# 三、其他

## 3.1、命名空间

如果将一些变量或者混合块一起打包起来，这样可以支持复用性，也可以通过嵌套多层id或者class来实现。

```less
// 14.命名空间
//实例1
#contain(){//加()，表示css不输出
    background-color: blue;
    .dad{
        width:300px;
        &:hover{
            height:200px;
        }
    }
    .father{
        width:100px;
        height:200px;
    }
}
//到css中显示
.contain1{
    background-color: aqua;
    #contain>.dad;
}
```

编译后的css：

```css
.contain1 {
  background-color: aqua;
  width: 300px;
}
.contain1:hover {
  height: 200px;
}
```

> 注意，.contain1:hover中没有` background-color: aqua;`这一句·。
>
> 这是因为`#contain>.dad;`这一句编译时，实际就是把对应的代码完全复制过来，成下面这样

```less
.contain1{
    background-color: aqua;
    width:300px;
    &:hover{
        height:200px;
    }
}
```

## 3.2、作用域

less中的作用域与编程语言中的作用域概念非常类似。首先会在局部查找变量和混合，如果没找到，编辑器就会在父作用域中查找，以此类推。

## 3.3、引入（importing）

可以引入一个或多个.less文件，然后这个文件中的所有变量都可以在当前的less项目中使用！

引用.less文件时可以带参数

```less
//@import "main.less";
//@import (reference) "main.less";  //引用LESS文件，但是不输出
//@import (inline) "main.less";  //引用LESS文件，但是不进行操作
//@import (once) "main.less";  //引用LESS文件，但是进行加工，只能使用一次
//@import (less) "index.css";  //无论是什么格式的文件，都把它作为LESS文件操作
//@import (css) "main.less";  //无论是什么格式的文件，都把它作为CSS文件操作
@import (multiple) "../main.less";  //multiple，允许引入多次相同文件名的文件
@import (multiple) "../main.less";  //multiple，允许引入多次相同文件名的文件
```

> 如果有引入的内容覆盖了默认变量则使用引入的值(或默认值定义前已有定义),否则使用默认值
