> Wamp使用: 项目要放在www里面  
> 访问：地址栏中输入127.0.0.1 或者输入localhost
> www目录： 快捷方式，直接找到项目所在的位置、
> phpmyAdmin: 配置数据的地方

#### 什么是服务器
> 服务器是一种高性能计算机，作为网络的节点，存储、处理网络上80％的数 据、信息，因此也被称为网络的灵魂。也可以这样讲，服务器指一个管理资源并为用户提供服务的计算机软件，通常分为文件服务器、数据库服务器和应用程序服务器。服务器类型
+ (1)	服务类型：  http服务器(网页服务)、数据库服务器（提供数据存储及访问服务）、邮件服务器、文件服务器
+ (2)	操作系统：服务器操作系统主要分为四大流派：Windows Server、Netware、Unix、Linux。
    * ①	Windows服务器
    * ②	Linux服务器
> 1)	一般windows服务器不会担任数据库服务器的角色，因为windows系列安全性极低，容易泄露数据
> 2)	Linux服务器通常担当数据库角色，是由于Linux系统性能极强，可以大批量处理数据，并具有很高的安全性。
> 3)	服务器软件:Apache服务器、Tomcat服务器

# Ajax-网络基础

> Ajax: 即“Asynchronous Javascript And XML”（异步 JavaScript 和 XML），是指一种创建交互式网页应用的网页开发技术。
> 简单地说：Ajax 是一种用于创建快速动态网页的技术。
> Ajax 是一种在无需重新加载整个网页的情况下，能够实现局部刷新的技术。
> 通过在后台与服务器进行少量数据交换，Ajax 可以使网页实现异步更新。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新。    
- Ajax的原理：通过XmlHttpRequest对象来向服务器发异步请求，从服务器获得数据，然后用javascript来操作DOM而更新页面
- XMLHttpRequest是ajax的核心机制
## Ajax优缺点：
#### 优点：
1. 无刷新更新数据
> Ajax最大的优点就是能在不刷新整个页面的情况下与服务器通信，提高了用户体验。
2. 异步与服务器通信
> 使用异步的方式与服务器通信，不打断用户的操作，具有更加迅速的响应能力。
3. 前端与后端负载均衡
> 将一些后端的工作移到前端，减少服务器与带宽的负担
4. 基于规范被广泛支持
> 不需要下载浏览器插件或者小程序，但需要客户允许JavaScript在浏览器上执行。
5. 界面与应用分离
> Ajax使得界面与应用分离，也就是数据与呈现分离

#### 缺点：
1. Ajax干掉了Back与History功能，即对浏览器机制的破坏。
> 在传统的网页中，用户经常会习惯性的使用浏览器自带的“前进”，“后退”按钮，然而Ajax改变了此Web浏览习惯。在Ajax中 前进，后退按钮都会失效。 虽然通过一定的方法（添加苗店） 来使得用户可以使用“前进”，“后退”按 钮，但相对于传统方法却麻烦很多。
2. 安全问题
> AJAX技术给用户带来很好的用户体验的同时也对IT企业带来了新的安全威胁，Ajax技术就如同对企业数据建立了一个直接通道。这使得开发者在不经意间会暴露比以前更多的数据和服务器逻辑。
0. 不能跨域
3. 对搜索引擎支持较弱（SEO不好）
> SEO  ：https://blog.csdn.net/H1069495874/article/details/78826382
4. 破坏程序的异常处理机制 
5. 违背URL与资源定位的初衷
6. 不能很好地支持移动设备
7. 客户端肥大，太多客户段代码造成开发上的成本

### Ajax的流程：

```js
// 打开浏览器
                /* 
                    1.创建一个ajax对象
                    ie6以下用new ActiveXObject('Microsoft.XML)
                */
                // var xhr = new XMLHttpRequest(); // ie7以上
                // 兼容写法
                var xhr = null;
                // if(window.XMLHttpRequest) {
                //     xhr = new XMLHttpRequest();
                // } else {
                //     xhr = new ActiveXObject('Microsoft.XML');
                // }
                try{
                    xhr = new XMLHttpRequest();
                }catch(e) {
                    xhr = new ActiveXObject('Microsoft.XML');
                }
                // 异常处理
                //地址栏输入地址
                xhr.open('get', '1.txt', true);
                // 提交
                xhr.send();
                // 等待响应
                xhr.onreadystatechange = function() {	
                    if(xhr.readyState == 4) {
                        alert(xhr.responseText);
                    }
                }
            }
```
> ajax请求五步骤：
1. 创建ajax对象（用户代理）
2. 建立连接
3. 发送请求
4. 接受响应
5. 处理数据

