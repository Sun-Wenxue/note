# JavaScript

## 1 基本语法

### 1.1 数据类型和变量

#### Number

不区分整数和浮点数，NaN/Infinity

#### 字符串

' ' / " "

#### 布尔值

#### 比较运算符

==会自动转换数据类型

===不会

isNaN

#### BitInt

BigInt() >2^53

不能和Number四则运算

#### null和undefined

空/未定义（参数传递时用）

#### 数组

[ ,  ] / new Array

索引从0开始

元素类型可以不同

#### 对象

键值对组成的无序集合

var/let name = {key: value, key: value};

#### 变量

var 任意类型，命名可有$和_

#### strict模式

'use strict' 强制变量申明

### 1.2 字符串

' ' / " " / \` \`

转义符\

ES6标准反引号可以换行

#### 模板字符串

串联字符可以用加号+

可以用模板

```javascript
`${var}`
```

#### 操作字符串

长度 s.length

索引 s[0]

常量不可赋值

大写 s.toUpperCase()

小写 s.toLowerCase()

搜索字符串出现的位置 s.indexOf()

指定区间，一个参数则默认到结束 s.subString()

### 1.3 数组

长度 arr.length()

可以通过索引修改，越界部分undefined

搜索元素出现的位置 arr.indexOf()

指定区间，一个参数则默认到结束 arr.slice()

末尾增删 arr.push()/arr.pop()

头部增删 arr.unshift()/arr.shift()

排序/翻转 arr.sort()/arr.reverse()

从指定位置删除/添加 arr.splice(索引，删除个数，添加元素1，添加元素2

数组拼接 arr.concat(arr1)

字符串数组以指定连接符拼接 arr.join(' ')

多维数组[[1,2,3], [4,5,6]]

### 1.4 对象

var/let name = {key1: value1, key2: value2};

添加属性 name.key2=value3;

删除属性 delete name.key/name['key']

检查属性是否存在 'key' in name

排除继承的属性，检查属性存在 name.hasOwnProperty

### 1.5 条件判断

if/else

### 1.6 循环

for

(do)while

### 1.7 Map和Set

let m = new Map([ [key, value], [key, value]])

```js
let m = new Map(); // 空Map
m.set('Adam', 67); // 添加新的key-value
m.set('Bob', 59);
m.has('Adam'); // 是否存在key 'Adam': true
m.get('Adam'); // 67
m.delete('Adam'); // 删除key 'Adam'
m.get('Adam'); // undefined
```

let s = new Set([1,2,3]) 一组不重复key的集合 添加/删除 s.add()/s.delete()

#### 1.8 iterable

for(let x of a)

Array, Set, Map都可以用

forEach()

```
let a = ['A', 'B', 'C'];
a.forEach(function (element, index, array) {
    // element: 指向当前元素的值
    // index: 指向当前索引
    // array: 指向Array对象本身
    console.log(`${element}, index = ${index}`);
});
```

## 2 函数

### 2.1 定义

```
function name(x)={}
let val = function (x) {};
```

arguments在函数内部指向所有传入的参数，类似Array

...rest多余的参数

### 2.2 变量作用域与解构赋值

变量提升：先扫描整个函数体的语句，把所有用var申明的变量提升到函数顶部，因此在函数内部首先申明所有变量

全局作用域：不在函数内定义的变量是全局作用域，window是最顶层的函数

名字空间：全局变量绑定到window上，不同js文件使用相同全局变量会造成命名冲突，可以把所有变量和函数绑定到一个唯一的全局变量中

局部作用域：只有函数内部可以定义局部变量，let可以定义块级作用域的变量

常量：const，也是块级作用域

解构赋值：

```
// 数组
let [ ,y,z] = ['hello','js','es6']; 
// 对象
{name, address:{city}} = person;
```

对已经申明的变量解构赋值报错，用小括号括起来

### 2.3 方法

绑定到对象上的函数

方法内部有一个指向当前对象的this关键字

单独调用方法，this指向window（解决方案：strict）

方法里面的函数指向window，strict模式指向undefined（解决方案：捕获this）

apply/call修复this指向

装饰器：利用apply改变函数行为

### 2.4 高阶函数

一个函数接收另一个函数作为参数

##### 2.4.1 map/reduce

映射

arr.map(函数对象)

累积

```
[x1,x2,x3,x4].reduce(f)=f(f(f(x1,x2),x3),x4);
```

##### 2.4.2 filter

映射，然后过滤删掉一部分

回调函数

##### 2.4.3 sort

把所有元素

转换为string再排序

是高阶函数，支持自定义排序

##### 2.4.4 其他Array函数

every

find

findIndex

forEach

### 2.5 闭包

函数作为返回值

返回函数最好不啊哟引用任何循环变量或者后续会发生变化的量

一定要用嵌套一个绑定循环当前变量的函数

或用let定义块级变量

作用：封装私有变量