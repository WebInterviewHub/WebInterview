## Ajax
* [1.什么是ajax？ajax作用是什么？](#1什么是ajaxajax作用是什么)
* [2.为什么要用ajax：](#2为什么要用ajax)
* [3.AJAX最大的特点是什么。](#3ajax最大的特点是什么)
* [4.请介绍一下XMLHttprequest对象。](#4请介绍一下xmlhttprequest对象)
* [5.AJAX技术体系的组成部分有哪些。](#5ajax技术体系的组成部分有哪些)
* [6.工作当中会和后台交互吗？ 那你能说说封装好的 ajax里的几个参数吗 ？](#6工作当中会和后台交互吗-那你能说说封装好的-ajax里的几个参数吗-)
* [7.Ajax的实现流程是怎样的？](#7ajax的实现流程是怎样的)
* [8.AJAX请求总共有多少种CALLBACK](#8ajax请求总共有多少种callback)
* [9.AJAX有哪些有点和缺点？](#9ajax有哪些有点和缺点)
* [10.Ajax 解决浏览器缓存问题？](#10ajax-解决浏览器缓存问题)
* [参考链接](#参考链接)

## Ajax



#### 1.什么是ajax？ajax作用是什么？

AJAX = 异步 JavaScript 和 XML。 **AJAX 是一种用于创建快速动态网页的技术**。 通过在后台与服务器进行少量数据交换,AJAX 可以使网页实现异步更新.

#### 2.为什么要用ajax：

Ajax应用程序的优势在于：

\1. 通过异步模式，提升了用户体验

\2. 优化了浏览器和服务器之间的传输，减少不必要的数据往返，减少了带宽占用

\3. Ajax引擎在客户端运行，承担了一部分本来由服务器承担的工作，从而减少了大用户量下的服务器负载。

#### 3.AJAX最大的特点是什么。

Ajax可以实现动态不刷新（局部刷新）
就是能在不更新整个页面的前提下维护数据。这使得Web应用程序更为迅捷地回应用户动作，并避免了在网络上发送那些没有改变过的信息。

####  4.请介绍一下XMLHttprequest对象。

Ajax的核心是JavaScript对象XmlHttpRequest。该对象在Internet Explorer 5中首次引入，它是一种支持异步请求的技术。简而言之，XmlHttpRequest使您可以使用JavaScript向服务器提出请求并处理响应，而不阻塞用户。通过XMLHttpRequest对象，Web开发人员可以在页面加载以后进行页面的局部更新。

####  5.AJAX技术体系的组成部分有哪些。

HTML，css，dom，xml，xmlHttpRequest，javascript

#### 6.工作当中会和后台交互吗？ 那你能说说封装好的 ajax里的几个参数吗 ？

url:  发送请求的地址。

type: 请求方式（post或get）默认为get。

async: 同步异步请求，默认true所有请求均为异步请求。

timeout : 超时时间设置，单位毫秒

data：要求为Object或String类型的参数，发送到服务器的数据

cache：默认为true（当dataType为script时，默认为false）, 设置为false将不会从浏览器缓存中加载请求信息。

dataType: 预期服务器返回的数据类型。

可用的类型如下：

              xml：返回XML文档，可用JQuery处理。

html：返回纯文本HTML信息；包含的script标签会在插入DOM时执行。

script：返回纯文本JavaScript代码。不会自动缓存结果。

json：返回JSON数据。

jsonp：JSONP格式。使用JSONP形式调用函数时，例如myurl?callback=?，JQuery将自动替换后一个“?”为正确的函数名，以执行回调函数。

text：返回纯文本字符串。

success：请求成功后调用的回调函数，有两个参数。

(1)   由服务器返回，并根据dataType参数进行处理后的数据。

(2)   描述状态的字符串。

error：要求为Function类型的参数，请求失败时被调用的函数。该函数有3个参数

(1) XMLHttpRequest对象

(2) 错误信息

(3) 捕获的错误对象(可选)

complete :function(XMLHttpRequest,status){ //请求完成后最终执行参数


#### 7.Ajax的实现流程是怎样的？

> Ajax的实现流程是怎样的？

- (1)创建XMLHttpRequest对象,也就是创建一个异步调用对象.
- (2)创建一个新的HTTP请求,并指定该HTTP请求的方法、URL及验证信息.
- (3)设置响应HTTP请求状态变化的函数.
- (4)发送HTTP请求.
- (5)获取异步调用返回的数据.
- (6)使用JavaScript和DOM实现局部刷新.

```
    <script type="text/javascript">

        var httpRequest;
        function checkUsername() {

            if(window.XMLHttpRequest) {

                //在IE6以上的版本以及其他内核的浏览器(Mozilla)等
                httpRequest = new XMLHttpRequest();
            }else if(window.ActiveXObject) {

                //在IE6以下的版本
                httpRequest = new ActiveXObject();
            }


            //创建http请求
            httpRequest.open("POST", "Servlet1", true);

            //因为我使用的是post方式，所以需要设置消息头
            httpRequest.setRequestHeader("Content-type", "application/x-www-form-urlencoded");

            //指定回调函数
            httpRequest.onreadystatechange = response22;

            //得到文本框的数据
            var name = document.getElementById("username").value;

            //发送http请求，把要检测的用户名传递进去
            httpRequest.send("username=" + name);

        }

        function response22() {

            //判断请求状态码是否是4【数据接收完成】
            if(httpRequest.readyState==4) {

                //再判断状态码是否为200【200是成功的】
                if(httpRequest.status==200) {

                    //得到服务端返回的文本数据
                    var text = httpRequest.responseText;

                    //把服务端返回的数据写在div上
                    var div = document.getElementById("result");
                    div.innerText = text;
                }

            }
        }
    </script>
```

#### 8.AJAX请求总共有多少种CALLBACK

> AJAX请求总共有多少种CALLBACK

Ajax请求总共有**八种**Callback

- onSuccess
- onFailure
- onUninitialized
- onLoading
- onLoaded
- onInteractive
- onComplete
- onException

#### 9.AJAX有哪些有点和缺点？

> AJAX有哪些有点和缺点？

优点：

- 1、最大的一点是页面无刷新，用户的体验非常好。
- 2、使用异步方式与服务器通信，具有更加迅速的响应能力。
- 3、可以把以前一些服务器负担的工作转嫁到客户端，利用客户端闲置的能力来处理，减轻服务器和带宽的负担，节约空间和宽带租用成本。并且减轻服务器的负担，ajax的原则是“按需取数据”，可以最大程度的减少冗余请求，和响应对服务器造成的负担。
- 4、基于标准化的并被广泛支持的技术，不需要下载插件或者小程序。

缺点：

- 1、ajax不支持浏览器back按钮。
- 2、安全问题 AJAX暴露了与服务器交互的细节。
- 3、对搜索引擎的支持比较弱。
- 4、破坏了程序的异常机制。
- 5、不容易调试。

#### 10.Ajax 解决浏览器缓存问题？

> Ajax 解决浏览器缓存问题？

- 1、在ajax发送请求前加上 anyAjaxObj.setRequestHeader("If-Modified-Since","0")。
- 2、在ajax发送请求前加上 anyAjaxObj.setRequestHeader("Cache-Control","no-cache")。
- 3、在URL后面加上一个随机数： "fresh=" + Math.random();。
- 4、在URL后面加上时间戳："nowtime=" + new Date().getTime();。
- 5、如果是使用jQuery，直接这样就可以了 $.ajaxSetup({cache:false})。这样页面的所有ajax都会执行这条语句就是不需要保存缓存记录。



#### 参考链接

https://zhuanlan.zhihu.com/p/98288927

https://segmentfault.com/a/1190000013291898

https://blog.csdn.net/dkh_321/article/details/79311367