> 客户端向后台发送数据
1. 地址栏输入URL地址
2. 特定属性元素 href/src
3. form表单
4. js中的src属性

> 异常机制处理
```js
try{
	// 代码尝试执行块中的内容，如果有错误，就会执行catch中的内容，并且传入错误信息参数
    Var xhr = new XMLHttpRequest();
}catch(e) {
    Var xhr = new ActiveXObject('Microsoft.XML');
}
```
###Ajax中同步、异步的区别 ？
- 异步：阻塞模式。前面的代码会影响后面的代码
  同步：非阻塞模式。前面的代码不会影响后面的代码

` xhr.setRequestHearder();`
` xhr.withcrendtails = true;`
#### 什么情况下用异步和同步
> 同步： 当你后续的代码需要用到前面的东西的时候，和前面内容挂钩的需求，
> 不可能因为一个ajax请求阻止了后续代码的执行，一个ajax没执行 就挂在那了后面不执行了是不对的
       
## readyState 工作状态：
0. （初始化），还没有调用open方法
1. （载入）已调用send()方法，正在发送请求
2. （载入完成）send()方法完成，已收到全部响应内容
3. （解析）正在解析响应内容
4. （完成） 响应内容解析完成，可以在客户端调用了
```
ajax 的生命周期/状态readyState
0: 请求未初始化
1: 服务器连接已建立
2: 请求已接收
3: 请求处理中
4: 请求已完成，且响应已就绪
```
### http状态码：
> 当浏览者访问一个网页时，浏览者的浏览器会向网页所在服务器发出请求。当浏览器接收并显示网页前，此网页所在的服务器会返回一个包含HTTP状态码的信息头（server header）用以响应浏览器的请求。
> HTTP状态码的英文为HTTP Status Code。
```
> 下面是常见的HTTP状态码：
200 | 请求成功
301 | 资源（网页等）被永久转移到其它URL
304 | 未修改。所请求的资源未修改，服务器返回此状态码时，不会返回任何资源
404 | 请求的资源（网页等）不存在
500 | 内部服务器错误（500及以上）
403 | 禁止请求
405 | 请求方法不允许
```
*****
|状态码|English|解释|
-----|-----|-----
|100	|Continue|	继续。客户端应继续其请求|
|101	|Switching Protocols|切换协议。服务器根据客户端的请求切换协议。只能切换到更高级的协议，例如，切换到HTTP的新版本协
|200|OK|	请求成功。一般用于GET与POST请求|
|201	|Created|	已创建。成功请求并创建了新的资源|
|202	|Accepted|	已接受。已经接受请求，但未处理完成
|203	|Non-Authoritative Information|	非授权信息。请求成功。但返回的meta信息不在原始的服务器，而是一个副本|
|204|No Content|	无内容。服务器成功处理，但未返回内容。在未更新网页的情况下，可确保浏览器继续显示当前文档|
|205	|Reset Content|	重置内容。服务器处理成功，用户终端（例如：浏览器）应重置文档视图。可通过此返回码清除浏览器的表单域|
|206	|Partial Content|部分内容。服务器成功处理了部分GET请求|
|300|	Multiple Choices	|多种选择。请求的资源可包括多个位置，相应可返回一个资源特征与地址的列表用于用户终端（例如：浏览器）选择
|301	|Moved Permanently|	永久移动。请求的资源已被永久的移动到新URI，返回信息会包括新的URI，浏览器会自动定向到新URI。今后任何新的请求都应使用新的URI代替
|302	|Found	|临时移动。与301类似。但资源只是临时被移动。客户端应继续使用原有URI
|303	|See Other|	查看其它地址。与301类似。使用GET和POST请求查看
|304	|Not Modified|	未修改。所请求的资源未修改，服务器返回此状态码时，不会返回任何资源。客户端通常会缓存访问过的资源，通过提供一个头信息指出客户端希望只返回在指定日期之后修改的资源
305	|Use Proxy	|使用代理。所请求的资源必须通过代理访问
306	|Unused|	已经被废弃的HTTP状态码
307	|Temporary Redirect|	临时重定向。与302类似。使用GET请求重定向
400	|Bad Request	|客户端请求的语法错误，服务器无法理解
401	|Unauthorized	|请求要求用户的身份认证
402	|Payment Required|	保留，将来使用
403	|Forbidden|	服务器理解请求客户端的请求，但是拒绝执行此请求
404	|Not Found|	服务器无法根据客户端的请求找到资源（网页）。通过此代码，网站设计人员可设置"您所请求的资源无法找到"的个性页面
405	|Method Not Allowed|	客户端请求中的方法被禁止
406	|Not Acceptable	|服务器无法根据客户端请求的内容特性完成请求
407	|Proxy Authentication Required|	请求要求代理的身份认证，与401类似，但请求者应当使用代理进行授权
408	|Request Time-out|	服务器等待客户端发送的请求时间过长，超时
409	|Conflict	|服务器完成客户端的PUT请求是可能返回此代码，服务器处理请求时发生了冲突
410	|Gone	|客户端请求的资源已经不存在。410不同于404，如果资源以前有现在被永久删除了可使用410代码，网站设计人员可通过301代码指定资源的新位置
411	|Length Required|	服务器无法处理客户端发送的不带Content-Length的请求信息
412	|Precondition Failed|	客户端请求信息的先决条件错误
413	|Request Entity Too Large|	由于请求的实体过大，服务器无法处理，因此拒绝请求。为防止客户端的连续请求，服务器可能会关闭连接。如果只是服务器暂时无法处理，则会包含一个Retry-After的响应信息
414	|Request-URI Too Large	|请求的URI过长（URI通常为网址），服务器无法处理
415	|Unsupported Media Type|	服务器无法处理请求附带的媒体格式
416	|Requested range not satisfiable	|客户端请求的范围无效
417	|Expectation Failed	|服务器无法满足Expect的请求头信息
500	|Internal Server Error|	服务器内部错误，无法完成请求
501|Not Implemented	|服务器不支持请求的功能，无法完成请求
502|	Bad Gateway|	作为网关或者代理工作的服务器尝试执行请求时，从远程服务器接收到了一个无效的响应
503	|Service Unavailable|	由于超载或系统维护，服务器暂时的无法处理客户端的请求。延时的长度可包含在服务器的Retry-After头信息中
504	|Gateway Time-out	|充当网关或代理的服务器，未及时从远端服务器获取请求
505|	HTTP Version not supported|	服务器不支持请求的HTTP协议的版本，无法完成处理
*****

