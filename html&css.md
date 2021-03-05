## html&&css
* [1. 如何理解CSS盒子模型](#1-如何理解css盒子模型)
* [2.BFC](#2bfc)
* [3.标签语义化](#3标签语义化)
* [4.meta标签](#4meta标签)
* [5.css与javascript引入设置](#5css与javascript引入设置)
* [6.HTML的块级元素，行内元素，行内块元素有哪些,区别是什么](#6html的块级元素行内元素行内块元素有哪些区别是什么)
* [7.CSS3有哪些新特性](#7css3有哪些新特性)
* [８.实现元素隐藏](#８实现元素隐藏)
* [9.如何实现元素水平居中](#9如何实现元素水平居中)
* [10.如何实现元素垂直居中](#10如何实现元素垂直居中)
* [11.Position](#11position)
* [12.定位元素水平垂直居中](#12定位元素水平垂直居中)
* [13.清除浮动](#13清除浮动)
* [14.css选择器有哪些，选择器的优先级](#14css选择器有哪些选择器的优先级)
* [15.各种布局优缺点](#15各种布局优缺点)
* [16.html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 HTML 和 HTML5？](#16html5有哪些新特性移除了那些元素如何处理html5新标签的浏览器兼容问题如何区分-html-和-html5)
* [17. CSS3新增伪类举例：](#17-css3新增伪类举例)
* [18.解释盒模型宽高值得计算方式，边界塌陷，负值作用，box-sizing概念？](#18解释盒模型宽高值得计算方式边界塌陷负值作用box-sizing概念)
* [19.如何实现浏览器内多个标签页之间的通信?](#19如何实现浏览器内多个标签页之间的通信)
* [20.解释下浮动和它的工作原理？清除浮动的方法](#20解释下浮动和它的工作原理清除浮动的方法)

### 1. 如何理解CSS盒子模型

标准盒子模型：宽度=内容的宽度（content）+ border + padding

低版本IE盒子模型：宽度=内容宽度（content+border+padding）

### 2.BFC

```html
## html和css部分

#### 1. 如何理解CSS盒子模型

标准盒子模型：宽度=内容的宽度（content）+ border + padding

低版本IE盒子模型：宽度=内容宽度（content+border+padding）

#### 2.BFC

​```html
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
​```

#### 3.标签语义化

代码结构更加清晰

见名知意，没有基础的人也能知道这部分代码是干嘛的

方便团队开发维护，代码可读性更强

有利于SEO优化，爬虫依赖于标签来确定上下文关系

#### 4.meta标签

meta标签提供关于html文档的元数据，不会显示在页面，但是对于机器是可读的，告诉浏览器怎么解析页面，告诉搜索引擎关键字（SEO优化）

meta作用：告诉机器浏览器该如何解析该页面，描述这个页面的主要内容，可以设置服务器发送到浏览器的http头部内容

charset="utf-8"设置页面使用的字符编码

viewport 设置视口，移动端的适配

#### 5.css与javascript引入设置

script标签的引入一般放在body最后，这样避免脚本过大，加载时间长，导致页面长时间空白，这是因为渲染进程与js进程是互斥的，脚本会阻塞页面的渲染，脚本之间的加载是同步进行的，按引入顺序执行，但是以下两个属性会影响脚本执行与页面渲染的顺序

defer：不会阻塞渲染，这样即使放在header内部，也不会阻塞页面加载，不过js会先于document加载完成，并且也不会影响脚本之间的执行顺序，按照引入顺序执行

async：与defer一样，都是解决阻塞渲染，但它是在document加载完成后才执行，并且它的执行顺序是按照谁先加载完成执行谁，所以对于文件顺序有要求，存在前后依赖的不要使用它

#### 6.HTML的块级元素，行内元素，行内块元素有哪些,区别是什么

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

#### 7.CSS3有哪些新特性

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

#### ８.实现元素隐藏

display：none 不占位，源码可见

opacity: 0 占位，源码可见，透明度0

visibility: hidden 占位，源码可见

position: top:-9999px,left:-9999px 利用定位将元素移出视窗

#### 9.如何实现元素水平居中

行内元素：text-align：center

块元素: margin: 0 auto

position: left: 50%; transform: translate(-50%)

#### 10.如何实现元素垂直居中

height = line-height

verticle-align: middle

position: top: 50%; transform: translate(0,-50%)

#### 11.Position

static 默认

relative 相对定位，不脱标，相对于自身位置进行偏离，不影响元素本身特性，z-index提升层级

absolute 绝对定位，脱标，相对于已有定位的父元素进行偏离，都没有就相对于body进行偏离

fixed 固定定位，脱标，相对于视窗进行偏离

#### 12.定位元素水平垂直居中

宽高固定 position: top:0,left:0,right:0,bottom:0,margin:auto

宽高固定 position：top: 50%, left: 50%, margin-left: -width/2px,margin-top: -height/2px

dispaly: flex; justify-content: center,align-items: center(极力推荐)

position: left: 50%,top: 50%; transform: translate(-50%,-50%)

#### 13.清除浮动

​```
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

​```

#### 14.css选择器有哪些，选择器的优先级

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

#### 15.各种布局优缺点

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

#### 16.html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 HTML 和 HTML5？

  **新特性：**

 HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加。
 拖拽释放(Drag and drop) API
 语义化更好的内容标签（header,nav,footer,aside,article,section）
 音频、视频API(audio,video)
 画布(Canvas) API
 地理(Geolocation) API
 本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失；
 sessionStorage 的数据在浏览器关闭后自动删除
 表单控件，calendar、date、time、email、url、search
 新的技术webworker, websocket, Geolocation

 **移除元素：**
 纯表现的元素：basefont，big，center，font, s，strike，tt，u；
 对可用性产生负面影响的元素：frame，frameset，noframes；
 **h5新标签兼容：**
 IE8/IE7/IE6支持通过document.createElement方法产生的标签，
 可以利用这一特性让这些浏览器支持HTML5新标签，
 当然最好的方式是直接使用成熟的框架、使用最多的是html5shim框架

​```html
 <!--[if lt IE 9]>

 <script> src="http://html5shim.googlecode.com/svn/trunk/html5.js"</script>

 <![endif]-->
​```

 **如何区分：**
 DOCTYPE声明\新增的结构元素\功能元素

#### 17. CSS3新增伪类举例：

 p:first-of-type 选择属于其父元素的首个 <p> 元素的每个 <p> 元素。

 p:last-of-type 选择属于其父元素的最后 <p> 元素的每个 <p> 元素。

 p:only-of-type 选择属于其父元素唯一的 <p> 元素的每个 <p> 元素。

 p:only-child 选择属于其父元素的唯一子元素的每个 <p> 元素。

 p:nth-child(2) 选择属于其父元素的第二个子元素的每个 <p> 元素。

 :enabled :disabled 控制表单控件的禁用状态。

 :checked 单选框或复选框被选中。

#### 18.解释盒模型宽高值得计算方式，边界塌陷，负值作用，box-sizing概念？

 \1. 盒模型：IE 678 下(不添加doctype) 使用ie盒模型，宽度 = 边框 + padding + 内容宽度； chrom、IE9+、(添加doctype) 使用标准盒模型， 宽度 = 内容宽度。
 \2. box-sizing : 为了解决标准黑子和IE盒子的不同，CSS3增添了盒模型属性box-sizing，content-box(默认)，border-box 让元素维持IE传统盒子模型， inherit 继承 父盒子模型；
 \3. 边界塌陷：块元素的 top 与 bottom 外边距有时会合并（塌陷）为单个外边距（合并后最大的外边距），这样的现象称之为 外边距塌陷。
 \4. 负值作用：负margin会改变浮动元素的显示位置，即使我的元素写在DOM的后面，我也能让它显示在最前面。

#### 19.如何实现浏览器内多个标签页之间的通信?

 调用localstorge、cookies等本地存储方式

#### 20.解释下浮动和它的工作原理？清除浮动的方法

浮动元素脱离文档流，不占据空间。浮动元素碰到包含它的边框或者浮动元素的边框停留。

 1.使用空标签清除浮动。

 这种方法是在所有浮动标签后面添加一个空标签 定义css clear:both. 弊端就是增加了无意义标签。

 2.使用after伪对象清除浮动

　该方法只适用于非IE浏览器。具体写法可参照以下示例。使用中需注意以下几点。一、该方法中必须为需要清除浮动元素的伪对象中设置 height:0，否则该元素会比实际高出若干像素；

  \#parent:after{

　　content:".";

　　height:0;

　　visibility:hidden;

　　display:block;

　　clear:both;

　}

 3.设置overflow为hidden或者auto

 4.浮动外部元素



#### 参考链接

https://www.cnblogs.com/cui-ting/p/11078833.html
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

#### 15.各种布局优缺点

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

#### 16.html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 HTML 和 HTML5？

  **新特性：**

 HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加。
 拖拽释放(Drag and drop) API
 语义化更好的内容标签（header,nav,footer,aside,article,section）
 音频、视频API(audio,video)
 画布(Canvas) API
 地理(Geolocation) API
 本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失；
 sessionStorage 的数据在浏览器关闭后自动删除
 表单控件，calendar、date、time、email、url、search
 新的技术webworker, websocket, Geolocation

 **移除元素：**
 纯表现的元素：basefont，big，center，font, s，strike，tt，u；
 对可用性产生负面影响的元素：frame，frameset，noframes；
 **h5新标签兼容：**
 IE8/IE7/IE6支持通过document.createElement方法产生的标签，
 可以利用这一特性让这些浏览器支持HTML5新标签，
 当然最好的方式是直接使用成熟的框架、使用最多的是html5shim框架

```html
 <!--[if lt IE 9]>

 <script> src="http://html5shim.googlecode.com/svn/trunk/html5.js"</script>

 <![endif]-->
```

 **如何区分：**
 DOCTYPE声明\新增的结构元素\功能元素

#### 17. CSS3新增伪类举例：

 p:first-of-type 选择属于其父元素的首个 <p> 元素的每个 <p> 元素。

 p:last-of-type 选择属于其父元素的最后 <p> 元素的每个 <p> 元素。

 p:only-of-type 选择属于其父元素唯一的 <p> 元素的每个 <p> 元素。

 p:only-child 选择属于其父元素的唯一子元素的每个 <p> 元素。

 p:nth-child(2) 选择属于其父元素的第二个子元素的每个 <p> 元素。

 :enabled :disabled 控制表单控件的禁用状态。

 :checked 单选框或复选框被选中。

#### 18.解释盒模型宽高值得计算方式，边界塌陷，负值作用，box-sizing概念？

 \1. 盒模型：IE 678 下(不添加doctype) 使用ie盒模型，宽度 = 边框 + padding + 内容宽度； chrom、IE9+、(添加doctype) 使用标准盒模型， 宽度 = 内容宽度。
 \2. box-sizing : 为了解决标准黑子和IE盒子的不同，CSS3增添了盒模型属性box-sizing，content-box(默认)，border-box 让元素维持IE传统盒子模型， inherit 继承 父盒子模型；
 \3. 边界塌陷：块元素的 top 与 bottom 外边距有时会合并（塌陷）为单个外边距（合并后最大的外边距），这样的现象称之为 外边距塌陷。
 \4. 负值作用：负margin会改变浮动元素的显示位置，即使我的元素写在DOM的后面，我也能让它显示在最前面。

#### 19.如何实现浏览器内多个标签页之间的通信?

 调用localstorge、cookies等本地存储方式

#### 20.解释下浮动和它的工作原理？清除浮动的方法

浮动元素脱离文档流，不占据空间。浮动元素碰到包含它的边框或者浮动元素的边框停留。

 1.使用空标签清除浮动。

 这种方法是在所有浮动标签后面添加一个空标签 定义css clear:both. 弊端就是增加了无意义标签。

 2.使用after伪对象清除浮动

　该方法只适用于非IE浏览器。具体写法可参照以下示例。使用中需注意以下几点。一、该方法中必须为需要清除浮动元素的伪对象中设置 height:0，否则该元素会比实际高出若干像素；

  \#parent:after{

　　content:".";

　　height:0;

　　visibility:hidden;

　　display:block;

　　clear:both;

　}

 3.设置overflow为hidden或者auto

 4.浮动外部元素



#### 参考链接

https://www.cnblogs.com/cui-ting/p/11078833.html
