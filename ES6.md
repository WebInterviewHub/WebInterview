## ES6

* [1.es5和es6的区别，说一下你所知道的es6](#1es5和es6的区别说一下你所知道的es6)
* [2.var、let、const之间的区别](#2varletconst之间的区别)
* [3.使用箭头函数应注意什么？](#3使用箭头函数应注意什么)
* [4.ES6的模板字符串有哪些新特性？并实现一个类模板字符串的功能](#4es6的模板字符串有哪些新特性并实现一个类模板字符串的功能)
* [5.介绍下 Set、Map的区别？](#5介绍下-setmap的区别)
* [6.ECMAScript 6 怎么写 class ，为何会出现 class？](#6ecmascript-6-怎么写-class-为何会出现-class)
* [7.Promise构造函数是同步执行还是异步执行，那么 then 方法呢？](#7promise构造函数是同步执行还是异步执行那么-then-方法呢)
* [8.setTimeout、Promise、Async/Await 的区别](#8settimeoutpromiseasyncawait-的区别)
* [9.promise有几种状态，什么时候会进入catch？](#9promise有几种状态什么时候会进入catch)
* [10.使用结构赋值，实现两个变量的值的交换](#10使用结构赋值实现两个变量的值的交换)
* [11.Promise 中reject 和 catch 处理上有什么区别](#11promise-中reject-和-catch-处理上有什么区别)
* [12.理解 async/await以及对Generator的优势](#12理解-asyncawait以及对generator的优势)
* [参考资料](#参考资料)



#### 1.es5和es6的区别，说一下你所知道的es6

ECMAScript5，即ES5，是ECMAScript的第五次修订，于2009年完成标准化ECMAScript6，即ES6，是ECMAScript的第六次修订，于2015年完成，也称ES2015ES6是继ES5之后的一次改进，相对于ES5更加简洁，提高了开发效率ES6新增的一些特性：
1）let声明变量和const声明常量，两个都有块级作用域ES5中是没有块级作用域的，并且var有变量提升，在let中，使用的变量一定要进行声明
2）箭头函数ES6中的函数定义不再使用关键字function()，而是利用了()=>来进行定义
3）模板字符串模板字符串是增强版的字符串，用反引号标识，可以当作普通字符串使用，也可以用来定义多行字符串
4）解构赋值ES6 允许按照一定模式，从数组和对象中提取值，对变量进行赋值
5）for of循环for...of循环可以遍历数组、Set和Map结构、某些类似数组的对象、对象，以及字符串
6）import、export导入导出ES6标准中，Js原生支持模块(module)。将JS代码分割成不同功能的小块进行模块化，将不同功能的代码分别写在不同文件中，各模块只需导出公共接口部分，然后通过模块的导入的方式可以在其他地方使用
7）set数据结构Set数据结构，类似数组。所有的数据都是唯一的，没有重复的值。它本身是一个构造函数
8）... 展开运算符可以将数组或对象里面的值展开；还可以将多个值收集为一个变量
9）修饰器 @decorator是一个函数，用来修改类甚至于是方法的行为。修饰器本质就是编译时执行的函数
10）class 类的继承ES6中不再像ES5一样使用原型链实现继承，而是引入Class这个概念11）async、await使用 async/await, 搭配promise,可以通过编写形似同步的代码来处理异步流程, 提高代码的简洁性和可读性async 用于申明一个 function 是异步的，而 await 用于等待一个异步方法执行完成
12）promisePromise是异步编程的一种解决方案，比传统的解决方案（回调函数和事件）更合理、强大
13）SymbolSymbol是一种基本类型。Symbol 通过调用symbol函数产生，它接收一个可选的名字参数，该函数返回的symbol是唯一的
14）Proxy代理使用代理（Proxy）监听对象的操作，然后可以做一些相应事情

#### 2.var、let、const之间的区别

var声明变量可以重复声明，而let不可以重复声明
var是不受限于块级的，而let是受限于块级
var会与window相映射（会挂一个属性），而let不与window相映射
var可以在声明的上面访问变量，而let有暂存死区，在声明的上面访问变量会报错
const声明之后必须赋值，否则会报错
const定义不可变的量，改变了就会报错
const和let一样不会与window相映射、支持块级作用域、在声明的上面访问变量会报错

#### 3.使用箭头函数应注意什么？

（1）用了箭头函数，this就不是指向window，而是父级（指向是可变的）
（2）不能够使用arguments对象
（3）不能用作构造函数，这就是说不能够使用new命令，否则会抛出一个错误
（4）不可以使用yield命令，因此箭头函数不能用作 Generator 函数

#### 4.ES6的模板字符串有哪些新特性？并实现一个类模板字符串的功能

基本的字符串格式化。
将表达式嵌入字符串中进行拼接。
用${}来界定在ES5时我们通过反斜杠()来做多行字符串或者字符串一行行拼接。
ES6反引号就能解决类模板字符串的功能

```
let name = 'web';
let age = 10;
let str = '你好，${name} 已经 ${age}岁了'
str = str.replace(/\$\{([^}]*)\}/g,function(){
     return eval(arguments[1]);
   })
console.log(str);//你好，web 已经 10岁了

```

#### 5.介绍下 Set、Map的区别？

应用场景：Set用于数据重组，Map用于数据储存
Set：　
（1）成员不能重复
（2）只有键值没有键名，类似数组
（3）可以遍历，方法有add, delete,has
Map:
（1）本质上是健值对的集合，类似集合
（2）可以遍历，可以跟各种数据格式转换

#### 6.ECMAScript 6 怎么写 class ，为何会出现 class？

ES6的class可以看作是一个语法糖，它的绝大部分功能ES5都可以做到，新的class写法只是让对象原型的写法更加清晰、更像面向对象编程的语法。

```
//定义类
class Point { 
  constructor(x,y) { 
      //构造方法
       this.x = x; //this关键字代表实例对象
       this.y = y; 
  } toString() {
       return '(' + this.x + ',' + this.y + ')'; 
  }
}

```

#### 7.Promise构造函数是同步执行还是异步执行，那么 then 方法呢？

promise构造函数是同步执行的，then方法是异步执行的

#### 8.setTimeout、Promise、Async/Await 的区别

事件循环中分为宏任务队列和微任务队列
其中setTimeout的回调函数放到宏任务队列里，等到执行栈清空以后执行promise.then里的回调函数会放到相应宏任务的微任务队列里，等宏任务里面的同步代码执行完再执行async函数表示函数里面可能会有异步方法，await后面跟一个表达式
async方法执行时，遇到await会立即执行表达式，然后把表达式后面的代码放到微任务队列里，让出执行栈让同步代码先执行

#### 9.promise有几种状态，什么时候会进入catch？

三个状态：
pending、fulfilled、reject
两个过程：
padding -> fulfilled、padding -> rejected当pending为rejectd时，会进入catch

#### 10.使用结构赋值，实现两个变量的值的交换

```
let a = 1;let b = 2;
[a,b] = [b,a];
```

#### 11.Promise 中reject 和 catch 处理上有什么区别

reject 是用来抛出异常，catch 是用来处理异常
reject 是 Promise 的方法，而 catch 是 Promise 实例的方法
reject后的东西，一定会进入then中的第二个回调，如果then中没有写第二个回调，则进入catch
网络异常（比如断网），会直接进入catch而不会进入then的第二个回调

#### 12.理解 async/await以及对Generator的优势

async await 是用来解决异步的，async函数是Generator函数的语法糖
使用关键字async来表示，在函数内部使用 await 来表示异步
async函数返回一个 Promise 对象，可以使用then方法添加回调函数
当函数执行的时候，一旦遇到await就会先返回，等到异步操作完成，再接着执行函数体内后面的语句
async较Generator的优势：
（1）内置执行器。Generator 函数的执行必须依靠执行器，而 Aysnc 函数自带执行器，调用方式跟普通函数的调用一样
（2）更好的语义。async 和 await 相较于 * 和 yield 更加语义化　　
（3）更广的适用性。yield命令后面只能是 Thunk 函数或 Promise对象，async函数的await后面可以是Promise也可以是原始类型的值
（4）返回值是 Promise。async 函数返回的是 Promise 对象，比Generator函数返回的Iterator对象方便，可以直接使用 then() 方法进行调用

#### 参考资料

https://zhuanlan.zhihu.com/p/102442557
