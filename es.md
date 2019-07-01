# ECMAScript 6

## ES6 声明变量的方式

### let 特点 ：
- 1.不存在变量提升(不存在预解析)
```
预解析：js代码执行时分两个阶段
编译阶段： var b ，会被提升到当前作用域的最前面
执行阶段： b = 5 , 会留在原地等待解析
```
- 2.块级作用域，用 {} 声明 --- let 是在代码块内有效，var 是在全局范围内有效
- 3.不能重复声明(在一个代码块中)

### const 特点：
- 1.不存在变量提升
- 2.块级作用域，用 {} 声明 --- const 是在代码块内有效，var 是在全局范围内有效
- 3.声明一个常量，变量一旦声明，必须赋值 (不能以后赋值)，不能修改

> const 声明一个只读变量，声明之后不允许改变。即一旦声明必须初始化，否则会报错
> ES6 明确规定，如果区块中存在let和const命令，这个区块对这些命令声明的变量，从一开始就形成了封闭作用域。凡是在声明之前就使用这些变量，就会报错。

### 暂时性死区

> 总之，在代码块内，使用let命令声明变量之前，该变量都是不可用的。这在语法上，称为“暂时性死区”（temporal dead zone，简称 TDZ）。暂时性死区的本质就是，只要一进入当前作用域，所要使用的变量就已经存在了，但是不可获取，只有等到声明变量的那一行代码出现，才可以获取和使用该变量。

## 模板字符串

## 符号表示 `` (反引号) 

> 在模板字符串中的空格、换行返回时会保留

### 优点：
- 1.可以充当普通字符串
- 2.用来字符串拼接 ${} ${数字/字符串/等} 元素添加时必须是 id 名
  定义多行字符串，还可以在字符串中加入变量和表达式

- es5 拼接
```js
var str1 = '你好';
console.log("我："+str1);
```
- es6 拼接
```js
var str2 = "跨域";
console.log(`你：${str2}`);
console.log(`你：${str2 + str1}`); //字符串
console.log(`你：${33 + 633}`); //数字
```
## 解构赋值
> ES6中允许按照一定的模式，从数组或对象中提取需要的值，赋值给一个变量。
> 交换变量的值

### 数组解构： [] 数组是有次序的，以序列号一一对应，如果结构失败，返回undefined
> 可以设置默认值
- 顺序： 有赋值找赋值，无赋值找默认值，无默认值则返回undefined

### ... 剩余解构 即后面的唯一整体(以数组形式) 

> 数组解构
- es5
```js
var arr = [5,16,49,65,98,89,54];
console.log(arr[0]);
```
- es6
```js
const [a,b,c,d=666,e] = [5,16,49]; //可以设置默认值
console.log(a,b,c);
const [a1,b1,...c1] = arr; //...剩余解构 即后面的唯一整体(以数组形式)
console.log(a1,b1,c1);
```

### 对象解构: {} 对象是无序的，变量名和属性名称对应，如果变量名和属性名不对应，起别名，别名与属性名对应，没有的 undefined
- 可以设置默认值
```js
var obj = {"name":'ert',"age":66,"sex":1}
```
- es5 获取属性值
```js
var name = obj.name;
console.log(name);
```
- es6
```js
const {sex:ee,age} = obj;   //sex:ee 别名 值不变
console.log(age,ee);
const {ss,gg} = obj;       //变量名和属性名要一致， 不存在变量返回undefined
console.log(ss,gg)
```

### 字符串解构： 会转换为一个类似数组的对象,类似数组的对象都有一个length属性，因此还可以对这个属性解构赋值
### 函数解构 ： 函数调用的时候，传入的实参表面上是一个数组，但在传入的那一刻，数组参数被解析为变量 x,y,... 在函数内部，函数感受的值就是变量 x,y,...
- 可以设置默认值
```js
function fun2({s,d=123}) { //形参和变量名要一致，不可起别名
   console.log(s,d)
}
fun2({a:33,b:55});
fun2({s:99});
fun2({});
// fun2() 报错
function fun3({s,d=123}={}) { //形参和变量名要一致，不可起别名
    console.log(s,d)
}
fun3() //未报错
```

## 数组新增方法

