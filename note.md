# git 的使用

#### 第一次配置 git 需要配置 username email

> paste 粘贴
> 桌面点击右键 --> git bash

1. git config --global user.name "ruanye"
2. git config --global user.email "55343581@qq.com"

### git 仓库提交的流程

> git bash 要在你提交的文件夹下面运行

#初始化 git 仓库 
  --初始化
        git init  一个仓库只需要初始化一次
  --添加文件到缓存区
        git add 文件名
        通常使用全部添加
        git add -A -A 表示 all 的意思 所有(git add \*)

  --提交文件到本地仓库（自己电脑）
        git commit -m'第一次提交'       -m 通常表示你此次提交内容的备注

  --添加远程仓库  
        git remote add origin 仓库名  
            https://github.com/ruanye/1808B.git 仓库地址
        git remote add origin https://github.com/WEB-LORD/6.27git

  --查看远程仓库地址
        git remote -v

  --推送代码到远程仓库  
        git push origin master

### 删除远程仓库

git remote rm origin

- 同一个仓库/项目

#### 如果是第一次提交 5 步

1. git init
2. git add -A
3. git commit -m'你的注释'
4. git remote add 仓库地址 添加远程仓库(第一次提交时候使用)
5. git push origin master

#### 如果有修改 第二、第三.....第 n 次 3 步

1. git add -A
2. git commit -m'注释'
3. git push origin master


#### 第一次提交的示例

1. git init
2. git add -A //添加上传的内容
3. git commit -m "VUE" //告诉云盘你传的是视频还是图片
4. git remote add origin https://github.com/ruanye/1808vue.git 存储的文件夹
5. git push -u origin master 上传按钮

### 拷贝仓库地址到本地

下载 git clone +仓库地址
例子：git clone https://github.com/ruanye/1807lesson.git

### 合作做项目或者远程仓库有更改这时每次提交（commit）之前必须 git pull origin master (拉取远程仓库) 为了保证同步
git pull origin master (拉取远程仓库)









# node 的基础知识

nodejs 后端语言 java/php 等价 单线程/异步，无阻塞 i/o

### node 的几个核心模块

1. http 模块 创建服务器
   新建文件 app.js
2. url 模块 解析 url
3. path 模块 解析路径 path.join path.resolve
4. fs filesystem 文件处理 读写文件

### node 的启动方式

1. vscode 插件 code runner
2. node + 文件名
3. 服务端代码有改动需要重启

### node 模块的使用 commonjs 规范

moulde.exports 表示导出模块
require 引入模块

- window 常用 linux 命令  
  touch 建立文件
  mkdir 新建文件夹
  cd 进入文件路径








#vue
### 一）package.json的作用(了解)
- node_moudules 文件夹 -->放着我们项目的依赖 
- dependencies(依赖)  devDependencies(开发依赖) 写代码的时候需要用，打包的时候不需要 npm install 其实就是走的依赖 
- scripts 脚本 npm run serve 
- name 项目名称, version:版本号
### 二）路由懒加载（掌握2，3）
1. /* webpackChunkName: "about" */   可以给懒加载模块起名 
2. import() 表示懒加载，es6的语法 
3. 路由懒加载的写法(跳转到当前路由才去加载组件) 
```js
() => import('./views/Home.vue')
```
4. 路由重定向 使用redirect 
### 三) 局部组件引入流程
1. 用import 标签导入
2. 在components里面注册
3. 用标签的形式使用 

### 四） 路由激活样式(掌握exact的使用) 
router-link-exact-active router-link-active
router- link   exact 属性 确切严格的匹配  
### 五）es6的module  import export（掌握） 
- import 导入
- export 表示导出  export 导出的是一个接口,不能是具体值 
- import 导入的变量 在顶级作用域，不能被更改 
- export defautl 默认导出 后面跟具体的值   
```js
 let a =1 
 let b =2 
@@ -37,9 +39,33 @@ router- link   exact 属性 确切严格的匹配
 //正确写法
 export{a,b}
```
<!-- - import {getBanner} from '../api'等价于 
import {getBanner} from '../api/index.js '  
 api->自动查找index.js 作为默认入口  -->
```js
//a.js 
export {a,b}   
//b.js 
//第一种写法(解构赋值)
import {a} form  'a.js' //直接使用a
// 第二种写法（全挂载到一个对象上面）
import * as type from 'a.js' //使用type.a 
```
```js
//a.js
export default 1
//b.js
import xxx from 'a.js'
```
### 六） async await 异步的终极解决方案(掌握) 
 - async 后面必须跟函数 表示函数路面有异步操作 
 - await 后面通常跟promise(也可以跟普通值) 跟promise  表示promise的执行结果 
###  七)  组件化的好处（了解）
 1. 可复用 
 2. 便于维护
 3. 可组合
### 八） axios （掌握）
 - axios.defaults.baseURL  抽离公共的请求路径 
 - axios.interceptors.response.use  响应拦截器  interceptors 拦截器 
 - axios.interceptors.request.use 请求拦截器  
 
## 二、流程
@@ -70,13 +96,21 @@ import {getBanner} from '../api/index.js '
import 'swiper/dist/css/swiper.css'
Vue.use(VueAwesomeSwiper)

```
6)api/index.js 写法
- import {getBanner} from '../api'等价于 
- api->自动查找index.js 作为默认入口 
- import {getBanner} from '../api/index.js ' 解构赋值 
- 第二种写法 //import * as obj from "../api";  会把所有的接口挂载obj 上面 
- 见到 export import 有2种写法  
```js
### 四) axios 的使用 src/api/index.js 
- npm install axios --save 
- index.js
```js
```

## 三、mock接口
 1) 和src同级建立mock（独立）文件夹(放在其他处也可以) mock(放mock数据) mock里面 建app.js(服务器)  banner.js（轮播图图片）  list.json（商品列表）
 2) express 使用 
 - npm install express 下载express (vue-cli创建项目里面不用下，因为vue-cli是基于webpack的，webpack自带了express)
@@ -93,10 +127,11 @@ Vue.use(VueAwesomeSwiper)
 const cors = require("cors")
 app.use(cors())
 ```
 
 ## getName  => get-name  相互转换  