> HTTP状态码由三个十进制数字组成，第一个十进制数字定义了状态码的类型，后两个数字没有分类的作用。HTTP状态码共分为5种类型：

#### Ajax中get和post两者最简单的区别施
1. 使用get请求时，参数在url中显示，而使用post方式，则不会显示出来（get请求会将参数跟在url后面进行传递，而post请求则是作为HTTP消息的实体内容发送给web服务器。当然在ajax请求中，这种区别对用户是不可见的。）
2. 使用get请求发送数据量小，只能传递大约1024字节。post请求发送数据量大，理论上无限制
3. get请求需注意缓存问题，post请求不需担心这个问题（get方式请求的数据会被浏览器缓存起来，因此其他人就可以从浏览器的历史记录中读取到这些数据，例如账号和密码等。某种情况下，get方式会带来严重的安全问题。而post方式相对来说就可以避免这些问题 ）

#### 使用get方式需要注意：
1. 缓存 在url?后面链接一个随机数，时间戳
2. 乱码  编码encodeURI
> 对于get请求，被传递的参数要先经encodeURIComponent方法处理，例如：xhr.open('get','2.get.php?username'+encodeURIComponent(leo)+'&age=30&'+new Date().getTime(),true);即get传递参数需要拼接到url当中(new Date().getTime()是添加的时间戳)。

#### 使用post方式需要注意：
1. 数据放在send()里面作为参数传递。例：xhr.send('username=leo&age=30');当xhr.send()没有数据向后台传输，则 xhr.send()或xhr.send(null)
2. 需要设置请求头，
> 需要设置requestHeader的content-type为application/x-www-form-urlencoded声明发送的数据类型。所以post没有缓存问题，也无需编码
`例：xhr.setRequestHeader('content-type','application/x-www-form-urlencoded');`

 
# Xml的相关知识
### 1.什么是 XML?
- XML 指可扩展标记语言（EXtensible Markup Language）
- XML 是一种标记语言，很类似 HTML
- XML 的设计宗旨是传输数据，而非显示数据（html）
- XML 标签没有被预定义。您需要自行定义标签。
- 数据交互格式
- xml是用来存储和传输数据的
> HTML: 用来显示数据的
       > XML 不会替代HTML, XML用来传输数据，HTML用来格式化并且显示数据，总之XML是信息传输工具

### xml的语法规则：

+ a.标签必须闭合，没有单标签
`声明没有关闭标签，声明不属于XML本身的组成部分。它不是 XML 元素，也不需要关闭标签。`
+ b.标签对大小写敏感 <Message>标签与<message>标签不同
+ c.标签合理的嵌套，不允许交叉嵌套
+ d.须有根元素，是所有其他元素的父元素

