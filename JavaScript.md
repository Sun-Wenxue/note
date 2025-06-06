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

unicode str.charCodeAt(i)

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

创建指定大小 Array(length)

用同一个值填充arr.fill(val)

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

func.apply(对象, arguments)将其他对象的方法func应用到当前对象



### 2.4 高阶函数

一个函数接收另一个函数作为参数

```js
function add(x, y, f) {
    return f(x) + f(y);
}
```

##### 2.4.1 map/reduce

映射

arr.map(函数对象f)

累积

```
[x1,x2,x3,x4].reduce(f)=f(f(f(x1,x2),x3),x4);
```

##### 2.4.2 filter

映射，然后过滤删掉一部分

回调函数

##### 2.4.3 sort

把所有元素转换为string再排序

是高阶函数，支持自定义排序l

```
arr.sort(f)
```

##### 2.4.4 其他Array函数

every

find

findIndex

forEach

### 2.5 闭包

函数作为返回值

```js
function lazy_sum(arr) {
    let sum = function () {
        return arr.reduce(function (x, y) {
            return x + y;
        });
    }
    return sum;
}

let f = lazy_sum([1, 2, 3, 4, 5]);
f();
```

返回函数最好不引用任何循环变量或者后续会发生变化的量

一定要用嵌套一个绑定循环当前变量的函数

或用let定义块级变量

作用：封装私有变量

### 2.6 箭头函数

```js
x => x*x;
```

```js
(x,y) => {
    if(x>0) return x*x+y*y;
    else return -x*x-y*y*;
}
```

相当于一个匿名函数

可以修复方法的this指向问题（？）

### 2.7 标签函数

数据库调用，方便

```js
const email = "test@example.com";
const password = 'hello123';

function sql(strings, ...exps) {
    console.log(`SQL: ${strings.join('?')}`);
    console.log(`SQL parameters: ${JSON.stringify(exps)}`);
    return {
        name: '小明',
        age: 20
    };
}

const result = sql`SELECT * FROM users WHERE email=${email} AND password=${password}`;

console.log(JSON.stringify(result));

```

### 2.8 生成器

可以多次返回的函数

```js
function* fib(max) {
    let
        a = 0,
        b = 1,
        n = 0;
    while (n < max) {
        yield a;
        [a, b] = [b, a + b];
        n ++;
    }
    return;
}

for (let x of fib(10)) {
    console.log(x); // 依次输出0, 1, 1, 2, 3, ...
}
```

## 3 标准对象

typeof 对象类型

```js
typeof 123; // 'number'
typeof 123n; // 'bigint'
typeof NaN; // 'number'
typeof 'str'; // 'string'
typeof true; // 'boolean'
typeof undefined; // 'undefined'
typeof Math.abs; // 'function'
typeof null; // 'object'
typeof []; // 'object'
typeof {}; // 'object'

```

包装对象

```js
let n = new Number(123); // 123,生成了新的包装类型
let b = new Boolean(true); // true,生成了新的包装类型
let s = new String('str'); // 'str',生成了新的包装类型
```

闲的蛋疼也不要使用包装对象

### 3.1 Date

```js
let now = new Date();
now; // Wed Jun 24 2015 19:49:22 GMT+0800 (CST)
now.getFullYear(); // 2015, 年份
now.getMonth(); // 5, 月份，注意月份范围是0~11，5表示六月
now.getDate(); // 24, 表示24号
now.getDay(); // 3, 表示星期三
now.getHours(); // 19, 24小时制
now.getMinutes(); // 49, 分钟
now.getSeconds(); // 22, 秒
now.getMilliseconds(); // 875, 毫秒数
now.getTime(); // 1435146562875, 以number形式表示的时间戳

let d = new Date(2015, 5, 19, 20, 15, 30, 123);
console.log(d); // Fri Jun 19 2015 20:15:30 GMT+0800 (CST)

let d = Date.parse('2015-06-24T19:49:22.875+08:00');
console.log(d); // 1435146562875

let d = new Date(1435146562875);
d; // Wed Jun 24 2015 19:49:22 GMT+0800 (CST)
d.getMonth(); // 5

let d = new Date(1435146562875);
d.toLocaleString(); // '2015/6/24 下午7:49:22'，本地时间（北京时区+8:00），显示的字符串与操作系统设定的格式有关
d.toUTCString(); // 'Wed, 24 Jun 2015 11:49:22 GMT'，UTC时间，与本地时间相差8小时
```

## 3.2 RegExp

\d数字 \w字母 *任意字符 +至少一个字符 ?0或1个字符 {n}n个字符 {n,m}n-m个字符

[0-9a-zA-Z\_]数字，字母或下划线

A|B A或B

^行的开头 $行的结束



构造正则表达式

```
let re1 = /ABC\-001/;
let re2 = new RegExp('ABC\\-001');

re1; // /ABC\-001/
re2; // /ABC\-001/

re.test(' '); 检查是否匹配
```



切分字符串.split()

分组.exec()

贪婪匹配默认，非贪婪匹配?

全局搜索

### 3.3 JSON

数据交换格式

## 4 面向对象编程

通过原型实现面向对象

```js
obj._proto_ = obj;
obj = Object.create(obj);
```

### 4.1 创建对象

构造函数+new

```js
function Student(name) {
    this.name = name;
    this.hello = function () {
        alert('Hello, ' + this.name + '!');
    }
}

let xiaoming = new Student('小明');
xiaoming.name; // '小明'
xiaoming.hello(); // Hello, 小明!
```

