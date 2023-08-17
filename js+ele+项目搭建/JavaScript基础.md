---
title: basic infomation of JavaScript
date: 2023-7-19
tags:
 - JavaScript 
categories:
 - JavaScript
---

<h1><center>JavaScript基础</center></h1>

[toc]

# 一、基于 ES6 的 JavaScript 

## 1.1、JavaScript的简介

**JavaScript** 是一款基于原型的的多范式动态脚本语言，支持命令式、函数式以及面向对象式的编程风格。其标准化工作主要由**欧洲计算机制造商协会**（**ECMA**，European Computer Manufacturers Association）负责，其语言标准被称为**ECMAScript**，其它组织可以遵循该标准开发各自的 JavaScript 实现，例如 Firefox 内置的 [**SpiderMonkey**](https://spidermonkey.dev/) 以及 Chrome 内置的 [**V8**](https://v8.dev/) 解析引擎（ECMAScript 规范文档主要针对解析引擎的开发人员，而非 JavaScript 脚本的编写人员）。

[![img](http://www.uinio.com/Web/Javascript/logo.png)](http://www.uinio.com/Web/Javascript/logo.png)

2012 年之后推出的 Web 浏览器都完整实现了 **ECMAScript 5.1** 标准，而 2015 年发布的 **ECMAScript 6** 标准（官方称为 **ECMAScript 2015**，俗称为 **ES6**），目前已经被 [Firefox](https://www.mozilla.org/) 和 [Chromium](https://www.chromium.org/) 以及 [NodeJS](https://nodejs.org/) 进行了较为完整的实现，所以本文将会基于此介绍 JavaScript 的重点语法特性，以及一些较为用常用的核心工具函数，本文在写作过程当中参考了 Mozilla 开发者社区的 [**《JavaScript Guide》**](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide) 和 [**《JavaScript Reference》**](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference) 两篇官方文档。

## 1.2、JavaScript的特点

|      <center>特点</center>      | <center>介绍</center>                                        |
| :-----------------------------: | ------------------------------------------------------------ |
|         **解释型语言**          | 不需要被编译为机器码在执行，而是直接执行                     |
|          **动态语言**           | 所谓的动态语言可以暂时理解为在语言中的一切内容都是不确定的。比如一个变量，这一时刻是个整型，下一时刻可能会变成字符串了。动态语言相比静态语言性能上要差一些 |
| **类似于 C 和 Java 的语法结构** | JavaScript的语法结构与C和Java很像，向for、if、while等语句和Java的基本上是一模一样的 |
|     **基于原型的面向对象**      | JavaScript是一门面向对象的语言。就是把现实中的事物都抽象为“对象”。每个对象是唯一的，且都可以拥有它的属性与行为。我们就可以通过调用这些对象的方法、属性去解决问题。 |
|       **严格区分大小写**        | JavaScript是严格区分大小写的，也就是abc和Abc会被解析器认为是两个不同的东西。 |



## 1.3、JavaScript的使用

### 1.3.1、标签引用

```html
<script>
    //JavaScript语句写在这里
    alert("Hello,World!");
</script>
```

### 1.3.2、文件引用

```js
//main.js
alert("Hello,World!");
```

```html
<!-----引用js文件------>
<script src="main.js"></script>
```

## 1.4、JavaScript的输出

|              |        解释        |                             方法                             |
| :----------: | :----------------: | :----------------------------------------------------------: |
|   页面输出   |    显示在页面上    |                           write()                            |
|  控制台输出  |  向控制台输出内容  | console.log()、console.info()、console.warn()、console.error() |
| 弹出窗口输出 | 向弹出窗口输出内容 |                           alert()                            |

## 

# 二、基础语法

## 2.1、语句

JavaScript 使用 **Unicode** 字符集，并且对于大小写敏感。源文件当中的每一条 JavaScript 语句都要使用分号 `;` 进行分隔，虽然这并非必需，但是可以大大降低代码发生错误的可能。

```js
var name = "www.uinio.com";
```

> **注意**：Javascript 源代码会被解析引擎从左至右进行扫描执行。

## 2.2、注释

JavaScript 的注释与许多 C/C++ 类语言相似，同样可以划分为**单行**与**多行**两种类型：

```
// 单行注释

/*
  多行注释
*/
```

## 2.3、变量

JavaScript 的变量是松散类型（弱类型）的，**可以用来保存任何类型的数据**。在定义变量的时候不需要指定变量的数据类型。

### 2.3.1、标识符

变量的名称叫做**标识符**，虽然可以使用大部分的 **ISO 8859-1** 或者 **Unicode** 编码字符作为标识符，其必须以字母、下划线 `_`、美元符号 `$` 作为前缀，后续可以是数字 `0 ~ 9` 或者大写字母 `A ~ Z` 以及小写字母 `a ~ z`，且变量名称对大小写敏感（y 和 Y 是不同的变量），例如：

```
zs  _uinika  $Chengdu  from2021  to_2022
```

### 2.3.2、声明

ECMAScript 6 当中一共拥有 `var`、`let`、`const` 三种变量声明关键字：

- `var`：声明一个**变量**；
- `let`：声明具有块作用域的**局部变量**；
- `const`：声明具有块作用域的**只读常量**；

**区别**：

- `var`声明是全局作用域或函数作用域，而`let`和`const`是块作用域。
- `var`变量可以在其范围内更新和重新声明； `let`变量可以被更新但不能重新声明； `const`变量既不能更新也不能重新声明。
- `var`不初始化会输出`undefined`，不会报错；但在声明期间必须初始化`const`

JavaScript 源代码当中可以采用如下三种方式来**声明**一个变量：

- 采用 `var` 关键字：用于声明**局部变量**和**全局变量**，例如 `var x = 2022`；
- 采用 `let` 关键字：用于声明具有**块作用域**的局部变量，例如 `let y = 13`，变量需要先声明再使用；
- 直接赋值：函数外使用会产生一个全局变量，严格模式下这种方式会发生错误，所以应该避免使用，例如 `x = 2021`；

### 2.3.3、求值

采用关键字 `var` 或者 `let` 声明的变量，如果没有赋予初始值，则其值将会默认为 `undefined`。而访问未经过声明的变量，将会导致解析引擎抛出一个 `ReferenceError` 引用错误异常：

```js
var a;
console.log("变量 a 的值为 " + a); // 变量 a 的值为 undefined

console.log("变量 b 的值为 " + b); // 变量 b 的值为 undefined
var b;

console.log("变量 c 的值为 " + c); // Uncaught ReferenceError: c is not defined

let x;
console.log("变量 x 的值为 " + x); // 变量 x 的值为 undefined

console.log("变量 y 的值为 " + y); // Uncaught ReferenceError: y is not defined
let y;
```

因此，可以使用 `undefined` 来判断一个变量是否已经赋值，下面代码当中，由于变量 `input` 未被赋值，所以 `if` 语句的求值结果为 `true`：

```js
var input;
if (input === undefined) {
  doThis();
} else {
  doThat();
}
```

类似的，由于下面代码当中数组 `myArray` 里的元素未被赋值，所以 `myFunction()` 函数将会得到执行：

```js
var myArray = [];

if (!myArray[0]) myFunction();
```

在数值类型的计算当中，`undefined` 值会被自动转换为**非数值** `NaN`：

```js
var number;

number + 2; // NaN
```

同样在数值计算当中，当对一个空值变量 `null` 进行求值时，其值会被自动转换为 `0`；而如果是在布尔类型运算当中，`null` 值则会被作为 `false` 进行处理：

```js
var test = null;

console.log(test * 32); // 0
```

### 2.3.4、作用域

**全局变量**是在函数之外声明的变量，可以在源文件当中的其它位置进行访问；而**局部变量**是在函数内部声明的变量，其只能在当前函数的内部进行访问。

ECMAScript 6 之前的 JavaScript 不存在`语句块`作用域的概念，语句块当中声明的变量将会成为语句块所在函数或者全局作用域的局部变量，例如下面代码会在控制台输出 `2022`，因为变量 `code` 的作用域处于全局范围，而并非仅限于 `if` 语句块。

```js
if (true) {
  var code = 610000;
}

console.log(code); // 610000
```

如果使用 ECMAScript 6 当中的 `let` 关键字进行声明，则上述行为将会发生变化：

```js
if (true) {
  let code = 610000;
}
console.log(code); // Uncaught ReferenceError: code is not defined
```

### 2.3.5、变量提升

JavaScript 变量支持**先使用再声明**，而且不会引发任何异常，称为**变量提升**。但是提升之后的变量，如果没有及时的进行初始化，则依然会返回 `undefined` 值：

```js
/* 示例 1 */
console.log(num === undefined); // true
var num = 2022;

/* 示例 2 */
var name = "zs";
(function () {
  console.log(name); // undefined
  var name = "uinika";
})();
```

> **注意**：由于 JavaScript 变量提升特性的存在，所有 `var` 变量的声明语句应当尽量放置该函数顶部，从而极大的提升代码清晰度。

ECMAScript 6 提供的 `let` 和 `const` 关键字声明的变量，同样会存在变量提升的情况，但是并不会被赋予任何初始值，如果在变量声明之前引用（此时该变量处于**暂时性死区**，该状态会持续到该变量被声明为止），则会抛出 `ReferenceError` 引用错误异常。

```js
console.log(week); // Uncaught ReferenceError: week is not defined
let week = 7;
```

### 2.3.6、函数提升

JavaScript 当中的函数，只有**函数声明**会被提升至源文件顶部，而**函数表达式**并不会被提升。

```js
/* 函数声明 */
test1(); // test1
function test1() {
  console.log("test1");
}

/* 函数表达式 */
test2(); // Uncaught TypeError: test2 is not a function
var test2 = function () {
  console.log("test2");
};
```

### 2.3.7、全局变量

**全局变量**本质上是**全局对象**的属性，**Web 浏览器**当中的全局对象是 `window`，可以通过 `window.variable` 设置和访问全局变量：

```js
var URL = "www.uinio.com";
console.log(window.URL); // www.uinio.com
```

而 **NodeJS** 当中的全局对象是 `global`，则需要使用 `global.variable` 来设置和访问全局变量。

```js
URL = "www.uinika.com";
console.log(global.URL); // www.uinika.com
```

### 2.3.8、常量

使用关键字 `const` 可以创建一个只读的**常量**，其命名规则与变量相同，必须以字母、下划线 `_`、美元符号 `$` 开头，并且可以包含有字母、数字、下划线。

```js
const PI = 3.141592654;
```

**常量**即不可以重新赋值，也不可以在代码运行时重新声明，所以声明常量的时候，必须显式的将其初始化为某个具体值。**常量**的作用域规则与 `let` 块级作用域变量相同，在同一个作用域当中，不能使用与**变量名**或者**函数名**相同的名字来命名常量：

```js
function WEEK() {}
const WEEK = 7; // Uncaught SyntaxError: Identifier 'WEEK' has already been declared
```

然而，对于**常量对象**的**属性**进行赋值并不会受到保护，所以下面语句在执行时不会产生错误：

```js
const TEST = { key: "value1" };
TEST.key = "value2"; // 'value2'
```

同样的，对于**常量数组**的**元素**进行赋值也不会受到保护，所以下面语句在执行时同样不会产生错误：

```js
const WEB = ["HTML", "CSS"];
WEB.push("JAVASCRIPT");
console.log(WEB); // ['HTML', 'CSS', 'JAVASCRIPT']
```

## 2.4数据类型

最新的 ECMAScript 标准当中一共定义了 8 种数据类型，其中 7 种基本数据类型，以及 1 种对象数据类型：

|  数据类型   |       名称       | 描述                                                         |
| :---------: | :--------------: | :----------------------------------------------------------- |
|  `Boolean`  |    **布尔值**    | 拥有 `true` 和 `false` 两个值；                              |
|   `null`    |     **空值**     | 表示空值，由于 JavaScript 大小写敏感，所以 `null`、`Null`、`NULL` 三者完全不同。 |
| `undefined` |    **未定义**    | 表示变量未赋值时的属性；                                     |
|  `Number`   |     **数值**     | 用于存放整数或者浮点数；+Infinity：正无穷；-Infinity：负无穷；NAN：非数 |
|  `BigInt`   |    **大整数**    | 用于安全的存储和操作大整数；                                 |
|  `String`   |    **字符串**    | 表示一串文本值的字符序列;                                    |
|  `Symbol`   | **独一无二的值** | ECMAScript 6 新增加的数据类型，是一种实例唯一并且不可改变的数据类型； |
|  `Object`   |     **对象**     | 用于充当各种数据类型的命名容器；                             |

### 2.4.1、数组

数组是一个在**方括号** `[]` 当中包含有零个或者多个表达式的列表，其中每个表达式代表数组的一个**元素**，元素的个数就是该数组的长度。下面示例声明并且初始化了一个拥有 3 个元素的数组 `motors`，同时采用 `length` 关键字获取数组长度，并通过索引 `Array[index]` 访问数组里的元素。

```js
var motors = ["Geely", "Haval", "Chery"];

console.log(motors.length); // 3
console.log(motors[0]); // Geely
```

> **注意**：数组字面量同时也是一个 `Array` 对象。

初始化数组时如果连续输入两个逗号 `,`，则数组当中就会产生一个初始值为 `undefined` 的元素。

```js
var animal = ["Lion", , "dog", "cat"];

console.log(animal.length); // 4
console.log(animal[1]); // undefined
```

如果在元素列表的尾部添加了一个逗号，则这个都好将会被忽略，数组依然保持原有的长度。

```js
var animal = ["zs", "uinika",];

console.log(animal.length); // 2
console.log(animal[2]); // undefined
```

> **注意**：尾部逗号在早期的 Web 浏览器当中会产生错误，所以最佳实践是移除它们。而在必要的时候，可以显式的将元素声明为 `undefined`。

### 2.4.2、布尔值

布尔类型只有 `true` 和 `false` 两种字面量，下面示例通过 `typeof` 运算符获取变量的数据类型：

```js
let yes = true;
let no = false;

console.log(typeof yes); // boolean
console.log(typeof no); // boolean
```

> **注意**：`Boolean` 只是布尔类型的包装对象，两者不能混淆使用；

其他类型转化为`Boolen`类型

```js
Boolen(0);   //false
Boolen(NaN); //false
Boolen("");  //false
Boolen(null);//false
Boolen(undefined); //false
//除上述类型转化为Boolen为false，其他类型转化为Boolen均为true
Boolen(1); //true
```

### 2.4.3、整数

整数可以采用**十进制**（基数为 `10`）、**十六进制**（基数为 `16`）、**八进制**（基数为 `8`）、**二进制**（基数为 `2`）进行表示：

- **十进制整数**：由一串数值序列组成，并且没有前缀 `0`，例如 `0`、117`、`-345`；
- **八进制的整数**：前缀为 `0`、`0O`、`0o`（严格模式下，必须以 `0o` 或 `0O` 开头），只能包含数字 `0 ~ 7`，例如 `015`、`0001`、`-0o77`；
- **十六进制整数**：以 `0x`、`0X` 开头，可以包含数字 `0 ~ 9` 和字母 `a ~ f` 或者 `A ~ F`，例如 `0x1123`、`0x00111`、`0xF1A7`；
- **二进制整数**：以 `0b`、`0B` 开头，只能包含数字 `0` 和 `1`，例如 `0b11`、`0b0011`、`-0b11`；

```
0, 117  -345  十进制, 基数为10)
015, 0001 and -0o77 (八进制, 基数为8)
0x1123, 0x00111 and -0xF1A7 (十六进制, 基数为16或"hex")
0b11, 0b0011 and -0b11 (二进制, 基数为2)
```

### 2.4.4、浮点数

浮点数的字面量可以由带正负号 `+/-` 前缀**的十进制整数部分**、**小数点** `.`、**十进制小数部分**、**指数部分**组成。其中指数部分以 `e` 或者 `E` 作为前缀，后面紧接着一个带有正负号 `+/-` 的整数。

```js
-0.12345789; // -0.12345789
3.14e10; // 31400000000
0.1e-20; // 1e-21
```

### 2.4.5、对象

对象是一种封闭在花括号 `{}` 当中，具有多个键值对元素的列表。下面示例创建了一个 `auto` 对象，将第 1 个元素 `motor1` 定义为变量 `motor1` 的值；第二个元素，属性 getCar，引用了一个函数（即 CarTypes("Honda")）；第三个元素，属性 special，使用了一个已有的变量（即 Sales）。

```js
var motor1 = "BYD";

function drive(name) {
  return name === "BYD" ? "对不起，" + name + " 的 EV 受限!" : "把 " + name + " 开回家!";
}

var auto = {
  motor1: motor1,
  motor2: "AION",
  getMotor: drive,
};

console.log(auto.motor1); // BYD
console.log(auto.motor2); // AION
console.log(auto.getMotor("BYD")); // 对不起，BYD 的 EV 受限!
```

可以采用**数值**作为对象的属性名称，引用该属性的时候，则需要采用类似于数组索引 `object.[property]` 的访问方式：

```js
let motor = { favorites: { 1: "BYD", 2: "AION" }, 3: "Tesla" };

console.log(motor.favorites[1]); // BYD
console.log(motor[3]); // Tesla
```

同理，如果需要采用其它不合法的属性名称，则同样可以通过数组索引的方式进行访问：

```js
let motor = {
  埃安: "AION",
  特斯拉: "Tesla",
};

console.log(motor["埃安"]); // AION
console.log(motor["特斯拉"]); // Tesla
```

ECMAScript 6 支持创建对象时通过 `__proto__` 设置原型、简化 `key: value` 属性赋值、直接在对象中定义函数、支持调用父对象方法、动态计算表达式属性名称。

```js
let property = "this is a property";

const Test = {
  /* 对象创建时设置原型 */
  __proto__: {
    name: "zs",
  },

  property, // 缩写 property: property

  /* 直接定义函数 */
  toString() {
    return super.toString(); // 调用父对象上的函数
  },

  ["property_" + (() => 1985)()]: 2022, // 动态计算属性名称
};

console.dir(Test);
/* 
property: "this is a property"
property_1985: 2022
toString: ƒ toString()
[[Prototype]]: Object
  name: "zs"
  [[Prototype]]: Object
*/
```

### 2.4.6、RegExp

**正则表达式**字面量是一个被两条**正斜线** `/ ... /` 包围起来的表达式。

```js
const RegExp = /ab+c/;
```

### 2.4.7、字符串

字符串是由**双引号** `"` 或者**单引号** `'` 括起来的零个或者多个字符：

```js
"2022";
"uinika";
"zs's \n motor";
```

JavaScript 会自动将字符串字面量转换为一个 `String` 对象进行处理，所以可以直接调用 `String.length` 属性：

```js
console.log("zs's motor".length); // 12
```

ECMAScript 6 提供一种**模板字面量**（Template Literals）功能，用于通过一些**语法糖**来构造字符串：

```js
let name = "zs";
const URL = "www.uinio.com";
var greet = `hello
world`; //

console.log(`${name}'s blog is ${URL}`); // zs's blog is www.uinio.com
console.log(greet);
/*
hello
world
*/
```

### 2.4.8、转义字符

下面的表格列举了可以在 JavaScript **字符串**当中使用的特殊**转义字符**。

|  特殊字符   | 功能解释                                                     |
| :---------: | :----------------------------------------------------------- |
|    `\0`     | Null 字节；                                                  |
|    `\b`     | 退格符；                                                     |
|    `\f`     | 换页符；                                                     |
|    `\n`     | 换行符；                                                     |
|    `\r`     | 回车符；                                                     |
|    `\t`     | Tab 制表符；                                                 |
|    `\v`     | 垂直制表符；                                                 |
|    `\'`     | 单引号；                                                     |
|    `\"`     | 双引号；                                                     |
|    `\\`     | 反斜杠字符；                                                 |
|   `\XXX`    | 由从 `0 ~ 377` 三位八进制数 `XXX` 表示的 **Latin-1** 字符，例如：`\251` 是版权符号 © 的八进制表达； |
|   `\xXX`    | 由从 00 和 FF 的两位十六进制数字 XX 表示的 **Latin-1** 字符，例如：`\xA9` 是版权符号 © 的十六进制表达； |
|  `\uXXXX`   | 由 4 位十六进制数字 `XXXX` 表示的 **Unicode** 字符，例如：`\u00A9` 是版权符号 © 的 Unicode 表达; |
| `\u{XXXXX}` | Unicode 代码点（Code Point）转义字符，例如：`\u{2F804}` 相当于 Unicode 转义字符 `\uD87E\uDC04` 的简写形式； |

> **注意**：严格模式下，不能使用八进制转义字符。

通过转义字符，可以在字符串当中方便的插入**引号**与**反斜线**，甚至于进行**字符串换行**处理：

```js
"zs's blog is 'www.uinio.com'"; // "zs's blog is 'www.uinio.com'"

"C:\\Workspace\\blog"; // 'C:\\Workspace\\blog'

"zs's Github is \
https://github.com/uinika"; // "zs's Github is https://github.com/uinika"
```

## 2.5数据类型转换

JavaScript 是一种**动态类型语言**，这意味着在声明变量时无需指定数据类型，变量的数据类型会在代码执行期间，根据需要自动进行转换：

```js
var temporary = 2022;
temporary = "wwww.uinio.com";
```

如果表达式当中同时包含**数字**和**字符串**，通过加法运算符 `+` 可以将数值转换成字符串：

```js
let x = "The Number is " + 2021; // 'The Number is 2021'

let y = 2022 + " is the Number"; // '2022 is the Number'
```

但是 JavaScript 当中并不能使用减法运算符 `-` 完成相同的任务：

```js
"36" - 16; // 20
"19" + 85; // '1985'
```

通过 `parseInt(string, radix)` 函数可以将字符串转换为**整数**（会丢弃小数部分），其中第 2 个参数 `radix` 表示**进制**或者**基数**，其取值范围介于 `2 ~ 36` 之间：

```js
parseInt("32", 16); // 50

parseInt("0x32"); // 50
```

而通过 `parseFloat(string)` 函数则可以将字符串转换为**浮点数**：

```js
parseFloat(3.141592654); // 3.141592654
```

> **注意**：如果第 1 个参数 `string` 并非表达一个有效数值，那么上述函数就会返回一个非数 `NaN` 。

将字符串转换为数字的另外一种方法，就是采用简单粗暴的加法运算符 `+`：

```js
"1.1" + "5.5" = "1.15.5"

(+"1.1") + (+"5.5") = 6.6
```

通过`Number()`把对象的值转换为数字，如果对象的值无法转换为数字，那么 Number() 函数返回 NaN。

```js
Number(true);  //1
Number("999"); //999
Number("999 888");  //NaN
```

通过`toString()`方法，把数字转化为字符串：

```js
var num=15;
num.toString();  //"15"
num.toString(2); //"1111"
```

> toString(radix): 参数radix可选，规定表示数字的基数，是 2 ~ 36 之间的整数。若省略该参数，则使用基数 10。但是要注意，如果该参数是 10 以外的其他值，则 ECMAScript 标准允许实现返回任意值。
>
> - 2 - 数字以二进制值显示
> - 8 - 数字以八进制值显示
> - 16 - 数字以十六进制值显示
>
> 注意：null和undefined这两个值没有toString()方法，如果调用它们的方法，会报错。



## 2.6、运算符

JavaScript 根据**操作数**的不同，可以划分为`一元`、`二元`、`三元`总共 3 类运算符。

### 2.6.1、赋值运算符

|      赋值运算符      |        | 示例       | 描述          |
| :------------------: | :----: | :--------- | :------------ |
|       **赋值**       |  `=`   | `x = y`    | `x = y`       |
|     **加法赋值**     |  `+=`  | `x += y`   | `x = x + y`   |
|     **减法赋值**     |  `-=`  | `x -= y`   | `x = x - y`   |
|     **乘法赋值**     |  `*=`  | `x *= y`   | `x = x * y`   |
|     **除法赋值**     |  `/=`  | `x /= y`   | `x = x / y`   |
|     **求余赋值**     |  `%=`  | `x %= y`   | `x = x % y`   |
|     **求幂赋值**     | `**=`  | `x **= y`  | `x = x ** y`  |
|    **左移位赋值**    | `<<=`  | `x <<= y`  | `x = x << y`  |
|    **右移位赋值**    | `>>=`  | `x >>= y`  | `x = x >> y`  |
| **无符号右移位赋值** | `>>>=` | `x >>>= y` | `x = x >>> y` |
|    **按位与赋值**    |  `&=`  | `x &= y`   | `x = x & y`   |
|   **按位异或赋值**   |  `^=`  | `x ^= y`   | `x = x ^ y`   |
|    **按位或赋值**    |  `│=`  | `x │= y`   | `x = x │ y`   |

### 2.6.2、比较运算符

|   比较运算符   |       | 示例                                                         | 描述                                                  |
| :------------: | :---: | :----------------------------------------------------------- | :---------------------------------------------------- |
|    **等于**    | `==`  | `2006 == 2006` 或者 `2006 == "2006"`，返回 `true`；          | 左右两侧操作数相等时返回 `true`；                     |
|   **不等于**   | `!=`  | `2006 != 2019` 或者 `2006 != "2019"`，返回 `true`；          | 左右两侧操作数不相等时返回 `true`；                   |
|  **严格等于**  | `===` | `2022 === 2022` 返回 `true`；`2022 === "2022"` 返回 `false`； | 左右两侧操作数相等并且**数据类型**相同时返回 `true`； |
| **不严格等于** | `!==` | `2022 !== 2022` 返回 `false`；`2022 !== "2022"` 返回 `true`； | 左右两侧操作数不相等并且数据类型不相同时返回 `true`； |
|    **大于**    |  `>`  | `2021 > 2022` 或者 `2021 > "2022"`，返回 `false`；           | 左侧操作数大于右侧时返回 `true`；                     |
|  **大于等于**  | `>=`  | `2021 >= 2021` 或者 `2021 >= "2021"`，返回 `true`；          | 左侧操作数大于或者等于右侧时返回 `true`；             |
|    **小于**    |  `<`  | `2019 < 2022` 或者 `2019 < "2022"`，返回 `true`；            | 左侧操作数小于右侧时返回 `true`；                     |
|  **小于等于**  | `<=`  | `2019 <= 2019` 或者 `2019 <= "2019"`，返回 `true`；          | 左侧操作数小于或者等于右侧时返回 `true`；             |

> 当涉及到Object时，需要两边都是指向同一地址“===”才会返回true。
>
> 如果是“===”，如果两边不都是Object，则会将Object转为基础数据类型再比较

### 2.6.3、算数运算符

|  算数运算符  |      | 示例                                                         | 描述                                                         |
| :----------: | :--: | :----------------------------------------------------------- | :----------------------------------------------------------- |
|   **求余**   | `%`  | `15 % 6`，返回 `3`；                                         | 返回左右两侧操作数相除之后的**余数**；                       |
|   **自增**   | `++` | 当 `let index = 0` 时，首先执行 `++index` 返回 `1`，然后再执行 `index++` 依然返回 `1`； | 如果放置在操作数**前面**，则返回**加上** `1` 之后的值；如果放置在操作数**后面**，则返回操作数之后再**加上** `1`； |
|   **自减**   | `--` | 当 `let index = 6` 时，首先执行 `--index` 返回 `5`，然后再执行 `index--` 依然返回 `5`； | 如果放置在操作数**前面**，则返回**减去** `1` 之后的值；如果放置在操作数**后面**，则返回操作数之后再**减去** `1`； |
|   **负值**   | `-`  | `console.log(-5)`，返回 `-5`；                               | 返回操作数的负值；                                           |
|   **正值**   | `+`  | `console.log( +"5" )`，返回 `5`；                            | 返回操作数的正值，同时将操作数转换为数值类型；               |
| **指数运算** | `**` | `2 ** 3`，返回 `8`；                                         | 返回指数运算之后的结果，左侧为**底数**部分，右侧为**指数**部分； |

### 2.6.4、位运算符

|    位运算符    |       | 示例      | 描述                                                         |
| :------------: | :---: | :-------- | :----------------------------------------------------------- |
|   **按位与**   |  `&`  | `a & b`   | 左右两侧操作数每一个位都为 `1` 时返回 `1`，否则返回 `0`；    |
|   **按位或**   |  `│`  | `a │ b`   | 左右两侧操作数每一个位只要其中一个为 `1` 则返回 `1`，否则返回 `0`； |
|  **按位异或**  |  `^`  | `a ^ b`   | 左右两侧操作数的每一个对应的位不相同就返回 `1`，否则返回 `0`； |
|   **按位非**   |  `~`  | `~ a`     | 对右侧操作数的二进制形式按位取反；                           |
|    **左移**    | `<<`  | `a << b`  | 将左侧操作数的二进制形式**向左移动**右侧操作数个位，并在**右侧**填充 `0`； |
|    **右移**    | `>>`  | `a >> b`  | 将左侧操作数的二进制形式**向右移动**右侧操作数个位，左侧**填充位**由左侧操作数的最高位是 `0` 还是 `1` 来决定； |
| **无符号右移** | `>>>` | `a >>> b` | 将左侧操作数的二进制形式**向右移动**右侧操作数个位，并将**左侧**全部填充为 `0`； |

### 2.6.5、逻辑运算符

| 逻辑运算符 |      | 示例                                                         | 描述                                                         |
| :--------: | :--: | :----------------------------------------------------------- | :----------------------------------------------------------- |
| **逻辑与** | `&&` | `true && true` 返回 `true`，`false && false` 返回 `false`，`true && false` 返回 `false`; | 当操作数都为 `true` 时返回 `true`，否则返回 `false`；        |
| **逻辑或** | `││` | `true ││ true` 返回 `true`，`false ││ false` 返回 `false`，`true ││ false` 返回 `true`; | 任意一个操作数为 `true` 时返回 `true`，如果操作数都为 `false` 则返回 `false`； |
| **逻辑非** | `!`  | `!true` 返回 `false` ，`!false` 返回 `true`；                | 如果操作数为 `true` 时返回 `false`，反之则会返回 `true`；    |

### 2.6.6、条件运算符

条件运算符是 JavaScript 当中唯一的**三目运算符**（需要 3 个操作数），其返回结果是根据指定条件在两个值当中选取一个。

```js
condition ? value1 : value2;
```

如果条件 `condition` 的判断结果为 `true`，则返回 `value1`，否则返回 `value2`。

```js
const getStage = (age) => {
  return age >= 18 ? "成年人" : "小孩";
};

console.log(getStage(36)); // 成年人
```

### 2.6.7、分组操作符

分组操作符 `()` 可以用于控制了表达式当中计算的优先级。

```js
let x = 1;
let y = 2;
let z = 3;

console.log(x + y * z); // 7
console.log((x + y) * z); // 9
```

### 2.6.8、typeof 操作符

`typeof` 操作符用于返回当前**操作数**的数据类型，可以通过如下方式进行调用：

```js
typeof operand;
```

上面的 `typeof` 操作符将会返回一个表示操作数 `operand` 数据类型的字符串。

```js
var year = new Function("2022 - 2010");
var name = "zs";
var age = 36;
var today = new Date();

/* 判断已定义变量的数据类型 */
console.log(typeof year); // function
console.log(typeof name); // string
console.log(typeof age); // number
console.log(typeof today); // object

/* 判断未定义变量的数据类型 */
console.log(typeof nothing); // undefined

/* JavaScript 预定义关键字的数据类型 */
console.log(typeof true); // boolean
console.log(typeof NaN); // number
console.log(typeof null); // object
console.log(typeof Infinity); // number
```

### 2.6.9、void 操作符

`void` 操作符用于表示右侧表达式**没有返回值**，通常用于标识 HTML 页面当中不需要操作返回值的 JavaScript 表达式。

```
void expression;
```

下面的代码创建了一个超文本链接，当用户使用鼠标点击之后，不会产生任何效果。

```
<a href="javascript:void(0)">无效果点击</a>
```

下面的超文本链接会在用户鼠标点击之后，提交一个 HTML 表单。

```
<a href="javascript:void(document.form.submit())">点击提交</a>
```

### 2.6.10、字符串连接符

**字符串连接符** `+` 用于连接两个字符串，也允许通过 `+=` 完成字符串拼接。

```js
/* 使用 + 拼接字符串 */
let string1 = "Hello";
let string2 = " zs";
console.log(string1 + string2); // Hello zs

/* 使用 += 拼接字符串 */
let string3 = "Hello";
string3 += " PCB";
console.log(string3); // Hello PCB
```

### 2.6.11、剩余参数运算符

ES6 提供的**剩余参数**运算符 `...` 可以用于快速原地展开一个**数组**或者一组**函数参数**。

```js
/* 展开函数参数 */
function total(x, y, z) {
  return x + y + z;
}
let arguments = [1, 2, 3];
total(...arguments); // 6

/* 展开数组 */
const color = ["B", "l", "u", "e"];
const pcb = [...color, "P", "C", "B"];
console.log(pcb); // ['B', 'l', 'u', 'e', 'P', 'C', 'B']
```

### 2.6.12、运算符优先级

![img](https://img-blog.csdnimg.cn/b39bf08dec044565ad36064eb4357269.png)

## 2.7、解构赋值

ES6 提供的**解构赋值语法**可以用于从**数组**当中提取元素，或者从**对象**当中提取属性。

```js
/* 提取数组当中的元素 */
const militaryArray = ["陆军", "海军", "空军"];
let [army, navy, airForce] = militaryArray;
console.log(army + "➙" + navy + "➙" + airForce); // 陆军➙海军➙空军

/* 提取对象上的属性 */
const up = {
  army: "陆军",
  navy: "海军",
};
const down = {
  airForce: "空军",
  missileForce: "火箭军",
};
const militaryObject = { ...up, ...down };
console.log(militaryObject); // {army: '陆军', navy: '海军', airForce: '空军', missileForce: '火箭军'}
```

# 三、流程控制

JavaScript 提供了一套灵活的流程控制语句，可以在应用程序当中实现大量的交互性功能。

## 3.1、语句块

**语句块**用于组合多条 JavaScript 语句，由一对大括号 `{}` 进行界定：

```js
{
  statement_1;
  statement_2;
  statement_3;
  .
  .
  .
  statement_n;
}
```

语句块通常与 `if`、`for`、`while` 等流程控制语句结合起来使用：

```js
let week = 1;

while (week <= 7) {
  console.log(week++); // 1 2 3 4 5 6 7
}
```

ECMAScript 6 标准之前，Javascript 并不存在**块作用域**的概念，变量的作用域从声明位置开始，一直会覆盖到源文件的末尾：

```js
var day = 27;

/* 块作用域 */
{
  var day = 1;
}

console.log(day); // 1
```

而使用 ECMAScript 6 的 `let` 和 `const` 关键字声明的变量，其作用域仅限于该声明所在的**语句块**：

```js
let year = 2022;

/* 块作用域 */
{
  let year = 2016;
  const month = 12;
}

console.log(year); // 2022
console.log(month); // Uncaught ReferenceError: month is not defined
```

## 3.2、条件判断

JavaScript 支持 `if...else` 和 `switch` 两种条件判断语句。

### 3.2.1、if...else 语句

条件表达式 `condition` 返回 `true` 或者 `false`，如果返回的是 `true`，就会执行 `statement_1` 语句；如果返回的是 `false`，则会执行 `statement_2` 语句：

```js
if (condition) {
  statement_1;
} else {
  statement_2;
}
```

通过组合使用 `else if` 语句，可以连续测试多种 `condition_x` 判断条件：

```js
if (condition_1) {
  statement_1;
} else if (condition_2) {
  statement_2;
} else if (condition_n) {
  statement_n;
} else {
  statement_last;
}
```

通常不建议在条件表达式 `condition` 当中使用赋值语句，因为阅读代码时容易将其视为等值比较运算符 `==`。如果一定要在条件表达式当中使用赋值语句，通常需要在赋值语句前后额外添加一对括号 `(condition)`：

```js
let x;
let y = 2022;

if ((x = y)) {
  console.log(x); // 2022
}
```

空字符串 `""`、`undefined`、`null`、`0`、`NaN` 在条件表达式 `condition` 当中，都将会被视为 `false` 条件：

```js
if ("" && undefined && null && 0 && NaN) {
  console.log("全部条件为 true");
} else {
  console.log("全部条件为 false"); // 全部条件为 false
}
```

切记不要混淆原始布尔值 `true` 和 `false` 与 `Boolean` 对象的比较关系：

```js
const test = new Boolean(false);

if (test) {
  console.log("Boolean 对象被视为 true"); // Boolean 对象被视为 true
}

if (test == true) {
  console.log("Boolean 对象被视为 false");
}
```

### 3.2.2、switch 语句

`switch` 语句首先会查找与 `expression` 匹配的 `case` 子句，然后执行该子句当中对应的代码；如果没有匹配值，则会执行 `default` 子句里的代码，通常会将 `default` 子句放置在 `switch` 语句的最后。

```js
switch (expression) {
  case label_1:
    statements_1
    [break;]
  case label_2:
    statements_2
    [break;]
  ...
  default:
    statements_def
    [break;]
}
```

可选的 `break` 语句放置在 `case` 子句当中，以确保匹配语句执行之后，执行流程可以跳出 `switch` 语句执行后续内容。如果忽略掉 `break` 语句，那么就会继续执行下一条 `case` 子句当中的内容：

```js
const day = new Date().getDay();

/* 使用 break 语句 */
switch (day) {
  case 0:
    console.log("今天是星期天");
    break;
  case 1:
    console.log("今天是星期一");
    break;
  case 2:
    console.log("今天是星期二");
    break;
  case 3:
    console.log("今天是星期三");
    break;
  case 4:
    console.log("今天是星期四");
    break;
  case 5:
    console.log("今天是星期五");
    break;
  case 6:
    console.log("今天是星期六");
    break;
}
/*
今天是星期一
*/

/* 不使用 break 语句 */
switch (day) {
  case 0:
    console.log("今天是星期天");
  case 1:
    console.log("今天是星期一");
  case 2:
    console.log("今天是星期二");
  case 3:
    console.log("今天是星期三");
  case 4:
    console.log("今天是星期四");
  case 5:
    console.log("今天是星期五");
  case 6:
    console.log("今天是星期六");
}
/* 
今天是星期一
今天是星期二
今天是星期三
今天是星期四
今天是星期五
今天是星期六
*/
```

## 3.3、循环

JavaScript 提供了 `for`、`do...while`、`while`、`label`、`break`、`continue`、`for...in`、`for...of` 一共 8 种循环相关的语法。

### 3.3.1、for 循环

`for` 循环会一直重复执行，直至循环条件变为 `false`。

```js
for ([initialExpression]; [condition]; [incrementExpression]) {
  statement;
}
```

1. 首先，执行初始化表达式 `initialExpression`，通常该表达式会初始化一个或多个循环计数器；
2. 然后，计算 `condition` 表达式的值，如果 `condition` 为 `true`，那么执行循环当中的语句；如果 `condition` 为 `false`，那么循环将会终止；如果省略 `condition` 表达式，则 `condition` 的值默认为 `true`；
3. 接着，执行循环里的 `statement` 语句，多条语句可以使用代码块 `{}` 进行包裹；
4. 如果 `incrementExpression` 表达式存在更新，则会执行更新表达式，并且重新执行第 2 个步骤；

```js
for (var index = 0; index < 6; index++) {
  console.log("当前索引为", index);
}

/*
当前索引为 0
当前索引为 1
当前索引为 2
当前索引为 3
当前索引为 4
当前索引为 5
*/
```

### 3.3.2、do...while 循环

`do...while` 循环同样会一直重复直执行，直至指定的条件为 `false`。

```
do {
  statement;
} while (condition);
```

`statement` 语句会在检查 `condition` 条件之前会执行一次，多条 `statement` 语句需要放置到花括号 `{}` 当中。如果 `condition` 为 `true`，那么 `statement` 语句将会再一次执行；而如果 `condition` 为 `false`，则循环终止运行。

```js
let index = 0;

do {
  index++;
  console.log("当前索引为", index);
} while (index < 5);

/*
当前索引为 0
当前索引为 1
当前索引为 2
当前索引为 3
当前索引为 4
当前索引为 5
*/
```

### 3.3.3、while 循环

`while` 循环只要指定的条件 `condition` 为 `true`，就会一直执行 `statement` 语句块。如果条件 `condition` 为 `false`，则会终止循环。

```js
while (condition) {
  statement;
}
```

与 `do...while` 循环不同的是，`while` 循环的 `condition` 条件检测会在每次 `statement` 执行之前发生。

```js
let index = 0;

while (index < 5) {
  index++;
  console.log("当前索引为", index);
}

/*
当前索引为 0
当前索引为 1
当前索引为 2
当前索引为 3
当前索引为 4
当前索引为 5
*/
```

### 3.3.4、label 语句

`label` 用于在程序当中提供一个**代码标识符**，然后结合 `break` 或 `continue` 语句精确的返回到代码指定的位置。

```js
label:
  statement;
```

这里的 `label` 可以是任意合法的 JavaScript 标识符，而 `statement` 则可以是任意需要标识的 JavaScript 语句。

```js
/* label 与 break 结合使用 */
let result1 = 0;
myLabel: for (var index1 = 0; index1 < 10; index1++) {
  for (var index2 = 0; index2 < 10; index2++) {
    if (index1 == 5 && index2 == 5) {
      break myLabel; // 当 i = 5 且 j = 5 时跳出全部循环，继续执行 myLabel 下方语句
    }
    result1++;
  }
}
console.log(result1); // 55

/* label 与 continue 结合使用 */
let result2 = 0;
myLabel: for (var index1 = 0; index1 < 10; index1++) {
  for (var index2 = 0; index2 < 10; index2++) {
    if (index1 == 5 && index2 == 5) {
      continue myLabel; // 当 i = 5 且 j = 5 时跳过本次循环，继续执行 myLabel 下方语句
    }
    result2++;
  }
}
console.log(result2); // 95
```

#### 3.3.4.1、break 语句

`break` 语句用于终止**全部循环**，当 `break` 没有指定 `label` 时，就会立刻终止当前所在的 `while`，`do...while`，`for` 循环语句，以及 `switch` 流程控制语句，并且执行这些语句之后的内容；而当使用带有 `label` 的 `break` 时，则会在终止全部循环之后，跳转至 `label` 所在的位置继续执行。

```js
break [label];
for (let index = 0; index < 5; index++) {
  console.log("当前索引为", index);
  if (index === 2) {
    console.log("当索引等于 2 时结束全部循环");
    break;
  }
}

/*
当前索引为 0
当前索引为 1
当前索引为 2
当索引等于 2 时结束全部循环
*/
```

#### 3.3.4.2、continue 语句

`continue` 语句用于终止**单次循环**，当 `continue` 没有指定 `label` 时，就会立刻终止本次的 `while`，`do...while`，`for` 循环，以及 `switch` 流程控制语句，并且继续执行下一次循环；而当使用带有 `label` 的 `continue` 时，则只会在中断本次循环之后，跳转至 `label` 所处位置继续执行。

```js
continue [label];
for (let index = 0; index < 5; index++) {
  console.log("当前索引为", index);
  if (index === 2) {
    console.log("当索引等于 2 时跳过该次循环");
    continue;
  }
}

/*
当前索引为 0
当前索引为 1
当前索引为 2
当索引等于 2 时跳过该次循环
当前索引为 3
当前索引为 4
*/
```

### 3.3.5、for...in 循环

`for...in` 循环通常用于遍历某个对象的**可枚举属性**：

```js
for (property in object) {
  statements;
}
```

当在 `for...in` 循环当中访问对象属性时，可以采用 `object[property]` 的语法形式：

```js
const URL = { blog: "www.uinika.com", github: "uinika.github.io", gitee: "uinika.gitee.io" };

for (url in URL) {
  console.log(url + " ➡ " + URL[url]);
}

/*
blog ➡ www.uinika.com
github ➡ uinika.github.io
gitee ➡ uinika.gitee.io
*/
```

除此之外，`for...in` 还可以用于遍历数组元素，但是此时返回的并非**对象名称**，而是**数组索引**：

```js
const URLs = ["www.uinika.com", "uinika.github.io", "uinika.gitee.io"];

for (index in URLs) {
  console.log(index + " ➡ " + URLs[index]);
}

/*
0 ➡ www.uinika.com
1 ➡ uinika.github.io
2 ➡ uinika.gitee.io
*/
```

> **注意**：`for...in` 是为了遍历对象属性而设计，由于会遍历出所有可枚举的属性，所以不建议使用它来遍历数组。

### 3.3.6、for...of 循环

`for...of` 用于遍历数组时，返回的结果是每一个数组元素。

```js
const URLs = ["www.uinika.com", "uinika.github.io", "uinika.gitee.io"];

for (url of URLs) {
  console.log(url);
}

/*
www.uinika.com
uinika.github.io
uinika.gitee.io
*/
```

### 3.3.7、Array.forEach() 方法

`Array.prototype.forEach()` 方法同样也可以用于迭代指定数组的每一个元素，并且执行一次给定的函数。

```js
array.forEach(callback(currentValue, index, array), thisArg);
```

`forEach` 的参数 `callback` 是迭代数组当中的每个元素时，所要执行的回调函数，该函数的 `currentValue` 参数表示当前正在迭代的元素，可选的 `index` 参数表示当前元素的索引，可选的 `array` 指代当前正在操作的数组；而另一个参数 `thisArg` 可选，表示执行 `callback` 回调函数时的 `this` 指针。

```js
const URLs = ["www.uinika.com", "uinika.github.io", "uinika.gitee.io"];

URLs.forEach((currentValue, index, array) => {
  console.log(index);
  console.log(array);
  console.log(currentValue + "\n");
});

/*
0
['www.uinika.com', 'uinika.github.io', 'uinika.gitee.io']
www.uinika.com

1
['www.uinika.com', 'uinika.github.io', 'uinika.gitee.io']
uinika.github.io

2
['www.uinika.com', 'uinika.github.io', 'uinika.gitee.io']
uinika.gitee.io
*/
```

# 四、数组

**数组**用于表示一个有序的数据集合，可以通过数组的名称和索引访问其中的元素。

## 4.1、创建数组

JavaScript 没有内置明确的**数组数据类型**，但是可以通过数组字面量语法，以及内置的 `Array` 对象，显式的创建拥有指定元素的数组：

```js
const array = [element0, element1, ..., elementN]; // 数组字面量方式
const array = Array(element0, element1, ..., elemntN);
const array = new Array(element0, element1, ..., elementN);
```

除此之外，还可以通过如下方式创建一个指定长度的**空数组**：

```js
const array = [];
const array = Array(arrayLength);
const array = new Array(arrayLength);
```

## 4.2、初始化数组

JavaScript 支持通过**直接为元素赋值**的方式来初始化数组：

```js
const URLs = [];
URLs[0] = "www.uinio.com";
URLs[1] = "www.uinimi.com";
URLs[2] = "www.uinika.com";

console.log(URLs); // ['www.uinio.com', 'www.uinimi.com', 'www.uinika.com']
```

也可以像本节内容开头所描述的那样，在**创建数组的时候**直接进行初始化：

```js
const fruits = ["苹果", "西柚", "橙子"];

const trees = new Array("松树", "柳树", "樟树");
console.log(trees); // ['松树', '柳树', '樟树']
```

## 4.3、引用数组元素

通过数组元素的**索引**，可以从 `0` 开始引用数组的元素：

```js
const trees = new Array("松树", "柳树", "樟树");

console.log(trees[0]); // 松树
console.log(trees[1]); // 柳树
console.log(trees[2]); // 樟树
```

## 4.4、数组长度

通过数组对象上提供的 `length` 属性，可以获取当前数组的实际长度信息，也就是数组元素的实际个数：

```js
const fruits = ["苹果", "西柚", "橙子"];
console.log(fruits.length); // 3
```

通过手动设置 `length` 属性，还可以对数组的长度进行调整：

```js
/* 当 length 属性大于实际数组长度时，采用 undefined 填充多余元素 */
const fruits = ["苹果", "西柚", "橙子"];
fruits.length = 4;
console.log(fruits); // ['苹果', '西柚', '橙子', empty]
console.log(fruits[3]); // undefined

/* 当 length 属性小于实际数组长度时，就会截取尾部多余的元素 */
fruits.length = 2;
console.log(fruits); // ['苹果', '西柚']

/* 将 length 属性设置为 0 可以直接清空数组 */
fruits.length = 0;
console.log(fruits); // []
```

## 4.5、遍历数组

### 4.5.1、`for`循环遍历

使用 `for` 循环遍历数组元素是一种比较常规的操作：

```js
const arr = [0, 1, 2, 3, 4, 5, 6, 7];

for (let index = 0; index < arr.length; index++) {
  console.log(arr[index]);
}
/*
0,1,2,3,4,5,6,7
*/
```

### 4.5.2、`while`循环遍历

功能与`for`循环一致

```js
const arr = [0, 1, 2, 3, 4, 5, 6, 7];
let index = -1;
while(index < arr.length){
	console.log(arr[index]);
	index++;
}
/*
0,1,2,3,4,5,6,7
*/
```

### 4.5.3、`foreach`方法

使用 `forEach()` 则是另外一种遍历数组元素的方法，传递给 `forEach()` 的函数会在遍历数组的每个元素时执行一次，数组元素将会作为**参数**传递给该函数。

此方法比较简洁，不过缺点比较明显，只能将数组的元素全部遍历，不支持`break`和`continue`，该函数返回值为`undefined`

```js
const arrs = [0, 1, 2, 3, 4, 5, 6, 7];

arrs.forEach(function (arr) {
  console.log(arr);
});
/*
0,1,2,3,4,5,6,7
*/
```

> **注意**：`forEach()` 不会遍历出定义数组时未经初始化的元素，但是会遍历出被手动赋值为 `undefined` 的元素：

### 4.5.4、`for...in`方法

原则上 `for...in` 语句是为遍历对象设计的，使用其迭代数组时，会枚举出所有的可枚举属性，生产环境下**不建议使用**。例如下面示例代码，就将定义在 `Array` 对象原型上的 `blog` 遍历打印了出来：

```js
Array.prototype.blog = function () {
  console.log("www.uinio.com");
};

const arrs = [0, 1, 2, 3, 4, 5, 6, 7];

for (index in arrs) {
  console.log(index + arrrs[index]);
}
/*
00
11
22
33
44
55
66
77
blogfunction () {
  console.log("www.uinio.com");
}
*/
```

### 4.5.5、`for...of`方法（ES6）

```js
const arrs = [0, 1, 2, 3, 4, 5, 6, 7];

for (let item of arrs) {
  console.log(item);  //[0, 1, 2, 3, 4, 5, 6, 7]
```



### 4.5.6、`every()`方法

该方法测试一个数组内的所有元素是否都能通过某个指定函数的测试。它返回一个布尔值。如果所有元素都通过检测返回 `true`，否则返回 `false`。

```js
const arr = [0, 1, 2, 3, 4, 5, 6, 7]
let a = arr.every((value) => value > -1)//判断数组元素是否都大于-1
console.log(a);//true
```

> 在方法体内`return false` 等同于`break`， `return true` 等同于 `continue`， 如果不写`return`语句， 默认是 `return false`

### 4.5.7、`some()`方法

该方法只要数组中存在某一个符合条件的就返回`true`，全部不符合条件则返回`false`；与`every()`不同，`every()`遇到不符合的元素就直接停止了，`some()`遇到符合的元素直接停止。

```js
const arr = [0, 1, 2, 3, 4, 5, 6, 7]
let a = arr.some((value) => value > 6)//判断数组是否存在一个元素大于6
console.log(a);//true
```

> 在方法体内`return false` 等同于`continue`， `return true` 等同于 `break`， 如果不写`return`语句， 默认是 `return true`

### 4.5.8、`filter()`方法

过滤数组，返回值为一个新数组，由原数组中符合条件的元素组成，若无符合条件的数组则返回空数组

```js
const arr = [0, 1, 2, 3, 4, 5, 6, 7]
let newArr = arr.filter((value) => value > 3) //判断数组元素是否大于3
console.log(newArr); //[ 4, 5, 6, 7 ]
```

### 4.5.9、`map()`方法

对每一个数组元素应用函数，并返回一个新的数组

```js
const arr = [0, 1, 2, 3, 4, 5, 6, 7]
let newArr = arr.map((value) => value * 2) //将数组中每一个元素都乘以2
console.log(newArr); //[0,  2,  4,  6, 8, 10, 12, 14]
```

### 4.5.10、`reduce()`方法

遍历数组全部元素，将函数处返回的数字累加到一起，并返回这个累加结果，可初始化一个值

```js
const arr = [0, 1, 2, 3, 4, 5, 6, 7]
let sum = arr.reduce((accumulator,currentValue) => { //accumulator为每次迭代后的累计值，currentValue为每次迭代时从arr传来的元素值
    return currentValue * 2 + accumulator
},100) //将数组中每一个元素都乘以2累加并加上初始值100
console.log(sum); //156
```

### 4.5.11、`find()`方法

遍历数组，找到第一个符合条件的项，并返回该项；不会继续遍历数组；否则返回undefined，不会改变数组

```js
const arr = [0, 1, 2, 3, 4, 5, 6, 7]
let newArr = arr.find((value) => value > 5)
console.log(newArr);   //6
```

## 4.6、数组常用方法

### 4.6.1、`push`、`pop`

在数组末尾操作

| 方法   | 描述                                                       |
| ------ | ---------------------------------------------------------- |
| push() | 向**数组的末尾**添加一个或多个元素，并返回数组的新的长度   |
| pop()  | 删除数组的**最后一个**元素，并将被删除的元素作为返回值返回 |

> **注意：**此方法改变数组的长度！

```js
const arr = [0, 1, 2, 3, 4, 5, 6, 7];
arr.push(8); //[0, 1, 2, 3, 4, 5, 6, 7, 8]
```

```js
const arr = [0, 1, 2, 3, 4, 5, 6, 7];
arr.pop(); //[0, 1, 2, 3, 4, 5, 6]
```

### 4.6.2、`unshift`,`shift`

在数组开头操作

| 方法      | 描述                                                     |
| --------- | -------------------------------------------------------- |
| unshift() | 向**数组开头**添加一个或多个元素，并返回新的数组长度     |
| shift()   | 删除数组的**第一个**元素，并将被删除的元素作为返回值返回 |

> **注意：**此方法改变数组的长度！

```js
const arr = [0, 1, 2, 3, 4, 5, 6, 7];
arr.unshift(-1); //[-1, 0, 1, 2, 3, 4, 5, 6, 7]
```

```js
const arr = [0, 1, 2, 3, 4, 5, 6, 7];
arr.shift(); //[1, 2, 3, 4, 5, 6, 7]
```

### 4.6.3、`slice`

该方法可以用来从数组中提取指定元素，**不会改变元素数组**，而是将截取到的元素封装到一个新数组中返回

参数：

- 第一个参数：截取**开始的位置**的索引，**包含**开始索引
- 第二个参数：截取**结束的位置**的索引，**不包含**结束索引，第二个参数可以省略不写，此时会截取从开始索引往后的所有元素

```js
const arr = [0, 1, 2, 3, 4, 5, 6, 7];
let result = arr.slice(1,4);  //[1,2,3]
```

### 4.6.4、`splice`

该方法可以用于删除数组中的指定元素，**会影响到原数组**，会将指定元素从原数组中删除，并将被删除的元素作为返回值返回

参数：

- 第一个参数：表示**开始位置**的索引
- 第二个参数：表示**要删除的元素数量**
- 第三个参数及以后参数：可以**传递一些新的元素**，这些元素将会自动插入到**开始位置索引前边**

```js
const arr = [0, 1, 2, 3, 4, 5, 6, 7];
let result = arr.splice(1, 1, 1.5, 1.6);  //[0, 1.5, 1.6, 2, 3, 4, 5, 6, 7]
```

### 4.6.5、`concat`

该方法可以连接两个或多个数组，并将新的数组返回，**不会对原数组产生影响**

```js
var arr1 = [0,1];
var arr2 = [3,4,5];
var arr3 = [6,7];
var result = arr1.concat(arr2,arr3,8,9); //[0,1,2,3,4,5,6,7,8,9]
```

### 4.6.6、`join`

该方法可以将数组转换为一个字符串，**不会对原数组产生影响**，而是将转换后的字符串作为结果返回。

在join()中可以指定一个字符串作为参数，这个字符串将会成为数组中元素的连接符，如果不指定连接符，则默认使用**","**作为连接符

```js
var arr = ["孙悟空", "猪八戒", "沙和尚"];
var result = arr.join("@-@");//孙悟空@-@猪八戒@-@沙和尚
```

### 4.6.7、`reverse`

该方法用来反转数组（前边的去后边，后边的去前边），该方法会**直接修改原数组**

```js
var arr = ["孙悟空", "猪八戒", "沙和尚"];
arr.reverse();//[ "沙和尚","猪八戒", "孙悟空"];
```

### 4.6.8、`sort`

该方法可以用来对数组中的元素进行排序，也**会影响原数组**，默认会按照Unicode编码进行排序

我们可以自己来指定排序的规则，我们可以在sort()添加一个回调函数，来指定排序规则，回调函数中需要定义两个形参，浏览器将会分别使用数组中的元素作为实参去调用回调函数，使用哪个元素调用不确定，但是肯定的是在数组中a一定在b前边，浏览器会根据回调函数的返回值来决定元素的顺序，如下：

* 如果返回一个大于0的值，则元素会交换位置
* 如果返回一个小于0的值，则元素位置不变
* 如果返回一个等于0的值，则认为两个元素相等，也不交换位置

经过上边的规则，我们可以总结下：

* 如果需要升序排列，则返回 a-b
* 如果需要降序排列，则返回 b-a

```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.sort();  //Apple,Banana,Mango,Orange
```

## 4.7、深拷贝和浅拷贝

### 4.7.1、数组深拷贝

![image-20210809222117471](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/55eecb22956f4bd691cbea51447fc19e~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

深拷贝复制所有字段，并复制字段所指向的动态分配内存。深拷贝发生在对象及其引用的对象被复制时。

默认情况下基本数据类型（number，string，null，undefined，boolean）都是深拷贝。

简单的理解就是：**深拷贝会开辟新的栈，两个对象对应两个不同的地址，修改对象A的属性，并不会影响到对象B**

#### 4.7.1.1、数组深拷贝方案

方案一：`slice()`

```js
let list = [1,2,3,4];
let box = list.clice();
console.log("list->",list);  //list->[1,2,3,4]
console.log("box->",box);	 //box->[1,2,3,4]

list[3] = 'a'
console.log("list->",list);  //list->[1,2,3,'a']
console.log("box->",box);	 //box->[1,2,3,4]

box[4] = 'b'
console.log("list->",list);  //list->[1,2,3,'a']
console.log("box->",box);	 //box->[1,2,3,4,'b']
```

方案二：`concat()`

```js
let list = [1,2,3,4];
let box = [].concat(list);
console.log("list->",list);  //list->[1,2,3,4]
console.log("box->",box);	 //box->[1,2,3,4]

list[3] = 'a'
console.log("list->",list);  //list->[1,2,3,'a']
console.log("box->",box);	 //box->[1,2,3,4]

box[4] = 'b'
console.log("list->",list);  //list->[1,2,3,'a']
console.log("box->",box);	 //box->[1,2,3,4,'b']
```

方案三：ES6扩展运算符

```js
let list = [1,2,3,4];
let box = [...list];
console.log("list->",list);  //list->[1,2,3,4]
console.log("box->",box);	 //box->[1,2,3,4]

list[3] = 'a'
console.log("list->",list);  //list->[1,2,3,'a']
console.log("box->",box);	 //box->[1,2,3,4]

box[4] = 'b'
console.log("list->",list);  //list->[1,2,3,'a']
console.log("box->",box);	 //box->[1,2,3,4,'b']
```

方案四：Array.from()

```js
let list = [1,2,3,4];
let box = Array.from(list);
console.log("list->",list);  //list->[1,2,3,4]
console.log("box->",box);	 //box->[1,2,3,4]

list[3] = 'a'
console.log("list->",list);  //list->[1,2,3,'a']
console.log("box->",box);	 //box->[1,2,3,4]

box[4] = 'b'
console.log("list->",list);  //list->[1,2,3,'a']
console.log("box->",box);	 //box->[1,2,3,4,'b']
```

方案五：JSON.stringify和JSON.parse方法

```js
let list = [1,2,3,4];
let box = JSON.parse(JSON.stringify(list));  //先将数组转为字符串，然后转成js对象
console.log("list->",list);  //list->[1,2,3,4]
console.log("box->",box);	 //box->[1,2,3,4]

list[3] = 'a'
console.log("list->",list);  //list->[1,2,3,'a']
console.log("box->",box);	 //box->[1,2,3,4]

box[4] = 'b'
console.log("list->",list);  //list->[1,2,3,'a']
console.log("box->",box);	 //box->[1,2,3,4,'b']
```



### 4.7.2、数组浅拷贝

![image-20210809221226279](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f0d87c6eb2bd4952b988bc8f855e129f~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

浅拷贝是对象的逐位复制。**创建一个新对象**，该对象具有原始对象中值的精确副本。如果对象的任何字段是对其他对象的引用，则只复制引用地址，即，复制内存地址。

默认情况下引用类型（object）都是浅拷贝

简单理解就是：**浅拷贝复制的是对象的引用地址，没有开辟新的栈，复制的结果是两个对象指向同一个地址，所以修改其中一个对象的属性，另一个对象的属性也跟着改变了。**

```js
var arr1 = [1, 2, 3, 4];
var arr2 = arr1; 
arr1[0] = 6;                //数组是用堆去保存的，相等的时候只是把存放的地址拷贝过去了，两个指向了同一个地址，所以在改变其中一个的值，其他的也跟着改变了
console.log(arr2[0]);       //输出结果为6
console.log(arr1);        //[6, 2, 3, 4]
console.log(arr2);        //[6, 2, 3, 4]
```



# 五、函数

函数是 JavaScript 的基本语法组件，由一系列用于执行计算任务的语句构成，而且与变量一样，只能在其有效的作用域当中进行调用。

## 5.1、函数定义

JavaScript 函数采用 `function` 关键字进行定义，主要由**函数名称**、**参数列表**（包围在圆括号 `()` 当中并且由逗号 `,` 进行分隔）、**函数体**（采用大括号 `{}` 包围，并且使用 `return` 关键字返回结果）三个部分组成。

```js
function square(size) {
  return size * size;
}
```

- **值传递**：**基本数据类型**的参数值会直接传递给函数，如果在函数当中修改了该参数的值，这种影响并不会传递到函数外部的作用域；
- **引用传递**：**对象类型**的参数值会将**引用**传递给函数，如果在函数当中修改了对象的属性，这种影响就会传递到函数外部的作用域；

```js
let number = 2022;
const object = { name: "zs" };

function update(number, object) {
  number = 1985; // 修改基本数据类型
  object.name = "uinika"; // 修改对象类型
}

update(number, object);

console.log(number); // 2022
console.log(object); // {name: 'uinika'}
```

### 5.1.1、函数表达式

通过**函数表达式**方式创建的函数不需要直接指定函数名称，例如前面的 `square()` 函数也可以采用如下方式进行声明：

```js
const square = function (size) {
  return size * size;
};
```

采用函数表达式，可以非常方便的将函数作为**参数**传递给另外一个函数：

```js
function battleax() {
  console.log("这是一枚战斧导弹!");
}

function destroyer(status, missile) {
  missile();
  if (status === "击中") {
    console.log("驱逐舰已经被击中!");
  }
}

destroyer("击中", battleax);

/*
这是一枚战斧导弹!
驱逐舰已经被击中!
*/
```

函数表达式的另外一个用途，则是可以根据判断条件来声明定义一个函数：

```js
let happy, depression;
let weather = "SUNNY";

if (weather === "SUNNY") {
  happy = function () {
    console.log("我的心情很开心!");
  };
} else {
  depression = function () {
    console.log("我的心情很沮丧!");
  };
}

happy(); // 我的心情很开心!
depression(); // Uncaught ReferenceError: depression is not defined
```

> **注意**：如果调用不符合判断条件的函数，JavaScript 解析引擎将会提示 `ReferenceError` 错误。

### 5.1.2、Function 对象

每一个 JavaScript 函数本质上都是一个 `Function` 对象，通过 `Function()` 构造函数就可以动态创建一个函数对象：

```js
new Function (参数1, 参数2, ..., 函数体)
```

**参数**是由 JavaScript 有效标识符组成的字符串，当具有多个参数时可以使用逗号 `,` 分隔。而**函数体**则是一个包含有函数定义语句的 JavaScript 字符串。

```js
const sum = new Function("a", "b", "return a + b");

console.log(sum(1985, 2022)); // 4007
```

通过 `Function()` 创建函数会存在与 `eval()` 类似的安全问题和相对较小的性能问题，并且 `Function` 创建的函数只能在全局作用域当中运行，只能访问到**全局变量**和自身的**局部变量**，并不能访问 `Function()` 构造函数所在作用域当中的变量。

```js
let local = 1985;

const year1 = function () {
  let local = 2022;
  return new Function("return local;"); // 此处的变量 local 指向全局作用域的 1985
};

const year2 = function () {
  let local = 2022;
  return function () {
    return local; // 此处的变量 local 指向函数 year2 作用域的 2022
  };
};

let resut1 = year1();
console.log(resut1()); // 1985

let resut2 = year2();
console.log(resut2()); // 2022
```

虽然上述代码可以在 Web 浏览器当中正常执行，但是在 NodeJS 当中函数 `year1()` 将会产生 `ReferenceError: local is not defined` 错误，这是由于 NodeJS 里 `.js` 源文件的顶级作用域并非全局作用域，函数 `year1()` 当中的变量 `local` 实质位于当前模块的作用域之中。

> **注意**：如果当前 JavaScript 运行环境是 Web 浏览器，执行以 `Function()` 方式构造的函数，需要修改 Web 浏览器默认的 **HTTP 内容安全策略** `"content_security_policy"` 为 `"unsafe-eval"`。

### 5.1.3、函数声明

方法一：

```js
var 函数名 = new Function("执行语句");
```

方法二：

```js
function 函数名([形参1,形参2,...,形参N]) {
    语句...
}
```

方法三：

```js
var 函数名  = function([形参1,形参2,...,形参N]) {
    语句....
}
```



## 5.2、调用函数

声明并且定义函数之后，就可以通过 `函数名称()` 的方式调用函数。这里要特别注意**函数定义**一定要位于调用语句所处的作用域，而**函数声明**则可以被提升，因而可以出现在调用语句之后。

```js
console.log(square(50)); // 2500

function square(size) {
  return size * size;
}
```

函数表达式无法进行提升，所以将上面代码修改为如下格式是错误的：

```js
console.log(square(50)); // Uncaught SyntaxError: Identifier 'square' has already been declared

const square = function (size) {
  return size * size;
};
```

**函数**可以在自身的**函数体**当中进行**递归调用**，下面的示例当中通过函数的递归调用来计算阶乘：

```js
function factorial(number) {
  if (number == 0 || number == 1) {
    return 1;
  } else {
    /* 递归调用函数本身 */
    return number * factorial(number - 1);
  }
}

factorial(3); // 6
```

## 5.3、函数的作用域

函数当中定义的**局部变量**只能在该函数体内部进行访问，除此之外，还可以访问到**全局变量**或者定义在父函数当中的**局部变量**。

```js
/* 全局变量 */
let name = "zs";
const URL = "www.uinio.com";

function printName1() {
  return name;
}

function printName2() {
  let name = "uinika"; // 局部变量

  function getName() {
    return name + "'s Blog " + URL; // 访问函数外层的局部变量以及全局变量
  }

  return getName();
}

console.log(printName1()); // zs
console.log(printName2()); // uinika's Blog www.uinio.com
```

## 5.4、递归函数调用

通过**函数名称**、`arguments.callee`、**指向该函数的变量名称**，就可以在一个函数的内部调用自身，也就是所谓的**递归**。例如下面函数里，`bar()`、`arguments.callee()`、`foo()` 三条语句都可以调用函数自身：

```js
const China = function chinese() {
  China(); // 函数名称
  arguments.callee();
  chinese(); // 指向该函数的变量名称
};
```

使用递归函数的时候，需要注意加入合适的循环终止条件，避免进入到**死循环**，锁死当前 JavaScript 解析引擎的执行线程。

```js
/* 采用 while 循环打印 0 ~ 3 范围的整数 */
let index = 0;
/* index <= 3 是循环中止条件 */
while (index <= 3) {
  console.log(index);
  index++;
}
/* 
0
1
2
3
*/

/* 将 while 循环转换为递归函数调用 */
function loop(index) {
  /* index > 3 是循环中止条件 */
  if (index > 3) {
    return;
  }
  console.log(index);
  loop(index + 1);
}
loop(0);
/* 
0
1
2
3
*/
```

当需要获取一个**树结构**当中的所有节点时，使用递归函数会比循环语句更为方便：

```js
function traversalTree(node) {
  if (node == null) {
    return;
  }
  console.log("可以在这个位置操作树节点");

  for (let i = 0; i < node.childNodes.length; i++) {
    traversalTree(node.childNodes[i]);
  }
}
```

除此之外，通过灵活的应用递归函数，还可以在函数当中模拟出**堆栈**数据结构的行为：

```js
function traversal(index) {
  if (index < 0) {
    return;
  }

  console.log("开始：" + index);
  traversal(index - 1);
  console.log("结束：" + index);
}

traversal(3);
/*
开始：3
开始：2
开始：1
开始：0
结束：0
结束：1
结束：2
结束：3
*/
```

## 5.5、嵌套函数

**父函数**当中可以嵌套一个**子函数**，此时**子函数**可以在**父函数**当中进行调用，**子函数**内部将会形成一个可以访问**父函数**参数与变量的**闭包**，而**父函数**并不能使用**子函数**当中的参数与变量。

```js
function totalSquares(size1, size2) {
  function square(size) {
    return size * size;
  }
  // console.log(size); // Uncaught ReferenceError: size is not defined
  return square(size1) + square(size2);
}

console.log(totalSquares(1, 2)); //  5
console.log(totalSquares(2, 3)); //  13
console.log(totalSquares(3, 4)); //  25
```

这是由于**闭包**可以保存其所见作用域当中的所有参数与变量，所以下面示例当中的子函数 `child` 被返回时，`parent` 的参数值 `x` 也会被一同保留下来：

```js
/* 父函数 */
function parent(x) {
  /* 子函数 */
  function child(y) {
    return x + y;
  }
  return child;
}

const childFunction = parent(2); // 使用静态变量 childFunction 接收返回的 child 函数

console.log(childFunction(6)); // 8
console.log(parent(5)(8)); // 13
```

JavaScript 函数支持多层嵌套，例如函数 `A` 可以包含函数 `B`，而函数 `B` 可以再包含函数 `C`。此时函数 `B` 和 `C` 都形成了**闭包**，它们都同时包含着多个作用域（`B` 可以访问 `A`，`C` 可以访问 `B` 和 `A`），这种递归式包含的作用域称为**作用域链**，具体请参考下面的示例：

```js
function A(x) {
  function B(y) {
    function C(z) {
      console.log(x + y + z);
    }
    C(3);
  }
  B(2);
}

A(1); // 6
```

当相同闭包**作用域链**当中的参数或者变量出现命名冲突时，距离**调用位置**更近的参数或者变量会拥有更高的优先级：

```js
function parent() {
  let number = 5;

  function child(number) {
    return (number = 8); // 变量 number 出现命名冲突
  }
  return child;
}

parent()(2022); // 8
```

### 5.5.1闭包 Closure

正如前面内容所提到的，JavaScript 允许函数嵌套，并且**子函数**可以访问**父函数**以及**父函数所能访问作用域**里的全部变量与函数，而**父函数**却不能访问定义在**子函数**当中的变量与函数。由于**子函数**可以访问到**父函数**的作用域，因此当**子函数**生命周期大于**父函数**的时候，**父函数**所定义变量与函数的生存周期将会比**子函数**更为持久。当**子函数**在**父函数**作用域当中被访问时，就产生了一个**闭包**。

```js
/* 变量 name */
const parent = function (name) {
  const child = function () {
    return name; // 子函数可以访问父函数的 name 参数
  };
  return child; // 返回子函数，将其暴露在父函数作用域
};

const temporary = parent("zs"); // 将返回的子函数赋值给变量 temporary
temporary(); // zs
```

实际的情况可能会更加复杂，下面代码返回了一个对象，这些对象上自定义的 `getter` 与 `setter` 函数可以用于操作父函数 `blogger` 当中的内部变量：

```js
const blogger = function (name) {
  let age;

  return {
    getName: function () {
      return name;
    },
    setName: function (newName) {
      name = newName;
    },
    getAge: function () {
      return age;
    },
    setAge: function (newAge) {
      age = newAge;
    },
  };
};

const article = blogger("uinika");
console.log(article.getName()); // uinika

article.setName("zs");
console.log(article.getName()); // zs

article.setAge(36);
console.log(article.getAge()); // 36
```

上述代码当中，子函数都可以获得 `blogger()` 父函数的 `name` 参数。除此之外，没有其它办法可以获得父函数内部定义的参数或者变量，从而为其提供了一个安全稳定的运行环境。例如下面代码当中，不能直接通过名称访问变量 `code` 的值，而只能通过 `getCode()` 函数获取变量 `code` 的值：

```js
const getCode = (function () {
  let code = "610000"; // 不希望被外部修改的 code 变量

  return function () {
    return code;
  };
})();

console.log(getCode()); // 610000
console.log(code); // Uncaught ReferenceError: code is not defined
```

尽管有着充当**局部变量**保险箱的优点，但是在使用闭包特性仍然需要避免一些陷阱，例如**子函数**闭包当中定义了一个与**父函数**相同名称的变量，那么在该闭包作用域当中，将会无法引用**父函数**当中的这个同名变量。例如下面代码当中，调用 `getCode()` 函数时同时传递了 `610000`（父函数参数）和 `610095`（子函数参数）两个参数，而最终返回的 `code` 值为 `610095` ：

```js
const getCode = function (code) {
  return function (code) {
    code = code;
    console.log(code);
  };
};

getCode(610000)(610095); // 610095
```

## 5.6、函数参数

### 5.6.1、arguments 对象

函数的实际参数会被保存在一个 `arguments` 对象当中，这个 `arguments` 是一个**类数组对象**，同样可以采用索引 `arguments[index]` 访问具体的参数，也可以使用 `arguments.length` 属性获得参数的具体个数（无参数时为 `0`）。

```js
function blog(URLs) {
  let string = "";
  for (let index = 1; index < arguments.length; index++) {
    string += arguments[index] + " ";
  }
  console.log(string);
  console.log(arguments.length);
}

blog("www.uinio.com", "www.uinika.com", "uinika.gitee.io", "uinika.github.io");
/* 
www.uinika.com uinika.gitee.io uinika.github.io
4
*/
```

> **注意**：`arguments` 对象常用于不确定函数会接收多少个参数的场景。

### 5.6.2、默认参数

JavaScript 函数参数的默认值是 `undefined`，通过 ECMAScript 6 提供的默认参数特性，可以为函数指定默认的参数值：

```js
function profile(name, URL = "www.uinio.com") {
  console.log(name + "'s Blog is " + URL);
}

profile("zs"); // zs's Blog is www.uinio.com
```

### 5.6.3、剩余参数

剩余参数同样也是 ECMAScript 6 提供的新特性，用于将不确定具体数量的参数表示为一个数组：

```js
function profile(name, ...URLs) {
  console.log(name);
  console.log(URLs);

  URLs.map((URL) => {
    console.log(URL);
  });
}

profile("zs", "ww", "www");
/*
zs ww www

*/
```

## 5.7、箭头函数

ECMAScript 6 提供的**箭头函数**相比于传统的 JavaScript 函数，具有更为简短的书写语法：

```js
const printName = () => {
  console.log("zs");
};

const printURL = (URL) => {
  console.log(URL);
};

printName(); // zs
printURL("www.uinio.com"); // www.uinio.com
```

采用关键字 `new` 实例化一个普通 JavaScript 函数时，总是会将 `this` 指针指向全局对象 `window` 或者 `global`。而箭头函数则会从词法上自动绑定 `this` 指针至当前对象：

```js
const Author = function () {
  this.name = "zs";
  console.dir(this); // Author

  /* 箭头函数会自动绑定当前对象的 this 指针 */
  const arrow = () => {
    console.dir(this); // Author
  };
  arrow();

  /* 传统函数会将 this 指针绑定到全局对象 window */
  function tradition() {
    console.dir(this); // window
  }
  tradition();
};

const author = new Author(); // 使用 new 关键字创建对象
```

如果需要让传统 JavaScript 函数当中的 `this` 指针指向当前对象，则可以将其赋值给一个命名为 `that` 或者 `self` 的局部变量：

```js
const Demo = function () {
  const self = this;
  const that = this;

  function getThat() {
    that.name = "zs";
    console.dir(that);
  }
  getThat();

  function getSelf() {
    self.URL = "www.uinio.com";
    console.dir(self);
  }
  getSelf();
};

const demo = new Demo();
/*
Demo
  URL: "www.uinio.com"
  name: "zs"
  [[Prototype]]: Object
Demo
  URL: "www.uinio.com"
  name: "zs"
  [[Prototype]]: Object
*/
```

## 5.8、预定义函数

JavaScript 语言内置了一系列可以在全局作用域当中直接进行调用的**预定义函数**：

|       预定义函数       | 功能描述                                                     |                                                              |
| :--------------------: | :----------------------------------------------------------- | :----------------------------------------------------------- |
|        `eval()`        | 解析一段字符串形式的 JavaScript 代码；                       | `eval("console.log(this)"); // Window`                       |
|      `isFinite()`      | 判断传入的参数值是否为有限数值；                             | `isFinite(2022); // true`                                    |
|       `isNaN()`        | 判断传入的参数值是否为 `NaN`；                               | `isNaN(NaN); // true`                                        |
|      `parseInt()`      | 将参数字符串解析为一个整数值；                               | `parseInt("2006"); // 2006`                                  |
|     `parseFloat()`     | 将参数字符串解析为一个浮点数值；                             | `parseFloat("3.14"); // 3.14`                                |
|     `encodeURI()`      | 编码 URI 当中除 `数字`、`大小写字母` 以及 `; , / ? : @ & = + $ - _ . ! ~ * ' ( ) #` 以外的字符； | `encodeURI("www.uinika.com?blog=博客");`                     |
|     `decodeURI()`      | 解码 URI 当中除 `数字`、`大小写字母` 以及 `; , / ? : @ & = + $ - _ . ! ~ * ' ( ) #` 以外的字符； | `decodeURI('www.uinika.com?blog=%E5%8D%9A%E5%AE%A2');`       |
| `encodeURIComponent()` | 编码 URI 当中除 `数字`、`大小写字母` 以及 `- _ . ! ~ * ' ( )` 之外的字符； | `encodeURIComponent("www.uinika.com?blog=博客");`            |
| `decodeURIComponent()` | 解码 URI 当中除 `数字`、`大小写字母` 以及 `- _ . ! ~ * ' ( )` 之外的字符； | `decodeURIComponent("www.uinika.com%3Fblog%3D%E5%8D%9A%E5%AE%A2");` |

> **注意**：相比于 `encodeURI()` 方法，`encodeURIComponent()` 方法的编码转义范围更为广泛，但是转换之后的 URI 地址无法直接进行访问。

# 六、对象

JavaScript 当中的**对象**是一系列属性和方法的集合。

## 6.1、创建对象

**JavaScript 当中对象创建方式的不同，也会导致 `this` 指针的的指向有所不同，在使用时必须特别注意。**

### 6.1.1、对象字面量 `{}`

JavaScript 允许通过字面量 `{}` 方式创建对象，其语法格式如下所示：

```js
const objectName = {
  propertyName: value,
  functionName: function () {},
};
```

下面代码采用字面量方式定义了一个 `Person` 对象，该对象拥有一个 `name` 参数和一个 `printName()` 方法：

```js
const Person = {
  name: "zs",
  printName: function () {
    console.log(this); // {name: 'zs', age: 36, printName: ƒ, printAge: ƒ}
    console.log(this.name);
  },
};

Person.printName(); // zs
```

> **注意**：在使用字面量创建的对象当中定义箭头函数时，箭头函数当中的 `this` 指针将会指向全局对象 `window`。

```js
const Person = {
  name: "zs",
  printAge: () => {
    console.log(this); // Window {window: Window, self: Window, document: document, name: '', location: Location, …}
    console.log(this.name);
  },
};

Person.printAge(); // undefined
```

#### 6.1.2、构造函数 function

采用 `function` 关键字同样可以创建一个对象，但是与字面量语法不同的是，在使用之前必须采用关键字 `new` 手动进行实例化。

```js
function objectName(parameter) {
  this.propertyName = parameter;
  this.functionName = function () {};
  this.functionName = () => {};
}

new objectName(parameter);
```

下面代码采用 `function` 构造函数方式定义了一个 `Person` 对象，该对象拥有一个 `name` 参数和一个 `printName()` 方法：

```js
function Person(name) {
  this.name = name;
  /* 采用普通 function 函数定义对象方法 */
  this.printName = function () {
    console.log(this); // Person {name: 'uinika', printName: ƒ}
    console.log(this.name);
  };
}

const person = new Person("uinika");
person.printName(); // uinika
```

在采用 `function` 构造函数创建的对象当中定义箭头函数时，箭头函数内的 `this` 指针依然会指向当前对象 `Person`：

```js
function Person(name) {
  this.name = name;
  /* 采用箭头函数定义对象方法 */
  this.printName = () => {
    console.log(this); // Person {name: 'uinika', printName: ƒ}
    console.log(this.name);
  };
}

const person = new Person("uinika");
person.printName(); // uinika
```

#### 6.1.3、Object.create() 方法

基于现有对象的 `__proto__` 创建一个新的对象，而不需要使用到字面量语法 `{}`，或者构造函数 `function`。

```js
Object.create(proto，[propertiesObject])
```

上面的 `proto` 表示新创建对象的原型（可缺省），而 `propertiesObject` 表示提供属性的对象，该方法执行后返回一个带有指定原型和属性的新对象。

```js
const Person = {
  URL: "",
  print: function () {
    console.log(this); // {name: 'zs', URL: 'www.uinika.com'}
    console.log(`我是 ${this.name}，我的博客是 ${this.URL}。`);
  },
};

const person = Object.create(Person); // 使用 Object.create() 创建对象

person.name = "zs";
person.URL = "www.uinika.com";
person.print(); // 我是 zs，我的博客是 www.uinika.com。
```

> **注意**：`prototype` 是函数才会拥有的属性，而 `proto` 是每个对象都会拥有的属性。

## 6.2、创建对象实例 new

`new` 操作符用于创建一个自定义对象的**实例**。

```js
const objectName = new objectType([parameter1, parameter2, ..., parameterN]);
```

上面的 `objectName` 是对象名称，而 `objectType` 是对象参数

```js
function Author(name, URL) {
  this.name = name;
  this.URL = URL;
  this.print = () => {
    console.log(this);
  };
}

const author = new Author("zs", "www.uinio.com");
author.print();
/* 
Author {name: 'zs', URL: 'www.uinio.com', print: ƒ}
  URL: "www.uinio.com"
  name: "zs"
  print: () => { console.log(this); }
  [[Prototype]]: Object
*/
```

## 6.3、指向对象自身 this

`this` 关键字指向当前对象本身，可以用于引用当前对象上定义的`方法`或者`属性`。

```js
/* 字面量对象的 this 指针 */
const Author = {
  name: "zs",
  print: function () {
    console.log(this);
  },
};
Author.print(); // {name: 'zs', print: ƒ}

/* 函数对象当中的 this 指针*/
const Writer = function () {
  this.name = "zs";
  this.print = function () {
    console.log(this);
  };
};
const writer = new Writer();
writer.print(); // Writer {name: 'zs', print: ƒ}
```

## 6.4、访问父对象 super

`super` 关键字可以用于引用当前对象的**父对象**构造函数，或者用于访问父对象上定义的`方法`和`属性`。

```
super([arguments]); // 调用父对象的构造函数
super.parentFunction([arguments]); // 调用父对象上的方法
```

上面的 `arguments` 是传递给父对象的构造函数或者普通方法的参数，而 `parentFunction` 指代的是父对象上定义的方法。

```js
/* 父对象 */
class Person {
  constructor(name) {
    this.name = name;
  }
  print() {
    console.log(this);
  }
}

/* 子对象 */
class zs extends Person {
  constructor(name, URL) {
    super(name); // 调用父对象 Person 上的构造函数
    this.URL = URL;
  }
  print() {
    super.print(); // 调用父对象 Person 上定义的 print() 方法，但是打印结果为 zs 对象上的 this 指针
  }
}

const zs = new zs("uinika", "www.uinio.com");
console.log(zs);
/*
zs {name: 'uinika', URL: 'www.uinio.com'}
  URL: "www.uinio.com"
  name: "uinika"
  [[Prototype]]: Person
*/
zs.print();
/*
zs {name: 'uinika', URL: 'www.uinio.com'}
  URL: "www.uinio.com"
  name: "uinika"
  [[Prototype]]: Person
*/
```

## 6.5、删除属性 delete

`delete` 操作符用于删除指定的**对象属性**（非继承）或者**数组元素**。如果 `delete` 操作成功，将会返回 `true`，否则返回 `false`。

```
delete arrayName[index]; // 删除数组元素
delete objectName.property; // 删除对象属性
```

上面的 `objectName` 表示对象名称，`arrayName` 则是指数组名称，而 `property` 是一个对象上的属性，`index` 则是数组当中的元素索引。

```js
const Author = {
  name: "zs",
  url: "www.uinio.com",
  age: 36,
};

let result = delete Author.age;

console.log(result); // true
console.log(Author); // {name: 'zs', url: 'www.uinio.com'}
```

删除数组中的元素时，数组的长度不会发生改变，只是被删除元素所在索引会指向 `undefine` 值。

```js
const trees = new Array("橡树", "松树", "柳树", "杉树", "樟树");
delete trees[2];

console.log(trees); // ['橡树', '松树', empty, '杉树', '樟树']
console.log(trees[2]); // undefined
console.log(trees.length); // 5
```

## 6.6、判断属性存在 in

`in` 操作符用于判断对象的**属性名称**或者数组的**元素索引**是否真实存在，如果存在就会返回 `true`，否则返回 `false`：

```
index in arrayName; // 判断数组的元素索引是否存在
property in objectName; // 判断对象的属性名称是否存在
```

上面的 `arrayName` 是数组名称，而 `index` 是数组索引。`objectName` 是对象名称，而 `property` 表示对象属性。

```js
/* 采用 in 操作符判断对象的属性名称是否存在 */
const Author = {
  name: "zs",
  url: "www.uinio.com",
  age: 36,
};
console.log("name" in Author); // true

/* 采用 in 操作符判断数组的元素索引是否存在 */
const trees = ["橡树", "松树", "柳树", "杉树", "樟树"];
console.log(2 in trees); // true
```

## 6.7、判断实例类型 instanceof

用于判断当前的实例是否为指定对象的实例，如果是就返回 `true`，否则返回 `false`：

```js
objectName instanceof objectType;
```

上面的 `objectName` 是需要进行判断的实例，而 `objectType` 则是对象的类型。例如, 下面的代码使用 instanceof 去判断 theDay 是否是一个 Date 对象. 因为 theDay 是一个 Date 对象, 所以 if 中的代码会执行.

```js
const date = new Date(2022, 1, 5);

console.log(date instanceof Date); // true
console.log(date instanceof Object); // true
console.log(date instanceof String); // false
```

## 6.8、getters & setters

JavaScript 对象的 `setter` 和 `getter` 是一种用于设置或者获取属性值的函数方法。其中，`getter` 方法没有参数，但是有返回值；而 `setter` 方法只会接受一个参数，但是没有返回值。

通过在使用**字面量语法** `{}` 定义对象时，添加 `get property()`（把对象属性绑定到**获取**该属性时将会被调用的函数）和 `set property(value)`（把对象属性绑定到**设置**属性时将会被调用的函数）就可以完成 `setter/getter` 方法的添加：

```js
const Author = {
  name: "zs",
  get age() {
    return this.name + " is 36!";
  },
  set blog(URL) {
    this.name = URL;
  },
};
console.log(Author.name); // zs

/* getter 生效 */
console.log(Author.age); // zs is 36!

/* setter 生效 */
Author.blog = "www.uinio.com";
console.log(Author.name); // www.uinio.com
console.log(Author);
/*
age: (...)
name: "www.uinio.com"
get age: ƒ age()
set blog: ƒ blog(URL)
[[Prototype]]: Object
*/
```

禁止在某个属性的 `setter` 方法中对该属性赋值，这样会导致递归调用的发生，从而引发 `RangeError` 错误：

```js
const Author = {
  blog: "",
  set blog(URL) {
    this.blog = URL; // Uncaught RangeError: Maximum call stack size exceeded
  },
};

Author.blog = "www.uinika.com";
```

对于已经定义完毕的对象，可以采用 `Object.defineProperty()` 方法添加 `setter/getter` 方法：

```js
const Author = {
  name: "zs",
};

Object.defineProperties(Author, {
  age: {
    get: function () {
      return this.name + " is 36!";
    },
  },
  blog: {
    set: function (URL) {
      this.name = URL;
    },
  },
});

/* getter 生效 */
console.log(Author.age); // zs is 36!

/* setter 生效 */
Author.blog = "www.uinio.com";
console.log(Author.name); // www.uinio.com
```

> **注意**：`Object.defineProperty(obj, prop, descriptor)` 方法可以用于在对象上定义新的属性，或者修改对象上的已有属性。其中 `obj` 是需要定义属性的对象，而 `prop` 是要定义或者修改的属性名称，`descriptor` 则是需要定义或者修改的属性描述符，该方法的返回值为处理之后的新对象。

## 6.9、遍历对象属性

JavaScript 提供了多方法来遍历一个对象上的所有属性。

### 6.9.1、`for...in`方法

`for...in` 会依次访问指定对象及其原型链上面所有可以枚举的属性，也包括继承的可枚举属性。

```js
const Author = {
  url: "www.uinio.com",
  name: "zs",
  age: 36,
};

for (propertyName in Author) {
  console.log("属性名称：" + propertyName);
  console.log("属性值：" + Author[propertyName]);
}
/*
属性名称：url
属性值：www.uinio.com
属性名称：name
属性值：zs
属性名称：age
属性值：36
*/
```

### 6.9.2、`Object.key(obj)方法`

`Object.keys(obj)` 会返回参数对象 `obj` 包含（不包括原型链）的所有可枚举属性的名称的数组，数组当中属性名称的排列顺序和正常循环遍历该对象的顺序保持一致。

```js
const Author = {
  url: "www.uinio.com",
  name: "zs",
  age: 36,
};

console.log(Object.keys(Author)); // ['url', 'name', 'age']
```

### 6.9.3、`Object.values()`

`Object.values()`与`Object.keys()`遍历对象的特性是相同的，但是其返回的结构是以遍历的属性值构成的数组

```js
const Author = {
  url: "www.uinio.com",
  name: "zs",
  age: 36,
};

Object.values(Author) // ['www.uinio.com', 'zs',36]
```

### 6.9.4、`Object.entries()`

`Object.entries()`的返回值为`Object.values()`与`Object.keys()`的结合，也就是说它会返回一个嵌套数组，数组内包括了属性名与属性值

```
const Author = {
  url: "www.uinio.com",
  name: "zs",
  age: 36,
};
Object.entries(Author) // [['url','name', 'age'],["www.uinio.com",'zs', 36]]
```

### 6.9.5、`Object.getOwnPropertyNames(obj)`

`Object.getOwnPropertyNames(obj)` 会返回参数对象 `obj`（不包括原型链）上全部属性（无论该属性是否可枚举）名称所构成的数组。

```js
const Author = {
  url: "www.uinio.com",
  name: "zs",
  age: 36,
};

console.log(Object.getOwnPropertyNames(Author)); // ['url', 'name', 'age']
```

## 6.10、Javascript常用对象

### 6.10.1、函数对象

#### 6.10.1.1、call、apply

call和apply的作用都是**改变this作用域**，都是在特定作用域中调用函数。当一个对象没有某个方法，而其他对象有，我们就可以使用call或apply实现某个方法的复用。
call和apply使用方法基本相同，唯一不同之处就是它们的参数规则：call方法接受一个参数列表，而apply方法接受一个包含多个参数的数组。

#### 6.10.1.2、this指向

- 以函数形式调用时，this永远都是window
- 以方法的形式调用时，this是调用方法的对象
- 以构造函数的形式调用时，this是新创建的那个对象
- 使用call和apply调用时，this是传入的那个指定对象

#### 6.10.1.3、arguments参数

在调用函数时，浏览器每次都会传递进两个隐含的参数：

1. 函数的上下文对象： **this**
2. 封装实参的对象： **arguments**

arguments是一个类数组对象，它也可以通过索引来操作数据，也可以获取长度，在调用函数时，我们所传递的实参都会在arguments中保存，比如：arguments.length 可以用来获取实参的长度，我们即使不定义形参，也可以通过arguments来使用实参，只不过比较麻烦，例如：

* arguments[0]：表示第一个实参
* arguments[1]：表示第二个实参
* …

它里边有一个属性叫做callee，这个属性对应一个函数对象，就是当前正在指向的函数的对象。

### 6.10.2、Date对象

在JavaScript中使用Date对象来表示一个时间，如果直接使用构造函数创建一个Date对象，则会封装为当前代码执行的时间。

```js
var date = new Date();
console.log(date);

console.log(date.getFullYear());//获取当前日期对象的年份(四位数字年份)
console.log(date.getMonth());//获取当前日期对象的月份(0 ~ 11)
console.log(date.getDate());//获取当前日期对象的日数(1 ~ 31)
console.log(date.getHours());//获取当前日期对象的小时(0 ~ 23)
console.log(date.getMinutes());//获取当前日期对象的分钟(0 ~ 59)
console.log(date.getSeconds());//获取当前日期对象的秒钟(0 ~ 59)
console.log(date.getMilliseconds());//获取当前日期对象的毫秒(0 ~ 999)
```

### 6.10.3、Math对象

Math和其它的对象不同，它不是一个构造函数，它属于一个工具类不用创建对象，它里边封装了数学运算相关的属性和方法。

Math对象属性：

| 属性                                                         | 描述                                    |
| :----------------------------------------------------------- | :-------------------------------------- |
| [E](https://www.w3school.com.cn/jsref/jsref_e.asp)           | 返回欧拉数（约 2.718）。                |
| [LN2](https://www.w3school.com.cn/jsref/jsref_ln2.asp)       | 返回 2 的自然对数（约 0.693）。         |
| [LN10](https://www.w3school.com.cn/jsref/jsref_ln10.asp)     | 返回 10 的自然对数（约 2.302）。        |
| [LOG2E](https://www.w3school.com.cn/jsref/jsref_log2e.asp)   | 返回 E 的以 2 为底的对数（约 1.442）。  |
| [LOG10E](https://www.w3school.com.cn/jsref/jsref_log10e.asp) | 返回 E 的以 10 为底的对数（约 0.434）。 |
| [PI](https://www.w3school.com.cn/jsref/jsref_pi.asp)         | 返回 PI（约 3.14）。                    |
| [SQRT1_2](https://www.w3school.com.cn/jsref/jsref_sqrt1_2.asp) | 返回 1/2 的平方根（约 0.707）。         |
| [SQRT2](https://www.w3school.com.cn/jsref/jsref_sqrt2.asp)   | 返回 2 的平方根（约 1.414）。           |

Math对象方法：

| 方法                                                         | 描述                                                       |
| :----------------------------------------------------------- | :--------------------------------------------------------- |
| [abs(*x*)](https://www.w3school.com.cn/jsref/jsref_abs.asp)  | 返回 x 的绝对值。                                          |
| [acos(*x*)](https://www.w3school.com.cn/jsref/jsref_acos.asp) | 返回 x 的反余弦值，以弧度为单位。                          |
| [acosh(*x*)](https://www.w3school.com.cn/jsref/jsref_acosh.asp) | 返回 x 的双曲反余弦值。                                    |
| [asin(*x*)](https://www.w3school.com.cn/jsref/jsref_asin.asp) | 返回 x 的反正弦值，以弧度为单位。                          |
| [asinh(*x*)](https://www.w3school.com.cn/jsref/jsref_asinh.asp) | 返回 x 的双曲反正弦值。                                    |
| [atan(*x*)](https://www.w3school.com.cn/jsref/jsref_atan.asp) | 返回 x 的反正切值，返回的值是 -PI/2 到 PI/2 之间的弧度值。 |
| [atan2(*y*, *x*)](https://www.w3school.com.cn/jsref/jsref_atan2.asp) | 返回其参数商的反正切值。                                   |
| [atanh(*x*)](https://www.w3school.com.cn/jsref/jsref_atanh.asp) | 返回 x 的双曲反正切值。                                    |
| [cbrt(*x*)](https://www.w3school.com.cn/jsref/jsref_cbrt.asp) | 返回 x 的三次方根。                                        |
| [ceil(*x*)](https://www.w3school.com.cn/jsref/jsref_ceil.asp) | 返回 x，向上舍入为最接近的整数。                           |
| [clz32(*x*)](https://www.w3school.com.cn/jsref/jsref_clz32.asp) | 返回 x 的 32 位二进制表示中前导零的数量。                  |
| [cos(*x*)](https://www.w3school.com.cn/jsref/jsref_cos.asp)  | 返回 x 的余弦值（x 以弧度为单位）。                        |
| [cosh(*x*)](https://www.w3school.com.cn/jsref/jsref_cosh.asp) | 返回 x 的双曲余弦值。                                      |
| [exp(*x*)](https://www.w3school.com.cn/jsref/jsref_exp.asp)  | 返回 Ex 的值。                                             |
| [expm1(*x*)](https://www.w3school.com.cn/jsref/jsref_expm1.asp) | 返回 Ex 减去 1 的值。                                      |
| [floor(*x*)](https://www.w3school.com.cn/jsref/jsref_floor.asp) | 返回 x，向下舍入为最接近的整数。                           |
| [fround(*x*)](https://www.w3school.com.cn/jsref/jsref_fround.asp) | 返回数的最接近的（32 位单精度）浮点表示。                  |
| [log(*x*)](https://www.w3school.com.cn/jsref/jsref_log.asp)  | 返回 x 的自然对数。                                        |
| [log10(*x*)](https://www.w3school.com.cn/jsref/jsref_log10.asp) | 返回 x 的以 10 为底的对数。                                |
| [log1p(*x*)](https://www.w3school.com.cn/jsref/jsref_log1p.asp) | 返回 1 + x 的自然对数。                                    |
| [log2(*x*)](https://www.w3school.com.cn/jsref/jsref_log2.asp) | 返回 x 的以 2 为底的对数。                                 |
| [max(*x*, *y*, *z*, ..., *n*)](https://www.w3school.com.cn/jsref/jsref_max.asp) | 返回值最高的数字。                                         |
| [min(*x*, *y*, *z*, ..., *n*)](https://www.w3school.com.cn/jsref/jsref_min.asp) | 返回值最小的数字。                                         |
| [pow(*x*, *y*)](https://www.w3school.com.cn/jsref/jsref_pow.asp) | 返回 x 的 y 次幂值。                                       |
| [random()](https://www.w3school.com.cn/jsref/jsref_random.asp) | 返回 0 到 1 之间的随机数。                                 |
| [round(*x*)](https://www.w3school.com.cn/jsref/jsref_round.asp) | 将 x 舍入为最接近的整数。                                  |
| [sign(*x*)](https://www.w3school.com.cn/jsref/jsref_sign.asp) | 返回数的符号（检查它是正数、负数还是零）。                 |
| [sin(*x*)](https://www.w3school.com.cn/jsref/jsref_sin.asp)  | 返回 x 的正弦值（x 以弧度为单位）。                        |
| [sinh(*x*)](https://www.w3school.com.cn/jsref/jsref_sinh.asp) | 返回 x 的双曲正弦值。                                      |
| [sqrt(*x*)](https://www.w3school.com.cn/jsref/jsref_sqrt.asp) | 返回 x 的平方根。                                          |
| [tan(*x*)](https://www.w3school.com.cn/jsref/jsref_tan.asp)  | 返回角度的正切值。                                         |
| [tanh(*x*)](https://www.w3school.com.cn/jsref/jsref_tanh.asp) | 返回数的双曲正切值。                                       |
| [trunc(*x*)](https://www.w3school.com.cn/jsref/jsref_trunc.asp) | 返回数字 (x) 的整数部分。                                  |

### 6.10.4、String对象

#### 6.10.4.1、属性

| 属性        | 描述                         |
| ----------- | ---------------------------- |
| constructor | 返回创建字符串对象的原型函数 |
| length      | 可以用来获取字符串的长度     |

#### 6.10.4.2、常用的字符串方法

| 方法                               | 描述                                                         |
| ---------------------------------- | ------------------------------------------------------------ |
| charAt(index)                      | 根据索引获取指定位置的字符                                   |
| charCodeAt(index)                  | 获取指定位置字符的字符编码（Unicode编码）                    |
| concat(str1,str2)                  | 可以用来连接两个或多个字符串                                 |
| indexOf(str1,start_pos)            | 该方法可以检索一个字符串中是否含有指定内容，如果字符串中含有该内容，则会返回其第一次出现的索引，如果没有找到指定的内容，则返回-1，可以指定一个第二个参数，指定开始查找的位置 |
| lastindexOf(str1,start_pos)        | 该方法的用法和indexOf()一样，不同的是indexOf是从前往后找，而lastIndexOf是从后往前找，也可以指定开始查找的位置 |
| slice(start_pos,end_pos)           | 可以从字符串中截取指定的内容，不会影响原字符串，而是将截取到内容返回.  第一个参数：开始位置的索引（包括开始位置） 第二个参数：结束位置的索引（不包括结束位置），如果省略第二个参数，则会截取到后边所有的.注意：也可以传递一个负数作为参数，负数的话将会从后边计算 |
| substring(start_pos,end_pos)       | 可以用来截取一个字符串，它和slice()类似.  第一个参数：开始截取位置的索引（包括开始位置） 第二个参数：结束位置的索引（不包括结束位置），如果省略第二个参数，则会截取到后边所有的.注意：不同的是这个方法不能接受负值作为参数，如果传递了一个负值，则默认使用0，而且它还自动调整参数的位置，如果第二个参数小于第一个，则自动交换 |
| substr(start_pos,intercept_length) | 该方法用来截取字符串.  第一个参数：截取开始位置的索引 第二个参数：截取的长度 |
| split(str)                         | 该方法可以将一个字符串拆分为一个数组，需要一个字符串作为参数，将会根据该字符串去拆分数组 |
| toUpperCase()                      | 将一个字符串转换为大写并返回                                 |
| toLowerCase()                      | 将一个字符串转换为小写并返回                                 |

### 6.10.5、RegExp对象

正则表达式用于定义一些字符串的规则，计算机可以根据正则表达式，来检查一个字符串是否符合规则，获取将字符串中符合规则的内容提取出来。

**对象创建方法**

| var 变量名 = new RegExp("正则表达式","匹配模式"); |
| ------------------------------------------------- |
| var 变量名 = /正则表达式/匹配模式;                |

**匹配模式：**

- i：忽略大小写
- g：全局匹配模式
- ig：忽略大小写且全局匹配模式

**正则方法：**

| 方法             | 描述                                                         |
| ---------------- | ------------------------------------------------------------ |
| split(reg)       | 该方法可以将一个字符串拆分为一个数组，方法中可以传递一个正则表达式作为参数，这样方法将会根据正则表达式去拆分字符串，这个方法即使不指定全局匹配，也会全都插分 |
| search(reg)      | 该方法可以搜索字符串中是否含有指定内容，如果搜索到指定内容，则会返回第一次出现的索引，如果没有搜索到返回-1，它可以接受一个正则表达式作为参数，然后会根据正则表达式去检索字符串，serach()只会查找第一个，即使设置全局匹配也没用 |
| match(reg)       | 该方法可以根据正则表达式，从一个字符串中将符合条件的内容提取出来，默认情况下我们的match()只会找到第一个符合要求的内容，找到以后就停止检索，我们可以设置正则表达式为全局匹配模式，这样就会匹配到所有的内容，可以为一个正则表达式设置多个匹配模式，且顺序无所谓，match()会将匹配到的内容封装到一个数组中返回，即使只查询到一个结果 |
| replace(reg,str) | 该方法可以将字符串中指定内容替换为新的内容，默认只会替换第一个，但是可以设置全局匹配替换全部 |
| reg.test(str)    | 字符串是否匹配正则                                           |

### 6.10.6、Map和Set对象

#### 6.10.6.1、Map

**Map：`Map`是一组键值对的结构，具有极快的查找速度。**

```js
var m = new Map([['Michael', 95], ['Bob', 75], ['Tracy', 85]]);
m.get('Michael'); // 95
```

由于一个key只能对应一个value，所以，多次对一个key放入value，后面的值会把前面的值冲掉：

```js
var m = new Map();
m.set('Adam', 67);
m.set('Adam', 88);
m.get('Adam'); // 88
```

> key判断相等是使用===，value如果是Object则是浅拷贝

#### 6.10.6.2、Set

**Set：`Set`和`Map`类似，也是一组key的集合，但不存储value。由于key不能重复，所以，在`Set`中，没有重复的key**

通过`add(key)`方法可以添加元素到`Set`中，可以重复添加，但不会有效果：

```
s.add(4);
s; // Set {1, 2, 3, 4}
s.add(4);
s; // 仍然是 Set {1, 2, 3, 4}
```

通过`delete(key)`方法可以删除元素：

```
var s = new Set([1, 2, 3]);
s; // Set {1, 2, 3}
s.delete(3);
s; // Set {1, 2}
```

> 注意：Set.add添加的值是浅拷贝的，也就是说如果add进去的是一个对象，那么Set里存的则是这个对象的引用，但是基础数据类型（除了Object）是没有引用的。

> key判断是否相等是用===

# 七、原型继承

JavaScript 是一种基于**原型**（Prototype）而非基于**类**（Class）的面向对象语言。

- 对于 Java 和 C++ 等基于**类**的面向对象语言，会应用关键字 `class` 声明一个类，然后通过**构造函数**（用于在创建类时初始化属性值），使用 `new` 关键字创建该类的**实例**（Instance）；
- JavaScript 的面向对象是基于**原型**的，只存在**对象**而没有**类**的概念，**原型可以被视为一个创建对象的模板，任何对象都可以作为另外一个对象的原型，从而允许后者共享前者的属性**；

> **注意**：传统 ES5 当中，可以通过对象字面量 `{}`、构造函数 `function`、`Object.create()` 三种方式来创建对象；而 ES6 当中新引入的 `class` 类定义语法，其实质是现有原型继承方式的语法糖。

接下来的内容当中，将会基于如下的对象继承结构，建立 `Employee`、`Manager`、`WorkerBee`、`Engineer`、`SalesPerson` 共 5 个对象：

[![img](http://www.uinio.com/Web/Javascript/inheritance.png)](http://www.uinio.com/Web/Javascript/inheritance.png)

1. `Employee` 拥有默认值为空字符串的 `name` 属性和默认值为 `"General"` 的 `department` 属性；
2. `Manager` 是 `Employee` 的子类，其增加了一个默认值为空数组的 `reports` 属性，后面会将其赋值为 `Employee` 对象数组；
3. `WorkerBee` 是 `Employee` 的子类，其增加了一个默认值为空数组的 `projects` 属性；
4. `Engineer` 也是 `WorkerBee` 的子类，其增加了一个默认值为空字符串的 `machine` 属性，同时将 `department` 属性重载为 `"Engineering"`；
5. `SalesPerson` 是 `WorkerBee` 的子类，其增加了一个默认值为 `100` 的 `quota` 属性，并且将继承来的 `department` 属性重载为 `"sales"`，表示所有销售人员都属于相同部门；

```js
/*===== Employee =====*/
function Employee() {
  this.name = "";
  this.department = "General";
}

/*===== Manager =====*/
function Manager() {
  Employee.call(this);
  this.reports = [];
}
Manager.prototype = Object.create(Employee.prototype);

/*===== WorkerBee =====*/
function WorkerBee() {
  Employee.call(this);
  this.projects = [];
}
WorkerBee.prototype = Object.create(Employee.prototype);

/*===== SalesPerson =====*/
function SalesPerson() {
  WorkerBee.call(this);
  this.department = "sales";
  this.quota = 100;
}
SalesPerson.prototype = Object.create(WorkerBee.prototype);

/*===== Engineer =====*/
function Engineer() {
  WorkerBee.call(this);
  this.department = "Engineering";
  this.machine = "";
}
Engineer.prototype = Object.create(WorkerBee.prototype);

const jim = new Employee();
console.log(jim);
/*
Employee {name: '', department: 'General'}
  department: "General"
  name: ""
  [[Prototype]]: Object
    constructor: ƒ Employee()
    [[Prototype]]: Object
*/

const sally = new Manager();
console.log(sally);
/*
Manager {name: '', department: 'General', reports: Array(0)}
  department: "General"
  name: ""
  reports: []
  [[Prototype]]: Employee
    [[Prototype]]: Object
      constructor: ƒ Employee()
      [[Prototype]]: Object
*/

const mark = new WorkerBee();
console.log(mark);
/*
WorkerBee {name: '', department: 'General', projects: Array(0)}
  department: "General"
  name: ""
  projects: []
  [[Prototype]]: Employee
    [[Prototype]]: Object
      constructor: ƒ Employee()
      [[Prototype]]: Object
*/

const fred = new SalesPerson();
console.log(fred);
/*
SalesPerson {name: '', department: 'sales', projects: Array(0), quota: 100}
  department: "sales"
  name: ""
  projects: []
  quota: 100
  [[Prototype]]: Employee
    [[Prototype]]: Employee
      [[Prototype]]: Object
        constructor: ƒ Employee()
        [[Prototype]]: Object
*/

const jane = new Engineer();
console.log(jane);
/*
Engineer {name: '', department: 'Engineering', projects: Array(0), machine: ''}
  department: "Engineering"
  machine: ""
  name: ""
  projects: []
  [[Prototype]]: Employee
    [[Prototype]]: Employee
      [[Prototype]]: Object
        constructor: ƒ Employee()
        [[Prototype]]: Object
*/
```

> **注意**：如果上面代码里的**构造函数**不需要接受任何参数，则可以省略构造函数名称后面的圆括号`()`。

## 7.1、继承属性

下面代码创建了一个 `mark` 对象作为 `WorkerBee` 的实例，当 JavaScript 执行 `new` 操作符的时候，首先会创建一个对象，并且将该对象当中的 `[[prototype]]` 指向 `WorkerBee.prototype`，然后再将该对象设置为执行 `WorkerBee` 构造函数时的 `this` 值。该对象的 `[[Prototype]]` 决定了其用于检索属性的原型链。当构造函数执行完毕之后，所有属性都完成了初始化，就可以将其引用赋值给一个 `mark` 变量：

```js
const mark = new WorkerBee();
```

上述过程不会显式将 `mark` 所继承的原型链属性，作为 `mark` 对象的本地属性。访问属性时，首先 JavaScript 会检查对象自身是否存在该属性，如果存在就返回属性值，如果不存在则会通过 `[[Prototype]]` 检查原型链。如果原型链当中依然未能查找出该属性，则会返回一个 `undefined`。当 `worker` 对象实例化完成之后，其属性值状态如下所示：

```
mark.name = "";
mark.department = "General";
mark.projects = [];
```

对象 `mark` 通过 `mark.__proto__` 从 `Employee` 继承了 `name` 与 `department` 属性，并且定义了一个新的 `projects` 属性，下面的示例代码修改了这些属性的默认值：

```
mark.name = "zs";
mark.department = "Blog";
mark.projects = ["www.uinio.com"];

console.log(mark);
/*
WorkerBee {name: 'zs', department: 'Blog', projects: Array(1)}
  department: "Blog"
  name: "zs"
  projects: ['www.uinio.com']
    [[Prototype]]: Employee
      [[Prototype]]: Object
*/
```

## 7.2、添加属性

JavaScript 允许在运行时为对象添加新的属性，例如通过 `mark.age = 18` 添加一个 `bonus` 属性，此时，除了 `mark` 对象之外的其它 `WorkerBee` 对象不会拥有该属性。

```js
/* mark 对象 */
const mark = new WorkerBee();
mark.age = 18;

/* zs 对象 */
const zs = new WorkerBee();
console.log(zs.age); // undefined
```

如果向对象的**原型**添加新的属性，那么该属性将会添加至从该原型继承属性的所有对象当中，例如下面代码会向所有 `Employee` 的对象添加 `specialty` 属性：

```js
Employee.prototype.specialty = "none";

const mark = new WorkerBee();
console.log(mark);
/*
WorkerBee {name: '', department: 'General', projects: Array(0)}
  department: "General"
  name: ""
  projects: []
  [[Prototype]]: Employee
    [[Prototype]]: Object
      specialty: "none"
      constructor: ƒ Employee()
      [[Prototype]]: Object
*/
```

向 `Employee` 原型当中添加 `specialty` 属性之后，可以在 `Engineer` 的原型里对该属性进行重载，将其默认值 `none` 重新修改为 `code`。

```js
Engineer.prototype.specialty = "code";
const jane = new Engineer();
console.log(jane);

/*
Engineer {name: '', department: 'Engineering', projects: Array(0), machine: ''}
  department: "Engineering"
  machine: ""
  name: ""
  projects: Array(0)
    length: 0
    [[Prototype]]: Array(0)
  [[Prototype]]: Employee
    specialty: "code"
  [[Prototype]]: Employee
    [[Prototype]]: Object
      specialty: "none"
      constructor: ƒ Employee()
      [[Prototype]]: Object
*/
```

## 7.3、属性默认值 & 构造函数参数

JavaScript 的**逻辑或**操作符 `||` 会判断第 1 个参数，如果其结果为 `true` 则返回该值，否则返回第 2 个参数的值，利用该特性可以巧妙定义对象属性的默认值：

```js
this.propertyName = newValue || defaultValue;
```

除此之外，采用 `function` 构造函数声明对象时，还可以同时对属性的参数值进行赋值：

```js
function Name(newValue) {
  this.propertyName = newValue || defaultValue;
}
```

接下来，修改开头示例代码当中的 `Employee`、`WorkerBee`、`Engineer` 类为下面的形式：

```js
/*===== Employee =====*/
function Employee(name, department) {
  this.name = name || "";
  this.department = department || "General";
}

/*===== WorkerBee =====*/
function WorkerBee(projects) {
  this.projects = projects || [];
}
WorkerBee.prototype = new Employee();

/*===== Engineer =====*/
function Engineer(machine) {
  this.department = "Engineering";
  this.machine = machine || "";
}
Engineer.prototype = new WorkerBee();
```

这样在创建 `Engineer` 对象的实例时，就可以通过构造函数指定属性的初始值：

```js
const zs = new Engineer("Keyboard");
console.log(zs);
/*
Engineer {department: 'Engineering', machine: 'Keyboard'}
  department: "Engineering"
  machine: "Keyboard"
  [[Prototype]]: Employee
    projects: []
    [[Prototype]]: Employee
      department: "General"
      name: ""
      [[Prototype]]: Object
        constructor: ƒ Employee(name, department)
        [[Prototype]]: Object
 */
```

通过 `function` 构造函数可以为对象指定**本地的属性值**，但是无法为**经过原型链继承而来的属性**进行赋值，因而需要调整 `WorkerBee` 和 `Engineer` 的构造函数定义，使得**父对象**的构造函数成为**子对象**的 `base` 成员方法，并且立刻在子对象当中进行调用：

```js
/*===== Employee =====*/
function Employee(name, department) {
  this.name = name || "";
  this.department = department || "General";
}

/*===== WorkerBee =====*/
function WorkerBee(name, department, projects) {
  this.base = Employee; // 指向父对象构造函数
  this.base(name, department);
  this.projects = projects || [];
}
WorkerBee.prototype = new Employee();

/*===== Engineer =====*/
function Engineer(name, projects, machine) {
  this.base = WorkerBee; // 指向父对象构造函数
  this.base(name, "Engineering", projects);
  this.machine = machine || "";
}
Engineer.prototype = new WorkerBee();

const zs = new Engineer("zs", ["www.uinio.com", "www.uinika.com"], "Keyboard");
console.log(zs);
/*
Engineer {name: 'zs', department: 'Engineering', projects: Array(2), machine: 'Keyboard', base: ƒ}
  base: ƒ Employee(name, department)
  department: "Engineering"
  machine: "Keyboard"
  name: "zs"
  projects: (2) ['www.uinio.com', 'www.uinika.com']
  [[Prototype]]: Employee
    base: ƒ Employee(name, department)
    department: "General"
    name: ""
    projects: []
    [[Prototype]]: Employee
      department: "General"
      name: ""
      [[Prototype]]: Object
        constructor: ƒ Employee(name, department)
        [[Prototype]]: Object
 */
```

除了使用上述的 `function` 构造函数之外，还可以通过 `call()` 或者 `apply()` 函数来实现继承，例如可以将上面的 `Engineer` 对象**等价**的修改为下面形式：

```js
function Engineer(name, projects, machine) {
  WorkerBee.call(this, name, "Engineering", projects); // 这种方式比定义 base 属性更加简洁
  this.machine = machine || "";
}
```

## 7.4、地属性 & 继承属性

JavaScript 当中访问一个对象的属性时，将会执行如下两个步骤：

1. 检查该属于是否存在于对象本地，如果存在，则直接返回属性值；
2. 如果不存在，就会通过 `__proto__` 属性检查原型链，如果存在就返回值，不存在则返回 `undefined`；

例如下面代码当中的 `amy` 对象具有本地属性 `projects`，而 `name` 和 `department` 属性则是通过 `__proto__` 获得：

```js
/*===== Employee =====*/
function Employee() {
  this.name = "";
  this.department = "General";
}

/*===== WorkerBee =====*/
function WorkerBee() {
  this.projects = [];
}
WorkerBee.prototype = new Employee();

const amy = new WorkerBee();
console.log(amy);
/*
WorkerBee {projects: Array(0)}
  projects: []
  [[Prototype]]: Employee
    department: "General"
    name: ""
    [[Prototype]]: Object
      constructor: ƒ Employee()
      [[Prototype]]: Object
*/
```

此时如果修改父对象 `Employee` 关联原型当中的 `name` 属性，这种影响并不会传递到子对象通过原型继承而来的 `name` 属性：

```js
/*===== Employee =====*/
function Employee() {
  this.name = "";
  this.department = "General";
}

/*===== WorkerBee =====*/
function WorkerBee() {
  this.projects = [];
}
WorkerBee.prototype = new Employee();

const amy = new WorkerBee();
Employee.prototype.name = "Unknown"; // 修改父对象 Employee 关联原型当中的 name 属性值
console.log(amy);
/*
WorkerBee {projects: Array(0)}
  projects: []
  [[Prototype]]: Employee
    department: "General"
    name: ""
    [[Prototype]]: Object
      name: "Unknown"
      constructor: ƒ Employee()
      [[Prototype]]: Object
*/
```

如果在修改**父对象**的属性值时，希望这种修改操作可以被所有的**子对象**继承，那么就不能将其定义为本地属性，而应该将其添加至关联的**原型**当中：

```js
function Employee() {
  this.department = "General";
}
Employee.prototype.name = ""; // 将 name 属性定义在原型上

function WorkerBee() {
  this.projects = [];
}
WorkerBee.prototype = new Employee();

const amy = new WorkerBee();
Employee.prototype.name = "Unknown";
console.log(amy);
/*
WorkerBee {projects: Array(0)}
  projects: Array(0)
    length: 0
    [[Prototype]]: Array(0)
  [[Prototype]]: Employee
    department: "General"
    [[Prototype]]: Object
      name: "Unknown"
      constructor: ƒ Employee()
      [[Prototype]]: Object
*/
```

JavaScript 会首先在对象自身的本地属性当中进行查找，如果没有找到则会到对象的特殊属性 `__proto__` 当中查找，这个过程称为在对象的原型链中查找，这就是 JavaScript 的对象属性查找机制。

## 7.5、prototype 与 `__proto__`

`__proto__` 是一个用于访问对象内部 `[[Prototype]]` 的访问器属性，该属性已经在 ECMAScript 6 规范当中得到了标准化。通过 `Object.prototype.__proto__` 方式访问 `__proto__` 属性的方法已经逐渐被废弃，Mozilla 官方更加推荐使用 `Object.getPrototypeOf` 方式进行访问。而 `prototype` 表示的是**原型对象**，所有的 JavaScript 对象都继承自 `Object.prototype`，该对象当中的默认属性列表如下所示：

```js
{
  constructor: ƒ Object()
  hasOwnProperty: ƒ hasOwnProperty()
  isPrototypeOf: ƒ isPrototypeOf()
  propertyIsEnumerable: ƒ propertyIsEnumerable()
  toLocaleString: ƒ toLocaleString()
  toString: ƒ toString()
  valueOf: ƒ valueOf()
  __defineGetter__: ƒ __defineGetter__()
  __defineSetter__: ƒ __defineSetter__()
  __lookupGetter__: ƒ __lookupGetter__()
  __lookupSetter__: ƒ __lookupSetter__()
  __proto__: （…）
  get __proto__: ƒ __proto__()
  set __proto__: ƒ __proto__()
}
```

除了 `Object` 对象以外，无论是采用对象字面量 `{}`，还是采用构造函数 `function`，或者是采用 `Object.create()` 方法创建的对象，都会拥有一个 `__proto__` 属性：

```js
/*===== 采用字面量方式创建的对象 =====*/
const test1 = {};
console.log(test1.prototype); // undefined
console.log(test1.__proto__);
/*
{constructor: ƒ, __defineGetter__: ƒ, __defineSetter__: ƒ, hasOwnProperty: ƒ, __lookupGetter__: ƒ, …}
  constructor: ƒ Object()
  hasOwnProperty: ƒ hasOwnProperty()
  isPrototypeOf: ƒ isPrototypeOf()
  propertyIsEnumerable: ƒ propertyIsEnumerable()
  toLocaleString: ƒ toLocaleString()
  toString: ƒ toString()
  valueOf: ƒ valueOf()
  __defineGetter__: ƒ __defineGetter__()
  __defineSetter__: ƒ __defineSetter__()
  __lookupGetter__: ƒ __lookupGetter__()
  __lookupSetter__: ƒ __lookupSetter__()
  __proto__: （…）
  get __proto__: ƒ __proto__()
  set __proto__: ƒ __proto__()
*/

/*===== 采用构造函数 function 方式创建的对象 =====*/
const temp = function () {};
const test2 = new temp();
console.log(test2.prototype); // undefined
console.log(test2.__proto__);
/*
{constructor: ƒ}
  constructor: ƒ ()
    arguments: null
    caller: null
    length: 0
    name: "temp"
    prototype: {constructor: ƒ}
    [[FunctionLocation]]: VM2674:1
    [[Prototype]]: ƒ ()
    [[Scopes]]: Scopes[2]
  [[Prototype]]: Object
    constructor: ƒ Object()
    hasOwnProperty: ƒ hasOwnProperty()
    isPrototypeOf: ƒ isPrototypeOf()
    propertyIsEnumerable: ƒ propertyIsEnumerable()
    toLocaleString: ƒ toLocaleString()
    toString: ƒ toString()
    valueOf: ƒ valueOf()
    __defineGetter__: ƒ __defineGetter__()
    __defineSetter__: ƒ __defineSetter__()
    __lookupGetter__: ƒ __lookupGetter__()
    __lookupSetter__: ƒ __lookupSetter__()
    __proto__: （…）
    get __proto__: ƒ __proto__()
    set __proto__: ƒ __proto__()
*/

/*===== 采用 Object.create() 方式创建的对象 =====*/
const test3 = Object.create({});
console.log(test3.__proto__);
/*
{}
  [[Prototype]]: Object
    constructor: ƒ Object()
    hasOwnProperty: ƒ hasOwnProperty()
    isPrototypeOf: ƒ isPrototypeOf()
    propertyIsEnumerable: ƒ propertyIsEnumerable()
    toLocaleString: ƒ toLocaleString()
    toString: ƒ toString()
    valueOf: ƒ valueOf()
    __defineGetter__: ƒ __defineGetter__()
    __defineSetter__: ƒ __defineSetter__()
    __lookupGetter__: ƒ __lookupGetter__()
    __lookupSetter__: ƒ __lookupSetter__()
    __proto__: （…）
    get __proto__: ƒ __proto__()
    set __proto__: ƒ __proto__()
*/
```

JavaScript 函数的 `prototype` 属性实际上指的是 `Function.prototype`，其属性值为解析引擎的原生代码。而下面示例里打印出的 `prototype` 属性，则是 JavaScript 解析引擎将 `test2` 视为构造函数之后的处理结果：

```js
const test2 = function () {};

console.log(test2.__proto__); // ƒ () { [native code] }
console.log(test2.prototype);
/*
{constructor: ƒ}
  constructor: ƒ ()
    arguments: null
    caller: null
    length: 0
    name: "test2"
    prototype: {constructor: ƒ}
    [[FunctionLocation]]: VM1976:1
    [[Prototype]]: ƒ ()
    [[Scopes]]: Scopes[2]
  [[Prototype]]: Object
    constructor: ƒ Object()
    hasOwnProperty: ƒ hasOwnProperty()
    isPrototypeOf: ƒ isPrototypeOf()
    propertyIsEnumerable: ƒ propertyIsEnumerable()
    toLocaleString: ƒ toLocaleString()
    toString: ƒ toString()
    valueOf: ƒ valueOf()
    __defineGetter__: ƒ __defineGetter__()
    __defineSetter__: ƒ __defineSetter__()
    __lookupGetter__: ƒ __lookupGetter__()
    __lookupSetter__: ƒ __lookupSetter__()
    __proto__: （…）
    get __proto__: ƒ __proto__()
    set __proto__: ƒ __proto__()
*/
```

对于本节内容开始时提到的 `Engineer` 类，如果在这里创建一个对象 `zs`：

```js
const zs = new Engineer("zs", ["www.uinio.com", "www.uinika.com"], "Keyboard");
```

则对于 `zs` 对象而言，下面语句的返回结果全部为 `true`：

```js
zs.__proto__ == Engineer.prototype; // true
zs.__proto__.__proto__ == WorkerBee.prototype; // true
zs.__proto__.__proto__.__proto__ == Employee.prototype; // true
zs.__proto__.__proto__.__proto__.__proto__ == Object.prototype; // true
zs.__proto__.__proto__.__proto__.__proto__.__proto__ == null; // true
```

## 7.6、instanceof 判断对象的实例

**除了 `Object` 对象之外，每一个对象都会拥有 `__proto__` 属性，而每一个函数都会拥有 `prototype` 属性**。创建对象时 JavaScript 会将特殊的 `__proto__` 属性设置为构造函数的 `prototype` 属性值，所以表达式 `new Example()` 时会创建一个对象，该对象的 `__proto__` 属性**等于** `Example.prototype`。如果修改 `Example.prototype` 的值，就会改变所有通过 `new Example()` 创建的对象。

通过比较**对象**的 `__proto__` 属性和**函数**的 `prototype` 属性，就可以检测出对象之间的继承关系。JavaScript 提供了便捷的 `instanceof` 操作符，用于检测对象与构造函数之间的关系，如果对象继承自构造函数的原型，则返回 `true`，否则就会返回 `false`：

```js
const empty = {};
console.log(empty instanceof Object); // true
console.log(empty instanceof Function); // false

function None() {}
const none = new None();
console.log(none instanceof None); // true
console.log(none instanceof Object); // true
```

## 7.7、多重继承

由于 JavaScript 的继承是基于对象的**原型链**实现的，每个对象只会存在一个与之关联的**原型**，所以 **JavaScript 不支持多重继承**。但是，可以通过在构造函数当中调用多个其它构造器函数，从而模拟出一种多重继承的假象：

```js
/*===== Employee =====*/
function Employee(name, department) {
  this.name = name || "";
  this.department = department || "General";
}

/*===== WorkerBee =====*/
function WorkerBee(name, department, projects) {
  this.base = Employee; // 指向父对象构造函数
  this.base(name, department);
  this.projects = projects || [];
}
WorkerBee.prototype = new Employee();

/*===== Hobbyist =====*/
function Hobbyist(hobby) {
  this.hobby = hobby || "Football";
}

/*===== Engineer =====*/
function Engineer(name, projects, machine, hobby) {
  /* 调用 WorkerBee 构造函数*/
  this.base1 = WorkerBee;
  this.base1(name, "Engineering", projects);
  /* 调用 Hobbyist 构造函数*/
  this.base2 = Hobbyist;
  this.base2(hobby);
  this.machine = machine || "";
}
Engineer.prototype = new WorkerBee();

const uinika = new Engineer("zs", ["Blog"], "Electronics");
console.log(uinika);
/*
Engineer {name: 'zs', department: 'Engineering', projects: Array(1), base1: ƒ, base: ƒ, …}
  base: ƒ Employee(name, department)
  base1: ƒ WorkerBee(name, department, projects)
  base2: ƒ Hobbyist(hobby)
  department: "Engineering"
  hobby: "Football"
  machine: "Electronics"
  name: "zs"
  projects: ['Blog']
  [[Prototype]]: Employee
    base: ƒ Employee(name, department)
    department: "General"
    name: ""
    projects: []
    [[Prototype]]: Employee
      department: "General"
      name: ""
      [[Prototype]]: Object
*/
```

上面代码当中，对象 `uinika` 确实从 `Hobbyist()` 构造函数当中获得了 `hobby` 属性，但是如果通过 `Hobbyist.prototype.equipment = ["Oscilloscope", "Multimeter", "Solder"]` 添加一个新的 `equipment` 属性到 `Hobbyist` 构造函数的原型，那么对象 `uinika` 并**不会自动继承该属性**。

# 八、类 class

**类是用于创建对象的模板**，ES6 规范当中提出的**类** `class` 依然是建立在**原型**基础之上的。

## 8.1、类的声明与定义

在 ES6 规范当中，通过 `class` 关键字就可以声明一个 JavaScript 类，该类同样属于 `Object` 的子类：

```
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}

const rectangle = new Rectangle();
console.log(rectangle instanceof Object); // true
```

上面代码当中的 `constructor()` 是一个构造函数，该方法用于创建和初始化 `class` 类的对象，**每个类都只能拥有一个构造函数**。

与函数声明不同，**类**必须要先声明之后才能够进行访问，否则就会抛出 `ReferenceError` 错误：

```js
let p = new Rectangle(); // Uncaught ReferenceError: Rectangle is not defined

class Rectangle {}
```

**类表达式**是定义 `class` 类的另外一种方法：

```js
const Rectangle = class {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};
```

## 8.2、类体

类体放置在一对花括号 `{}` 当中，用于定义**成员属性**、**成员函数**以及**构造函数**，类体当中的代码总是在 JavaScript 严格模式下执行：

```js
class Rectangle {
  /* 构造函数 */
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
  /* 成员函数 */
  calcArea() {
    return this.height * this.width;
  }
  /* Getter 方法 */
  get area() {
    return this.calcArea();
  }
}

const square = new Rectangle(10, 10);
console.log(square.area); // 100
```

## 8.3、static 静态成员

`static` 关键字用于在 `class` 类当中定义一个静态的成员函数或者属性，调用静态方法时不需要进行实例化，直接通过**类**的名称就可以调用：

```js
class Point {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }
  /* 静态成员属性 */
  static displayName = "Point";
  /* 静态成员方法 */
  static distance(a, b) {
    const dx = a.x - b.x;
    const dy = a.y - b.y;
    return Math.hypot(dx, dy); // 返回直角三角形的斜边长度
  }
}

/* 通过对象的实例调用静态成员是错误的，会直接返回 undefined */
const p1 = new Point(5, 5);
const p2 = new Point(10, 10);
console.log(p1.displayName); // undefined
console.log(p1.distance); // undefined

/* 通过对象直接调用静态成员是正确的 */
console.log(Point.displayName); // Point
console.log(Point.distance(p1, p2)); // 7.0710678118654755
```

> **注意**：静态方法通常用于为 `class` 类创建工具函数。

## 8.4、私有属性

`class` 类当中声明属性，默认都是**公有属性**：

```
class Rectangle {
  width;
  height = 0;
  constructor(height, width) {
    this.width = width;
    this.height = height;
  }
}
```

通过在成员属性前面添加 `#` 符号，就可以将其声明为**私有属性**：

```
class Rectangle {
  #width;
  #height = 0;
  constructor(height, width) {
    this.#width = width;
    this.#height = height;
  }
}

const rectangle = new Rectangle(10, 10);
rectangle.#width; // Uncaught SyntaxError: Private field '#width' must be declared in an enclosing class
```

## 8.5、extends 关键字

通过使用 `extends` 关键字，可以定义**父类**与**子类**之间的继承关系：

```js
/*===== 父类 =====*/
class Animal {
  constructor(name) {
    this.name = name;
  }
  bark() {
    console.log(`${this.name}发出声音`);
  }
}

/*===== 子类 =====*/
class Dog extends Animal {
  constructor(name) {
    super(name); // 调用父类构造函数，并且传入 name 参数
  }
  bark() {
    console.log(`${this.name}正在汪汪汪`);
  }
}

const dog = new Dog("豆豆");
dog.bark(); // 豆豆正在汪汪汪
```

> **注意**：如果子类当中定义有构造函数，那么这个子类必须调用 `super()` 之后才能够使用 `this` 指针。

ES6 规范的 `class` **类**同样也可以继承 ES5 当中基于构造函数 `function` 定义的**对象**：

```js
function Animal(name) {
  this.name = name;
}
Animal.prototype.bark = function () {
  console.log(this.name + "发出声音");
};

class Dog extends Animal {
  bark() {
    super.bark();
    console.log(this.name + "正在汪汪汪");
  }
}

const dog = new Dog("豆豆");
dog.bark();
/*
豆豆发出声音
豆豆正在汪汪汪
*/
```

但是要注意，`class` 类不能继承没有构造函数的字面量 `{}` 对象，这样会引发 `TypeError` 错误：

```js
const Animal = {
  bark: function () {
    console.log("豆豆发出声音");
  },
};

/* Uncaught TypeError: Class extends value #<Object> is not a constructor or null */
class Dog extends Animal {
  bark() {
    super.bark();
    console.log("豆豆正在汪汪汪");
  }
}
```

可以通过 `Object.setPrototypeOf()` 方法设置原型的方式，实现字面量对象 `{}` 到 `class` 类的继承：

```js
const Animal = {
  bark() {
    console.log(this.name + "发出声音");
  },
};

class Dog {
  constructor(name) {
    this.name = name;
  }
}

Object.setPrototypeOf(Dog.prototype, Animal); // 通过原型链实现继承，避免调用 bark 时会返回 TypeError

const dog = new Dog("豆豆");
dog.bark(); // 豆豆发出声音
```

## 8.6、super 指向父类

`class` 当中的关键字 `super` 可以用于调用父类当中的**成员函数**或者**构造函数**。

```
class Cat {
  constructor(name) {
    this.name = name;
  }
  meowth() {
    console.log(this.name + "喵喵叫");
  }
}

class Lion extends Cat {
  constructor() {
    super("木法沙"); // 在子类构造函数当中，调用父类构造函数
  }
  meowth() {
    super.meowth(); // 调用父类的成员函数
    console.log(this.name + "正在咆哮");
  }
}

const lion = new Lion("辛巴"); // 这里的参数 “辛巴“ 会被丢弃，取而代之的是 Lion 类构造函数当中的 “木法沙“
lion.meowth();
/*
木法沙喵喵叫
木法沙正在咆哮
*/
```

# 九、异常处理

JavaScript 当中可以使用 `throw` 语句抛出一个异常，然后再用 `try...catch` 进行捕获。

## 9.1、异常类型

JavaScript 可以抛出任意对象作为错误信息，但是更加规范的做法是抛出如下的**错误对象**类型：

- `EvalError`：全局函数 `eval()` 产生的错误实例；
- `RangeError`：数值变量或者参数不在有效范围的错误实例；
- `ReferenceError`：引用无效的错误实例；
- `SyntaxError`：语法相关的错误实例；
- `TypeError`：变量或参数的类型不合法的错误实例；
- `URIError`：当 `encodeURI()` 或者 `decodeURI()` 传入无效参数时发生的错误实例；
- `AggregateError`：当操作包含多个错误时（例如`Promise.any()`），可用于包装多个错误实例；
- `InternalError`：JavaScript 解析引擎抛出的错误实例，例如在递归过多的时候；
- `DOMException`：Web 浏览器 DOM 操作异常；

## 9.2、throw 语句

`throw` 语句用于抛出一个异常表达式 `expression`：

```
throw expression;
```

这里的异常表达式 `expression` 可以是任意类型：

```
throw "Error"; // 抛出字符串类型

throw 0; // 抛出数值类型

throw false; // 抛出布尔类型

throw {
  toString: function () {
    return "抛出对象类型";
  },
};
```

可以在抛出异常时声明一个对象，这样就可以在 `catch` 代码块中读取到这个对象的属性。

```js
/* 创建一个用户异常对象 UserException */
function UserException(info) {
  this.name = "UserException";
  this.info = info;
}

/* 将异常信息格式化为字符串 */
UserException.prototype.toString = function () {
  return this.name + ': "' + this.info + '"';
};

/* 创建并且抛出 UserException 实例 */
throw new UserException("发生用户异常!"); // UserException {name: 'UserException', info: '发生用户异常!'}
```

## 9.3、try...catch 语句

如果 `try` 代码块当中的语句抛出异常，那么程序的执行流程就会立即进入 `catch` 代码块。如果 `try` 代码块没有抛出异常，那么程序的执行流程就会跳过 `catch` 代码块。

```js
let result;

function verify(component) {
  if (component === "Transistor") {
    return "是晶体管";
  } else {
    throw "不是晶体管";
  }
}

try {
  verify();
} catch (exception) {
  console.log(exception); // 不是晶体管
}
```

`catch` 代码块用于捕捉所有发生在 `try` 代码块当中的异常，其中的 `exception` 参数用于接收由 `throw` 语句抛出的异常对象或者错误信息。

## 9.4、finally 语句

`finally` 代码块通常会放置在 `try...catch` 语句之后，无论是否抛出异常都会得到执行，通常用于优雅的退出操作或者释放资源。

```js
try {
  throw "发生异常";
} catch (exception) {
  console.log(exception);
  console.log("处理异常");
} finally {
  console.log("异常处理完毕");
}

/*
发生异常
处理异常
异常处理完毕
*/
```

`finally` 语句块里使用 `return` 关键字返回的结果，也将是整个 `try...catch...finally` 语句块的返回值，这里无需关心 `try` 或者 `catch` 语句块里的返回值。

```js
function test() {
  try {
    return "try 语句";
  } catch (exception) {
    return "catch 语句";
  } finally {
    return "finally 语句";
  }
}

console.log(test()); // 'finally 语句'
```

## 9.5、Error 对象

`Error` 对象包含有 `name`（错误名称）和 `message`（错误信息）两个属性，通过该对象提供的 `Error()` 构造函数，可以非常方便的自定义错误对象。

```js
function test() {
  throw new Error("错误");
}

try {
  test();
} catch (exception) {
  console.log(exception.name); // Error
  console.log(exception.message); // 错误
}
```

# 十、Promise 对象

早期的 Web 浏览器端的异步编程主要依靠 `回调函数`、`事件监听`、`发布/订阅`、`Promise 的各种 polyfill` 这四种方式来进行，当 ES6 规范正式推出之后，在完整实现 **Promise** 规范的同时，还引入了 `Generator` 函数及其衍生的 `async/await` 语法糖，将 JavaScript 异步编程带入了全新的时代。

[ES6 Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) 规范源自于开源社区的 [Promises/A+](https://promisesaplus.com/)，是浏览器 JavaScript 以及 NodeJS 上较为早期的异步事件处理方案，也是目前较常使用的异步处理机制。

## 10.1、Promise 的 3 种状态

ES6 Promises 使用**一个 Promise 对象来代表一个异步操作**，它可以包含如下三种状态：

| 状 态     | 描 述                                                   |
| :-------- | :------------------------------------------------------ |
| fulfilled | 操作成功，then()方法的`onFulfilled`函数被调用。         |
| rejected  | 操作失败，then()方法的`onRejected`函数被调用。          |
| pending   | 初始状态，可能触发`fulfilled`或`rejected`状态中的一种。 |

`pending`状态的 Promise 对象可能触发`fulfilled`状态并传递一个值给相应的状态处理方法，也可能触发失败状态`rejected`并传递一个失败信息。当其中任意一种情况出现时，`Promise`对象`then`方法所绑定的处理函数（`onfulfilled()`和`onrejected()`）就会被调用。当`Promise`状态为`fulfilled`时调用`onfulfilled()`，当`Promise`状态为`rejected`时调用`onrejected()`，三种状态之间的转换图如下：

[![img](http://www.uinio.com/Web/Javascript/promise-flow.png)](http://www.uinio.com/Web/Javascript/promise-flow.png)

> `Promise.prototype.then()`和`Promise.prototype.catch()`方法会返回一个全新的 Promise 对象，因此它们之间可以进行链式调用。

可以通过`new`关键字调用构造函数`Promise()`去实例化一个 Promise 异步对象。

```js
const promise = new Promise((resolve, reject) => {
  // ... ...
});
```

## 10.2、Promise 示例代码

一个简单易于理解的使用 Promise 的示例如下：

```js
function asyncFunction() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("你好，异步操作！");
    }, 5000);
  });
}

asyncFunction()
  .then(function (value) {
    console.info(value); // 打印"你好，异步操作！"
  })
  .catch(function (error) {
    console.error(error); // 打印错误信息
  });
```

下面的代码通过 Promise 的异步处理方式来获取 XMLHttpRequest 的数据：

```js
function getURL(URL) {
  return new Promise((resolve, reject) => {
    let xhr = new XMLHttpRequest();
    xhr.open("GET", URL, true);
    xhr.onload = function () {
      if (xhr.status === 200) {
        resolve(xhr.responseText);
      } else {
        reject(new Error(xhr.statusText));
      }
    };
    xhr.onerror = function () {
      reject(new Error(xhr.statusText));
    };
    xhr.send();
  });
}

const URL = "http://www.sina.cn/demo";

getURL(URL)
  .then(function onFulfilled(value) {
    console.info(value);
  })
  .catch(function onRejected(error) {
    console.error(error);
  });
```

## 10.3、Promise 构造函数上的原型

### 10.3.1、`Promise.prototype.constructor`

表示 Promise 构造函数的原型，以便于在原型上放置`then()`、`catch()`、`finally()`方法。

```js
let promise = new Promise((resolve, reject) => {
  // resolve('') or reject('')
});
```

### 10.3.2、`Promise.prototype.then(onFulfilled, onRejected)`

`then()`方法返回一个`Promise`，两个参数分别是 Promise 成功或者失败状态的回调函数。如果忽略某个状态的回调函数参数，或者提供非函数参数，`then()`方法将会丢失该状态的回调信息，但是并不会产生错误。如果调用`then()`的 Promise 的状态发生改变，但是`then()`中并没有对应状态的回调函数，则`then()`最终将创建一个未经回调函数处理的全新 Promise 对象，并使用最初的 Promise 状态来作为这个全新 Promise 的状态。

```js
let promise = new Promise((resolve, reject) => {
  resolve("传递给then内的value值。");
});

promise.then(
  (value) => {
    console.info(value); // 打印“传递给then内的value值。”
  },
  (error) => {
    console.error(error);
  }
);
```

### 10.3.3、`Promise.prototype.catch(onRejected)`

`catch()`只处理`rejected`的情况，该方法返回一个 Promise，实质是`Promise.prototype.then(undefined, onRejected)`的语法糖。

```js
let promise = new Promise((resolve, reject) => {
  resolve("传递给then内的value值。");
});

promise.then(
  (value) => {
    console.info(value); // 打印“传递给then内的value值。”
  },
  (error) => {
    console.error(error);
  }
);
```

### 10.3.4、`Promise.prototype.finally(onFinally)`

`finally()`方法返回一个 Promise，在`then()`和`catch()`执行完成之后，都会调用`finally`指定的回调函数，这样可以避免一些重复的语句同时出现在`then()`和`catch()`当中。

```js
let promise = new Promise((resolve, reject) => {
  resolve("传递给then内的value值。");
  reject("传递给catch内error的值。"); // 此处reject并未被执行，因为Promise状态已经在上面一条语句resolve。
});

promise
  .then((value) => {
    console.info(value);
  })
  .catch((error) => {
    console.error(error);
  })
  .finally(() => {
    console.log("执行到finally方法。");
  });

/* 打印结果 */
// 传递给then内的value值。
// 执行到finally方法。
```

> 包括 Eage 在内的 IE 系列浏览器目前都不支持`finally()`方法。

## 10.4、Promise 对象实例方法

### 10.4.1、`Promise.resolve(value)`

该方法会根据参数的不同，返回不同的 Promise 对象。当接收`Promise`对象作为参数的时候，返回的还是接收到的`Promise`对象；

```js
let jqueryPromise = $.ajax("http://gc.ditu.aliyun.com/geocoding?a=成都市"); // jquery返回的promise对象

let nativePromise = Promise.resolve(jqueryPromise);

nativePromise.then((value) => {
  console.info(value); // API接口的返回值
});
```

当接收到 thenable 类型对象（*由 ES6 Promise 提出的 Thenable 是指具有`.then()`方法的对象*）的时候，返回一个具有该 then 方法的全新 Promise 对象；

```js
let thenablePromise = Promise.resolve(
  // thenable类型对象
  {
    then: (onFulfill, onReject) => {
      onFulfill("fulfilled!");
    },
  }
);

console.log(thenablePromise instanceof Promise); // 打印true

thenablePromise.then(
  (value) => {
    console.info(value);
  },
  function (error) {
    console.error(error);
  }
);

// true
// fulfilled!
```

当接收其它数据类型参数的时候（字符串或`null`）将会返回一个将该参数作为值的全新 Promise 对象。

```js
let promise = Promise.resolve([1, 2, 3]);

promise.then((values) => {
  console.info(values[0]); // 1
});
```

### 10.4.2、`Promise.reject(reason)`

返回一个被`reason`拒绝的 Promise，但是与`resolve()`不同之处在于，即使`reject()`接收的参数是一个 Promise 对象，该函数依然会返回一个全新的 Promise。

```js
let rejectedPromise = Promise.reject(new Error("this is a error!"));

console.info(
  rejectedPromise === Promise.reject(rejectedPromise) // 打印false
);
```

### 10.4.3、`Promise.all(iterable)`

当`iterable`参数中所有 Promise 都被`resolve`, 或者参数并不包含 Promise 时, `all()`方法返一个回`resolve`的全新 Promise 对象。当`iterable`中一个 Promise 返回拒绝`reject`时, `all()`方法会立即终止并返回一个`reject`的全新 Promise 对象。

```js
let promise1 = Promise.resolve(1),
  promise2 = Promise.resolve(2),
  promise3 = Promise.resolve(3);

Promise.all([promise1, promise2, promise3]).then((results) => {
  console.info(results); // 打印[1, 2, 3]
});
```

### 10.4.4、`Promise.race(iterable)`

当`iterable`参数数组中的任意一个 Promise 对象变为`resolve`或者`reject`状态，该函数就会立刻返回一个全新的 Promise 对象，并使用该 Promise 对象进行`resolve`或者`reject`。

```js
let promise1 = Promise.resolve(1),
  promise2 = Promise.resolve(2),
  promise3 = Promise.resolve(3);

Promise.race([promise1, promise2, promise3]).then((results) => {
  console.info(results); // 打印 1
});
```

## 10.5、Promise 方法链

[![img](http://www.uinio.com/Web/Javascript/promise-then-catch-flow.png)](http://www.uinio.com/Web/Javascript/promise-then-catch-flow.png)

```js
function taskA() {
  console.log("Task A");
}
function taskB() {
  console.log("Task B");
}
function onRejected(error) {
  console.log("Catch Error: A or B", error);
}
function finalTask() {
  console.log("Final Task");
}

let promise = Promise.resolve();

promise.then(taskA).then(taskB).catch(onRejected).then(finalTask);
```

如果`taskA()`发生异常的话，会按照`taskA() → onRejected() → finalTask()`这个流程进行处理，`taskB()`并不会被调用的。

> 在上面代码`taskA()`或`taskB()`的处理中，如果发生异常或者返回了`Rejected`状态的`Promise`对象，就会调用`onRejected()`方法。

Promise 中的各个 Task 相互独立，如果`taskA()`想为`taskB()`传递参数，需要在`taskA()`当中`return`相应的值，该值将会作为`taskB()`的参数。

```js
function increment(value) {
  return value + 1;
}

function doubleUp(value) {
  return value * 2;
}

function output(value) {
  console.log(value); // => (1 + 1) * 2
}

let promise = Promise.resolve(1);

promise
  .then(increment)
  .then(doubleUp)
  .then(output)
  .catch(function (error) {
    console.error(error); // Promise Chain发生异常时调用
  });
```

> `return`的值不仅只局限于字符串或者数值，也可以是普通对象或者 Promise。`return`值经由`Promise.resolve( return返回值 );`包装处理，无论回调函数内部返回什么，`then()`方法总是返回一个新建的 Promise 对象。

### 10.5.1、then()方法

#### 10.5.1.1、异步调用

**then()方法内的函数是异步调用的**

执行`Promise.resolve(value)`等方法时，如果 Promise 对象立刻进入`resolve`状态，则是否意味`.then()`里指定的函数是同步调用的？

```js
var promise = new Promise((resolve) => {
  console.log("Inner Promise"); // 1
  resolve(2018);
});
promise.then((value) => {
  console.log(value); // 3
});
console.log("Outer Promise"); // 2

// Inner Promise
// Outer Promise
// 2018
```

上面的示例代码说明：**传入`then()`内的函数是被异步执行的**。JavaScript 代码编写原则之一是尽量**不要对异步回调函数进行同步调用**，否则处理顺序可能会与预期不符，甚至导致栈溢出或异常处理错乱；如果需要在将来某个时刻调用异步回调函数，可以使用`setTimeout()`、`setInterval()`等异步 API（*绑定的函数不会立刻执行，而是延迟到队列的最后*）。

> 为了避免同时使用同步、异步调用可能引起的混乱，Promise 规范约定只能使用异步调用方式 。

#### 10.5.1.2、返回新建的Promise

**每次调用 then()都会返回新建的 Promise**

Promise 之所以能够进行链式的方法调用，是由于无论`then()`还是`catch()`都会返回一个全新的 Promise 对象。

```js
let promise = new Promise((resolve) => {
  resolve(2018);
});

let thenPromise = promise.then((value) => {
  console.log(value);
});

let catchPromise = thenPromise.catch((error) => {
  console.error(error);
});

console.info(promise === thenPromise); // false
console.info(thenPromise === catchPromise); // false
```

通过`===`进行严格相等比较，可以看出上述 3 个 Promise 对象是互不相同的，也就证明`then()`和`catch()`都返回了不同的 Promise 对象。

[![img](http://www.uinio.com/Web/Javascript/then-catch.png)](http://www.uinio.com/Web/Javascript/then-catch.png)

下面是一个通过`then()`返回新创建 Promise 对象的错误使用方法：

```js
/* 错误的返回方式 */
function incorrectAsyncCall() {
  let promise = Promise.resolve();

  promise.then(() => {
    return value;
  });

  return promise;
}
```

上述写法存在诸多问题，首先在`promise.then()`中产生的异常不会被外部捕获，其次也不能得到`then()`的返回值。由于每次调用`promise.then()`都会返回一个新创建的 Promise 对象，因此需要通过*Promise Chain*将调用链式化，修改后的代码如下：

```js
/* 正确的做法 */
function correctAsyncCall() {
  let promise = Promise.resolve();

  // 直接将链式调用的then()返回
  return promise.then(() => {
    return value;
  });
}
```

> 与`Promise.then()`类似，包括`Promise.all()`和`Promise.race()`都会接收`Promise`对象作为参数，然后返回一个与接收参数不同的全新 Promise 对象，使用时应多加注意。

#### 10.5.1.3、使用reject

**使用 reject 而不是 throw**

Promise 的构造函数以及`then()`中执行的函数都可以认为是在`try...catch`块中运行，因此即便使用了`throw`，程序本身也不会因为抛出异常而终止。

```js
let promise = new Promise((resolve, reject) => {
  throw new Error("throw message");
});

promise.catch((error) => {
  console.error(error); // => "throw message"
});
```

上面的代码运行时没有任何问题，但是如果需要把 Promise 对象状态设置为`Rejected`的话，相比`throw`关键字`reject()`方法会更加合理。接下来，我们方便的通过 Promise 构造函数中的`reject`参数，将 Promise 对象的状态设置为`Rejected`。

```js
let promise = new Promise((resolve, reject) => {
  reject(new Error("reject message")); // 发生错误的时候可以向reject()传递Error对象
});

promise.catch((error) => {
  console.error(error); // => "reject message"
});
```

> `reject`比`throw`更安全另一个原因在于，有些场景下很难届定`throw`是开发人员主动抛出，还因为真正的代码异常导致的。

当需要在`then()`中执行`reject`操作的时候，可以通过`then()`当中的回调函数`return`一个自定义的 Promise 对象。然后根据这个自定义 Promise 对象的状态，下一个`then()`中注册的的`onFulfilled()`或`onRejected()`回调函数会相应进行调用，从而实现`then()`中不通过`throw`关键字也能进行`reject`操作。

```js
let promise = Promise.resolve();

promise
  .then(() => {
    let newPromise = new Promise((resolve, reject) => {
      // resolve或者reject的状态决定了下一个then()当中的onFulfilled或onRejected哪个会被调用
    });
    return newPromise;
  })
  .then(onFulfilled, onRejected);
```

例如下面代码中，`newPromise`对象状态为`Rejected`的时候，后续`catch()`中的`onRejected`方法会被调用。

```js
let onRejected = console.error.bind(console);

let promise = Promise.resolve();

promise
  .then(() => {
    let newPromise = new Promise((resolve, reject) => {
      reject(new Error("Promise is rejected !"));
    });
    return newPromise;
  })
  .catch(onRejected);
```

接下来，再通过`Promise.reject()`来简化代码：

```js
let onRejected = console.error.bind(console);

let promise = Promise.resolve();

promise
  .then(() => {
    return Promise.reject(new Error("Promise is rejected !"));
  })
  .catch(onRejected);
```

Promise 的缺点在于一旦新建就会立即执行，并且无法中途取消。其次，如果不设置回调函数，Promise 内部抛出的错误，不会反应到外部。第三，当处于 pending 状态时，无法得知目前进展到哪一个阶段（**刚刚开始还是即将完成**）。

# 十一、Generator 函数

Generator 函数是 ES6 提供的一种异步编程解决方案，Generator 函数是一个封装了多个内部状态的状态机，执行 Generator 函数会返回一个遍历器对象，可以通过该对象遍历 Generator 函数内部的每个状态。Generator 函数与普通函数的区别在于：声明时在`function`关键字与函数名称之间添加`*`号，函数体内部使用`yield`（*[jild] n.产出，收益*）表达式定义不同的内部状态。

下面代码定义了一个 Generator 函数`myGenerator()`，其内部拥有`Hi`和`Generator`两个`yield`表达式，该函数共拥有`Hi`、`Generator`、`!`三个状态。与普通函数不同的是，Generator 函数被调用后并不立刻执行，返回的也并非函数执行结果，而是一个指向内部状态的遍历器对象（*Iterator Object*）。通过调用遍历器对象的`next()`方法，可以将执行流程移动至下一状态（*即接下来的`yield`表达式或`return`语句*）。换而言之，**Generator 函数是分段执行的，`yield`表达式是暂停执行的标记，而`next()`方法可以恢复执行**。

```js
function* myGenerator() {
  yield "Hi";
  yield "Generator";
  return "!";
}

let generator = myGenerator();

generator.next(); //{ value: 'Hi', done: false }
generator.next(); //{ value: 'Generator', done: false }
generator.next(); //{ value: '!', done: true }
generator.next(); //{ value: undefined, done: true }
```

每次调用遍历器对象的`next()`就会返回一个拥有`value`和`done`属性的对象，其中`value`属性表示当前内部状态的值（*即`yield`后面表达式的值*）；`done`属性是一个布尔值（*用来表示遍历是否结束*）。只有调用`next()`方法之后，对应`yield`关键字后的表达式才会被执行（*即惰性求值 Lazy Evaluation*）。

[![img](http://www.uinio.com/Web/Javascript/my-generator.gif)](http://www.uinio.com/Web/Javascript/my-generator.gif)

ES6 规范没有指定`function`关键字与函数名称之间星号`*`出现的位置，所以下面的写法都是等效的：

```js
function* demo(x, y) {
  // 星号靠左
}

function* demo(x, y) {
  // 星号靠右
}

function* demo(x, y) {
  // 星号居中
}

function* demo(x, y) {
  // 直接连接function关键字与函数名称
}
```

## 11.1、Generator 函数与 Iterator

Generator 函数返回的是遍历器对象，因此将其赋值给一个对象的`Symbol.iterator`属性，使该对象具备 Iterator 接口，从而能够通过`...`运算符进行遍历。

```js
let myIterator = {};

myIterator[Symbol.iterator] = function* () {
  yield "A";
  yield "B";
  yield "C";
  yield 1;
  yield 2;
  yield 3;
};

[...myIterator]; // ["A", "B", "C", 1, 2, 3]
```

Generator 函数执行后返回的遍历器对象本身就具有`Symbol.iterator`属性，执行后将会返回自身。

```js
function* generator() {
  // ...
}

/* 生成遍历器对象 */
let generated = generator();

/* 遍历器对象的Symbol.iterator属性调用后将会返回自身 */
generated[Symbol.iterator]() === generated; // true
```

# 十二、JavaScript DOM

## 12.1、DOM概述

当网页被加载时，浏览器会创建页面的文档对象模型（**D**ocument **O**bject **M**odel）。

HTML **DOM** 模型被结构化为 **对象树** ：

![image-20230724114356477](C:\Users\lenovo\AppData\Local\Temp\360zip$Temp\360)\Image\image-20230724114356477.png)

通过这个对象模型，JavaScript 获得创建动态 HTML 的所有力量：

* JavaScript 能改变页面中的所有 HTML 元素
* JavaScript 能改变页面中的所有 HTML 属性
* JavaScript 能改变页面中的所有 CSS 样式
* JavaScript 能删除已有的 HTML 元素和属性
* JavaScript 能添加新的 HTML 元素和属性
* JavaScript 能对页面中所有已有的 HTML 事件作出反应
* JavaScript 能在页面中创建新的 HTML 事件

## 12.2、DOM文档节点

### 12.2.1、节点概述

节点Node，是构成我们网页的最基本的组成部分，网页中的每一个部分都可以称为是一个节点。

比如：html标签、属性、文本、注释、整个文档等都是一个节点。

虽然都是节点，但是实际上它们的具体类型是不同的。

比如：标签我们称为元素节点、属性称为属性节点、文本称为 文本节点、文档称为文档节点。

节点的类型不同，属性和方法也都不尽相同。

节点：Node——构成HTML文档最基本的单元。

常用节点分为四类：

- 文档节点：整个HTML文档
- 元素节点：HTML文档中的HTML标签
- 属性节点：元素的属性
- 文本节点：HTML标签中的文本内容

![image-20230724114614645](.\Image\image-20230724114614645.png)

### 12.2.2、节点属性

![image-20230724114644043](Image\image-20230724114644043.png)

### 12.2.3、文档节点

文档节点（Document）代表的是整个HTML文 档，网页中的所有节点都是它的子节点。

document对象作为window对象的属性存在的，我们不用获取可以直接使用。

通过该对象我们可以在整个文档访问内查找节点对象，并可以通过该对象创建各种节点对象。

### 12.2.4、元素节点

HTML中的各种标签都是元素节点（Element），这也是我们最常用的一个节点。

浏览器会将页面中所有的标签都转换为一个元素节点， 我们可以通过document的方法来获取元素节点。

例如：`document.getElementById()`，根据id属性值获取一个元素节点对象。

### 12.2.5、属性节点

属性节点（Attribute）表示的是标签中的一个一个的属 性，这里要注意的是属性节点并非是元素节点的子节点，而是元素节点的一部分。可以通过元素节点来获取指定的属性节点。

例如：`元素节点.getAttributeNode("属性名")`，根据元素节点的属性名获取一个属性节点对象。

### 12.2.6、文本节点

文本节点（Text）表示的是HTML标签以外的文本内容，任意非HTML的文本都是文本节点，它包括可以字面解释的纯文本内容。文本节点一般是作为元素节点的子节点存在的。获取文本节点时，一般先要获取元素节点，在通过元素节点获取文本节点。

例如：元素节点.firstChild;，获取元素节点的第一个子节点，一般为文本节点。

## 12.3、DOM文档操作

文档对象代表您的网页,，如果您希望访问 HTML 页面中的任何元素，那么您总是从访问 document 对象开始。

下面是一些如何使用 document 对象来访问和操作 HTML 的实例。

### 12.3.1、查找 HTML 元素

| 方法                                    | 描述                        |
| --------------------------------------- | --------------------------- |
| document.getElementById(*id*)           | 通过元素 id 来查找元素。    |
| document.getElementsByTagName(*name*)   | 通过标签名来查找元素。      |
| document.getElementsByClassName(*name*) | 通过类名来查找元素。        |
| document.querySelector(*CSS选择器*)     | 通过CSS选择器选择一个元素。 |
| document.querySelectorAll(*CSS选择器*)  | 通过CSS选择器选择多个元素。 |

### 12.3.2、获取 HTML 的值

| **方法**                           | **描述**                      |
| ---------------------------------- | ----------------------------- |
| 元素节点.innerText                 | 获取 HTML 元素的 inner Text。 |
| 元素节点.innerHTML                 | 获取 HTML 元素的 inner HTML。 |
| 元素节点.属性                      | 获取 HTML 元素的属性值。      |
| 元素节点.getAttribute(*attribute*) | 获取 HTML 元素的属性值。      |
| 元素节点.style.样式                | 获取 HTML 元素的行内样式值。  |

### 12.3.3、改变 HTML 的值

| 方法                                        | 描述                         |
| ------------------------------------------- | ---------------------------- |
| 元素节点.innerText = *new text content*     | 改变元素的 inner Text。      |
| 元素节点.innerHTML = *new html content*     | 改变元素的 inner HTML。      |
| 元素节点.属性 = *new value*                 | 改变 HTML 元素的属性值。     |
| 元素节点.setAttribute(*attribute*, *value*) | 改变 HTML 元素的属性值。     |
| 元素节点.style.样式 = *new style*           | 改变 HTML 元素的行内样式值。 |

### 12.3.4、修改 HTML 元素

| 方法                                  | **描述**                           |
| ------------------------------------- | ---------------------------------- |
| document.createElement(*element*)     | 创建 HTML 元素节点。               |
| document.createAttribute(*attribute*) | 创建 HTML 属性节点。               |
| document.createTextNode(*text*)       | 创建 HTML 文本节点。               |
| 元素节点.removeChild(*element*)       | 删除 HTML 元素。                   |
| 元素节点.appendChild(*element*)       | 添加 HTML 元素。                   |
| 元素节点.replaceChild(*element*)      | 替换 HTML 元素。                   |
| 元素节点.insertBefore(*element*)      | 在指定的子节点前面插入新的子节点。 |

### 12.3.5、查找 HTML 父子

| 方法                            | 描述                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| 元素节点.parentNode             | 返回元素的父节点。                                           |
| 元素节点.parentElement          | 返回元素的父元素。                                           |
| 元素节点.childNodes             | 返回元素的一个子节点的数组（包含空白文本Text节点）。         |
| 元素节点.children               | 返回元素的一个子元素的集合（不包含空白文本Text节点）。       |
| 元素节点.firstChild             | 返回元素的第一个子节点（包含空白文本Text节点）。             |
| 元素节点.firstElementChild      | 返回元素的第一个子元素（不包含空白文本Text节点）。           |
| 元素节点.lastChild              | 返回元素的最后一个子节点（包含空白文本Text节点）。           |
| 元素节点.lastElementChild       | 返回元素的最后一个子元素（不包含空白文本Text节点）。         |
| 元素节点.previousSibling        | 返回某个元素紧接之前节点（包含空白文本Text节点）。           |
| 元素节点.previousElementSibling | 返回指定元素的前一个兄弟元素（相同节点树层中的前一个元素节点）。 |
| 元素节点.nextSibling            | 返回某个元素紧接之后节点（包含空白文本Text节点）。           |
| 元素节点.nextElementSibling     | 返回指定元素的后一个兄弟元素（相同节点树层中的下一个元素节点）。 |

## 12.4、DOM文档事件

### 12.4.1、事件概述

HTML事件可以触发浏览器中的行为，比方说当用户点击某个 HTML 元素时启动一段 JavaScript。

### 12.4.2、窗口事件

由窗口触发该事件 (同样适用于 \<body> 标签)：

| 属性      | 描述                                                         |
| --------- | ------------------------------------------------------------ |
| onblur    | 当窗口失去焦点时运行脚本。                                   |
| onfocus   | 当窗口获得焦点时运行脚本。                                   |
| onload    | 当文档加载之后运行脚本。                                     |
| onresize  | 当调整窗口大小时运行脚本。                                   |
| onstorage | 当 Web Storage 区域更新时（存储空间中的数据发生变化时）运行脚本。 |



# 十三、Windows API

详细内容可参考文档：[Window - Web API 接口参考 | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Web/API/Window)

## 13.1、`onresize`事件

onresize 事件会在窗口或框架被调整大小时发生，通过监听对象的高和宽，其中任何一个属性发生变化都会触发 onresize 事件。

> onresize响应事件处理中。获取到的页面尺寸參数是变更后的參数。

onresize事件在vue中的应用：

```vue
//vue页面
<template>
  <div id='echart'>
    报表
  </div>
</template>

<script>
  export default {
    data() {
      return {

      };
    },
    methods: {
      pageResize(){
        this.$nextTick(()=>{
          var echart = document.getElementById('echart');
          echart.style.height = document.documentElement.offsetHeight-220 + 'px'
        })
      }
    },
　　//挂载window.onresize事件
    mounted(){
      let _this = this;//赋值vue的this
      window.onresize = ()=>{
　　　　//调用methods中的事件
        _this.pageResize();
      }
    },
　　//注销window.onresize事件
    destroyed(){
      window.onresize = null;
    }
  }
</script>
<style lang="scss">
#echart{
  background-color: #fff;
  border-radius: 4px;
  padding: 20px;
  min-height: 400px;
}
</style>
```

注意事项：

- window.onresize事件一般放在**created**或者**mounted**生命周期中，这样界面改变时能触发。
- window.onresize中的this指向的是window，不是指向vue，如果需要调用methods中的函数，需要在window.onresize事件的前面把指向vue的this赋值给其他字符，比如"_this"。
- 由于window.onresize是全局事件，在其他页面改变界面时也会执行，这样可能会出现问题，需要在出这个界面时注销window.onresize事件。
- window.onresize说明一个问题：beforeCreate、created、beforeMount、mounted、beforeUpdate、updated中的会触发浏览器事件需要在destroyed、beforeDestory中销毁掉。

## 13.2、JavaScript屏幕宽高

### 13.2.1、屏幕

#### 13.2.1.1、屏幕尺寸

> 屏幕尺寸是屏幕的宽度和高度：显示器或移动屏幕。window.screen是保存屏幕尺寸信息的对象。

- **screen.width**：屏幕的宽。
- **screen.height**：屏幕的高。

![img](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1107d8d8506d47cd9f0dcc2c07f1a0d9~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

#### 13.2.1.2、可用屏幕尺寸

> 可用的屏幕大小由活动屏幕的宽度和高度组成，没有操作系统工具栏。

- **screen.availWidth**：可利用的宽，等于屏幕的宽。
- **screen.availHeight**：可利用的高，等于屏幕的高减去 mac 顶部栏或 windows 底部栏。

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/c2923c1ce69248f1ab6a02b5ad0c02d0~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

#### 13.2.1.3、屏幕距离

- **screenTop**：浏览器窗口左上角到屏幕上边缘的距离。
- **screenLeft**：浏览器窗口左上角到屏幕左边缘的距离。 `Firefox` 浏览器不支持上述属性，但是可以使用：
    - **screenX**：等于 screenLeft。
    - **screenY**：等于 screenTop。

![img](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/651192c54f874591bd8864cc5c62dd2a~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

### 13.2.2、windows窗口

#### 13.2.2.1、窗口外部尺寸

> 窗口的外部大小由整个浏览器窗口的宽度和高度组成，包含地址栏，选项卡栏和其他浏览器面板。

- window.outerWidth：浏览器窗口的宽。
- window.outerHeight：浏览器窗口的高。

![img](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/63dcd2ec483344b6b4658939538c44c5~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

> 1、 在Chrome和Opera中，当浏览器窗口全屏化时，`outerWidth`和`outerHeight`指的是可以看到的`浏览器部分`所占据的空间。
>
> 2、在FireFox、Safari、IE9和IE10中，当浏览器窗口全屏化时，`outerWidth`和`outerHeight`指的不仅是可以看到的浏览器所占据的空间，还包括其未显示部分。当浏览器窗口退出全屏化时，其四周会有8px的`边框`。而当浏览器窗口全屏化时，边框虽然未被显示，但仍然是计算在`outerWidth`和`outerHeight`内。
>
> 3、IE7、8不支持。

#### 13.2.2.2、窗口内部尺寸

> 窗口的内部大小（也称为视口大小）由显示网页的视口的宽度和高度组成，包含滚动条。

- **window.innerWidth**：视口的宽。
- **window.innerHeight**：视口的高。

![img](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/537ec6617dc24480869890c70c03a2a9~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

#### 13.2.2.3、客户区

> 元素的客户区大小（client dimension），指的是元素内容及其内边距所占据的空间大小

- **clientWidth**：内容可视区的宽度。
- **clientHeight**：内容可视区的高度。

![img](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a0e68083ce3d4a0cb3749ff590641fbf~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

> 1、如果有滚动条clientWidth = 元素宽 + padding（左右） - 滚动条
>
> 2、如果没有滚动条clientWidth = 元素宽 + padding（左右）
>
> 3、获取页面大小:let pageWidth = document.documentElement.clientWidth || document.body.clientWidth（ie7之前的版本）;



#### 13.2.2.4、网页大小

> 网页大小由呈现的页面内容的宽度和高度组成。

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8c40700cd4554305ad2ffdc6ecc76ad6~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

- **scrollWidth**：实际内容的宽度。没有垂直滚动条时与clientWidth相同。否则是等于实际内容的宽度 + padding。scrollWidth也包括 ::before 和 ::after这样的伪元素。
- **scrollHeight**：实际内容的高度。没有垂直滚动条时与clientHeight相同。否则是等于实际内容的高度 + padding。scrollHeight也包括 ::before 和 ::after这样的伪元素。

#### 13.2.2.5、**滚动距离**

- **scrollLeft**：元素最左端和窗口中可见内容的最左端之间的距离。即当前左滚的距离
- **scrollTop**：元素最顶端和窗口中可见内容的最顶端之间的距离。即当前上滚的距离

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/445b27b77fc440478e72b5f51cdbaeb3~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

> 1、如果有滚动条scrollLeft = 隐藏内容宽度 + border
> 2、如果没有滚动条scrollLeft = 0

#### 13.2.2.6、偏移量

> 偏移量包括元素在屏幕上占用的所有可见的空间。元素的可见大小由其高度、宽度决定，包括所有内边距、滚动条和边框大小（注意，不包括外边距）。

- **offsetHeight**：元素在垂直方向上占用的空间大小，包括元素的高度、（可见的） 水平滚动条的高度、上边框高度和下边框高度。
- **offsetWidth**：元素在水平方向上占用的空间大小。包括元素的宽度、（可见的）垂 直滚动条的宽度、左边框宽度和右边框宽度。
- **offsetLeft**：当前元素内容区域（包括border）左边缘到 offsetParent 内容区域（不包括border）左边缘的距离。
- **offsetTop**：当前元素内容区域（包括border）顶部到 offsetParent 内容区域（不包括border）顶部的距离。

![img](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/7bf95016785c43b5896fece6a22032cd~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

> offsetWidth = 元素宽 + padding（左右）+ border（左右）+ 滚动条宽度