## html和css部分

### 1. 如何理解CSS盒子模型

标准盒子模型：宽度=内容的宽度（content）+ border + padding

低版本IE盒子模型：宽度=内容宽度（content+border+padding）

### 2.BFC

```html
* 什么是 BFC

   BFC（Block Formatting Context）格式化上下文，是 Web 页面中盒模型布局的 CSS 渲染模式，指一个独立的渲染区域或者说是一个隔离的独立容器。
* 形成 BFC 的条件

   * 浮动元素，float 除 none 以外的值
   * 定位元素，position（absolute，fixed）
   * display 为以下其中之一的值 inline-block，table-cell，table-caption
   * overflow 除了 visible 以外的值（hidden，auto，scroll）
* BFC 的特性
   * 内部的 Box 会在垂直方向上一个接一个的放置。
   * 垂直方向上的距离由 margin 决定
   * bfc 的区域不会与 float 的元素区域重叠。
   * 计算 bfc 的高度时，浮动元素也参与计算
   * bfc 就是页面上的一个独立容器，容器里面的子元素不会影响外面元素。
```

### 3.标签语义化

代码结构更加清晰

见名知意，没有基础的人也能知道这部分代码是干嘛的

方便团队开发维护，代码可读性更强

有利于SEO优化，爬虫依赖于标签来确定上下文关系

### 4.meta标签

meta标签提供关于html文档的元数据，不会显示在页面，但是对于机器是可读的，告诉浏览器怎么解析页面，告诉搜索引擎关键字（SEO优化）

meta作用：告诉机器浏览器该如何解析该页面，描述这个页面的主要内容，可以设置服务器发送到浏览器的http头部内容

charset="utf-8"设置页面使用的字符编码

viewport 设置视口，移动端的适配

### 5.css与javascript引入设置

script标签的引入一般放在body最后，这样避免脚本过大，加载时间长，导致页面长时间空白，这是因为渲染进程与js进程是互斥的，脚本会阻塞页面的渲染，脚本之间的加载是同步进行的，按引入顺序执行，但是以下两个属性会影响脚本执行与页面渲染的顺序

defer：不会阻塞渲染，这样即使放在header内部，也不会阻塞页面加载，不过js会先于document加载完成，并且也不会影响脚本之间的执行顺序，按照引入顺序执行

async：与defer一样，都是解决阻塞渲染，但它是在document加载完成后才执行，并且它的执行顺序是按照谁先加载完成执行谁，所以对于文件顺序有要求，存在前后依赖的不要使用它

### 6.HTML的块级元素，行内元素，行内块元素有哪些,区别是什么

块级元素：div，h1-h6，p，ul，ol，dl，li，hr，dt，dd，form，table

块元素独占一行
宽高生效
默认宽和父元素一样，内容撑开高度
margin，padding全部生效


行内元素：em，i，del，small，strong，ins，span，a

宽高不生效
左右margin生效上下不生效
在一行排列
大小靠内容撑开
padding都生效


行内块元素：img，input(表单元素，除去form)

在一行排列
宽高生效
margin，padding生效

### 7.CSS3有哪些新特性

border-radius圆角

border-image 边框图片

border-image: url() top right bottom left

border-width: top right bottom left

box-shadow盒子阴影: x,y,size,opcity

text-shadow文字阴影

linear-gradient 线性渐变

background: linear-gradient(to position , color,color,...,color)

radial-gradient 径向渐变

background: radial-gradient(shap size at position , color,color,...,color)

2D/3D转换 transform：rotate(旋转) scale(缩放) translate(位移)
@media媒体查询，根据屏幕宽度，设置，用来解决移动端适配,根据屏幕大小使相应的css生效
flex布局(弹性盒子)

### ８.实现元素隐藏

display：none 不占位，源码可见

opacity: 0 占位，源码可见，透明度0

visibility: hidden 占位，源码可见

position: top:-9999px,left:-9999px 利用定位将元素移出视窗

### 9.如何实现元素水平居中

行内元素：text-align：center

块元素: margin: 0 auto

position: left: 50%; transform: translate(-50%)

### 10.如何实现元素垂直居中

height = line-height

verticle-align: middle

position: top: 50%; transform: translate(0,-50%)

### 11.Position

static 默认

relative 相对定位，不脱标，相对于自身位置进行偏离，不影响元素本身特性，z-index提升层级

absolute 绝对定位，脱标，相对于已有定位的父元素进行偏离，都没有就相对于body进行偏离

fixed 固定定位，脱标，相对于视窗进行偏离

### 12.定位元素水平垂直居中

宽高固定 position: top:0,left:0,right:0,bottom:0,margin:auto

宽高固定 position：top: 50%, left: 50%, margin-left: -width/2px,margin-top: -height/2px

dispaly: flex; justify-content: center,align-items: center(极力推荐)

position: left: 50%,top: 50%; transform: translate(-50%,-50%)

### 13.清除浮动

```
不清楚浮动会发生高度塌陷：浮动元素父元素高度自适应（父元素不写高度时，子元素写了浮动后，父元素会发生高度塌陷）
* clear清除浮动（添加空div法）在浮动元素下方添加空div,并给该元素写css样式：   {clear:both;height:0;overflow:hidden;}
* 给浮动元素父级设置高度
* 父级同时浮动（需要给父级同级元素添加浮动）
* 父级设置成inline-block，其margin: 0 auto居中方式失效
* 给父级添加overflow:hidden 清除浮动方法
* 万能清除法 after伪类 清浮动（现在主流方法，推荐使用）

.float_div:after{
	content:".";
	clear:both;
	display:block;
	height:0;
	overflow:hidden;
	visibility:hidden;
}
.float_div{
	zoom:1
} 

```

### 14.css选择器有哪些，选择器的优先级

- id选择器
- 类选择器
- 属性选择器
- 伪类选择器
- 标签选择器
- 伪元素选择器
- 通配符选择器


优先级：内联样式 > ID选择器(100)> 类选择器(10) = 属性选择器 = 伪类选择器 > 元素选择器(1) = 关系选择器 = 伪元素选择器 > 通配符选择器(0)
!important
后代选择器选全部
子代选择器只选亲孩子

### 15.各种布局优缺点

1. float 布局
   优点： 比较简单，兼容性也比较好。只要清除浮动做的好，是没有什么问题的缺点：浮动元素是脱离文档流，要做清除浮动，这个处理不好的话，会带来很多问题，比如高度塌陷等。
2. 绝对布局
   优点：很快捷，设置很方便，而且也不容易出问题缺点：绝对定位是脱离文档流的，意味着下面的所有子元素也会脱离文档流，这就导致了这种方法的有效性和可使用性是比较差的。
3. flex 布局
   优点：简单快捷缺点：不支持 IE8 及以下
4. table布局
   优点：实现简单，代码少缺点：当其中一个单元格高度超出的时候，两侧的单元格也是会跟着一起变高的，而有时候这种效果不是我们想要的。
5. grid布局
   跟 flex 相似。



## JS 基础

### 1.什么是闭包

能够读取其他函数内部变量的函数。
或简单理解为定义在一个函数内部的函数，内部函数持有外部函数内变量的引用。

### 2.闭包的用途

1、读取函数内部的变量

2、让这些变量的值始终保持在内存中。不会再f1调用后被自动清除。

3、方便调用上下文的局部变量。利于代码封装。

原因：f1是f2的父函数，f2被赋给了一个全局变量，f2始终存在内存中，f2的存在依赖f1，因此f1也始终存在内存中，不会在调用结束后，被垃圾回收机制回收。

### 3.闭包的缺点

1、由于闭包会使得函数中的变量都被保存在内存中，内存消耗很大，所以不能滥用闭包，否则会造成网页的性能问题，在IE中可能导致内存泄露。解决方法是，在退出函数之前，将不使用的局部变量全部删除。

2、闭包会在父函数外部，改变父函数内部变量的值。所以，如果你把父函数当作对象（object）使用，把闭包当作它的公用方法（Public Method），把内部变量当作它的私有属性（private value），这时一定要小心，不要随便改变父函数内部变量的值。

### 4.闭包实用场景
https://juejin.cn/post/6844903619595075592

### 5. JS 有哪些数据类型？
根据 JavaScript 中的变量类型传递方式，分为基本数据类型和引用数据类型两大类七种。
基本数据类型包括Undefined、Null、Boolean、Number、String、Symbol (ES6新增)六种。

引用数据类型只有Object一种，主要包括对象、数组和函数。
判断数据类型采用typeof操作符，有两种语法：
```javascript
typeof 123;//语法一

const FG = 123;
typeof FG;//语法二

typeof(null) //返回 object;
null == undefined //返回true，因为undefined派生自null;
null === undefined //返回false。
```


### 6.基本数据类型和引用数据类型有什么区别？
（1）两者作为函数的参数进行传递时：
        基本数据类型传入的是数据的副本，原数据的更改不会影响传入后的数据。
        引用数据类型传入的是数据的引用地址，原数据的更改会影响传入后的数据。
        
（2）两者在内存中的存储位置：
        基本数据类型存储在栈中。
        引用数据类型在栈中存储了指针，该指针指向的数据实体存储在堆中。

### 7.判断数据类型的方法有哪些？
（1）利用typeof可以判断数据的类型；
    （2）A instanceof B可以用来判断A是否为B的实例，但它不能检测 null 和 undefined；
    （3）B.constructor == A可以判断A是否为B的原型，但constructor检测 Object与instanceof不一样，还可以处理基本数据类型的检测。

```
不过函数的 constructor 是不稳定的，这个主要体现在把类的原型进行重写，在重写的过程中很有可能出现把之前的constructor给覆盖了，这样检测出来的结果就是不准确的。
```
（4）Object.prototype.toString.call()
```
Object.prototype.toString.call() 是最准确最常用的方式。

```

### 8.与深拷贝有何区别？如何实现？
浅拷贝只复制指向某个对象的指针，而不复制对象本身。浅拷贝的实现方式有：
        （1）Object.assign()：需注意的是目标对象只有一层的时候，是深拷贝；
        （2）扩展运算符；
     深拷贝就是在拷贝数据的时候，将数据的所有引用结构都拷贝一份。深拷贝的实现方式有：
        （1）手写遍历递归赋值；
        （2）结合使用JSON.parse()和JSON.stringify()方法。

### 9. let、const的区别是什么？
 var、let、const都是用于声明变量或函数的关键字。其区别在于：


