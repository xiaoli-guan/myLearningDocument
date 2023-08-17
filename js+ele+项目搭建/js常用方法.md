<h1><center>js常用方法</center></h1>

# 一、Array

## 1、includes

includes()方法用来判断一个数组是否包含一个指定的值，如果是返回 true，否则false。

`includes（searchElement，fromIndex）`

| *searchElement* | 必须。需要查找的元素值。                                     |
| --------------- | ------------------------------------------------------------ |
| *fromIndex*     | 可选。从该索引处开始查找 searchElement。如果为负值，则按升序从 array.length + fromIndex 的索引开始搜索。默认为 0。 |

```js
var arr = [10,20,30,40,50];
arr.includes(10); //true
arr.includes(10,1); //false
--------------------------------
var arr = [1,2,3,4];
arr.includes(1,-1); //false
arr.includes(2,-4); //true
```

# 二、JSON

## 1、parse和stringify

```js
//将json字符串转对象
JSON.parse(jsonString)
//将对象转json字符串
JSON.stringify(obj)
```

例子：

```js
//数组深拷贝
arr = JSON.parse(JSON.stringify(arr));
```

> 将数组转json字符串再转回数组，是深拷贝，而且没有原型链

# 三、Set

```js
let s = new Set();//声明
s.add(item);
```



# 四、Map

```js
let m = new Map();
m.set(key,value);
```

