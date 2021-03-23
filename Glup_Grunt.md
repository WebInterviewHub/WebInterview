## Glup_Grunt
* [1.Grunt的特点](#1grunt的特点)
* [2.Gulp和Grunt的异同点](#2gulp和grunt的异同点)
* [3.差异和不同](#3差异和不同)
* [4.I/O流程的不同](#4io流程的不同)
* [5.Gulp中的流](#5gulp中的流)
* [6.为什么应该使用流？](#6为什么应该使用流)
* [7.为什么要使用Grunt?](#7为什么要使用grunt)
* [8.Grunt都有哪些插件?](#8grunt都有哪些插件)
* [9.哪些人都在使用Grunt?](#9哪些人都在使用grunt)
* [10.Gulp优点：](#10gulp优点)
* [参考链接](#参考链接)




#### 1.Grunt的特点

- Grunt有一个完善的社区，插件丰富 它简单易学，
- 你可以随便安装插件并配置它们
- 你不需要多先进的理念，也不需要任何经验

完善 – Grunt的插件繁多。

易用 – Grunt的插件丰富： 许多常见的任务都有现成的Grunt插件，而且有众多第三方插件，如：CoffeeScript，Handlebars，Jade，JsHint，Less，RequireJS，Sass，Styles。通过参考文档进行配置便可以快速使用。

#### 2.Gulp和Grunt的异同点

易于使用：采用代码优于配置策略，Gulp让简单的事情继续简单，复杂的任务变得可管理。

高效：通过利用Node.js强大的流，不需要往磁盘写中间文件，可以更快地完成构建。

高质量：Gulp严格的插件指导方针，确保插件简单并且按你期望的方式工作。

易于学习：通过把API降到最少，你能在很短的时间内学会Gulp。构建工作就像你设想的一样：是一系列流管道。

**易用** Gulp相比Grunt更简洁，而且遵循代码优于配置策略，维护Gulp更像是写代码。

**高效** Gulp相比Grunt更有设计感，核心设计基于Unix流的概念，通过管道连接，不需要写中间文件。

**高质量** Gulp的每个插件只完成一个功能，这也是Unix的设计原则之一，各个功能通过流进行整合并完成复杂的任务。
例如：Grunt的imagemin插件不仅压缩图片，同时还包括缓存功能。
他表示，在Gulp中，缓存是另一个插件，可以被别的插件使用，这样就促进了插件的可重用性。

**易学** Gulp的核心API只有5个，掌握了5个API就学会了Gulp，之后便可以通过管道流组合自己想要的任务。

#### 3.差异和不同

- 流：Gulp是一个基于流的构建系统，使用代码优于配置的策略。
- 插件：Gulp的插件更纯粹，单一的功能，并坚持一个插件只做一件事。
- 代码优于配置：维护Gulp更像是写代码，而且Gulp遵循CommonJS规范，因此跟写Node程序没有差别。
- 没有产生中间文件

#### 4.I/O流程的不同

使用Grunt的I/O过程中会产生一些中间态的临时文件，一些任务生成临时文件，其它任务可能会基于临时文件再做处理并生成最终的构建后文件。
而使用Gulp的优势就是利用流的方式进行文件的处理，通过管道将多个任务和操作连接起来，因此只有一次I/O的过程，流程更清晰，更纯粹。

#### 5.Gulp中的流

Gulp通过流和代码优于配置策略来尽量简化任务编写的工作。这看起来有点“像jQuery”的方法，把动作串起来创建构建任务。早在Unix的初期，流就已经存在了。流在Node.js生态系统中也扮演了重要的角色，类似于*nix将几乎所有设备抽象为文件一样，Node将几乎所有IO操作都抽象成了Stream的操作。因此用Gulp编写任务也可看作是用Node.js编写任务。当使用流时，Gulp去除了中间文件，只将最后的输出写入磁盘，整个过程因此变得更快。

Doug McIlroy, then head of the Bell Labs CSRC (Computing Sciences Research Center), and inventor of the Unix pipe, summarized the Unix philosophy as follows:

> This is the Unix philosophy: Write programs that do one thing and do
> it well. Write programs to work together. Write programs to handle
> text streams, because that is a universal interface.

基于流的模块特点：

- Write modules that do one thing and do it well.
- Write modules that work together.
  Write modules that handle events and streams.

Unix管道示例：

```
tput setaf 88 ; whoami | figlet | tr _ … | tr \ \` | tr \| ¡ | tr / √
1
```



#### 6.为什么应该使用流？

Node中的I/O操作是异步的，因此磁盘的读写和网络操作都需要传递回调函数。

```
var http = require('http');
var fs = require('fs');

var server = http.createServer(function (req, res) {
        fs.readFile(__dirname + '/data.txt', function (err, data) {
                res.end(data);
        });
});
server.listen(8000);
123456789
```

这个Node.js应用很简单，所有学习过Node的人应该都做过这样的练习，可以说是Node版的Hello World了。这段代码没有任何问题，你使用node可以正常的运行起来，使用浏览器或者其他的http客户端都可以正常的访问运行程序主机的8000端口读取主机上的data.txt文件。
但是这种方式隐含了一个潜在的问题，node会把整个data.txt文件都缓存到内存中以便响应客户端的请求（request），随着客户端请求的增加内存的消耗将是非常惊人的，而且客户端需要等待很长传输时间才能得到结果。让我们再看一看另外一种方式，使用流：

```
var http = require('http');
var fs = require('fs');

var server = http.createServer(function (req, res) {
        var stream = fs.createReadStream(__dirname + '/data.txt');
        stream.pipe(res);
});
server.listen(8000);
12345678
```

这里面有一个非常大的变化就是使用createReadStream这个fs的方法创建了stream这个变量，并由这个变量的pip方法来响应客户端的请求。使用stream这个变量就可以让node读取data.txt一定量的时候就开始向客户端发送响应的内容，而无需服务缓存以及客户端的等待。

#### 7.为什么要使用Grunt?

Grunt是一个庞大的生态系统, 每天都在成长. 你可以自由的选择数以百计的插件以帮助你自动化的处理任务.

如果你所需要的插件还没有被人创建, 那么你可以自己创建插件并通过npm很方便的发布以供更多人使用并一起完善.

#### 8.Grunt都有哪些插件?

大多数的任务Grunt都提供了可用的Grunt插件, 并且每天都有插件诞生并发布到社区中. 我想你所熟悉的有:

- JSHint
- Uglify
- Less
- Sass
- CoffeeScript
- CSSLint

等等. 更多的插件可以在Grunt官方的[插件清单](http://gruntjs.com/plugins)中查看.

#### 9.哪些人都在使用Grunt?

众所周知的有:

- jQuery
- Modernizr
- Twitter
- Adobe

等等. 还有更多的人在使用Grunt, 比如: 你.

#### 10.Gulp优点：

1.gulp 将开发流程中让人痛苦或耗时的任务自动化，从而减少你所浪费的时间、创造更大价值。

2.代码优于配置、node 最佳实践、精简的 API 集，gulp 让工作前所未有的简单。

3.基于 node 强大的流(stream)能力，gulp 在构建过程中并不把文件立即写入磁盘，从而提高了构建速度。

4.遵循严格的准则，确保我们的插件结构简单、运行结果可控。



#### 参考链接

https://blog.csdn.net/weixin_40191445/article/details/83065015

https://www.w3cschool.cn/grunt/
