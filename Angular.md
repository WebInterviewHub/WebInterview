## Angular

* [1.什么是Angular 7？与AngularJS有何不同？](#1什么是angular-7与angularjs有何不同)
* [2.什么是Angular框架？](#2什么是angular框架)
* [3.Angular 7中的结构指令和属性指令有什么区别？](#3angular-7中的结构指令和属性指令有什么区别)
* [4.NgModule中的”声明”, “提供者”和”导入”之间有什么区别？](#4ngmodule中的声明-提供者和导入之间有什么区别)
* [5.Angular的关键组件是什么？](#5angular的关键组件是什么)
* [6.解释Angular的体系结构概述](#6解释angular的体系结构概述)
* [7.如何将Angular 6更新为Angular 7？](#7如何将angular-6更新为angular-7)
* [8.什么是angular material?](#8什么是angular-material)
* [9. 什么是aot编译?](#9-什么是aot编译)
* [10.什么是数据绑定？在Angular中有几种方式?](#10什么是数据绑定在angular中有几种方式)
* [参考链接](#参考链接)


####  1.什么是Angular 7？与AngularJS有何不同？

Angular7是Angular的最新版本。 AngularJS是Angular的第一个版本, 也称为Angular 1.0。

Angular7是Angular1.0的完整重写。它支持双向数据绑定, 以及其他一些功能, 例如ng更新, ng添加, Angular元素, Angular材质+ CDK组件, Angular材质入门组件, CLI工作区, 库支持, Tree Shakable Providers, 动画性能改进和RxJS v6等等

#### 2.什么是Angular框架？

Angular是基于TypeScript的开源Web框架和平台。它用于构建Web /移动和桌面应用程序。

该框架的主要功能包括：声明性模板, 依赖项注入, 端到端工具等。这些功能使Angular中的Web开发变得容易。

#### 3.Angular 7中的结构指令和属性指令有什么区别？

结构化指令用于通过删除和添加DOM元素来更改DOM布局。这些指令在更改视图结构方面要好得多。结构指令的示例是NgFor和Nglf。

属性指令用作元素的特征。例如, 模板”语法”指南中的内置NgStyle之类的指令是属性指令。

#### 4.NgModule中的”声明”, “提供者”和”导入”之间有什么区别？

NgModule中的声明之间的区别”, “提供者”和”导入”：

- 声明用于使当前模块中的指令(包括组件和管道)可用于当前模块中的其他指令。指令, 组件或管道的选择器只有在声明或导入时才与HTML匹配。
- 提供者用于使DI知道服务和价值。它们被添加到根范围, 并且被注入到其他具有它们依赖关系的服务或指令中。提供程序的一种特殊情况是延迟加载的模块, 它们具有自己的子注入器。默认情况下, 仅将延迟加载的模块的提供程序提供给该延迟加载的模块(不像其他模块那样提供整个应用程序)。
- import使其他模块的导出声明在当前模块中可用。

#### 5.Angular的关键组件是什么？

Angular的关键组件：

组件：组件是角度应用程序的基本构建块, 用于控制HTML视图。

模块：模块是有角度的基本构建块的集合, 例如组件, 指令, 服务等。应用程序分为逻辑部分, 每段代码称为”模块”, 用于执行单个任务。

模板：模板用于表示Angular应用程序的视图。

服务：用于创建可以在整个应用程序之间共享的组件。

元数据：可用于向Angular类添加更多数据。

#### 6.解释Angular的体系结构概述

Angular是用于开发移动和Web应用程序的最受欢迎的Web开发框架。它使用称为IONIC的跨平台移动开发, 这就是为什么它不仅限于Web应用程序。

Angular应用程序有7个主要构建块：

- 零件
- 范本
- 元数据
- 数据绑定
- 指令
- 服务
- 依赖注入

Angular应用程序的基本构建块是NgModules, 它为组件提供编译上下文。 Angular应用程序由一组NgModule定义, 并且始终至少具有启用引导的根模块以及更多功能模块。

- 组件定义模板视图
- 组件使用服务

NgModules使开发人员可以将应用程序组织成相互连接的功能块。

CLI生成的最小” AppModule”的NgModule属性如下：

- 声明：用于声明应用程序组件。
- 导入：每个应用程序都必须导入BrowserModule才能在浏览器中运行该应用程序。
- 提供者：没有什么可以开始的。
- Bootstrap：这是Angular创建并插入到index.html主机网页中的根AppComponent。

#### 7.如何将Angular 6更新为Angular 7？

你可以使用以下命令将Angular 6更新为Angular 7：

```
ng update @angular/cli @angular/core
```

#### 8.什么是angular material?

这是Angular的用户界面组件库。

#### 9. 什么是aot编译?

aot是ahead of time。就是Angular的内部编译机制。

#### 10.什么是数据绑定？在Angular中有几种方式?

一共有三种方式。一种是事件绑定，这种方式使得应用程序可以对用户的输入做出反应。另一种是属性绑定。这种方式是从应用数据向html传递数据。最后一种方式是双向绑定。这种绑定可以支持用程序数据的修改影响视图，同时视图上数据的改动也会影响到应用程序的数据。

#### 参考链接

http://www.srcmini.com/33381.html

https://zhuanlan.zhihu.com/p/80791364