### find() 		
> 找出第一个符合属性的数组成员，参数是回调函数 数组成员依次这个回调函数，返回第一个返回值为true的数组项， 没有符合的返回undefined
## find(function(item,index,arr){})
- item 数组项
- index 数组索引
- arr 原数组
### map() 		
> 映射 把数组映射成新数组，不改变原数组，参数为回调函数，返回数组
### every() 	
> 返回布尔值 有假则假，全真才真
### some() 		
> 返回布尔值 有真则真，全假才假
### includes() 
> 返回布尔值 直接调用，判断是否包含给定的值
### filter() 	
> 返回新数组 过滤掉不满足条件的值，不改变原数组
- 作用 数组去重，去掉空数组项，undefined
### fill() 		
> 使用给定值填充一个新数组 ，用来数组初始化，数组中已有的元素，会被全部抹去。
- 第二个参数和第三个参数，用于指定填充的起始位置和结束位置(不包括结束位)
### Array.from() 
> 把类似数组的对象或可遍历的对象转化为数组
### reduce() 	
> 接受一个函数作为参数，函数累加器，函数是用来做运算的。 数组从左向右依次所见，最终计算出一个值
```js
      reduce(function (prev,next,index,arr) {})
- 函数参数 prev:计算初始值或上一次计算的返回值 必选
- next:当前参与计算的值 必选
- index:当前参与计算值的索引
- arr:数组本身

- 购物车

var obj1 = [
   {name:'香蕉',price:10,mount:4},
   {name:'榴莲',price:30,mount:5},
   {name:'芒果',price:3,mount:8}
];
var total = obj1.reduce(function (prev,next) { 
   return prev + next.price*next.mount
},0)
console.log(total);
```
> reduce 可以传参 参数为prev的初始值 reduce(function(){},intial)
> reduce(function (prev,next,index,arr) {},intial)

#### 如果传参，为prev的初始值，next的取值为数组第一项
#### 如果不传参，prev为数组第一项，next顺延取值(数组下一项)
#### intial可以为任何值
```js
var a1 = ['name','age'];
var a2 = ['aaa',45];
// var aobj = {}; => {name: "aaa", age: 45}
var aobj = a1.reduce(function (prev,next,index,arr) { 
   prev[next] = a2[index];
   return prev; 
},{})
console.log(aobj)
```

## 箭头函数

- es5 函数
`function name(e) {};`
- es6 将function关键字和函数名去掉 ()=>{}
> 使代码更简洁 
`var fun = ()=>{}`
> 当只有一个参数时：() 可选，可以省略
`var fu1 = e => {}`
> 没有参数时， () 必选
`var fn2 = () => {}`
> 多个参数时， () 必选 每个参数用 , 分隔
`var fn3 = (e,r,g) => {}`
> 多条语句时 {} 和 return 不能省略
```js
var fn4 = (e) => {
for (let i = 0; i < 5; i++) {
   return e+i
   }
}
```
> 只有一条语句， {} 和 return 可以省略

`var fn5 = (a,b) => a+b; `

########Promise异步编程
```js
var ajax = (url,type,callback) => {
  var xhr = new XMLHttpRequest();
  xhr.open(url,type);
  xhr.send();
  xhr.onredaystatechange = () => {
   //...监听事态
  callback()
  }
}
ajax('a.php',get,()=>{
   //设置div颜色
ajax('',get,()=>{
   //设置宽增加
ajax('',get,()=>{
   //设置left
   // ajax(...)...
    })
  })
})
以上写法称为回调地狱 (一层套一层)
```
解决方法 ： promise    ES6
#### Promise 承诺，解决异步请求，比传统的更强大更合理 构造函数 new Promise()
> 函数参数是一个立即执行函数,这个函数叫立即执行器(exquter)，执行器有两个参数resolve,reject 也是函数

- resolve作用 将promise对象的状态从 “等待” 变为 “成功” ，即pending变成fulfillde，在异步加载成功时调用，并将操作请求成功的结果作为参数传递出去
`resolve('zhi') zhi 可以是任意值`

- reject作用 将promise对象的状态从 “等待” 变为 “失败” ，即pending变成rejected，在异步加载失败时调用，并将操作请求失败的结果作为参数传递出去
`reject('zhi') zhi 可以是任意值`

##### promise三种状态：

- pending 等待中 在创建promise实例时就产生
- fulfilled 成功
- rejected 失败

> 其状态只能从pending变成 成功 或 失败，一旦成功不能失败，一旦失败不能成功
> 每一个promise对象都有 then 方法

##### then() 两个函数(参数) 第一个函数异步调用成功时执行，第二个函数异步调用失败时调用

> 每一个 then 方法都会返回一个新的 promise ,又因为每一个promise对象都有 then 方法，所以可以无限调用 then()方法

