# Fundamentals


## 如何Hello world

1. 输出到控制台
```js
console.log("Hello, world!\n");
```
2. 弹窗
```js
alert("Hello, world!\n");
```

## 基本数据类型
JavaScript 有7种原始数据类型

```number```：浮点数，JavaScript不区分整形和浮点型，数字均为十进制浮点数。

```string```：字符串类型。

```boolean```：布尔值，true和false。

```undefined```：未被赋值的变量的类型。

```null```：空类型。

```symbol```：独一无二且不可改变的类型。

```bigint```：大整数类型，赋值时在数字后加 n 。除法向下取整。

在JavaScript中值有类型，而变量没有，变量存储具有类型的值，因此我们可以把不同类型的值复制到一个变量里。

使用 ```typeof``` 运算符可知道一个变量的类型。
```js
let str = "suck"
console.log(typeof str);
```
输出：
```
string
```

## ```let```、```const``` 和 ```var```
```let``` 变量值可变。

```const``` 变量值不可变，且其必须被初始化。

```var``` 是定义变量的旧方法，尽量别用。其与 ```let``` 的区别在于： ```let``` 变量的生命周期是代码块，而 ```var``` 变量的生命周期是函数域内。

## 运算符

```==``` 和 ```===```：

前者会发生隐式转换然后比较其值，后者比较类型和值。

```js
let a = 123n; //bigint
let b = 123; //number

console.log(a == b);
console.log(a === b);
```
输出：
```
true
false
```

## 字符串
两种方法拼接字符串
```js
let str = "sunday";
console.log("Today is " + str + "!\n");
```
```js
let str = "sunday";
console.log(`Today is ${str}!\n`);
```

## 类型转换

### 显式转换

可直接使用函数转换。

注意，在 JavaScript 中非纯数字字符串转换为 ```number``` 类型，其值为 ```NaN```，而 ```NaN``` 类型为数字。
```js
console.log(Number("asd"));
console.log(typeof NaN);
```
输出：
```
NaN
number
```

### 隐式转换

此例中 ```21``` 被隐式转换成 ```string``` 类型。
```js
console.log("I am " + 21 + " years old.\n");
```

```string``` 之间可以用加号连接，而减号不行，因此字符串间的减法被隐式转换为数字间的减法。

```js
console.log("1234" + "123");
console.log("1234" - "123");
console.log(Number("1234") + Number("123"));

let n = '1' + 1;
n = n - 1;
console.log(n);

let m = '10' - '4' - '3' - 2 + '5'
console.log(m);
```
输出
```
1234123
1111
1357
10
15
```

## 布尔值
在 JavaScript 中如下几种值会被隐式转换成 ```false```
```js
Null
0
""
NaN
Undefined
```

## strict mode
strict 模式可以开启更严格的静态语法检查。（例如在 JavaScript 默认可以使用未声明变量，可能产生bug。开启 strict 模式后，禁止使用未声明变量。）

使用以下代码打开 strict 模式，其作用域为代码块。
```js
'use strict'；
```

## 函数
声明并定义函数
```js
function gcd(a, b) {
    return b? gcd(b, a % b) : a;
}
```

声明并定义函数的一种新方法（ES6），类似 lambda 表达式。
```js
const yearUntilRetirement = (personName, birthYeah) => {
    const age = new Date().getFullYear() - birthYeah;
    const retirement = 65 - age;
    return `${personName} retires in ${retirement} years.\n`;
}
```

## 数组
！**JavaScript 数组并不要求所存储元素是同一类型**

<a href = "https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array">MDN web doc Array</a>

### 声明并定义数组两种方法
```js
const obj1 = "Michael";
const obj2 = "Steve";
const obj3 = "Peter";

const arr1 = new Array(obj1, obj2, obj3);
const arr2 = [obj1, obj2, obj3];
```
### 基本操作
```js
arr.length; //注意这个不是函数
arr.push("bce"); //结尾加入
arr.pop(); //删除结尾
arr.unshift("234"); //开头加入
arr.shift(); //删除开头
arr.indexOf("Peter"); //查元素下标
arr.includes("john"); //查元素是否存在
```

## 对象
在 JavaScript 中，创建对象的最基本方法是
```js
const person = {
    firstName: "John",
    lastName: "Wick",
    age: 20,
    friends: [obj1, obj2, obj3],
    listFriends: function() {
        return this.friends;
    }
}
```
可以通过以下两种方法访问其成员，注意访问不存在成员返回 ```undefined```。
```js
console.log(person.firstName);

let str = "lastName";
console.log(person[str]); //方括号方法使用字符串访问成员
```
输出：
```
John
Wick
```