## React
* [1.什么是React？](#1什么是react)
* [2.React有什么特点？](#2react有什么特点)
* [3.列出React的一些主要优点。](#3列出react的一些主要优点)
* [4.React有哪些限制？](#4react有哪些限制)
* [5.什么是JSX？](#5什么是jsx)
* [6.你了解 Virtual DOM 吗？解释一下它的工作原理。](#6你了解-virtual-dom-吗解释一下它的工作原理)
* [7.为什么浏览器无法读取JSX？](#7为什么浏览器无法读取jsx)
* [8.如何理解“在React中，一切都是组件”这句话？](#8如何理解在react中一切都是组件这句话)
* [9.解释 React 中 render() 的目的。](#9解释-react-中-render-的目的)
* [10.什么是 Props?](#10什么是-props)
* [11.React中的状态是什么？它是如何使用的？](#11react中的状态是什么它是如何使用的)
* [12.React组件生命周期的阶段是什么？](#12react组件生命周期的阶段是什么)
* [13.详细解释 React 组件的生命周期方法。](#13详细解释-react-组件的生命周期方法)
* [14.React中的事件是什么？](#14react中的事件是什么)
* [15.React中的合成事件是什么？](#15react中的合成事件是什么)
* [16.列出一些应该使用 Refs 的情况。](#16列出一些应该使用-refs-的情况)
* [17.什么是高阶组件（HOC）？](#17什么是高阶组件hoc)
* [18.你能用HOC做什么？](#18你能用hoc做什么)
* [19.什么是纯组件？](#19什么是纯组件)
* [20.React 中 key 的重要性是什么？](#20react-中-key-的重要性是什么)
* [21.什么是React 路由？](#21什么是react-路由)
* [22.为什么需要 React 中的路由？](#22为什么需要-react-中的路由)
* [23.列出 React Router 的优点。](#23列出-react-router-的优点)
* [24.类组件和函数组件之间有什么区别？](#24类组件和函数组件之间有什么区别)
* [25.state 和 props有什么区别？](#25state-和-props有什么区别)
* [26.constructor中super与props参数一起使用的目的是什么？](#26constructor中super与props参数一起使用的目的是什么)
* [27.什么是受控组件？](#27什么是受控组件)
* [28.使用React Hooks有什么优势？](#28使用react-hooks有什么优势)
* [29.React中的StrictMode是什么？](#29react中的strictmode是什么)
* [30.React context是什么？](#30react-context是什么)
* [31.React Fiber是什么？](#31react-fiber是什么)
* [32.react diff 原理](#32react-diff-原理)
* [33.setState 和 replaceState 的区别](#33setstate-和-replacestate-的区别)
* [34.React 中有三种构建组件的方式](#34react-中有三种构建组件的方式)
* [35.应该在 React 组件的何处发起 Ajax 请求](#35应该在-react-组件的何处发起-ajax-请求)
* [参考资料](#参考资料)


#### 1.什么是React？

React 是 Facebook 在 2011 年开发的前端 JavaScript 库。
它遵循基于组件的方法，有助于构建可重用的UI组件。
它用于开发复杂和交互式的 Web 和移动 UI。
尽管它仅在 2015 年开源，但有一个很大的支持社区。

#### 2.React有什么特点？

它使用虚拟DOM而不是真正的DOM。
它可以用服务器端渲染。
它遵循单向数据流或数据绑定。

#### 3.列出React的一些主要优点。

它提高了应用的性能
可以方便地在客户端和服务器端使用
由于 JSX，代码的可读性很好
React 很容易与 Meteor，Angular 等其他框架集成
使用React，编写UI测试用例变得非常容易

#### 4.React有哪些限制？

React 只是一个库，而不是一个完整的框架
它的库非常庞大，需要时间来理解
新手程序员可能很难理解
编码变得复杂，因为它使用内联模板和 JSX

#### 5.什么是JSX？

JSX 是J avaScript XML 的简写。是 React 使用的一种文件，它利用 JavaScript 的表现力和类似 HTML 的模板语法。这使得 HTML 文件非常容易理解。此文件能使应用非常可靠，并能够提高其性能。下面是JSX的一个例子：

```
render(){
    return(        
        <div>
            <h1> Hello World from Edureka!!</h1>
        </div>
    );
}


```

#### 6.你了解 Virtual DOM 吗？解释一下它的工作原理。

Virtual DOM 是一个轻量级的 JavaScript 对象，它最初只是 real DOM 的副本。它是一个节点树，它将元素、它们的属性和内容作为对象及其属性。 React 的渲染函数从 React 组件中创建一个节点树。然后它响应数据模型中的变化来更新该树，该变化是由用户或系统完成的各种动作引起的。

Virtual DOM 工作过程有三个简单的步骤。

每当底层数据发生改变时，整个 UI 都将在 Virtual DOM 描述中重新渲染。
然后计算之前 DOM 表示与新表示的之间的差异。
完成计算后，将只用实际更改的内容更新 real DOM。

#### 7.为什么浏览器无法读取JSX？

浏览器只能处理 JavaScript 对象，而不能读取常规 JavaScript 对象中的 JSX。所以为了使浏览器能够读取 JSX，首先，需要用像 Babel 这样的 JSX 转换器将 JSX 文件转换为 JavaScript 对象，然后再将其传给浏览器。

#### 8.如何理解“在React中，一切都是组件”这句话？

组件是 React 应用 UI 的构建块。这些组件将整个 UI 分成小的独立并可重用的部分。每个组件彼此独立，而不会影响 UI 的其余部分。

#### 9.解释 React 中 render() 的目的。

每个React组件强制要求必须有一个 render()。它返回一个 React 元素，是原生 DOM 组件的表示。如果需要渲染多个 HTML 元素，则必须将它们组合在一个封闭标记内，例如 form、group、div 等。此函数必须保持纯净，即必须每次调用时都返回相同的结果。


#### 10.什么是 Props?

Props 是 React 中属性的简写。它们是只读组件，必须保持纯，即不可变。它们总是在整个应用中从父组件传递到子组件。子组件永远不能将 prop 送回父组件。这有助于维护单向数据流，通常用于呈现动态生成的数据。

#### 11.React中的状态是什么？它是如何使用的？

状态是 React 组件的核心，是数据的来源，必须尽可能简单。基本上状态是确定组件呈现和行为的对象。与props 不同，它们是可变的，并创建动态和交互式组件。可以通过 this.state() 访问它们。

#### 12.React组件生命周期的阶段是什么？

React 组件的生命周期有三个不同的阶段：

初始渲染阶段：这是组件即将开始其生命之旅并进入 DOM 的阶段。
更新阶段：一旦组件被添加到 DOM，它只有在 prop 或状态发生变化时才可能更新和重新渲染。这些只发生在这个阶段。
卸载阶段：这是组件生命周期的最后阶段，组件被销毁并从 DOM 中删除。

#### 13.详细解释 React 组件的生命周期方法。

componentWillMount() – 在渲染之前执行，在客户端和服务器端都会执行。
componentDidMount() – 仅在第一次渲染后在客户端执行。
componentWillReceiveProps() – 当从父类接收到 props 并且在调用另一个渲染器之前调用。
shouldComponentUpdate() – 根据特定条件返回 true 或 false。如果你希望更新组件，请返回true 否则返回 false。默认情况下，它返回 false。
componentWillUpdate() – 在 DOM 中进行渲染之前调用。
componentDidUpdate() – 在渲染发生后立即调用。
componentWillUnmount() – 从 DOM 卸载组件后调用。用于清理内存空间。

#### 14.React中的事件是什么？

在 React 中，事件是对鼠标悬停、鼠标单击、按键等特定操作的触发反应。处理这些事件类似于处理 DOM 元素中的事件。但是有一些语法差异，如：

用驼峰命名法对事件命名而不是仅使用小写字母。
事件作为函数而不是字符串传递。

事件参数重包含一组特定于事件的属性。每个事件类型都包含自己的属性和行为，只能通过其事件处理程序访问。

#### 15.React中的合成事件是什么？

合成事件是围绕浏览器原生事件充当跨浏览器包装器的对象。它们将不同浏览器的行为合并为一个 API。这样做是为了确保事件在不同浏览器中显示一致的属性。

#### 16.列出一些应该使用 Refs 的情况。

需要管理焦点、选择文本或媒体播放时
触发式动画
与第三方 DOM 库集成

#### 17.什么是高阶组件（HOC）？

高阶组件是重用组件逻辑的高级方法，是一种源于 React 的组件模式。 HOC 是自定义组件，在它之内包含另一个组件。它们可以接受子组件提供的任何动态，但不会修改或复制其输入组件中的任何行为。你可以认为 HOC 是“纯（Pure）”组件。

#### 18.你能用HOC做什么？

代码重用，逻辑和引导抽象
渲染劫持
状态抽象和控制
Props 控制

#### 19.什么是纯组件？

纯（Pure） 组件是可以编写的最简单、最快的组件。它们可以替换任何只有 render() 的组件。这些组件增强了代码的简单性和应用的性能。

#### 20.React 中 key 的重要性是什么？

key 用于识别唯一的 Virtual DOM 元素及其驱动 UI 的相应数据。它们通过回收 DOM 中当前所有的元素来帮助 React 优化渲染。这些 key 必须是唯一的数字或字符串，React 只是重新排序元素而不是重新渲染它们。这可以提高应用程序的性能。

#### 21.什么是React 路由？

React 路由是一个构建在 React 之上的强大的路由库，它有助于向应用程序添加新的屏幕和流。这使 URL 与网页上显示的数据保持同步。它负责维护标准化的结构和行为，并用于开发单页 Web 应用。 React 路由有一个简单的API。

#### 22.为什么需要 React 中的路由？

Router 用于定义多个路由，当用户定义特定的 URL 时，如果此 URL 与 Router 内定义的任何 “路由” 的路径匹配，则用户将重定向到该特定路由。所以基本上我们需要在自己的应用中添加一个 Router 库，允许创建多个路由，每个路由都会向我们提供一个独特的视图。

#### 23.列出 React Router 的优点。

就像 React 基于组件一样，在 React Router v4 中，API 是 ‘All About Components’。可以将 Router 可视化为单个根组件（BrowserRouter），其中我们将特定的子路由（route）包起来。
无需手动设置历史值：在 React Router v4 中，我们要做的就是将路由包装在 BrowserRouter 组件中。
包是分开的：共有三个包，分别用于 Web、Native 和 Core。这使我们应用更加紧凑。基于类似的编码风格很容易进行切换。

#### 24.类组件和函数组件之间有什么区别？

类组件（ Class components ）
无论是使用函数或是类来声明一个组件，它决不能修改它自己的 props 。
所有 React 组件都必须是纯函数，并禁止修改其自身 props 。


React是单项数据流，父组件改变了属性，那么子组件视图会更新。
属性 props 是外界传递过来的，状态 state 是组件本身的，状态可以在组件中任意修改
组件的属性和状态改变都会更新视图。

函数组件（functional component）
函数组件接收一个单一的 props 对象并返回了一个React元素

区别
函数组件和类组件当然是有区别的，而且函数组件的性能比类组件的性能要高，因为类组件使用的时候要实例化，而函数组件直接执行函数取返回结果即可。为了提高性能，尽量使用函数组件。


#### 25.state 和 props有什么区别？

state 和 props都是普通的JavaScript对象。尽管它们两者都具有影响渲染输出的信息，但它们在组件方面的功能不同。即

props 是一个从外部传进组件的参数，主要作为就是从父组件向子组件传递数据，它具有可读性和不变性，只能通过外部组件主动传入新的 props 来重新渲染子组件，否则子组件的 props 以及展现形式不会改变。

state 的主要作用是用于组件保存、控制以及修改自己的状态，它只能在 constructor 中初始化，它算是组件的私有属性，不可通过外部访问和修改，只能通过组件内部的 this.setState 来修改，修改 state 属性会导致组件的重新渲染。

#### 26.constructor中super与props参数一起使用的目的是什么？

在调用方法之前，子类构造函数无法使用 this 引用 super() 。

在ES6中，在子类的 constructor 中必须先调用 super 才能引用 this 。

在 constructor 中可以使用 this.props

#### 27.什么是受控组件？

在HTML当中，像 input , textarea , 和 select 这类表单元素会维持自身状态，并根据用户输入进行更新。但在React中，可变的状态通常保存在组件的状态属性中，并且只能用 setState() 方法进行更新。

非受控组件
非受控组件，即组件的状态不受React控制的组件，例如下边这个

```
import React, { Component } from 'react';
import ReactDOM from 'react-dom';

class Demo1 extends Component {
    render() {
        return (
            <input />
        )
    }
}

ReactDOM.render(<Demo1/>, document.getElementById('content'))
```

在这个最简单的输入框组件里,我们并没有干涉input中的value展示,即用户输入的内容都会展示在上面。如果我们通过props给组件设置一个初始默认值,defaultValue属性是React内部实现的一个属性,目的类似于input的placeholder属性。

受控组件
同样的，受控组件就是组件的状态受React控制。上面提到过，既然通过设置input的value属性, 无法改变输入框值,那么我们把它和state结合在一起,再绑定onChange事件,实时更新value值就行了。

```
class Demo1 extends Component {
    constructor(props) {
        super(props);
        this.state = {
            value: props.value
        }
    }

    handleChange(e) {
        this.setState({
            value: e.target.value
        })
    }

    render() {
        return (
            <input value={this.state.value} onChange={e => this.handleChange(e)}/>
        )
    }
}
```


#### 28.使用React Hooks有什么优势？

hooks 是react 16.8 引入的特性，他允许你在不写class的情况下操作state 和react的其他特性。
hooks 只是多了一种写组件的方法，使编写一个组件更简单更方便，同时可以自定义hook把公共的逻辑提取出来，让逻辑在多个组件之间共享。

Hook 是什么
Hook 是什么？ Hook 是一个特殊的函数，它可以让你“钩入” React 的特性。例如，useState 是允许你在 React 函数组件中添加 state 的 Hook。稍后我们将学习其他 Hook。

什么时候我会用 Hook？ 如果你在编写函数组件并意识到需要向其添加一些 state，以前的做法是必须将其它转化为 class。现在你可以在现有的函数组件中使用 Hook。

ReactHooks的优点
无需复杂的DOM结构
简洁易懂

#### 29.React中的StrictMode是什么？

React的StrictMode是一种帮助程序组件，可以帮助您编写更好的react组件，您可以使用包装一些组件， <StrictMode /> 并且基本上可以：

验证内部组件是否遵循某些推荐做法，如果不在控制台中，则会发出警告。
验证不赞成使用的方法，如果使用了严格模式，则会在控制台中警告您。
通过识别潜在风险来帮助您预防某些副作用。

#### 30.React context是什么？

React文档官网并未对 Context 给出“是什么”的定义，更多是描述使用的 Context 的场景，以及如何使用 Context 。

官网对于使用 Context 的场景是这样描述的：

In Some Cases, you want to pass data through the component tree without having to pass the props down manuallys at every level. you can do this directly in React with the powerful "context" API.

简单说就是，当你不想在组件树中通过逐层传递 props 或者 state 的方式来传递数据时，可以使用 Context 来实现 跨层级 的组件数据传递。

使用props或者state传递数据，数据自顶下流。

使用 Context ，可以跨越组件进行数据传递。

#### 31.React Fiber是什么？

React Fiber 并不是所谓的纤程（微线程、协程），而是一种基于浏览器的单线程调度算法，背后的支持 API 是大名鼎鼎的：requestIdleCallback。

Fiberl是一种将 recocilation （递归 diff），拆分成无数个小任务的算法；它随时能够停止，恢复。停止恢复的时机取决于当前的一帧（16ms）内，还有没有足够的时间允许计算。

#### 32.react diff 原理

把树形结构按照层级分解，只比较同级元素。

给列表结构的每个单元添加唯一的 key 属性，方便比较。

React 只会匹配相同 class 的 component（这里面的 class 指的是组件的名字） 合并操作，调用 component 的 setState 方法的时候, React 将其标记为 dirty.
到每一个事件循环结束, React 检查所有标记 dirty 的 component 重新绘制. 选择性子树渲染。开发人员可以重写 shouldComponentUpdate 提高 diff 的性能。

#### 33.setState 和 replaceState 的区别

setState 是修改其中的部分状态，相当于 Object.assign，只是覆盖，
不会减少原来的状态

replaceState 是完全替换原来的状态，相当于赋值，将原来的 state 替换为另一个对象，如果新状态属性减少，那么 state 中就没有这个状态了

#### 34.React 中有三种构建组件的方式

React.createClass()、ES6 class 和无状态函数。

#### 35.应该在 React 组件的何处发起 Ajax 请求

在 React 组件中，应该在 componentDidMount 中发起网络请求。这个方法会在组件第一次“挂载”(被添加到 DOM)时执行，在组件的生命周期中仅会执行一次。

更重要的是，你不能保证在组件挂载之前 Ajax 请求已经完成，如果是这样，也就意味着你将尝试在一个未挂载的组件上调用 setState，这将不起作用。
在 componentDidMount 中发起网络请求将保证这有一个组件可以更新了。

#### 参考资料

https://blog.csdn.net/eyeofangel/article/details/88797314

https://zhuanlan.zhihu.com/p/91725031

https://www.jianshu.com/p/7b07550699c9