- catch()        对应then第二个参数
- finally()
```js
var promise = new Promise((resolve,reject)=>{
console.log('sss');

   resolve和reject 的执行顺序 ：谁在上谁先执行

resolve('then 第一个函数传参'); //调用方法，成功时调用
reject('then 第二个函数传参'); //失败时调用 
});

promise.then((num)=>{
  console.log(num) // => then 第一个函数传参
},(e)=>{
   console.log(e)
}).then().then().then() //无限调用then方法
console.log(promise);

> 上面then的简写

var newP = promise.then((f)=>{
//请求成功的执行函数
console.log(f)
}).catch((e)=>{
//请求失败的执行函数
console.log(e)
}).finally(()=>{
//永远都会被执行
})
```
#### Promise静态方法

#### Promise.all() 参数是一个数组，返回一个新的promise ，如果数组中promise全成功，新promise状态为成功，有一个失败，新promise状态为失败
#### Promise.race() 参数是一个数组，返回一个新的promise, 谁执行快，返回谁

> then()方法,catch，finally方法 都是挂到 promise.prototype下面， 因此由promise创作出来实例都可以使用这些方法 静态方法(自身有的)

```js
var p = new Promise((resolve,reject)=>{
   // resolve('p')
   // reject('失败')
   setTimeout(()=>{
      resolve('p')
   },1800)
});

var p1 = new Promise((resolve,reject)=>{
   setTimeout(()=>{
      resolve('p1')
   },1500)
});

var p2 = new Promise((resolve,reject)=>{
   setTimeout(()=>{
      resolve('p2')
   },2000)
});
console.log(p,p1,p2); 

var a = Promise.all([p,p1,p2])
console.log(a)
a.then((res)=>{
   console.log(res)
})
var r = Promise.race([p,p1,p2]);
console.log(r)
```

### Axios
- 是一个基于 promise 的 HTTP 库，可以用在浏览器和 node.js 中。
- 基于promise封装的ajax类型的库。----类型和ajax类似，源码利用promise开发

> 配置参数：
- URL:接口
- 请求类型：get/post(常用) header,put,patch,delete,option (非常用)
- 调用：
> axios.get() 基于请求方式get发送请求 axioc.post() 
- get请求发送数据
```js
1.url?参数
2.axioc.get('url',{
   params:{ }
  }) 
  返回的数据在then中获取 
  后端发送get请求的方式
- 1.axios.get('http://132.232.89.22:3000/list?page=1')
- 2.axios.get(url.{params:{}})

var ul = document.getElementById('ul1'); 
axios.get('http://132.232.89.22:3000/list?',{
	params:{
		'page':1
}
```
### 控制台：
- config 本次请求的配置信息
- data 请求返回的数据
- headers 后端返回的请求头
- request ajax实例
- status 响应状态码
- statusText 响应状态描述

## *重点：所有请求方式返回的是promise对象，then方法
> node_modules 项目使用的依赖包、插件、库等

```js
axios.post() 基于post方式向后端发送请求
   axios.post(url,{
   要发送的数据
	})
   向后端发送的数据都是以 json 格式发送的，相当于把数据放在了请求主题里面
```
> 配置默认的全局URL地址，axios会把其与后边的拼接起来

```js
axios.defaults.baseURL = 'http://132.232.89.22:3000'; 
function fn1() {
   return axios.get('/slider')
}
function fn2() {	
	return axios.get('/list')
}
axios.all([fn1(),fn2()]).then(res=>{
console.log(res);
let [arr1,arr2] = res; //解构方法
// res[0] 数组方法
// res[1]
})
```
### axios另类写法 (ajax类似)
```js
axios({
	url:'http://132.232.89.22:3000/addcar',
	baseURL:'http://132.232.89.22:3000',
	url:'/addcar',
	data:{ //向后端发送的数据
   name:'德润定光',
 	 id:66
	},
	method:'post', //默认get
	headers:{ //自定义请求头
	author:'sss',
	age:30
	},
	timeout:3000, //请求超时 如果请求超过3秒未请求到，那么请求中断
	responseType:'json', //后端返回的数据类型， 默认json
})
```

## 扩展运算符 ...

### 数组的扩展运算符 ：
- 1.把数组的项目转化为参数序列 
- 2.复制数组
- 3.与解构赋值结合使用，用于生成数组
- 4.将字符串转为真正的数组
### 对象的扩展运算符 ：用于取出参数对象中的所有可遍历属性，拷贝到当前对象中