![](https://imgkr2.cn-bj.ufileos.com/24f8aa4d-062c-40c6-b98a-eae83e9ae13d.png?UCloudPublicKey=TOKEN_8d8b72be-579a-4e83-bfd0-5f6ce1546f13&Signature=8vH6kelDZGCub1Do0yMI6feLums%253D&Expires=1612167304)

### 10. 什么是执行上下文和执行栈？
    变量或函数的执行上下文，决定了它们的行为以及可以访问哪些数据。每个上下文都有一个关联的变量对象，而这个上下文中定义的所有变量和函数都存在于这个对象上(如DOM中全局上下文关联的便是window对象)。
    每个函数调用都有自己的上下文。当代码执行流进入函数时，函数的上下文被推到一个执行栈中。在函数执行完之后，执行栈会弹出该函数上下文，在其上的所有变量和函数都会被销毁，并将控制权返还给之前的执行上下文。 JS的执行流就是通过这个执行栈进行控制的。


​    
### 11.什么是作用域和作用域链？
  作用域可以理解为一个独立的地盘，可以理解为标识符所能生效的范围。作用域最大的用处就是隔离变量，不同作用域下同名变量不会有冲突。ES6中有全局作用域、函数作用域和块级作用域三层概念。
    当一个变量在当前块级作用域中未被定义时，会向父级作用域(创建该函数的那个父级作用域)寻找。如果父级仍未找到，就会再一层一层向上寻找，直到找到全局作用域为止。这种一层一层的关系，就是作用域链 。

### 12.作用域和执行上下文的区别是什么？
（1）函数的执行上下文只在函数被调用时生成，而其作用域在创建时已经生成；
    （2）函数的作用域会包含若干个执行上下文(有可能是零个，当函数未被调用时)。
    
### 13.this指向的各种情况都有什么？
this的指向只有在调用时才能被确定，因为this是执行上下文的一部分。
（1）全局作用域中的函数：其内部this指向window：
```
var a = 1;
function fn(){
  console.log(this.a)
}
fn() //输出1
```
（2）对象内部的函数：其内部this指向对象本身：

```
var a = 1;
var obj = {
  a:2,
  fn:function(){
  	console.log(this.a)
	}
}

obj.fn() //输出2

```
(3）构造函数：其内部this指向生成的实例：

```
function createP(name,age){
	this.name = name //this.name指向P
  this.age = age //this.age指向P
}
var p = new createP("老李",46)
```
（4）由apply、call、bind改造的函数：其this指向第一个参数：
```
function add(c,d){
	return this.a + this.b + c + d
}
var o = {a:1,b:2)
add.call(o,5,7) //输出15
```
 （5）箭头函数：箭头函数没有自己的this，看其外层的是否有函数，如果有，外层函数的this就是内部箭头函数的this，如果没有，则this是window。

### 14.如何改变this指针的指向？

 可以使用apply、call、bind方法改变this指向(并不会改变函数的作用域)。比较如下：
        （1）三者第一个参数都是this要指向的对象，也就是想指定的上下文，上下文就是指调用函数的那个对象(没有就指向全局window)；
        （2）apply和bind的第二个参数都是数组，call接收多个参数并用逗号隔开；
        （3）apply和call只对原函数做改动，bind会返回新的函数(要生效还得再调用一次)。

### 15.如何理解同步和异步？
同步：按照代码书写顺序一一执行处理指令的一种模式，上一段代码执行完才能执行下一段代码。

异步：可以理解为一种并行处理的方式，不必等待一个程序执行完，可以执行其它的任务。

```
JS之所以需要异步的原因在于JS是单线程运行的。常用的异步场景有：定时器、ajax请求、事件绑定。
```

### 16.JS是如何实现异步的？
 JS引擎是单线程的，但又能实现异步的原因在于事件循环和任务队列体系。
    事件循环：
        JS 会创建一个类似于 while (true) 的循环，每执行一次循环体的过程称之为 Tick。每次 Tick 的过程就是查看是否有待处理事件，如果有则取出相关事件及回调函数放入执行栈中由主线程执行。待处理的事件会存储在一个任务队列中，也就是每次 Tick 会查看任务队列中是否有需要执行的任务。
    任务队列：
        异步操作会将相关回调添加到任务队列中。而不同的异步操作添加到任务队列的时机也不同，如 onclick, setTimeout, ajax 处理的方式都不同，这些异步操作是由浏览器内核的 webcore 来执行的，浏览器内核包含3种 webAPI，分别是 DOM Binding、network、timer模块。
        onclick 由 DOM Binding 模块来处理，当事件触发的时候，回调函数会立即添加到任务队列中。
setTimeout 由 timer 模块来进行延时处理，当时间到达的时候，才会将回调函数添加到任务队列中。
ajax 由network 模块来处理，在网络请求完成返回之后，才将回调添加到任务队列中。
    主线程：
        JS 只有一个线程，称之为主线程。而事件循环是主线程中执行栈里的代码执行完毕之后，才开始执行的。所以，主线程中要执行的代码时间过长，会阻塞事件循环的执行，也就会阻塞异步操作的执行。
        只有当主线程中执行栈为空的时候（即同步代码执行完后），才会进行事件循环来观察要执行的事件回调，当事件循环检测到任务队列中有事件就取出相关回调放入执行栈中由主线程执行。

### 17.什么是AJAX？如何实现？
ajax是一种能够实现局部网页刷新的技术，可以使网页异步刷新。
          
  ajax的实现主要包括四个步骤：
    
  （1）创建核心对象XMLhttpRequest；
        
  （2）利用open方法打开与服务器的连接；
        
  （3）利用send方法发送请求；（"POST"请求时，还需额外设置请求头）
        
  （4）监听服务器响应，接收返回值。
```
  ajax是一种能够实现局部网页刷新的技术，可以使网页异步刷新。
    ajax的实现主要包括四个步骤：
        （1）创建核心对象XMLhttpRequest；
        （2）利用open方法打开与服务器的连接；
        （3）利用send方法发送请求；（"POST"请求时，还需额外设置请求头）
        （4）监听服务器响应，接收返回值。

```
### 18.实现异步的方式有哪些？
（1）回调函数模式：将需要异步执行的函数作为回调函数执行，其缺点在于处理复杂逻辑异步逻辑时，会造成回调地狱(回调嵌套层数太多，代码结构混乱)；

（2）事件监听模式：采用事件驱动的思想，当某一事件发生时触发执行异步函数，其缺点在于整个代码全部得变为事件驱动模式，难以分辨主流程；

（3）发布订阅模式：当异步任务执行完成时发布消息给信号中心，其他任务通过在信号中心中订阅消息来确定自己是否开始执行；

（4）Promise(ES6)：Promise对象共有三种状态pending(初始化状态)、fulfilled(成功状态)、rejected(失败状态)。

（5）async/await(ES7)：基于Promise实现的异步函数；

（6）利用生成器实现。

### 19.怎么理解Promise对象？
Promise对象有如下两个特点：
        （1）对象的状态不受外界影响。Promise对象共有三种状态pending、fulfilled、rejected。状态值只会被异步结果决定，其他任何操作无法改变。
        （2）状态一旦成型，就不会再变，且任何时候都可得到这个结果。状态值会由pending变为fulfilled或rejected，这时即为resolved。
    Promise的缺点有如下三个缺点：
        （1）Promise一旦执行便无法被取消；
        （2）不可设置回调函数，其内部发生的错误无法捕获；
        （3）当处于pending状态时，无法得知其具体发展到了哪个阶段。
    Pomise中常用的方法有：
        （1）Promise.prototype.then()：Promise实例的状态发生改变时，会调用then内部的回调函数。then方法接受两个参数（第一个为resolved状态时时执行的回调，第一个为rejected状态时时执行的回调）
        （2）Promise.prototype.catch()：.then(null, rejection)或.then(undefined, rejection)的别名，用于指定发生错误时的回调函数。
### 20.怎么理解宏任务，微任务？？？
  宏任务有：script(整体代码)、setTimeout、setInterval、I/O、页面渲染；
    微任务有：Promise.then、Object.observe、MutationObserver。
    执行顺序大致如下：
        主线程任务——>宏任务——>微任务——>微任务里的宏任务——>.......——>直到任务全部完成

### 21.实现继承的方法有哪些？？？
  实现继承的方法有：
        （1）class+extends继承（ES6）

```
//类模板
class Animal {
  constructor(name){
    this.name = name
  }
}
//继承类
class Cat extends Animal{//重点。extends方法，内部用constructor+super
  constructor(name) {
    super(name);
    //super作为函数调用时，代表父类的构造函数
  }//constructor可省略
  eat(){
    console.log("eating")
  }
}
```
 （2）原型继承
 ```
 //类模板
function Animal(name) {
  this.name = name; 
}
//添加原型方法
Animal.prototype.eat = function(){
  console.log("eating")
}

function Cat(furColor){ 
   this.color = color ;
};
//继承类
Cat.prototype = new Animal()//重点：子实例的原型等于父类的实例
 ```
   （3）借用构造函数继承
   ```
   function Animal(name){
	this.name = name
}
function Cat(){
	Animal.call(this,"CatName")//重点，调用父类的call方法
}
   ```
（4）寄生组合式继承（重点）

### 22.require/import之间的区别？
（1）require是CommonJS语法，import是ES6语法；

（2）require只在后端服务器支持，import在高版本浏览器及Node中都可以支持；

（3）require引入的是原始导出值的复制，import则是导出值的引用；

（4）require时运行时动态加载，import是静态编译；

（5）require调用时默认不是严格模式，import则默认调用严格模式.

## BOM & DOM
### 1.BOM事件?
事件就是用户或浏览器自身执行的某种动作.事件可能是用户在某些内容上的点击、鼠标经
过某个特定元素或按下键盘上的某些按键。事件还可能是 Web 浏览器中发生的事情，比如说某个 Web 页面加载完成，或者是用户滚动窗口或改变窗口大小。
通过使用 JavaScript ，你可以监听特定事件的发生，并规定让某些事件发生以对这些事件做出响应。
JavaScript可以处理的事件类型为：鼠标事件、键盘事件、HTML事件

### 2.常见BOM事件?
load：当页面或图像加载完后立即触发
blur：元素失去焦点
focus：元素获得焦点
click：鼠标点击某个对象
change：用户改变域的内容
mouseover：鼠标移动到某个元素上
mouseout：鼠标从某个元素上离开
keyup：某个键盘的键被松开
keydown：某个键盘的键被按下

### 3.BOM事件处理程序?
响应某个事件的函数就叫做事件处理程序（或事件侦听器）。事件处理程序的名字以“on”开头，因此click事件的事件处理程序就是onclick，为事件指定处理程序的方式有好几种
### 4.BOM对象方法?
这里主要说一下系统对话框:
浏览器通过（实际是window对象的方法）alert()、confirm()、prompt()方法可以调用系统对话框向用户显示消息


消息框:alert， 常用。

alert() 方法用于显示带有一条指定消息和一个 OK 按钮的警告框。

输入框:prompt，返回提示框中的值。

prompt() 方法用于显示可提示用户进行输入的对话框。
参数（可选）：

第一个参数：要在对话框中显示的纯文本。
第二个参数：默认的输入文本。


确认框:confirm，返回 true/false.

confirm() 方法用于显示一个带有指定消息和 OK 及取消按钮的对话框。
### 5.BOM对象
#### 1.history
history 对象是历史对象。包含用户（在浏览器窗口中）访问过的 URL。history 对象是 window 对象的一部分，可通过 window.history 属性对其进行访问。
history对象的属性：length，返回浏览器历史列表中的 URL 数量。
history对象的方法：

back()：加载 history 列表中的前一个 URL。
forward()：加载历史列表中的下一个 URL。当页面第一次访问时，还没有下一个url。
go(number|URL): URL 参数使用的是要访问的 URL。而 number 参数使用的是要访问的 URL 在 History 的 URL 列表中的相对位置。go(-1)，到上一个页面

#### 2.location
location 对象是window对象之一，提供了与当前窗口中加载的文档有关的信息，还提供了一些导航功能。也可通过 window.location 属性来访问。

location 对象的属性href：设置或返回完整的 URL
location 对象的方法

reload()：重新加载当前文档。
replace()：用新的文档替换当前文档。

#### 3.document

### 6.DOM?
DOM：Document Object Model 文档对象模型
要实现页面的动态交互效果，bom 操作远远不够，需要操作 html 才是核心。如何操作 htm，就是 DOM。
简单的说，dom 提供了用程序动态控制 html 接口。DOM即文档对象模型描绘了一个层次化的节点树，运行开发人员添加、移除和修改页面的某一部分。dom 处于javascript 的核心地位上。
每个载入浏览器的 HTML 文档都会成为 Document 对象。Document 对象使我们可以从脚本中对 HTML 页面中的所有元素进行访问。Document 对象是 Window 对象的一部分，可通过 window.document 属性对其进行访问。

### 7.DOM节点

![](https://gitee.com/WebInterviewHub/WebInterview/raw/master/imgs/dom7.png)

### 8.DOM获取节点
获取节点的四种方法:

getElementById()--通过id属性值获取元素对象
getElementByName()--通过name属性值获取元素对象数组
getElementByClass()--通过class属性值获取元素对象数组
getElementByTagName()--通过元素名/标签名获取元素对象数

后三个获取的是数组,所以需要通过数组下标取值
注意:操作dom节点是在等节点初始化完毕后,才会执行
处理方式:
把script标签移到html末尾即可
使用onload事件来处理JS,等待html加载完毕再加载onload事件里的JS

### 9.DOM创建节点与插入节点

![](https://gitee.com/WebInterviewHub/WebInterview/raw/master/imgs/dom9.png)
## 跨域
### 1.什么是跨域
协议、端口和域名不一致导致的跨域 跨域是因为浏览器需要遵守同源策略，发出的请求即使相应成功，也被浏览器拦截下来

### 2.同源策略
同源策略限制了从同一个源加载的文档或脚本如何与来自另一个源的资源进行交互、这是一个用于隔离潜在恶意文件的重要安全机制、
### 3.为什么有同源策略
如果缺少了同源策略，浏览器很容易受到XSS、CSFR等攻击。
1、 防御 XSS 攻击

XSS，即 Cross Site Script，中译是跨站脚本攻击。
HttpOnly 防止劫取 Cookie
用户的输入检查
服务端的输出检查

2、防御 CSRF 攻击

CSRF，即 Cross Site Request Forgery，中译是跨站请求伪造，是一种劫持受信任用户向服务器发送非预期请求的攻击方式。
验证码
Referer Check
Token验证
### 4.跨域的解决方案
1、通过jsonp跨域
2、document.domain + iframe跨域
3、location.hash + iframe
4、window.name + iframe跨域
5、postMessage跨域
6、跨域资源共享(CORS)
7、nginx代理跨域
8、nodejs中间代理跨域
9、WebSocket协议跨域

### 5.jsonp原理

jsonp的核心则是动态添加 script 标签调用服务器提供的js脚本，允许用户传递一个callback参数给服务器，然后服务器返回数据时会将这个callback参数作为函数名老包裹JSON数据，这样客户端就可以随意定制自己的函数来自动处理返回数据了

仅支持GET方法

## HTTP

### 1.什么是域名发散和域名收敛？
1、域名发散
为了突破浏览器对于同一域名并发请求数的限制，http 静态资源采用多个子域名，通常为2～4个。
目的是充分利用现代浏览器的多线程并发下载能力。
2、域名收敛
域名收敛和域名发散正好相反：就是将静态资源只放在一个域名下面，而非发散情况下的多个域名下。
主要是为了适应移动端的发展需求。

### 2.为什么浏览器要做并发限制呢？
1.以前网速慢、服务器硬件设备差、负载能力差，容易崩溃，所以要对最大并发数进行限制

### 3.什么是 DDOS 攻击
分布式拒绝服务攻击(Distributed denial of service attack)

向目标系统同时提出数量庞大的服务请求。
### 4.DDOS 攻击方式
1.通过使网络过载来干扰甚至阻断正常的网络通讯；

2.通过向服务器提交大量请求，使服务器超负荷；

3.阻断某一用户访问服务器；

4.阻断某服务与特定系统或个人的通讯。

### 5.如何应对 DDOS 攻击
黑名单
DDOS 清洗：对用户请求数据进行实时监控，及时发现DOS攻击等异常流量，在不影响正常业务开展的情况下清洗掉这些异常流量。
CDN 加速
高防服务器：高防服务器主要是指能独立硬防御 50Gbps 以上的服务器，能够帮助网站拒绝服务攻击，定期扫描网络主节点

### 6.http请求过程
1.对www.abc.com这个网址进行DNS域名解析，得到对应的IP地址

2.根据这个IP，找到对应的服务器，发起TCP的三次握手

3.建立TCP连接后发起HTTP请求

4.服务器响应HTTP请求，浏览器得到html代码

5.浏览器解析html代码，并请求html代码中的资源（如js、css、图片等）（先得到html代码，才能去找这些资源）

6.浏览器对页面进行渲染呈现给用户

7.服务器关闭关闭TCP连接

![](https://gitee.com/WebInterviewHub/WebInterview/raw/master/imgs/http6.png)

### 7.DNS 域名如何解析的？
DNS域名解析采用的是递归查询的方

先去找DNS缓存->缓存找不到就去找根域名服务器->根域名又会去找下一级，递归查找之后，找到了，给我们的web浏览器。

1.浏览器首先搜索自身的DNS缓存，看缓存中是否有 www.abc.com 这个域名，有而且没有过期的话，解析结束。

2.如果浏览器自身的缓存中没有找到，则会搜索操作系统自身的DNS缓存，如果找到且没有过期则停止搜索，解析到此结束。

3.如果在操作系统的DNS缓存中也没有找到，那么尝试读取hosts文件，有则解析成功，解析到此结束。

4.如果在hosts文件中也没有找到，浏览器会发起一个DNS（Domain Name System：域名服务协议）系统调用，向本地配置的首选DNS服务器发起域名解析请求 （递归请求）

1.运营商的DNS服务器首先查找自身的缓存，如果能找到且没有过期则解析成功。

2.如果没有找到，则运营商的DNS代我们的浏览器发起迭代DNS解析请求。

3.运营商DNS首先会查找根域DNS的IP地址（这个DNS服务器内置13台根DNS域服务器的IP地址），找到根域的DNS地址，就会向其发起请求（（问一下www.abc.com这个域名的ip地址是多少啊？））。根域发现这是一个com域（顶级域）的域名，于是返回com域的IP地址，然后运营商的DNS就得到com域的IP地址。

4.运营商的DNS得到com域的IP地址之后又向com域的IP地址发起地址请求（问一下www.abc.com这个域名的IP地址是多少啊？）。com域这台服务器告诉运营商的DNS我不知道www.abc.com这个域名的IP地址，但是我知道abc.com这个域名的DNS地址，你去找它吧。

5.运营商的DNS又向abc.com这个域名的DNS地址发起请求，（问一下www.abc.com这个域名的IP地址是多少？）

6.这个时候abc.com域的DNS服务器在本地查找。

7.把找到的结果发给运营商的DNS服务器，这个时候运营商的DNS服务器就拿到了www.abc.com对应的IP地址，并返回给Windows系统内核，内核就把这个结果返回给浏览器，最终浏览器得到这个IP地址，进行下一步动作。

### 8.TCP三次握手
1.客服端首先发送一个连接试探。

2.服务器监听到连接请求报文后，如果同意建立连接，则向Client发送确认。

3.Client收到确认后还需要再次发送确认，同时携带要发送给Server的数据。

### 9.为什么要三次握手？
1.验证服务端和客户端是否遵循TCP/IP协议

2.为了防止已失效的连接请求报文段突然又传送到了服务端，因而产生错误。

### 10.为什么HTTP协议要基于TCP来实现？
TCP是一个端到端的可靠的面相连接的协议，HTTP基于传输层TCP协议不用担心数据传输的各种问题（当发生错误时，会重传）

### 11.什么是面相连接协议？面向无链接协议又是什么？

#### 1. 面相连接协议定义
通信双方在通信时，要事先建立好一条通信线路（虚拟的）。

其过程有建立连接、维护连接、释放（断开）连接三个过程。
```
TCP是面向连接的
```

#### 2. 面向无链接协议定义
与面向连接相对，面向无连接是指通信双方不需要事先建立通信线路，而是把每个带有目的地址的报文分组送到线路上，由系统自主选定线路进行传输。

面向无连接只有**“传送数据”**的过程。

```
UDP是面向无连接的
```
### 12.说到三次握手，那在说下四次挥手吧？

1.客户端进程发出连接释放报文，并且停止发送数据。

2.服务器收到连接释放报文，发出确认报文，此时，服务端就进入了CLOSE-WAIT（关闭等待）状态。(客户端向服务器方向释放了，但是服务器发送数据，客户端依然要接受)

3.客户端收到服务器的确认请求后，客户端就进入FIN-WAIT-2（终止等待2）状态，等待服务器发送连接释放报文（在这之前还需要接受服务器发送的最后的数据）。

4.服务器将最后的数据发送完毕后，就向客户端发送连接释放报文，服务器就进入了LAST-ACK（最后确认）状态，等待客户端的确认。

5.客户端收到服务器的连接释放报文后，必须发出确认，客户端就进入了TIME-WAIT（时间等待）状态。

6.服务器只要收到了客户端发出的确认，立即进入CLOSED状态。同样，撤销TCB后，就结束了这次的TCP连接。（服务器结束TCP连接的时间要比客户端早一些。）

#### 13.为什么要四次挥手
TCP协议是一种面向连接的、可靠的、基于字节流的运输层通信协议。TCP是全双工模式，这就意味着，当主机1发出FIN报文段时，只是表示主机1已经没有数据要发送了，主机1告诉主机2，它的数据已经全部发送完毕了；但是，这个时候主机1还是可以接受来自主机2的数据；当主机2返回ACK报文段时，表示它已经知道主机1没有数据发送了，但是主机2还是可以发送数据到主机1的；当主机2也发送了FIN报文段时，这个时候就表示主机2也没有数据要发送了，就会告诉主机1，我也没有数据要发送了，之后彼此就会愉快的中断这次TCP连接。

### 14.为什么建立连接是三次握手，关闭连接确是四次挥手呢？
建立连接的时候， 服务器在LISTEN状态下，收到建立连接请求的SYN报文后，把ACK和SYN放在一个报文里发送给客户端。
而关闭连接时，服务器收到对方的FIN报文时，仅仅表示对方不再发送数据了但是还能接收数据，而自己也未必全部数据都发送给对方了，所以己方可以立即关闭，也可以发送一些数据给对方后，再发送FIN报文给对方来表示同意现在关闭连接，因此，己方ACK和FIN一般都会分开发送，从而导致多了一次。

### 15.如果已经建立了连接，但是客户端突然出现故障了怎么办？
TCP还设有一个保活计时器。但是客户端如果出现故障，服务器不能一直等下去，白白浪费资源。服务器每收到一次客户端的请求后都会重新复位这个计时器，时间通常是设置为2小时，若两小时还没有收到客户端的任何数据，服务器就会发送一个探测报文段，以后每隔75秒发送一次。若一连发送10个探测报文仍然没反应，服务器就认为客户端出了故障，接着就关闭连接。

### 16.http请求方式有哪些？

1.GET：请求一个指定资源的表示形式. 使用GET的请求应该只被用于获取数据。

2.HEAD：请求一个与GET请求的响应相同的响应，但没有响应体。

3.POST：将实体提交到指定的资源。

4.PUT：请求有效载荷替换目标资源的所有当前表示。

5.DELETE：删除指定的资源。

6.OPTIONS：用于描述目标资源的通信选项。

7.PATCH：对资源应用部分修改。

8.CONNECT：建立一个到由目标资源标识的服务器的隧道。

9.TRACE：沿着到目标资源的路径执行一个消息环回测试。

### 17.常用的请求状态码？

![](https://gitee.com/WebInterviewHub/WebInterview/raw/master/imgs/http17.png)

![](https://gitee.com/WebInterviewHub/WebInterview/raw/master/imgs/http17-1.png)

![](https://gitee.com/WebInterviewHub/WebInterview/raw/master/imgs/http17-2.png)




### 18.TCP和UDP的区别以及应用场景

#### 1.UDP
1.UDP在传输层上

2.是面向无连接的

3.不需要建立可靠的连接

4.是面向报文

5.限制就是发送一些比较小的包文件，而且没有错误处理机制。包没了就是没了。可以做一些处理，比如超时重发

6.一对一、一对多、多对一、多对多通信

7.适用于实时应用

#### 1.TCP

1.TCP在传输层上

2.是TCP是面向连接的

3.可以互相信任的进行数据发送，这样的保密性强一些

4.面向字节流

5.一对一通信

6.适用于可靠传输的应用

#### 3.应用场景

![](https://gitee.com/WebInterviewHub/WebInterview/raw/master/imgs/http18.png)



## https

### 1.https的访问过程
1.客户使用https的URL访问Web服务器，要求与Web服务器建立SSL连接。

2.Web服务器收到客户端请求后，会将网站的证书信息（证书中包含公钥）传送一份给客户端。

3.客户端的浏览器与Web服务器开始协商SSL连接的安全等级，也就是信息加密的等级。

4.客户端的浏览器根据双方同意的安全等级，建立会话密钥，然后利用网站的公钥将会话密钥加密，并传送给网站。

5.Web服务器利用自己的私钥解密出会话密钥。

6.Web服务器利用会话密钥加密与客户端之间的通信。

#### 详细解释：
1. 客户端发起HTTPS请求

用户在浏览器里输入一个https网址，然后连接到server的443端口。

2.服务端的配置

就是指上述提到的数字证书；

3.传送证书

Web服务器收到客户端请求后，会将网站的证书信息（证书中包含公钥）传送一份给客户端。

4.客户端解析证书

客户端会对证书进行判断，验证公钥是否有效，存在问题弹出会警告；若没有问题，生成一个随机值（私钥），然后用证书继续进行加密；

5.传送加密信息

客户端将上加密后的随机值（私钥）提供给服务端，服务端会对其进行解密；

6.服务端解密信息

服务端解密后得到随机值（私钥），然后把内容通过该值进行对称加密。对称加密就是指把要返回的信息和随机值（私钥）混合加密，这样除非知道随机值（私钥），不然无法获取数据。

7.传输加密后的信息

继续将加密后的信息传递给客户端；

8.客户端解密信息

客户端用之前生成的私钥（随机值）解密服务端传过来的信息，于是获取了解密后的内容。

![](https://gitee.com/WebInterviewHub/WebInterview/raw/master/imgs/https1.png)

### 2.https的优缺点？
#### 1. 优点

1.正确发送数据到客户端

使用HTTPS协议可认证用户和服务器，确保数据发送到正确的客户机和服务器

2.更安全

HTTPS协议是由SSL+HTTP协议构建的可进行加密传输、身份认证的网络协议，要比http协议安全，可防止数据在传输过程中不被窃取、改变，确保数据的完整性

3.增加中间人攻击的成本

HTTPS是现行架构下最安全的解决方案，虽然不是绝对安全，但它大幅增加了中间人攻击的成本。

4.搜索排名更高

谷歌在2014跳转搜索算法，采用HTTPS加密的网站在搜索结果中的排名将会更高
百度也在2018年发布百度对HTTPS站点的扶持态度，表明HTTPS将作为优质特征之一影响搜索排序。

#### 2、缺点

1.页面渲染更耗时间

因为SSL的缘故，HTTPS协议握手阶段比较费时，会使页面的加载时间延长近50%；

2.成本增加

SSL证书需要花钱，功能越强大的证书费用越高；

3.HTTPS连接缓存不如HTTP高效

HTTPS连接缓存不如HTTP高效，会增加数据开销和功耗，甚至已有的安全措施也会因此而受到影响；

4.SSL证书通常需要绑定IP

SSL证书通常需要绑定IP，不能在同一IP上绑定多个域名，IPv4资源不可能支撑这个消耗。

5.有局限性

HTTPS协议的加密范围也比较有限，在黑客攻击、拒绝服务攻击、服务器劫持等方面几乎起不到什么作用。最关键的，SSL证书的信用链体系并不安全，特别是在某些国家可以控制CA根证书的情况下，中间人攻击一样可行。

### 3.https如何进行性能优化？
#### 1.https访问速度优化

1.设置HSTS

服务端返回一个 HSTS 的 http header，浏览器获取到 HSTS 头部之后，在一段时间内，不管用户输入www.baidu.com还是http://www.baidu.com，都会默认将请求内部跳转成https://www.baidu.com。

2.Session resume

Session Resume 顾名思义就是复用 Session，实现简化握手。
```
1. 减少了 CPU 消耗，因为不需要进行非对称密钥交换的计算。
2. 提升访问速度，不需要进行完全握手阶段二，节省了一个 RTT 和计算耗时。
```

3.Nginx设置Ocsp stapling

OSCP Stapling 工作原理简单来说就是浏览器发起 Client Hello 时会携带一个 certificate status request 的扩展，服务端看到这个扩展后将 OCSP 内容直接返回给浏览器，完成证书状态检查。由于浏览器不需要直接向 CA 站点查询证书状态，这个功能对访问速度的提升非常明显。

4.使用 SPDY 或者 HTTP2

SPDY 最大的特性就是多路复用，能将多个 HTTP 请求在同一个连接上一起发出去，不像目前的 HTTP 协议一样，只能串行地逐个发送请求。
HTTP2支持多路复用，有同样的效果。
```
1. SPDY 和 HTTP2 目前的实现默认使用 HTTPS 协议。
2. SPDY 和 HTTP2 都支持现有的 HTTP 语义和 API，对 WEB 应用几乎是透明的。
```

5.False start

简单概括 False Start 的原理就是在 client_key_exchange 发出时将应用层数据一起发出来，能够节省一个 RTT。

#### 2.https计算性能优化
1. 优先使用 ECC椭圆加密算术。

ECC 椭圆加密算术相比普通的离散对数计算速度性能要强很多。

![](https://static01.imgkr.com/temp/4a4005b6b9de4e90af1f2b103271eae9.png)

2.使用最新版的 openssl。

一般来讲，新版的 OpenSSL 相比老版的计算速度和安全性都会有提升。

3.硬件加速方案。
- SSL 专用加速卡。
- GPUSSL 加速。

4.TLS 远程代理计算

### 4.http和https
HTTP：(HyperText Transfer Protocol)超文本传输协议

HTTPS：(Hypertext Transfer Protocol Secure)超文本传输安全协议

#### http和https的区别

https://www.ihuandu.com/help/zsk/46.html

## HTTP2 && HTTP缓存

### 1.http/2项目设定目标
1.页面加载时间 (PLT) 减少 50%。

2.无需网站作者修改任何内容。

3.将部署复杂性降至最低，无需变更网络基础设施。

4.与开源社区合作开发此新协议。

5.收集真实性能数据，验证实验性协议是否有效。

### 2.http/2特性 
#### 1. 二进制分帧层
HTTP/2 所有性能增强的核心在于新的二进制分帧层，它定义了如何封装 HTTP 消息并在客户端与服务器之间传输。

#### 2. 多路复用(请求与响应复用)
HTTP/2 中新的二进制分帧层突破了这些限制，实现了完整的请求和响应复用：客户端和服务器可以将 HTTP 消息分解为互不依赖的帧，然后交错发送，最后再在另一端把它们重新组装起来。
#### 3. 数据流优先级
将 HTTP 消息分解为很多独立的帧之后，我们就可以复用多个数据流中的帧，客户端和服务器交错发送和传输这些帧的顺序就成为关键的性能决定因素。 为了做到这一点，HTTP/2 标准允许每个数据流都有一个关联的权重和依赖关系：

- 可以向每个数据流分配一个介于 1 至 256 之间的整数。
- 每个数据流与其他数据流之间可以存在显式依赖关系。
#### 4. 每个来源一个连接
每个数据流都拆分成很多帧，而这些帧可以交错，还可以分别设定优先级。 因此，所有 HTTP/2 连接都是永久的，而且仅需要每个来源一个连接，随之带来诸多性能优势。
#### 5. 流控制
流控制是一种阻止发送方向接收方发送大量数据的机制，以免超出后者的需求或处理能力：发送方可能非常繁忙、处于较高的负载之下，也可能仅仅希望为特定数据流分配固定量的资源。
#### 6. 服务器推送
HTTP/2 新增的另一个强大的新功能是，服务器可以对一个客户端请求发送多个响应。 换句话说，除了对最初请求的响应外，服务器还可以向客户端推送额外资源，而无需客户端明确地请求。

#### 7.标头压缩

每个 HTTP 传输都承载一组标头，这些标头说明了传输的资源及其属性。
HTTP/2 使用 HPACK 压缩格式压缩请求和响应标头元数据，这种格式采用两种简单但是强大的技术：

- 这种格式支持通过静态霍夫曼代码对传输的标头字段进行编码，从而减小了各个传输的大小。
- 这种格式要求客户端和服务器同时维护和更新一个包含之前见过的标头字段的索引列表（换句话说，它可以建立一个共享的压缩上下文），此列表随后会用作参考，对之前传输的值进行有效编码。

### 3.什么是缓存？又有什么用？
定义：缓存是一种保存资源副本并在下次请求时直接使用该副本的技术。

作用：

1.可以显著提高网站和应用程序的性能。

2.减少了等待时间和网络流量

3.减少了显示资源表示形式所需的时间。

4.是页面更加响应性。

5.缓解服务器端压力，提升性能。

### 4.你知道有哪些缓存方式吗？
1.浏览器缓存

2.代理缓存

3.网关缓存

4.CDN缓存

5.反向代理缓存

### 5.缓存位置

- Service Worker
Service Worker 的缓存与浏览器其他内建的缓存机制不同，它可以让我们自由控制缓存哪些文件、如何匹配缓存、如何读取缓存，并且缓存是持续性的。

- Memory Cache
读取高效，但是持续性很短，一旦关闭 Tab 页面，内存中的缓存也就被释放了。


- Disk Cache
读取速度慢，容量和存储时效性上有优势，


- Push Cache
读取速度慢，容量和存储时效性上有优势，

### 6.http缓存怎样生效的？
http缓存分为强制缓存和协商缓存

1. 强制缓存
强制缓存就是文件直接从缓存中获取，不需要发送请求

2. 协商缓存
协商缓存意思是文件已经被缓存了，但是否从缓存中读取是需要和服务器进行协商，具体如何协商要看请求头/响应头的字段设置。
协商缓存还是会发送请求的。

3. 强缓存-Cache-Control
Cache-Control 通用消息头字段，被用于在http请求和响应中，通过指定指令来实现缓存机制。

1. 缓存请求指令
```
Cache-Control: max-age=<seconds>
Cache-Control: max-stale[=<seconds>]
Cache-Control: min-fresh=<seconds>
Cache-control: no-cache
Cache-control: no-store
Cache-control: no-transform
Cache-control: only-if-cached
```
2. 缓存响应指令
```
Cache-control: must-revalidate
Cache-control: no-cache
Cache-control: no-store
Cache-control: no-transform
Cache-control: public
Cache-control: private
Cache-control: proxy-revalidate
Cache-Control: max-age=<seconds>
Cache-control: s-maxage=<seconds>
```
3. 指令解释

4.协商缓存生效过程

1. 浏览器第一次请求：

![](https://gitee.com/WebInterviewHub/WebInterview/raw/master/imgs/http2-1.png)

2 浏览器第二次请求：

![## WEBPACK
### 1.webpack与grunt、gulp的不同？
三者都是前端构建工具，grunt和gulp在早期比较流行，现在webpack相对来说比较主流，不过一些轻量化的任务还是会用gulp来处理，比如单独打包CSS文件等。

grunt和gulp是基于任务和流（Task、Stream）的。类似jQuery，找到一个（或一类）文件，对其做一系列链式操作，更新流上的数据， 整条链式操作构成了一个任务，多个任务就构成了整个web的构建流程。

webpack是基于入口的。webpack会自动地递归解析入口所需要加载的所有资源文件，然后用不同的Loader来处理不同的文件，用Plugin来扩展webpack功能。

所以总结一下：

- 从构建思路来说
1.gulp和grunt需要开发者将整个前端构建过程拆分成多个`Task`，并合理控制所有`Task`的调用关系

2.webpack需要开发者找到入口，并需要清楚对于不同的资源应该使用什么Loader做何种解析和加工

- 对于知识背景来说

gulp更像后端开发者的思路，需要对于整个流程了如指掌 webpack更倾向于前端开发者的思路

### 2.与webpack类似的工具还有哪些？谈谈你为什么最终选择（或放弃）使用webpack？

同样是基于入口的打包工具还有以下几个主流的：

- webpack
- rollup
- parcel

从应用场景上来看：

- webpack适用于大型复杂的前端站点构建
- rollup适用于基础库的打包，如vue、react
- parcel适用于简单的实验性项目，他可以满足低门槛的快速看到效果
```
由于parcel在打包过程中给出的调试信息十分有限，所以一旦打包出错难以调试，所以不建议复杂的项目使用parcel
```
### 3.有哪些常见的Loader？他们是解决什么问题的？


- file-loader：把文件输出到一个文件夹中，在代码中通过相对 URL 去引用输出的文件

- url-loader：和 file-loader 类似，但是能在文件很小的情况下以 base64 的方式把文件内容注入到代码中去

- source-map-loader：加载额外的 Source Map 文件，以方便断点调试

- image-loader：加载并且压缩图片文件

- babel-loader：把 ES6 转换成 ES5

- css-loader：加载 CSS，支持模块化、压缩、文件导入等特性

- style-loader：把 CSS 代码注入到 JavaScript 中，通过 DOM 操作去加载 CSS。

- eslint-loader：通过 ESLint 检查 JavaScript 代码

### 4.有哪些常见的Plugin？他们是解决什么问题的？

- define-plugin：定义环境变量
- commons-chunk-plugin：提取公共代码
- uglifyjs-webpack-plugin：通过UglifyES压缩ES6代码

### 5.Loader和Plugin的不同？

#### 不同的作用


- Loader直译为"加载器"。Webpack将一切文件视为模块，但是webpack原生是只能解析js文件，如果想将其他文件也打包的话，就会用到loader。 所以Loader的作用是让webpack拥有了加载和解析非JavaScript文件的能力。

- Plugin直译为"插件"。Plugin可以扩展webpack的功能，让webpack具有更多的灵活性。 在 Webpack 运行的生命周期中会广播出许多事件，Plugin 可以监听这些事件，在合适的时机通过 Webpack 提供的 API 改变输出结果。

### 不同的用法

- Loader在module.rules中配置，也就是说他作为模块的解析规则而存在。 类型为数组，每一项都是一个Object，里面描述了对于什么类型的文件（test），使用什么加载(loader)和使用的参数（options）

- Plugin在plugins中单独配置。 类型为数组，每一项是一个plugin的实例，参数都通过构造函数传入。

### 6.webpack的构建流程是什么?从读取配置到输出文件这个过程尽量说全
Webpack 的运行流程是一个串行的过程，从启动到结束会依次执行以下流程：

1.初始化参数：从配置文件和 Shell 语句中读取与合并参数，得出最终的参数；

2.开始编译：用上一步得到的参数初始化 Compiler 对象，加载所有配置的插件，执行对象的 run 方法开始执行编译；

3.确定入口：根据配置中的 entry 找出所有的入口文件；

4.编译模块：从入口文件出发，调用所有配置的 Loader 对模块进行翻译，再找出该模块依赖的模块，再递归本步骤直到所有入口依赖的文件都经过了本步骤的处理；

5.完成模块编译：在经过第4步使用 Loader 翻译完所有模块后，得到了每个模块被翻译后的最终内容以及它们之间的依赖关系；

6.输出资源：根据入口和模块之间的依赖关系，组装成一个个包含多个模块的 Chunk，再把每个 Chunk 转换成一个单独的文件加入到输出列表，这步是可以修改输出内容的最后机会；

7.输出完成：在确定好输出内容后，根据配置确定输出的路径和文件名，把文件内容写入到文件系统。

在以上过程中，Webpack 会在特定的时间点广播出特定的事件，插件在监听到感兴趣的事件后会执行特定的逻辑，并且插件可以调用 Webpack 提供的 API 改变 Webpack 的运行结果。
### 7.是否写过Loader和Plugin？描述一下编写loader或plugin的思路？

Loader像一个"翻译官"把读到的源文件内容转义成新的文件内容，并且每个Loader通过链式操作，将源文件一步步翻译成想要的样子。

编写Loader时要遵循单一原则，每个Loader只做一种"转义"工作。 每个Loader的拿到的是源文件内容（source），可以通过返回值的方式将处理后的内容输出，也可以调用this.callback()方法，将内容返回给webpack。 还可以通过 this.async()生成一个callback函数，再用这个callback将处理后的内容输出出去。 此外webpack还为开发者准备了开发loader的工具函数集——loader-utils。

相对于Loader而言，Plugin的编写就灵活了许多。 webpack在运行的生命周期中会广播出许多事件，Plugin 可以监听这些事件，在合适的时机通过 Webpack 提供的 API 改变输出结果。

### 8.webpack的热更新是如何做到的？说明其原理？

webpack的热更新又称热替换（Hot Module Replacement），缩写为HMR。 这个机制可以做到不用刷新浏览器而将新变更的模块替换掉旧的模块。

#### 原理：

![](https://gitee.com/WebInterviewHub/WebInterview/raw/master/imgs/webpack1.png)

图片来自饿了么前端@知乎专栏

首先要知道server端和client端都做了处理工作

1.第一步，在 webpack 的 watch 模式下，文件系统中某一个文件发生修改，webpack 监听到文件变化，根据配置文件对模块重新编译打包，并将打包后的代码通过简单的 JavaScript 对象保存在内存中。

2.第二步是 webpack-dev-server 和 webpack 之间的接口交互，而在这一步，主要是 dev-server 的中间件 webpack-dev-middleware 和 webpack 之间的交互，webpack-dev-middleware 调用 webpack 暴露的 API对代码变化进行监控，并且告诉 webpack，将代码打包到内存中。

3.第三步是 webpack-dev-server 对文件变化的一个监控，这一步不同于第一步，并不是监控代码变化重新打包。当我们在配置文件中配置了devServer.watchContentBase 为 true 的时候，Server 会监听这些配置文件夹中静态文件的变化，变化后会通知浏览器端对应用进行 live reload。注意，这儿是浏览器刷新，和 HMR 是两个概念。

4.第四步也是 webpack-dev-server 代码的工作，该步骤主要是通过 sockjs（webpack-dev-server 的依赖）在浏览器端和服务端之间建立一个 websocket 长连接，将 webpack 编译打包的各个阶段的状态信息告知浏览器端，同时也包括第三步中 Server 监听静态文件变化的信息。浏览器端根据这些 socket 消息进行不同的操作。当然服务端传递的最主要信息还是新模块的 hash 值，后面的步骤根据这一 hash 值来进行模块热替换。

5.webpack-dev-server/client 端并不能够请求更新的代码，也不会执行热更模块操作，而把这些工作又交回给了 webpack，webpack/hot/dev-server 的工作就是根据 webpack-dev-server/client 传给它的信息以及 dev-server 的配置决定是刷新浏览器呢还是进行模块热更新。当然如果仅仅是刷新浏览器，也就没有后面那些步骤了。

6.HotModuleReplacement.runtime 是客户端 HMR 的中枢，它接收到上一步传递给他的新模块的 hash 值，它通过 JsonpMainTemplate.runtime 向 server 端发送 Ajax 请求，服务端返回一个 json，该 json 包含了所有要更新的模块的 hash 值，获取到更新列表后，该模块再次通过 jsonp 请求，获取到最新的模块代码。这就是上图中 7、8、9 步骤。

7.而第 10 步是决定 HMR 成功与否的关键步骤，在该步骤中，HotModulePlugin 将会对新旧模块进行对比，决定是否更新模块，在决定更新模块后，检查模块之间的依赖关系，更新模块的同时更新模块间的依赖引用。

8.最后一步，当 HMR 失败后，回退到 live reload 操作，也就是进行浏览器刷新来获取最新打包代码。

### 9.如何利用webpack来优化前端性能？（提高性能和体验）

用webpack优化前端性能是指优化webpack的输出结果，让打包的最终结果在浏览器运行快速高效。

- 压缩代码。删除多余的代码、注释、简化代码的写法等等方式。可以利用webpack的UglifyJsPlugin和ParallelUglifyPlugin来压缩JS文件， 利用cssnano（css-loader?minimize）来压缩css
- 利用CDN加速。在构建过程中，将引用的静态资源路径修改为CDN上对应的路径。可以利用webpack对于output参数和各loader的publicPath参数来修改资源路径
- 删除死代码（Tree Shaking）。将代码中永远不会走到的片段删除掉。可以通过在启动webpack时追加参数--optimize-minimize来实现
- 提取公共代码。

### 10.如何提高webpack的构建速度？


1.多入口情况下，使用CommonsChunkPlugin来提取公共代码

2.通过externals配置来提取常用库

3.利用DllPlugin和DllReferencePlugin预编译资源模块 通过DllPlugin来对那些我们引用但是绝对不会修改的npm包来进行预编译，再通过DllReferencePlugin将预编译的模块加载进来。

4.使用Happypack 实现多线程加速编译

5.使用webpack-uglify-parallel来提升uglifyPlugin的压缩速度。 原理上webpack-uglify-parallel采用了多核并行压缩来提升压缩速度

6.使用Tree-shaking和Scope Hoisting来剔除多余代码

### 11.怎么配置单页应用？怎么配置多页应用？
单页应用可以理解为webpack的标准模式，直接在entry中指定单页应用的入口即可，这里不再赘述

多页应用的话，可以使用webpack的 AutoWebPlugin来完成简单自动化的构建，但是前提是项目的目录结构必须遵守他预设的规范。 多页应用中要注意的是：

 - 每个页面都有公共的代码，可以将这些代码抽离出来，避免重复的加载。比如，每个页面都引用了同一套css样式表

- 随着业务的不断扩展，页面可能会不断的追加，所以一定要让入口的配置足够灵活，避免每次添加新页面还需要修改构建配置

### 12.npm打包时需要注意哪些？如何利用webpack来更好的构建？

Npm是目前最大的 JavaScript 模块仓库，里面有来自全世界开发者上传的可复用模块。你可能只是JS模块的使用者，但是有些情况你也会去选择上传自己开发的模块。 关于NPM模块上传的方法可以去官网上进行学习，这里只讲解如何利用webpack来构建。

NPM模块需要注意以下问题：

1.要支持CommonJS模块化规范，所以要求打包后的最后结果也遵守该规则。

2.Npm模块使用者的环境是不确定的，很有可能并不支持ES6，所以打包的最后结果应该是采用ES5编写的。并且如果ES5是经过转换的，请最好连同SourceMap一同上传。

3.Npm包大小应该是尽量小（有些仓库会限制包大小）

4.发布的模块不能将依赖的模块也一同打包，应该让用户选择性的去自行安装。这样可以避免模块应用者再次打包时出现底层模块被重复打包的情况。

5.UI组件类的模块应该将依赖的其它资源文件，例如.css文件也需要包含在发布的模块里。

基于以上需要注意的问题，我们可以对于webpack配置做以下扩展和优化：

1.CommonJS模块化规范的解决方案： 设置output.libraryTarget='commonjs2'使输出的代码符合CommonJS2 模块化规范，以供给其它模块导入使用

2.输出ES5代码的解决方案：使用babel-loader把 ES6 代码转换成 ES5 的代码。再通过开启devtool: 'source-map'输出SourceMap以发布调试。

3.Npm包大小尽量小的解决方案：Babel 在把 ES6 代码转换成 ES5 代码时会注入一些辅助函数，最终导致每个输出的文件中都包含这段辅助函数的代码，造成了代码的冗余。解决方法是修改.babelrc文件，为其加入transform-runtime插件

4.不能将依赖模块打包到NPM模块中的解决方案：使用externals配置项来告诉webpack哪些模块不需要打包。

5.对于依赖的资源文件打包的解决方案：通过css-loader和extract-text-webpack-plugin来实现，配置如下
```
const ExtractTextPlugin = require('extract-text-webpack-plugin');
 
module.exports = {
  module: {
    rules: [
      {
        // 增加对 CSS 文件的支持
        test: /\.css/,
        // 提取出 Chunk 中的 CSS 代码到单独的文件中
        use: ExtractTextPlugin.extract({
          use: ['css-loader']
        }),
      },
    ]
  },
  plugins: [
    new ExtractTextPlugin({
      // 输出的 CSS 文件名称
      filename: 'index.css',
    }),
  ],
};
```
### 13.如何在vue项目中实现按需加载？

Vue UI组件库的按需加载 为了快速开发前端项目，经常会引入现成的UI组件库如ElementUI、iView等，但是他们的体积和他们所提供的功能一样，是很庞大的。 而通常情况下，我们仅仅需要少量的几个组件就足够了，但是我们却将庞大的组件库打包到我们的源码中，造成了不必要的开销。

不过很多组件库已经提供了现成的解决方案，如Element出品的babel-plugin-component和AntDesign出品的babel-plugin-import 安装以上插件后，在.babelrc配置中或babel-loader的参数中进行设置，即可实现组件按需加载了。

```
{
  "presets": [["es2015", { "modules": false }]],
  "plugins": [
    [
      "component",
      {
        "libraryName": "element-ui",
        "styleLibraryName": "theme-chalk"
      }
    ]
  ]
}
```

单页应用的按需加载 现在很多前端项目都是通过单页应用的方式开发的，但是随着业务的不断扩展，会面临一个严峻的问题——首次加载的代码量会越来越多，影响用户的体验。

通过import(*)语句来控制加载时机，webpack内置了对于import(*)的解析，会将import(*)中引入的模块作为一个新的入口在生成一个chunk。 当代码执行到import(*)语句时，会去加载Chunk对应生成的文件。import()会返回一个Promise对象，所以为了让浏览器支持，需要事先注入Promise polyfill

## Git

### 1.列举工作中常用的几个git命令？
新增文件的命令：git add file或者git add .

提交文件的命令：git commit –m或者git commit –a

查看工作区状况：git status –s

拉取合并远程分支的操作：git fetch/git merge或者git pull

查看提交记录命令：git reflog

### 2. 提交时发生冲突，你能解释冲突是如何产生的吗？你是如何解决的？

开发过程中，我们都有自己的特性分支，所以冲突发生的并不多，但也碰到过。诸如公共类的公共方法，我和别人同时修改同一个文件，他提交后我再提交就会报冲突的错误。
发生冲突，在IDE里面一般都是对比本地文件和远程分支的文件，然后把远程分支上文件的内容手工修改到本地文件，然后再提交冲突的文件使其保证与远程分支的文件一致，这样才会消除冲突，然后再提交自己修改的部分。特别要注意下，修改本地冲突文件使其与远程仓库的文件保持一致后，需要提交后才能消除冲突，否则无法继续提交。必要时可与同事交流，消除冲突。
发生冲突，也可以使用命令。

- 通过git stash命令，把工作区的修改提交到栈区，目的是保存工作区的修改；
- 通过git pull命令，拉取远程分支上的代码并合并到本地分支，目的是消除冲突；
- 通过git stash pop命令，把保存在栈区的修改部分合并到最新的工作空间中；

### 3. 如果本次提交误操作，如何撤销？
如果想撤销提交到索引区的文件，可以通过git reset HEAD file；如果想撤销提交到本地仓库的文件，可以通过git reset –soft HEAD^n恢复当前分支的版本库至上一次提交的状态，索引区和工作空间不变更；可以通过git reset –mixed HEAD^n恢复当前分支的版本库和索引区至上一次提交的状态，工作区不变更；可以通过git reset –hard HEAD^n恢复当前分支的版本库、索引区和工作空间至上一次提交的状态。

### 4. 如果我想修改提交的历史信息，应该用什么命令？
如果修改最近一次提交的历史记录，就可以用git commit –amend命令；vim编辑的方式；
如果修改之前提交的历史记录，就需要按照下面的步骤：
第一步：首先查看前三次的提交历史记录：

```
$ git log -3
commit a762fcafecbd92bbde088054644e1b0586589c4b (HEAD -> slave)
Author: 18073638 <18073638@cnsuning.com>
Date:   Sat Mar 30 10:58:44 2019 +0800

    four commit

commit eedbc93d58780f63dd47f8388f8217892096e89a
Author: 18073638 <18073638@cnsuning.com>
Date:   Thu Mar 28 17:19:52 2019 +0800

    third commit third commit

commit 05396135eba85140602107e01e5c211d74f6c739
Author: 18073638 <18073638@cnsuning.com>
Date:   Thu Mar 28 16:56:19 2019 +0800

    second commit
```
注意：这里我们想把053961的committer对象信息修改为“second commit second commit”.

#### 第二步：执行命令git rebase –i HEAD~3，会把前3次的提交记录按照倒叙列出来；
```
pick 0539613 second commit
pick eedbc93 third commit third commit
pick a762fca four commit

# Rebase c8d7ad7..a762fca onto c8d7ad7 (3 commands)
#
# Commands:
# p, pick <commit> = use commit
# r, reword <commit> = use commit, but edit the commit message
# e, edit <commit> = use commit, but stop for amending
# s, squash <commit> = use commit, but meld into previous commit
# f, fixup <commit> = like "squash", but discard this commit's log message
# x, exec <command> = run command (the rest of the line) using shell
# b, break = stop here (continue rebase later with 'git rebase --continue')
# d, drop <commit> = remove commit
# l, label <label> = label current HEAD with a name
# t, reset <label> = reset HEAD to a label
# m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
# .       create a merge commit using the original merge commit's
# .       message (or the oneline, if no original merge commit was
# .       specified). Use -c <commit> to reword the commit message.
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out
```
这里把第一行的‘pick’修改为‘edit’，然后esc + :wq退出vim编辑器；
```
\$ git rebase -i HEAD~3
Stopped at 0539613...  second commit
You can amend the commit now, with

  git commit --amend

Once you are satisfied with your changes, run

  git rebase --continue
```
第三步：根据提示，执行git commit –amend命令，进入vim编辑器并修改提交信息。
```
$ git commit --amend
[detached HEAD 20fe643] second commit second commit
 Date: Thu Mar 28 16:56:19 2019 +0800
 1 file changed, 1 insertion(+)
```

第四步：然后执行git rebase –continue命令
```
$ git rebase --continue
Successfully rebased and updated refs/heads/slave.
```

查看修改结果

```
$ git log -3
commit 9024049ef990e79fa61295d5c2b64d70017cf412 (HEAD -> slave)
Author: 18073638 <18073638@cnsuning.com>
Date:   Sat Mar 30 10:58:44 2019 +0800

    four commit

commit 79cb4e26dd300591e6352d0488802f43b65c8ba2
Author: 18073638 <18073638@cnsuning.com>
Date:   Thu Mar 28 17:19:52 2019 +0800

    third commit third commit

commit 20fe643cbf80cdcc649d732065e8ebf4caf773c7
Author: 18073638 <18073638@cnsuning.com>
Date:   Thu Mar 28 16:56:19 2019 +0800

    second commit second commit
```
修改成功。

### 5. 你使用过git stash命令吗？你一般什么情况下会使用它？

命令git stash是把工作区修改的内容存储在栈区。
以下几种情况会使用到它：

- 解决冲突文件时，会先执行git stash，然后解决冲突；
- 遇到紧急开发任务但目前任务不能提交时，会先执行git stash，然后进行紧急任务的开发，然后通过git stash pop取出栈区的内容继续开发；
- 切换分支时，当前工作空间内容不能提交时，会先执行git stash再进行分支切换；

### 6. 如何查看分支提交的历史记录？查看某个文件的历史记录呢？

查看分支的提交历史记录：

- 命令git log –number：表示查看当前分支前number个详细的提交历史记录；
- 命令git log –number –pretty=oneline：在上个命令的基础上进行简化，只显示sha-1码和提交信息；
- 命令git reflog –number: 表示查看所有分支前number个简化的提交历史记录；
- 命令git reflog –number –pretty=oneline：显示简化的信息历史信息；
如果要查看某文件的提交历史记录，直接在上面命令后面加上文件名即可。
注意：如果没有number则显示全部提交次数。

### 7. 能不能说一下git fetch和git pull命令之间的区别？
简单来说：git fetch branch是把名为branch的远程分支拉取到本地；而git pull branch是在fetch的基础上，把branch分支与当前分支进行merge；因此pull = fetch + merge。


### 8. 使用过git merge和git rebase吗？它们之间有什么区别？
简单的说，git merge和git rebase都是合并分支的命令。
git merge branch会把branch分支的差异内容pull到本地，然后与本地分支的内容一并形成一个committer对象提交到主分支上，合并后的分支与主分支一致；
git rebase branch会把branch分支优先合并到主分支，然后把本地分支的commit放到主分支后面，合并后的分支就好像从合并后主分支又拉了一个分支一样，本地分支本身不会保留提交历史。

### 9. 能说一下git系统中HEAD、工作树和索引之间的区别吗？
HEAD文件包含当前分支的引用（指针）；

工作树是把当前分支检出到工作空间后形成的目录树，一般的开发工作都会基于工作树进行；

索引index文件是对工作树进行代码修改后，通过add命令更新索引文件；GIT系统通过索引index文件生成tree对象；
### 10. 之前项目中是使用的GitFlow工作流程吗？它有什么好处？

GitFlow可以用来管理分支。GitFlow工作流中常用的分支有下面几类：
- master分支：最为稳定功能比较完整的随时可发布的代码，即代码开发完成，经过测试，没有明显的bug，才能合并到 master 中。请注意永远不要在 master 分支上直接开发和提交代码，以确保 master 上的代码一直可用；
- develop分支；用作平时开发的主分支，并一直存在，永远是功能最新最全的分支，包含所有要发布 到下一个 release 的代码，主要用于合并其他分支，比如 feature 分支； 如果修改代码，新建 feature 分支修改完再合并到 develop 分支。所有的 feature、release 分支都是从 develop 分支上拉的。
- feature分支；这个分支主要是用来开发新的功能，一旦开发完成，通过测试没问题（这个测试，测试新功能没问题），我们合并回develop 分支进入下一个 release
- release分支；用于发布准备的专门分支。当开发进行到一定程度，或者说快到了既定的发布日，可以发布时，建立一个 release 分支并指定版本号(可以在 finish 的时候添加)。开发人员可以对 release 分支上的代码进行集中测试和修改bug。（这个测试，测试新功能与已有的功能是否有冲突，兼容性）全部完成经过测试没有问题后，将 release 分支上的代码合并到 master 分支和 develop 分支
- hotfix分支；用于修复线上代码的bug。**从 master 分支上拉。**完成 hotfix 后，打上 tag 我们合并回 master 和 develop 分支。
GitFlow主要工作流程
- 1.初始化项目为gitflow , 默认创建master分支 , 然后从master拉取第一个develop分支
- 2.从develop拉取feature分支进行编码开发(多个开发人员拉取多个feature同时进行并行开发 , 互不影响)
- 3.feature分支完成后 , 合并到develop(不推送 , feature功能完成还未提测 , 推送后会影响其他功能分支的开发)；合并feature到develop , 可以选择删除当前feature , 也可以不删除。但当前feature就不可更改了，必须从release分支继续编码修改

4.从develop拉取release分支进行提测 , 提测过程中在release分支上修改BUG

5.release分支上线后 , 合并release分支到develop/master并推送；合并之后，可选删除当前release分支，若不删除，则当前release不可修改。线上有问题也必须从master拉取hotfix分支进行修改；

6.上线之后若发现线上BUG , 从master拉取hotfix进行BUG修改；

7.hotfix通过测试上线后，合并hotfix分支到develop/master并推送；合并之后，可选删除当前hotfix ，若不删除，则当前hotfix不可修改，若补丁未修复，需要从master拉取新的hotfix继续修改；

8.当进行一个feature时 , 若develop分支有变动 , 如其他开发人员完成功能并上线 , 则需要将完成的功能合并到自己分支上，即合并develop到当前feature分支；

9.当进行一个release分支时 , 若develop分支有变动 , 如其他开发人员完成功能并上线 , 则需要将完成的功能合并到自己分支上，即合并develop到当前release分支 (!!! 因为当前release分支通过测试后会发布到线上 , 如果不合并最新的develop分支 , 就会发生丢代码的情况)；
GitFlow的好处

为不同的分支分配一个明确的角色，并定义分支之间如何交互以及什么时间交互；可以帮助大型项目理清分支之间的关系，简化分支的复杂度。

### 11. 使用过git cherry-pick，有什么作用？

命令git cherry-pick可以把branch A的commit复制到branch B上。
在branch B上进行命令操作：

- 复制单个提交：git cherry-pick commitId
- 复制多个提交：git cherry-pick commitId1…commitId3
注意：复制多个提交的命令不包含commitId1.

### 12. git跟其他版本控制器有啥区别？
GIT是分布式版本控制系统，其他类似于SVN是集中式版本控制系统。

分布式区别于集中式在于：每个节点的地位都是平等，拥有自己的版本库，在没有网络的情况下，对工作空间内代码的修改可以提交到本地仓库，此时的本地仓库相当于集中式的远程仓库，可以基于本地仓库进行提交、撤销等常规操作，从而方便日常开发。

### 13.我们在本地工程常会修改一些配置文件，这些文件不需要被提交，而我们又不想每次执行git status时都让这些文件显示出来，我们该如何操作？
首先利用命令touch .gitignore新建文件
```
$ touch .gitignore
```
然后往文件中添加需要忽略哪些文件夹下的什么类型的文件
```
$ vim .gitignore
$ cat .gitignore
/target/class
.settings
.imp
*.ini
```
注意：忽略/target/class文件夹下所有后缀名为.settings，.imp的文件，忽略所有后缀名为.ini的文件。
### 14. 如何把本地仓库的内容推向一个空的远程仓库？

首先确保本地仓库与远程之间是连同的。如果提交失败，则需要进行下面的命令进行连通：
```
git remote add origin XXXX
```
意：XXXX是你的远程仓库地址。
如果是第一次推送，则进行下面命令：
```
git push -u origin master
```
注意：-u 是指定origin为默认主分支
之后的提交，只需要下面的命令：

```
git push origin master
```

## 计算机基础

### 1.CPU基础

CPU即处理器，是计算机中控制数据操控的电路。它主要由三部分构成：算术/逻辑单元、控制单元和寄存器单元。它们的作用分别为执行运算、协调机器活动以及临时存储。

### 2.CPU与主存

CPU中的寄存器分为通用寄存器和专用寄存器，通用寄存器用于临时存放CPU正在使用的数据，而专用寄存器用于CPU专有用途，比如指令寄存器和程序计数器。CPU与主存的通过总线进行通信，CPU通过控制单元能够操作主存中的数据。
执行两个数值相加的过程大致为：从主存读取第一个值放到寄存器1->从主存读取第二个值放到寄存器2->两个寄存器保存的值作为输入送到加法电路->将加法结果保存到寄存器3->控制单元将结果放到主存中。


![](https://static01.imgkr.com/temp/a4b5222a2041439ab23e94b665d10694.png)

### 3.程序等同数据
原始的计算机并不像现代计算机一样将程序保存起来，以前的人们只对数据进行保存，而设备执行的步骤作为计算机的一部分而被内置在控制单元中。这样就很不灵活，最多只能通过重新布线来提升灵活性。将程序与数据视作相同本质是很大的思想突破，因为人们一直认为它们是不同的事物，数据应该存放在主存中而程序应该属于CPU的一部分。
将程序作为数据一样保存在主存中大有好处，控制单元能够从主存读取程序，然后对它们解码并执行。当我们要修改执行程序时可以在计算机的主存中修改，而不必对CPU更改或重新布线。

### 4.指令系统
程序包含了大量的机器指令，CPU对这些指令进行解码并执行。CPU分为两类体系：精简指令集计算机（RISC）和复杂指令集计算机(CISC)。RISC提供了最小的机器指令集，计算机效率高速度快且制造成本低。而CISC提供了强大丰富的指令集，能更方便实现复杂的软件。
机器指令分为三类：数据传输类、算术/逻辑类与控制类。
数据传输类指令用于将数据从一个地方移动到另一个地方。比如将主存单元的内容加载到寄存器的LOAD指令，反之将寄存器的内容保存到主存的STORE指令。此外，CPU与其它设备（键盘、鼠标、打印机、显示器、磁盘等）进行通信的指令被称为I/O指令。
算术/逻辑类指令用于让控制单元请求在算术/逻辑单元内执行运算。这些运算包括算术、与、或、异或和位移等。
控制类指令用于指导程序执行。比如转移（JUMP）指令，它包括无条件转移和条件转移。


![](https://imgkr2.cn-bj.ufileos.com/1a58b20a-d665-46d5-b2e3-84a8596a8e1c.png?UCloudPublicKey=TOKEN_8d8b72be-579a-4e83-bfd0-5f6ce1546f13&Signature=93EHWcgxOjJFJ%252FTvyIvs%252FiM886g%253D&Expires=1612336614)

### 5.指令寄存器与程序计数器

CPU将主存的指令加载进来解码并执行，其中涉及两个重要寄存器：指令寄存器与程序计数器。指令寄存器用于存储正在执行的指令，而程序计数器则保持下一个待执行的指令地址。
CPU向主存请求加载程序计数器指定的地址的指令，将其存放到指令寄存器中，加载后将程序计数器的值加2（假如指令长度为2个字节）。


### 6.指令如何执行

比如我们要计算11+22，假设过程为：将主存地址为00的内容加载到寄存器1中->将主存地址为01的内容加载到寄存器2中->将寄存器1和寄存器2的数据相加并将结果保存到寄存器3->将寄存器3的结果存储到主存地址为02的位置->停止。
这个过程CPU涉及到四个操作：加载(load)、存储(store)、加法(add)和停止(halt)。可以对这些操作进行编码，比如可以分别用1、2、3、0000表示。

```
1100
1201
3312
2302
0000
```

![](https://imgkr2.cn-bj.ufileos.com/85a20090-1ce0-4d8c-9e8e-e919f629e381.png?UCloudPublicKey=TOKEN_8d8b72be-579a-4e83-bfd0-5f6ce1546f13&Signature=Awh7DkmykHlscKsweKoxAayw4oc%253D&Expires=1612336658)

### 7.控制器
CPU与其他设备的通信一般通过控制器来实现，控制器可能在主板上，也可能以电路板形式插到主板。控制器本身可以看成是小型计算机，也有自己简单的CPU。以前每连接一种外设都需要购买对应的控制器，而现在随着通用串行总线（USB）成为通用的标准，很多外设都可以直接用USB控制器作为通信接口。每个控制器都连接在总线上，通过总线进行通信。

### 8.直接存储器存取
直接存储器存取（DMA）是一种提升外设通信性能的措施，CPU并非总是需要使用总线，在总线空闲的时间里控制器能够充分利用起来。因为控制器都与总线相连接，而控制器又有执行指令的能力，所以可以将CPU的一些工作分给控制器来完成。比如在磁盘中检索数据时，CPU可以将告知控制器，然后由控制器找到数据并放到主存上，期间CPU可以去执行其他任务。这样能节省CPU资源。不过DMA会使总线通信更加复杂，而且会导致总线竞争问题。总线瓶颈源自冯诺依曼体系结构。
专注于人工智能、读书与感想、聊聊数学、计算机科学、分布式、机器学习、深度学习、自然语言处理、算法与数据结构、Java深度、Tomcat内核等。

## 数据结构与算法

### 1. 什么是复杂度分析 ？

1.数据结构和算法解决是 “如何让计算机更快时间、更省空间的解决问题”。

2.因此需从执行时间和占用空间两个维度来评估数据结构和算法的性能。

3.分别用时间复杂度和空间复杂度两个概念来描述性能问题，二者统称为复杂度。

4.复杂度描述的是算法执行时间（或占用空间）与数据规模的增长关系。

### 2. 为什么要进行复杂度分析 ？

1.和性能测试相比，复杂度分析有不依赖执行环境、成本低、效率高、易操作、指导性强的特点。

2.掌握复杂度分析，将能编写出性能更优的代码，有利于降低系统开发和维护成本。

### 3. 如何进行复杂度分析 ？

#### 1 大 O 表示法
算法的执行时间与每行代码的执行次数成正比，用 T(n) = O(f(n)) 表示，其中 T(n) 表示算法执行总时间，f(n) 表示每行代码执行总次数，而 n 往往表示数据的规模。这就是大 O 时间复杂度表示法。

#### 2 时间复杂度
1）定义

算法的时间复杂度，也就是算法的时间量度。

大 O 时间复杂度表示法 实际上并不具体表示代码真正的执行时间，而是表示 代码执行时间随数据规模增长的变化趋势，所以也叫 渐进时间复杂度，简称 时间复杂度（asymptotic time complexity）。
例子1：

```
function aFun() {
    console.log("Hello, World!");      //  需要执行 1 次
    return 0;       // 需要执行 1 次
}
```

那么这个方法需要执行 2 次运算。

例子 2：

```
function bFun(n) {
    for(let i = 0; i < n; i++) {         // 需要执行 (n + 1) 次
        console.log("Hello, World!");      // 需要执行 n 次
    }
    return 0;       // 需要执行 1 次
}
```
那么这个方法需要执行 ( n + 1 + n + 1 ) = 2n +2 次运算。

例子 3：

```
 function cal(n) {
   let sum = 0; // 1 次
   let i = 1; // 1 次
   let j = 1; // 1 次
   for (; i <= n; ++i) {  // n 次
     j = 1;  // n 次
     for (; j <= n; ++j) {  // n * n ，也即是  n平方次
       sum = sum +  i * j;  // n * n ，也即是  n平方次
     }
   }
 }
```
注意，这里是二层 for 循环，所以第二层执行的是 n * n = n2 次，而且这里的循环是 ++i，和例子 2 的是 i++，是不同的，是先加与后加的区别。

那么这个方法需要执行 ( n2 + n2 + n + n + 1 + 1 +1 ) = 2n2 +2n + 3 。

2）特点
以时间复杂度为例，由于 时间复杂度 描述的是算法执行时间与数据规模的 增长变化趋势，所以 常量、低阶、系数 实际上对这种增长趋势不产生决定性影响，所以在做时间复杂度分析时 忽略 这些项。

所以，上面例子1 的时间复杂度为 T(n) = O(1)，例子2 的时间复杂度为 T(n) = O(n)，例子3 的时间复杂度为 T(n) = O(n2)。
#### 3 时间复杂度分析

- 只关注循环执行次数最多的一段代码
单段代码看高频：比如循环。
```
function cal(n) { 
   let sum = 0;
   let i = 1;
   for (; i <= n; ++i) {
     sum = sum + i;
   }
   return sum;
 }
```
执行次数最多的是 for 循环及里面的代码，执行了 n 次，所以时间复杂度为 O(n)。

- 加法法则：总复杂度等于量级最大的那段代码的复杂度
多段代码取最大：比如一段代码中有单循环和多重循环，那么取多重循环的复杂度。

```
function cal(n) {
   let sum_1 = 0;
   let p = 1;
   for (; p < 100; ++p) {
     sum_1 = sum_1 + p;
   }

   let sum_2 = 0;
   let q = 1;
   for (; q < n; ++q) {
     sum_2 = sum_2 + q;
   }
 
   let sum_3 = 0;
   let i = 1;
   let j = 1;
   for (; i <= n; ++i) {
     j = 1; 
     for (; j <= n; ++j) {
       sum_3 = sum_3 +  i * j;
     }
   }
 
   return sum_1 + sum_2 + sum_3;
 }
```

 上面代码分为三部分，分别求 sum_1、sum_2、sum_3 ，主要看循环部分。

第一部分，求 sum_1 ，明确知道执行了 100 次，而和 n 的规模无关，是个常量的执行时间，不能反映增长变化趋势，所以时间复杂度为 O(1)。

第二和第三部分，求 sum_2 和 sum_3 ，时间复杂度是和 n 的规模有关的，为别为 O(n) 和 O(n2)。

所以，取三段代码的最大量级，上面例子的最终的时间复杂度为 O(n2)。

同理类推，如果有 3 层 for 循环，那么时间复杂度为 O(n3)，4 层就是 O(n4)。

所以，总的时间复杂度就等于量级最大的那段代码的时间复杂度。

- 乘法法则：嵌套代码的复杂度等于嵌套内外代码复杂度的乘积
嵌套代码求乘积：比如递归、多重循环等。
```
function cal(n) {
   let ret = 0; 
   let i = 1;
   for (; i < n; ++i) {
     ret = ret + f(i); // 重点为  f(i)
   } 
 } 
 
function f(n) {
  let sum = 0;
  let i = 1;
  for (; i < n; ++i) {
    sum = sum + i;
  } 
  return sum;
 }
```
方法 cal 循环里面调用 f 方法，而 f 方法里面也有循环。

所以，整个 cal() 函数的时间复杂度就是，T(n) = T1(n) * T2(n) = O(n*n) = O(n2) 。

- 多个规模求加法：比如方法有两个参数控制两个循环的次数，那么这时就取二者复杂度相加
```
function cal(m, n) {
  let sum_1 = 0;
  let i = 1;
  for (; i < m; ++i) {
    sum_1 = sum_1 + i;
  }

  let sum_2 = 0;
  let j = 1;
  for (; j < n; ++j) {
    sum_2 = sum_2 + j;
  }

  return sum_1 + sum_2;
}
```
以上代码也是求和 ，求 sum_1 的数据规模为 m、求 sum_2 的数据规模为 n，所以时间复杂度为 O(m+n)。

公式：T1(m) + T2(n) = O(f(m) + g(n)) 。

- 多个规模求乘法：比如方法有两个参数控制两个循环的次数，那么这时就取二者复杂度相乘
```
function cal(m, n) {
  let sum_3 = 0;
   let i = 1;
   let j = 1;
   for (; i <= m; ++i) {
     j = 1; 
     for (; j <= n; ++j) {
       sum_3 = sum_3 +  i * j;
     }
   }
}

```
以上代码也是求和，两层 for 循环 ，求 sum_3 的数据规模为 m 和 n，所以时间复杂度为 O(m*n)。

公式：T1(m) * T2(n) = O(f(m) * g(n)) 。

### 4.常用的时间复杂度分析


- 多项式阶：随着数据规模的增长，算法的执行时间和空间占用，按照多项式的比例增长。

包括 O(1)（常数阶）、O(logn)（对数阶）、O(n)（线性阶）、O(nlogn)（线性对数阶）、O(n2) （平方阶）、O(n3)（立方阶）。

除了 O(logn)、O(nlogn) ，其他的都可从上面的几个例子中看到。

下面举例说明 O(logn)（对数阶）：

```
let i=1;
while (i <= n)  {
   i = i * 2;
}
```

代码是从 1 开始，每次循环就乘以 2，当大于 n 时，循环结束。

其实就是高中学过的等比数列，i 的取值就是一个等比数列。在数学里面是这样子的：

20 21 22 ... 2k ... 2x = n

所以，我们只要知道 x 值是多少，就知道这行代码执行的次数了，通过 2x = n 求解 x，数学中求解得 x = log2n 。所以上面代码的时间复杂度为 O(log2n)。

实际上，不管是以 2 为底、以 3 为底，还是以 10 为底，我们可以把所有对数阶的时间复杂度都记为 O(logn)。为什么呢？

因为对数之间是可以互相转换的，log3n = log32 * log2n，所以 O(log3n) = O(C * log2n)，其中 C=log32 是一个常量。

由于 时间复杂度 描述的是算法执行时间与数据规模的 增长变化趋势，所以 常量、低阶、系数 实际上对这种增长趋势不产生决定性影响，所以在做时间复杂度分析时 忽略 这些项。

因此，在对数阶时间复杂度的表示方法里，我们忽略对数的 “底”，统一表示为 O(logn)。

下面举例说明 O(nlogn)（对数阶）：

```
function aFun(n){
  let i = 1;
  while (i <= n)  {
     i = i * 2;
  }
  return i
}

function cal(n) { 
   let sum = 0;
   for (let i = 1; i <= n; ++i) {
     sum = sum + aFun(n);
   }
   return sum;
 }
```
aFun 的时间复杂度为 O(logn)，而 cal 的时间复杂度为 O(n)，所以上面代码的时间复杂度为 T(n) = T1(logn) * T2(n) = O(logn*n) = O(nlogn) 。

- 非多项式阶：随着数据规模的增长，算法的执行时间和空间占用暴增，这类算法性能极差。
包括 O(2n)（指数阶）、O(n!)（阶乘阶）。

O(2n)（指数阶）例子：

```
aFunc( n ) {
    if (n <= 1) {
        return 1;
    } else {
        return aFunc(n - 1) + aFunc(n - 2);
    }
}
```

参考答案：
显然运行次数，T(0) = T(1) = 1，同时 T(n) = T(n - 1) + T(n - 2) + 1，这里的 1 是其中的加法算一次执行。
显然 T(n) = T(n - 1) + T(n - 2) 是一个斐波那契数列，通过归纳证明法可以证明，当 n >= 1 时 T(n) < (5/3)n，同时当 n > 4 时 T(n) >= (3/2)n。
所以该方法的时间复杂度可以表示为 O((5/3)n)，简化后为 O(2n)。
可见这个方法所需的运行时间是以指数的速度增长的。
如果大家感兴趣，可以试下分别用 1，10，100 的输入大小来测试下算法的运行时间，相信大家会感受到时间复杂度的无穷魅力。


### 5.时间复杂度分类

时间复杂度可以分为：

- 最好情况时间复杂度（best case time complexity）：在最理想的情况下，执行这段代码的时间复杂度。
- 最坏情况时间复杂度（worst case time complexity）：在最糟糕的情况下，执行这段代码的时间复杂度。
- 平均情况时间复杂度（average case time complexity），用代码在所有情况下执行的次数的加权平均值表示。也叫 加权平均时间复杂度 或者 期望时间复杂度。
- 均摊时间复杂度（amortized time complexity）: 在代码执行的所有复杂度情况中绝大部分是低级别的复杂度，个别情况是高级别复杂度且发生具有时序关系时，可以将个别高级别复杂度均摊到低级别复杂度上。基本上均摊结果就等于低级别复杂度。
举例说明：

```
// n 表示数组 array 的长度
function find(array, n, x) {
  let i = 0;
  let pos = -1;
  for (; i < n; ++i) {
    if (array[i] == x) {
      pos = i; 
      break;
    }
  }
  return pos;
}
```

find 函数实现的功能是在一个数组中找到值等于 x 的项，并返回索引值，如果没找到就返回 -1 。

最好情况时间复杂度，最坏情况时间复杂度

如果数组中第一个值就等于 x，那么时间复杂度为 O(1)，如果数组中不存在变量 x，那我们就需要把整个数组都遍历一遍，时间复杂度就成了 O(n)。所以，不同的情况下，这段代码的时间复杂度是不一样的。

所以上面代码的 最好情况时间复杂度为 O(1)，最坏情况时间复杂度为 O(n)。

平均情况时间复杂度

如何分析平均时间复杂度 ？代码在不同情况下复杂度出现量级差别，则用代码所有可能情况下执行次数的加权平均值表示。

要查找的变量 x 在数组中的位置，有 n+1 种情况：在数组的 0～n-1 位置中和不在数组中。我们把每种情况下，查找需要遍历的元素个数累加起来，然后再除以 n+1，就可以得到需要遍历的元素个数的平均值，即：



省略掉系数、低阶、常量，所以，这个公式简化之后，得到的平均时间复杂度就是 O(n)。

我们知道，要查找的变量 x，要么在数组里，要么就不在数组里。这两种情况对应的概率统计起来很麻烦，我们假设在数组中与不在数组中的概率都为 1/2。另外，要查找的数据出现在 0～n-1 这 n 个位置的概率也是一样的，为 1/n。所以，根据概率乘法法则，要查找的数据出现在 0～n-1 中任意位置的概率就是 1/(2n)。

因此，前面的推导过程中存在的最大问题就是，没有将各种情况发生的概率考虑进去。如果我们把每种情况发生的概率也考虑进去，那平均时间复杂度的计算过程就变成了这样：



这个值就是概率论中的 加权平均值，也叫 期望值，所以平均时间复杂度的全称应该叫 加权平均时间复杂度 或者 期望时间复杂度。

所以，根据上面结论推导出，得到的 平均时间复杂度 仍然是 O(n)。

均摊时间复杂度

均摊时间复杂度就是一种特殊的平均时间复杂度 (应用场景非常特殊，非常有限，这里不说)。


### 6.时间复杂度消耗时间排序
常用的时间复杂度所耗费的时间从小到大依次是：

O(1) < O(logn) < (n) < O(nlogn) < O(n2) < O(n3) < O(2n) < O(n!) < O(nn)

### 7.空间复杂度分析

时间复杂度的全称是 渐进时间复杂度，表示 算法的执行时间与数据规模之间的增长关系 。

类比一下，空间复杂度全称就是 渐进空间复杂度（asymptotic space complexity），表示 算法的存储空间与数据规模之间的增长关系 。

定义：算法的空间复杂度通过计算算法所需的存储空间实现，算法的空间复杂度的计算公式记作：S(n) = O(f(n))，其中，n 为问题的规模，f(n) 为语句关于 n 所占存储空间的函数。

```
function print(n) {
 const newArr = []; // 第 2 行
 newArr.length = n; // 第 3 行
  for (let i = 0; i <n; ++i) {
    newArr[i] = i * i;
  }

  for (let j = n-1; j >= 0; --j) {
    console.log(newArr[i])
  }
}
```
跟时间复杂度分析一样，我们可以看到，第 2 行代码中，我们申请了一个空间存储变量 newArr ，是个空数组。第 3 行把 newArr 的长度修改为 n 的长度的数组，每项的值为 undefined ，除此之外，剩下的代码都没有占用更多的空间，所以整段代码的空间复杂度就是 O(n)。

我们常见的空间复杂度就是 O(1)、O(n)、O(n2)，像 O(logn)、O(nlogn) 这样的对数阶复杂度平时都用不到。

### 8.如何掌握好复杂度分析方法 ？
平时我们在写代码时，是用 空间换时间 还是 时间换空间，可以根据算法的时间复杂度和空间复杂度来衡量。



## 性能优化

### 1.性能优化的几个方面?
1.资源压缩合并,减少HTTP请求

2.非核心代码异步加载

3.利用浏览器缓存

4.使用CDN

5.预解析DNS

### 2.如何进行首屏优化
1》首先对于首屏，我认为用户体验有三个阶段：

①就是页面第一个东西加载出来：用户会感觉到自己已经成功访问到这个网址了

②页面第一个含有有用信息的东西加载出来：用户会觉得能在这个网站上获取到有用的信息

③页面可以进行交互：用户进行交互体验

2》然后对前面所学的性能优化进行一下总结即可


### 3.什么情况会造成内存泄漏？

避免意外的全局变量的产生（非严格模式）
称为全局变量后 就不会在函数执行完被回收掉了

避免反复运行形成大量的闭包

避免脱离的DOM元素
举个例子：

![](https://imgkr2.cn-bj.ufileos.com/7562ab7d-3565-4dda-8dc3-4f59e180dd9e.png?UCloudPublicKey=TOKEN_8d8b72be-579a-4e83-bfd0-5f6ce1546f13&Signature=qKULRS7roAWcJ%252BTIwrdgRJRX4wc%253D&Expires=1612438773)

### 4.异步加载?
- 动态脚本加载
- defer
- async

### 5.加载方式区别？
- defer是在html解析完毕才执行,如果有多个则按加载顺序执行
- async是加载完毕后立即执行,如果是多个,执行顺序与加载顺序无关

### 6.浏览器缓存?

#### 分类
强缓存

是指在时间之内不会询问服务器是否需要缓存。

Expires(过期时间) Expries:Sun Jun 16 2019 23:55:21 GMT(服务器时间)

Cache-Control(相对时间)

协商缓存

如果本地有缓存,则需要向服务器询问是否需要使用本地缓存。

Last-Modified if-Modified-Since

Etag If-None-Matc

### 7.预加载?
在开发中，可能会遇到这样的情况。有些资源不需要马上用到，但是希望尽早获取，这时候就可以使用预加载。

预加载其实是声明式的 fetch ，强制浏览器请求资源，并且不会阻塞 onload 事件，可以使用以下代码开启预加载
```
<link rel="preload" href="http://example.com">
```
预加载可以一定程度上降低首屏的加载时间，因为可以将一些不影响首屏但重要的文件延后加载，唯一缺点就是兼容性不好。

### 8.预渲染？
可以通过预渲染将下载的文件预先在后台渲染，可以使用以下代码开启预渲染

```
<link rel="prerender" href="http://example.com"> 
```
预渲染虽然可以提高页面的加载速度，但是要确保该页面大概率会被用户在之后打开，否则就是白白浪费资源去渲染。

### 9.CDN?
CDN 的原理是尽可能的在各个地方分布机房缓存数据，这样即使我们的根服务器远在国外，在国内的用户也可以通过国内的机房迅速加载资源。

因此，我们可以将静态资源尽量使用 CDN 加载，由于浏览器对于单个域名有并发请求上限，可以考虑使用多个 CDN 域名。并且对于 CDN 加载静态资源需要注意 CDN 域名要与主站不同，否则每次请求都会带上主站的 Cookie，平白消耗流量。

### 10.DNS 预解析?
DNS 解析也是需要时间的，可以通过预解析的方式来预先获得域名所对应的 IP。
```
<meta http-equiv='x-dns-prefetch-control' content='on'>
<link rel="dns-prefetch" href="//yuchengkai.cn">
```
在https协议中默认a标签不会开启预解析,因此需要手动设置meta

### 11.节流?
考虑一个场景，滚动事件中会发起网络请求，但是我们并不希望用户在滚动过程中一直发起请求，而是隔一段时间发起一次，对于这种情况我们就可以使用节流。

理解了节流的用途，我们就来实现下这个函数
```
// func是用户传入需要防抖的函数
// wait是等待时间
const throttle = (func, wait = 50) => {
  // 上一次执行该函数的时间
  let lastTime = 0
  return function(...args) {
    // 当前时间
    let now = +new Date()
    // 将当前时间和上一次执行函数时间对比
    // 如果差值大于设置的等待时间就执行函数
    if (now - lastTime > wait) {
      lastTime = now
      func.apply(this, args)
    }
  }
}

setInterval(
  throttle(() => {
    console.log(1)
  }, 500),
  1
)

```
### 12.防抖?
考虑一个场景，有一个按钮点击会触发网络请求，但是我们并不希望每次点击都发起网络请求，而是当用户点击按钮一段时间后没有再次点击的情况才去发起网络请求，对于这种情况我们就可以使用防抖。

理解了防抖的用途，我们就来实现下这个函数
```
// func是用户传入需要防抖的函数
// wait是等待时间
const debounce = (func, wait = 50) => {
  // 缓存一个定时器id
  let timer = 0
  // 这里返回的函数是每次用户实际调用的防抖函数
  // 如果已经设定过定时器了就清空上一次的定时器
  // 开始一个新的定时器，延迟执行用户传入的方法
  return function(...args) {
    if (timer) clearTimeout(timer)
    timer = setTimeout(() => {
      func.apply(this, args)
    }, wait)
  }
}
```
### 13.懒执行?
懒执行就是将某些逻辑延迟到使用时再计算。该技术可以用于首屏优化，对于某些耗时逻辑并不需要在首屏就使用的，就可以使用懒执行。懒执行需要唤醒，一般可以通过定时器或者事件的调用来唤醒。

### 14.懒加载?
懒加载就是将不关键的资源延后加载。

懒加载的原理就是只加载自定义区域（通常是可视区域，但也可以是即将进入可视区域）内需要加载的东西。对于图片来说，先设置图片标签的 src 属性为一张占位图，将真实的图片资源放入一个自定义属性中，当进入自定义区域时，就将自定义属性替换为 src 属性，这样图片就会去下载资源，实现了图片懒加载。

懒加载不仅可以用于图片，也可以使用在别的资源上。比如进入可视区域才开始播放视频等等。

### 15.图片优化?

计算图片大小
对于一张 100 * 100 像素的图片来说，图像上有 10000 个像素点，如果每个像素的值是 RGBA 存储的话，那么也就是说每个像素有 4 个通道，每个通道 1 个字节（8 位 = 1个字节），所以该图片大小大概为 39KB（10000 * 1 * 4 / 1024）。

但是在实际项目中，一张图片可能并不需要使用那么多颜色去显示，我们可以通过减少每个像素的调色板来相应缩小图片的大小。

了解了如何计算图片大小的知识，那么对于如何优化图片，想必大家已经有 2 个思路了：

- 减少像素点
- 减少每个像素点能够显示的颜色

### 16.图片加载优化?
1.不用图片。很多时候会使用到很多修饰类图片，其实这类修饰图片完全可以用 CSS 去代替。

2.对于移动端来说，屏幕宽度就那么点，完全没有必要去加载原图浪费带宽。一般图片都用 CDN 加载，可以计算出适配屏幕的宽度，然后去请求相应裁剪好的图片。2。 对于移动端来说，屏幕宽度就那么点，完全没有必要去加载原图浪费带宽。一般图片都用 CDN 加载，可以计算出适配屏幕的宽度，然后去请求相应裁剪好的图片。
3.小图使用 base64 格式

4.将多个图标文件整合到一张图片中（雪碧图）

5.选择正确的图片格式：

1.对于能够显示 WebP 格式的浏览器尽量使用 WebP 格式。因为 WebP 格式具有更好的图像数据压缩算法，能带来更小的图片体积，而且拥有肉眼识别无差异的图像质量，缺点就是兼容性并不好

2.小图使用 PNG，其实对于大部分图标这类图片，完全可以使用 SVG 代替

3.照片使用 JPEG

### 17.js css 顺序对前端优化影响?
上面我们说到了整个渲染流程，但是没有说到 css 和 js 对渲染的影响。渲染树的构成必须要 DOM 树和 CSSOM 树的，所以尽快的构建 CSSOM 树是一个重要的优化手段，如果 css 文件放在尾部，那么整个过程就是一个串行的过程先解析了 dom，再去解析 css。所以 css 我们一般都是放在头部，这样 DOM 树和 CSSOM 树的构建是同步进行的。

再来看 js，因为 js 的运行会阻止 DOM 树的渲染的，所以一旦我们的 js 放在了头部，而且也没有异步加载这些操作的话，js 一旦一直在运行，DOM 树就一直构建不出来，那么页面就会一直出现白屏界面，所以一般我们会把 js 文件放在尾部。当然放到尾部也不是就没有问题了，只是问题相对较小，放到尾部的 js 文件如果过大，运行时间长，代码加载时，就会有大量耗时的操作造成页面不可点击，这就是另一个问题，但这肯定比白屏要好，白屏是什么页面都没有，这种是页面有了只是操作不流畅。

js 脚本放在尾部还有一个原因，有时候 js 代码会有操作 dom 节点的情况，如果放在头部执行，DOM树还没有构建，拿不到 DOM 节点但是你又去使用就会出现报错情况，错误没处理好的话页面会直接崩掉

### 18.重排重绘为什么会影响渲染，如何避免?
重排和重绘为什么会影响渲染，哪个影响更大，如何避免是经常被问到的一道题目，我们先来说一下重绘

- 重绘

重绘指的是不影响界面布局的操作，比如更改颜色，那么根据上面的渲染讲解我们知道，重绘之后我们只需要在重复进行一下样式计算，就可以直接渲染了，对浏览器渲染的影响相对较小

- 重排

重排指的是影响界面布局的操作，比如改变宽高，隐藏节点等。对于重排就不是一个重新计算样式那么简单了，因为改变了布局，根据上面的渲染流程来看涉及到的阶段有样式计算，布局树重新生成，分层树重新生成，所以重排对浏览器的渲染影响是比较高的

- 避免方法

 1.js 尽量减少对样式的操作，能用 css 完成的就用 css

 2.对 dom 操作尽量少，能用 createDocumentFragment 的地方尽量用

 3.如果必须要用 js 操作样式，能合并尽量合并不要分多次操作

 4.resize 事件 最好加上防抖，能尽量少触发就少触发

 5.加载图片的时候，提前写好宽高

### 本文整理自如下连接:

https://juejin.cn/post/6913016498957221901

https://juejin.cn/post/6844903828278493197

https://juejin.cn/post/6871956933775982606#heading-21

https://juejin.cn/post/6913022820691738631

https://juejin.cn/post/6844903998177148935

https://juejin.cn/post/6844903862634037255

https://juejin.cn/post/6921945687559143437

https://zhuanlan.zhihu.com/p/44438844

https://blog.csdn.net/nobody_1/article/details/88956315

https://juejin.cn/post/6844903943487619080

https://github.com/biaochenxuying/blog/issues/29

https://blog.csdn.net/qq_25503949/article/details/108956145

https://blog.csdn.net/qq_37674616/article/details/86490686

https://blog.csdn.net/qianyu6200430/article/details/109712717