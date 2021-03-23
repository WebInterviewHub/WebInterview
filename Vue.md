## Vue

* [1.vue 优点？](#1vue-优点)
* [2.vue 父组件向子组件传递数据？](#2vue-父组件向子组件传递数据)
* [3.子组件像父组件传递事件？](#3子组件像父组件传递事件)
* [4.v-show 和 v-if 指令的共同点和不同点？](#4v-show-和-v-if-指令的共同点和不同点)
* [5. 如何让 CSS 只在当前组件中起作用？](#5-如何让-css-只在当前组件中起作用)
* [6. 的作用是什么?](#6-的作用是什么)
* [7.如何获取 dom?](#7如何获取-dom)
* [8.说出几种 vue 当中的指令和它的用法？](#8说出几种-vue-当中的指令和它的用法)
* [9.vue-loader 是什么？使用它的用途有哪些？](#9vue-loader-是什么使用它的用途有哪些)
* [10.为什么使用 key?](#10为什么使用-key)
* [11.axios 及安装?](#11axios-及安装)
* [12.v-modal 的使用。](#12v-modal-的使用)
* [13. 请说出 vue.cli 项目中 src 目录每个文件夹和文件的用法？](#13-请说出-vuecli-项目中-src-目录每个文件夹和文件的用法)
* [14. 分别简述 computed 和 watch 的使用场景](#14-分别简述-computed-和-watch-的使用场景)
* [15.v-on 可以监听多个方法吗？](#15v-on-可以监听多个方法吗)
* [16.$nextTick 的使用](#16nexttick-的使用)
* [17.vue 组件中 data 为什么必须是一个函数？](#17vue-组件中-data-为什么必须是一个函数)
* [18. 渐进式框架的理解](#18-渐进式框架的理解)
* [19.Vue 中双向数据绑定是如何实现的？](#19vue-中双向数据绑定是如何实现的)
* [20. 单页面应用和多页面应用区别及优缺点](#20-单页面应用和多页面应用区别及优缺点)
* [21.v-if 和 v-for 的优先级](#21v-if-和-v-for-的优先级)
* [22.assets 和 static 的区别](#22assets-和-static-的区别)
* [23.vue 常用的修饰符](#23vue-常用的修饰符)
* [24.vue 的两个核心点](#24vue-的两个核心点)
* [25.vue 和 jQuery 的区别](#25vue-和-jquery-的区别)
* [26. 引进组件的步骤](#26-引进组件的步骤)
* [27.delete 和 Vue.delete 删除数组的区别](#27delete-和-vuedelete-删除数组的区别)
* [28.SPA 首屏加载慢如何解决](#28spa-首屏加载慢如何解决)
* [29.Vue-router 跳转和 location.href 有什么区别](#29vue-router-跳转和-locationhref-有什么区别)
* [30. vue slot](#30-vue-slot)
* [31. 你们 vue 项目是打包了一个 js 文件，一个 css 文件，还是有多个文件？](#31-你们-vue-项目是打包了一个-js-文件一个-css-文件还是有多个文件)
* [32.Vue 里面 router-link 在电脑上有用，在安卓上没反应怎么解决？](#32vue-里面-router-link-在电脑上有用在安卓上没反应怎么解决)
* [33.Vue2 中注册在 router-link 上事件无效解决方法](#33vue2-中注册在-router-link-上事件无效解决方法)
* [34.RouterLink 在 IE 和 Firefox 中不起作用（路由不跳转）的问题](#34routerlink-在-ie-和-firefox-中不起作用路由不跳转的问题)
* [35.axios 的特点有哪些](#35axios-的特点有哪些)
* [36. 请说下封装 vue 组件的过程？](#36-请说下封装-vue-组件的过程)
* [37.params 和 query 的区别](#37params-和-query-的区别)
* [38.vue 初始化页面闪动问题](#38vue-初始化页面闪动问题)
* [39.vue 更新数组时触发视图更新的方法](#39vue-更新数组时触发视图更新的方法)
* [40.vue 常用的 UI 组件库](#40vue-常用的-ui-组件库)
* [41. Vue的生命周期？](#41-vue的生命周期)
* [42.虚拟DOM和DIFF算法？](#42虚拟dom和diff算法)
* [43.vue2和vue3原理？](#43vue2和vue3原理)
* [44.生命周期钩子的一些使用方法：](#44生命周期钩子的一些使用方法)
* [45.开发中常用的指令有哪些?](#45开发中常用的指令有哪些)
* [参考链接](#参考链接)




#### 1.vue 优点？

轻量级框架：只关注视图层，是一个构建数据的视图集合，大小只有几十 kb；

简单易学：国人开发，中文文档，不存在语言障碍 ，易于理解和学习；

双向数据绑定：保留了 angular 的特点，在数据操作方面更为简单；

组件化：保留了 react 的优点，实现了 html 的封装和重用，在构建单页面应用方面有着独特的优势；

视图，数据，结构分离：使数据的更改更为简单，不需要进行逻辑代码的修改，只需要操作数据就能完成相关操作；

虚拟 DOM：dom 操作是非常耗费性能的， 不再使用原生的 dom 操作节点，极大解放 dom 操作，但具体操作的还是 dom 不过是换了另一种方式；

运行速度更快: 相比较与 react 而言，同样是操作虚拟 dom，就性能而言，vue 存在很大的优势。

#### 2.vue 父组件向子组件传递数据？

通过 props

#### 3.子组件像父组件传递事件？

$emit 方法

#### 4.v-show 和 v-if 指令的共同点和不同点？

 共同点：都能控制元素的显示和隐藏；

不同点：实现本质方法不同，v-show 本质就是通过控制 css 中的 display 设置为 none，控制隐藏，只会编译一次；v-if 是动态的向 DOM 树内添加或者删除 DOM 元素，若初始值为 false，就不会编译了。而且 v-if 不停的销毁和创建比较消耗性能。

总结：如果要频繁切换某节点，使用 v-show(切换开销比较小，初始开销较大)。如果不需要频繁切换某节点使用 v-if（初始渲染开销较小，切换开销比较大）。

#### 5. 如何让 CSS 只在当前组件中起作用？

在组件中的 style 前面加上 scoped

#### 6.<keep-alive></keep-alive > 的作用是什么?

 keep-alive 是 Vue 内置的一个组件，可以使被包含的组件保留状态，或避免重新渲染。

#### 7.如何获取 dom?

ref="domName" 用法：this.$refs.domName

#### 8.说出几种 vue 当中的指令和它的用法？

答：v-model 双向数据绑定；

v-for 循环；

v-if v-show 显示与隐藏；

v-on 事件；v-once: 只绑定一次。

#### 9.vue-loader 是什么？使用它的用途有哪些？

答：vue 文件的一个加载器，将 template/js/style 转换成 js 模块。

用途：js 可以写 es6、style 样式可以 scss 或 less、template 可以加 jade 等

#### 10.为什么使用 key?

答：需要使用 key 来给每个节点做一个唯一标识，Diff 算法就可以正确的识别此节点。

作用主要是为了高效的更新虚拟 DOM。

#### 11.axios 及安装?

答：请求后台资源的模块。npm install axios --save 装好，

js 中使用 import 进来，然后. get 或. post。返回在. then 函数中如果成功，失败则是在. catch 函数中。

#### 12.v-modal 的使用。

答：v-model 用于表单数据的双向绑定，其实它就是一个语法糖，这个背后就做了两个操作：

v-bind 绑定一个 value 属性；

v-on 指令给当前元素绑定 input 事件。

#### 13. 请说出 vue.cli 项目中 src 目录每个文件夹和文件的用法？

答：assets 文件夹是放静态资源；components 是放组件；router 是定义路由相关的配置; app.vue 是一个应用主组件；main.js 是入口文件。

#### 14. 分别简述 computed 和 watch 的使用场景

答：computed:

当一个属性受多个属性影响的时候就需要用到 computed

最典型的栗子： 购物车商品结算的时候

watch:

当一条数据影响多条数据的时候就需要用 watch

栗子：搜索数据

#### 15.v-on 可以监听多个方法吗？

答：可以，栗子：<input type="text" v-on="{ input:onInput,focus:onFocus,blur:onBlur,}">。

#### 16.$nextTick 的使用

答：当你修改了 data 的值然后马上获取这个 dom 元素的值，是不能获取到更新后的值，

你需要使用 $nextTick 这个回调，让修改后的 data 值渲染更新到 dom 元素之后在获取，才能成功。

#### 17.vue 组件中 data 为什么必须是一个函数？

答：因为 JavaScript 的特性所导致，在 component 中，data 必须以函数的形式存在，不可以是对象。

组建中的 data 写成一个函数，数据以函数返回值的形式定义，这样每次复用组件的时候，都会返回一份新的 data，相当于每个组件实例都有自己私有的数据空间，它们只负责各自维护的数据，不会造成混乱。而单纯的写成对象形式，就是所有的组件实例共用了一个 data，这样改一个全都改了。

#### 18. 渐进式框架的理解

答：主张最少；可以根据不同的需求选择不同的层级；

#### 19.Vue 中双向数据绑定是如何实现的？

答：vue 双向数据绑定是通过 数据劫持 结合 发布订阅模式的方式来实现的， 也就是说数据和视图同步，数据发生变化，视图跟着变化，视图变化，数据也随之发生改变；

核心：关于 VUE 双向数据绑定，其核心是 Object.defineProperty() 方法。

#### 20. 单页面应用和多页面应用区别及优缺点

答：单页面应用（SPA），通俗一点说就是指只有一个主页面的应用，浏览器一开始要加载所有必须的 html, js, css。所有的页面内容都包含在这个所谓的主页面中。但在写的时候，还是会分开写（页面片段），然后在交互的时候由路由程序动态载入，单页面的页面跳转，仅刷新局部资源。多应用于 pc 端。

多页面（MPA），就是指一个应用中有多个页面，页面跳转时是整页刷新

单页面的优点：

用户体验好，快，内容的改变不需要重新加载整个页面，基于这一点 spa 对服务器压力较小；前后端分离；页面效果会比较炫酷（比如切换页面内容时的专场动画）。

单页面缺点：

不利于 seo；导航不可用，如果一定要导航需要自行实现前进、后退。（由于是单页面不能用浏览器的前进后退功能，所以需要自己建立堆栈管理）；初次加载时耗时多；页面复杂度提高很多。

#### 21.v-if 和 v-for 的优先级

答：当 v-if 与 v-for 一起使用时，v-for 具有比 v-if 更高的优先级，这意味着 v-if 将分别重复运行于每个 v-for 循环中。所以，不推荐 v-if 和 v-for 同时使用。

如果 v-if 和 v-for 一起用的话，vue 中的的会自动提示 v-if 应该放到外层去。

####  22.assets 和 static 的区别

答：相同点：assets 和 static 两个都是存放静态资源文件。项目中所需要的资源文件图片，字体图标，样式文件等都可以放在这两个文件下，这是相同点

不相同点：assets 中存放的静态资源文件在项目打包时，也就是运行 npm run build 时会将 assets 中放置的静态资源文件进行打包上传，所谓打包简单点可以理解为压缩体积，代码格式化。而压缩后的静态资源文件最终也都会放置在 static 文件中跟着 index.html 一同上传至服务器。static 中放置的静态资源文件就不会要走打包压缩格式化等流程，而是直接进入打包好的目录，直接上传至服务器。因为避免了压缩直接进行上传，在打包时会提高一定的效率，但是 static 中的资源文件由于没有进行压缩等操作，所以文件的体积也就相对于 assets 中打包后的文件提交较大点。在服务器中就会占据更大的空间。

建议：将项目中 template 需要的样式文件 js 文件等都可以放置在 assets 中，走打包这一流程。减少体积。而项目中引入的第三方的资源文件如 iconfoont.css 等文件可以放置在 static 中，因为这些引入的第三方文件已经经过处理，我们不再需要处理，直接上传。

#### 23.vue 常用的修饰符

答：.stop：等同于 JavaScript 中的 event.stopPropagation()，防止事件冒泡；

.prevent：等同于 JavaScript 中的 event.preventDefault()，防止执行预设的行为（如果事件可取消，则取消该事件，而不停止事件的进一步传播）；

.capture：与事件冒泡的方向相反，事件捕获由外到内；

.self：只会触发自己范围内的事件，不包含子元素；

.once：只会触发一次。

#### 24.vue 的两个核心点

答：数据驱动、组件系统

数据驱动：ViewModel，保证数据和视图的一致性。

组件系统：应用类 UI 可以看作全部是由组件树构成的。

#### 25.vue 和 jQuery 的区别

答：jQuery 是使用选择器（$）选取 DOM 对象，对其进行赋值、取值、事件绑定等操作，其实和原生的 HTML 的区别只在于可以更方便的选取和操作 DOM 对象，而数据和界面是在一起的。比如需要获取 label 标签的内容：$("lable").val();, 它还是依赖 DOM 元素的值。

Vue 则是通过 Vue 对象将数据和 View 完全分离开来了。对数据进行操作不再需要引用相应的 DOM 对象，可以说数据和 View 是分离的，他们通过 Vue 对象这个 vm 实现相互的绑定。这就是传说中的 MVVM。

#### 26. 引进组件的步骤

答: 在 template 中引入组件；

在 script 的第一行用 import 引入路径；

用 component 中写上组件名称。

#### 27.delete 和 Vue.delete 删除数组的区别

答：delete 只是被删除的元素变成了 empty/undefined 其他的元素的键值还是不变。Vue.delete 直接删除了数组 改变了数组的键值。

#### 28.SPA 首屏加载慢如何解决

答：安装动态懒加载所需插件；使用 CDN 资源。

#### 29.Vue-router 跳转和 location.href 有什么区别

答：使用 location.href='/url'来跳转，简单方便，但是刷新了页面；

使用 history.pushState('/url')，无刷新页面，静态跳转；

引进 router，然后使用 router.push('/url') 来跳转，使用了 diff 算法，实现了按需加载，减少了 dom 的消耗。

其实使用 router 跳转和使用 history.pushState() 没什么差别的，因为 vue-router 就是用了 history.pushState()，尤其是在 history 模式下。

####  30. vue slot

答：简单来说，假如父组件需要在子组件内放一些 DOM，那么这些 DOM 是显示、不显示、在哪个地方显示、如何显示，就是 slot 分发负责的活。

#### 31. 你们 vue 项目是打包了一个 js 文件，一个 css 文件，还是有多个文件？

答：根据 vue-cli 脚手架规范，一个 js 文件，一个 CSS 文件。

#### 32.Vue 里面 router-link 在电脑上有用，在安卓上没反应怎么解决？

答：Vue 路由在 Android 机上有问题，babel 问题，安装 babel polypill 插件解决。

#### 33.Vue2 中注册在 router-link 上事件无效解决方法

答： 使用 @click.native。原因：router-link 会阻止 click 事件，.native 指直接监听一个原生事件。

#### 34.RouterLink 在 IE 和 Firefox 中不起作用（路由不跳转）的问题

答: 方法一：只用 a 标签，不适用 button 标签；方法二：使用 button 标签和 Router.navigate 方法

#### 35.axios 的特点有哪些

答：从浏览器中创建 XMLHttpRequests；

node.js 创建 http 请求；

支持 Promise API；

拦截请求和响应；

转换请求数据和响应数据；

取消请求；

自动换成 json。

axios 中的发送字段的参数是 data 跟 params 两个，两者的区别在于 params 是跟请求地址一起发送的，data 的作为一个请求体进行发送

params 一般适用于 get 请求，data 一般适用于 post put 请求。

#### 36. 请说下封装 vue 组件的过程？

答：1. 建立组件的模板，先把架子搭起来，写写样式，考虑好组件的基本逻辑。(os：思考 1 小时，码码 10 分钟，程序猿的准则。)

\2. 准备好组件的数据输入。即分析好逻辑，定好 props 里面的数据、类型。

\3. 准备好组件的数据输出。即根据组件逻辑，做好要暴露出来的方法。

\4. 封装完毕了，直接调用即可

#### 37.params 和 query 的区别

答：用法：query 要用 path 来引入，params 要用 name 来引入，接收参数都是类似的，分别是 this.$route.query.name 和 this.$route.params.name。

url 地址显示：query 更加类似于我们 ajax 中 get 传参，params 则类似于 post，说的再简单一点，前者在浏览器地址栏中显示参数，后者则不显示

注意点：query 刷新不会丢失 query 里面的数据

params 刷新 会 丢失 params 里面的数据。

#### 38.vue 初始化页面闪动问题

答：使用 vue 开发时，在 vue 初始化之前，由于 div 是不归 vue 管的，所以我们写的代码在还没有解析的情况下会容易出现花屏现象，看到类似于 {{message}} 的字样，虽然一般情况下这个时间很短暂，但是我们还是有必要让解决这个问题的。

首先：在 css 里加上 [v-cloak] {

display: none;

}。

如果没有彻底解决问题，则在根元素加上 style="display: none;" :style="{display:'block'}"

#### 39.vue 更新数组时触发视图更新的方法

答: push()；pop()；shift()；unshift()；splice()； sort()；reverse()

#### 40.vue 常用的 UI 组件库

答：Mint UI，element，VUX

#### 41. Vue的生命周期？

beforeCreate 、created、beforeMount、mounted、beforeUpdate、updated、beforeDestroy、destroyed（创建、挂载、更新、卸载）

挂载中可以操作DOM，创建中不能操作DOM；常用挂载或者创建生命周期就行了

####  42.虚拟DOM和DIFF算法？

将DOM抽象为虚拟DOM, 然后通过新旧虚拟DOM 这两个对象的差异(Diff算法),最终只把变化的部分重新渲染,提高渲染效率的过程; 

diff 是通过JS层面的计算，返回一个patch对象，即补丁对象，在通过特定的操作解析patch对象，完成页面的重新渲染

#### 43.vue2和vue3原理？

**1. vue2和vue3双向数据绑定原理发生了改变**

**vue2** 的双向数据绑定是利用ES5 的一个 API Object.definePropert()对数据进行劫持 结合 发布订阅模式的方式来实现的。

**vue3** 中使用了 es6 的 ProxyAPI 对数据代理。

相比于vue2.x，使用proxy的优势如下

defineProperty只能监听某个属性，不能对全对象监听

可以省去for in、闭包等内容来提升效率（直接绑定整个对象即可）

可以监听数组，不用再去单独的对数组做特异性操作 vue3.x可以检测到数组内部数据的变化

**2、默认进行懒观察（lazy observation）**

在 2.x 版本里，不管数据多大，都会在一开始就为其创建观察者。当数据很大时，这可能会在页面载入时造成明显的性能压力。3.x 版本，只会对「被用于渲染初始可见部分的数据」创建观察者，而且 3.x 的观察者更高效。

**3、更精准的变更通知**

比例来说：2.x 版本中，使用 Vue.set 来给对象新增一个属性时，这个对象的所有 watcher 都会重新运行；3.x 版本中，只有依赖那个属性的 watcher 才会重新运行。

**4、vue3新加入了TypeScript以及PWA的支持**

**5、vue2和vue3组件发送改变**



#### 44.生命周期钩子的一些使用方法：

```js
1.beforecreate:可以在加个loading事件，在加载实例是触发
2.created:初始化完成时的事件写在这里，如在这结束loading事件，异步请求也适宜在这里调用
3.mounted:挂载元素，获取到dom节点
4.updated:如果对数据统一处理，在这里写上相应函数
5.beforeDestroy:可以一个确认停止事件的确认框
6.nextTick:更新数据后立即操作dom
```

#### 45.开发中常用的指令有哪些?

v-model:一般用在表达输入，很轻松的实现表单控件和数据的双向绑定
v-html：更新元素的innerHTML
v-show与v-if：条件渲染，注意二者区别
v-on:click:可以简写为@click,@绑定一个事件。如果事件触发了，就可以指定事件的处理函数
v-for：基于源数据多次渲染元素或模板
v-bind:当表达式的值改变时，将其产生的连带影响，响应式地作用于DOM语法
v-bind:title=”msg”简写：title="msg"

#### 参考链接

https://zhuanlan.zhihu.com/p/92407628

https://blog.csdn.net/qq_37481512/article/details/94400698

https://www.jianshu.com/p/9489fdf7c145

https://zhuanlan.zhihu.com/p/97950650