```js
<root>
    <child></child>
    <child></child>
</root>
```
+ e.Exml标签的属性值必须加引号
+ f.实体引用
```js
<message>if number<100 then</message>
```
> 会发生错误，解析器会把它当做新元素的开始，为了避免发生错误，用实体引用来写 
`&lt—小于` ` &gt — 大于` ` &quot — 双引号` `&apos—单引号`
### Xml元素命名规则
1. 名称可以含数字、字母以及其他字符
2. 不能以数字和其他标点符号开始
3. 不能包含空格
4. 不能以字符xml开始
5. <?xml version="1.0" encoding="ISO-8859-1"?> 必须要写 不写会报错，version: 定义了xml的版本，encoding: 告知浏览器解析编码的格式
6. 如果要使用xml进行数据交互，要通过php进行处理
7. 在PHP中获取要互交的xml文件file_get_contents（‘xml文件的相对地址’）
8. 将获取的xml文件响应到前端，直接echo即可

> 前端接收后台响应的xml数据
`注意：不能使用xhr.responseText来接收，应该用xhr.responseXML来接收`

> html 是用来显示数据的，为了数据与结构分离，我们可以把数据放在xml里面，用javascript来把xml里面的数据展示在html里
> html用来显示数据的为了数据与结构分离，我们可以把数据放在xml里面，用JavaScript来把xml显示在html中。

# JSON
```
JSON：JavaScript 对象表示法（JavaScript Object Notation）。
JSON 是存储和交换文本信息的语法。类似 XML。
JSON 比 XML 更小、更快，更易解析。
```
### 优点：数据结构简单，便于读写
    易于解析，使用方便，较XML更加的便捷
    编译、预编译时节省时间
    数据轻量型，传输数据更小
### 缺点：书写格式更加严谨，在编写时容易出错
### 书写规则：文件名：xxx.json
  > json数据中最后一个数据不能加 “ , ”

<font color=#AA3731 size=7 face="黑体">JOSN.parse()      从字符串中解析出JSON对象</font>
<font color=#AA3731 size=7 face="黑体">JSON.stringify()  把ISON对象转化为字符串的形式</font>

# jsonp     跨域
## json with padding ：使用内嵌的形式把json数据获取到，然后就可以进行数据的渲染了
1. 为什么学jsonp?						只能使用get方式
- Ajax不能实现跨域请求
```js
什么是跨域？（不会解析IP地址）
非同源策略
1.源
https://www.sina.com:80？username=aaa&age=18
https:// 协议 
sinna.com 域名
80： 端口号
username=aaa&age=18: 参数
同源： 协议、域名、端口号都相同就是同源
http://www.baidu.com
http://www.baida.com 不同源，域名不同
http://www.aaa.com
https://www.aaa.com 不同源，协议不同

http://www.asd.com:80
http://www.asd.com:8080 不同源 端口号不同
同源： 协议域名端口号必须都相同才是同源
```
- 同源策略
> 浏览器的一种安全功能，如果a.com域名下的文件想请求另一个域名b.com下的文件的时候，是无法获取到的。

> 同源策略限制从一个源加载的文档或脚本如何与来自另一个源的资源进行交互。这是一个用于隔离潜在恶意文件的关键的安全机制。
> 浏览器的同源策略，出于防范跨站脚本的攻击，禁止客户端脚本（如 JavaScript）对不同域的服务进行跨站调用（通常指使用XMLHttpRequest请求）


> 【注】src写url时，要给后端传callback的函数名

- 注意：jsonp和json并没有什么关系

## jsonp 只能用‘get’方式传递数 必须与后端配合
 
### jsonp原理：
> 通过script标签请求一个服务端的文件（php），这个文件返回的是一段js代码，作用是调用我们先前定义好的一个函数。从而将服务端想要给客户端的数据，发给客户端

- 注意：函数名要唯一

> $.ajax()  
`在jQuery中，没有兼容问题，ajax不用创建，直接调用方法`
```js
$.ajax({
    type:'post'//请求方式
    dataType:'jsonp',   //期望后台返回的数据类型，若果不指定，浏览器自身解析
    data:'id=10',
    jsonp:'jsonp_callback',
    url:'http://www.yiwuku.com/getdata', //发送请求地址
    success:function(){
        //dostuff
    },
});
```

#### form表单三个重要属性：
> method：提交方式
> action：提交地址
> name 属性的表单元素才能在提交表单时传递它们的值。
```js
enctype
   application/x-www-form-urlencoded
action 请求地址 URL
method 请求方式、方法 get/post 
get:在URL地址可以看到
post：如果用post发送数据，必须设置form表单 enctype="multipart/form-data"
```