共享原型函数

```js
function Student(name) {
    this.name = name;
}

Student.prototype.hello = function () {
    alert('Hello, ' + this.name + '!');
};
```

Getter和Setter

```JS
let user = {
  name: "John",
  surname: "Smith"
};

Object.defineProperty(user, 'fullName', {
  get() {
    return `${this.name} ${this.surname}`;
  },

  set(value) {
    [this.name, this.surname] = value.split(" ");
  }
});
```



```JS
let user = {
  get name() {
    return this._name;
  },

  set name(value) {
    if (value.length < 4) {
      alert("Name is too short, need at least 4 characters");
      return;
    }
    this._name = value;
  }
};

user.name = "Pete";
alert(user.name); // Pete

user.name = ""; // Name 太短了……
```



### 4.2 原型继承

call

需要空函数

### 4.3 class继承

比原型继承简单

```js
class Student {
    constructor(name) {
        this.name = name;
    }

    hello() {
        alert('Hello, ' + this.name + '!');
    }
}

class PrimaryStudent extends Student {
    constructor(name, grade) {
        super(name); // 记得用super调用父类的构造方法!
        this.grade = grade;
    }

    myGrade() {
        alert('I am at grade ' + this.grade);
    }
}
```

## 5 浏览器

### 5.1 浏览器对象

window 浏览器窗口

navigator 浏览器的信息

screen 屏幕的信息

location 页面URL信息

```js
location.protocol; // 'http'
location.host; // 'www.example.com'
location.port; // '8080'
location.pathname; // '/path/index.html'
location.search; // '?a=1&b=2'
location.hash; // 'TOP'
```

document 当前页面 DOM树的根节点

`getElementById()`和`getElementsByTagName()`可以按ID获得一个DOM节点和按Tag名称获得一组DOM节点：

history 浏览器的历史记录

### 5.2 操作DOM

HTML文档被浏览器解析为DOM树，通过JS改变DOM树结构

更新，遍历，添加，删除

### 5.3 操作表单

获取值

设置值

提交表单

### 5.4 操作文件

```
<input type="file">
```

### 5.5 AJAX

执行异步网络请求，通过回调函数获得响应

Fetch API

### 5.6 Promise

承诺将来会执行的对象

### 5.7 asynch函数

asynch function

内部用await

异步，和promise一样

### 5.8 Canvas

绘制图表和动画

## 6 错误处理

当代码块被try { ... }包裹的时候，就表示这部分代码执行过程中可能会发生错误，一旦发生错误，就不再继续执行后续代码，转而跳到catch块。catch (e) { ... }包裹的代码就是错误处理代码，变量e表示捕获到的错误。最后，无论有没有错误，finally一定会被执行。

```js
try {
    ...
} catch (e) {
    ...
} finally {
    ...
}
```

抛出错误

```js
throw new Error('输入错误');
```

### 6.1 错误传播

没有捕获的错误会被抛到外层调用函数。

### 6.2 异步错误处理

代码总是单线程执行

异步错误无法在调用时捕获

## 7 DOM事件

### 7.1 DOM 0级事件

```
el.onclick = function(){}
// 例
var btn = document.getElementById('btn');
    btn.onclick = function(){
        alert(this.innerHTML)
    }
```

同一个元素不能绑定多个同类型事件。

DOM0事件绑定给元素的事件行为绑定方法，这些方法在当前元素事件行为的冒泡阶段或者目标阶段执行

## 8 常用函数

Math.random()

Math.ceil/floor(num)

iterator.every(x=>x>10)检查元素是否都满足某个条件

## 9 其它补充

### Proxy

内置对象，用于创建一个对象的代理，从而可以**拦截并自定义该对象的基本操作**（如属性查找、赋值、枚举、函数调用等）。

核心概念：

代理（Proxy）：包装目标对象的新对象，拦截对目标对象的操作。
处理程序（Handler）：定义拦截行为的对象，包含多个 “陷阱”（trap）方法。
陷阱（Trap）：拦截特定操作的方法（如 get、set、has 等）。

基本语法：

```JS
const proxy = new Proxy(target, handler);
```

- **`target`**：被代理的原始对象。
- **`handler`**：包含陷阱方法的对象，用于自定义操作行为。

常用方法：

| 陷阱方法                             | 拦截的操作                           |
| ------------------------------------ | ------------------------------------ |
| `get(target, prop, receiver)`        | 读取属性值（如 `obj.key`）           |
| `set(target, prop, value, receiver)` | 设置属性值（如 `obj.key = value`）   |
| `has(target, prop)`                  | 判断属性是否存在（如 `key in obj`）  |
| `deleteProperty(target, prop)`       | 删除属性（如 `delete obj.key`）      |
| `ownKeys(target)`                    | 获取所有属性名（如 `Object.keys()`） |
| `apply(target, thisArg, args)`       | 调用函数（如 `func()`）              |
| `construct(target, args)`            | 使用 `new` 实例化对象                |

### Object.defineProperty

确控制对象属性的底层方法。它允许你直接为对象添加或修改属性，并精确配置这些属性的行为（如可读写性、可枚举性、可配置性等）。

基本语法

```
Object.defineProperty(obj, prop, descriptor);
```

- **`obj`**：需要定义属性的目标对象。
- **`prop`**：需要定义或修改的属性名称（字符串或 Symbol）。
- **`descriptor`**：属性描述符对象，定义属性的配置。