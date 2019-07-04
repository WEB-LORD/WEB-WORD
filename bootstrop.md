# Bootstrap
##
- Bootstrap 4 不兼容IE8

> 简洁、直观、强悍的前端开发框架，让web开发更迅速、简单 
。Bootstrap是基于HTML、CSS、JAVASCRIPT的，让书写代码更容易 
## 响应式 : 
> 同一个网站，在不同的设备或不同的尺寸的屏幕下，显示不一样的样式，实现多设备多尺寸的兼容，提高用户的体验。 
> 响应式开发方法 : 
> rem布局、fiex布局、媒体查询、bootstrap 

>> 开发环境----未压缩，可以看源码,有报错和提示信息
>> 生产环境----压缩版 

### 使用： 
> CDN加速、命令行安装 
- 使用boostsrap.js需先引入jquery.js, 前者依赖后者
```js
<link rel="stylesheet" href="bootsrap/css/bootstrap.min.css">
<script src="bootsrap/js/jquery.js"></script>
<script src="bootsrap/js/bootstrap.min.js"></script>
```
> 工作步骤
>> 1.有父级容器 container
>> 2.有行 row
>> 3.有列 col 盛放实际内容 , 列必须是行的直接子集 
>>> col-md-数字 12/数字 = 列数
******
## 栅格系统 

> 栅格系统将页面分为12列，不同分辨率根据设置的栅格数呈现对应的栅格数量
- 通过控制类名来实现不同的布局和样式
- 类名后面的数字尽量不要写小数，如果总列数大于12，多余的“列（column）”所在的元素将被作为一个整体另起一行排列

### 容器
> calss="container" 固体宽度 ：两端留白、居中，使用媒体查询实现自适应`固定宽度不是开发人员设定的，是通过内置的媒体查询方法在浏览器视口变化时设置不同的宽`

> class="container-fluid" 流体宽度 ：页面宽度始终100%视图窗口宽度
`默认：padding(15px)、margin(auto)`

> container容器和container-fluid容器不能出现嵌套关系

*******
**| 超小屏幕 手机 (<768px)|	小屏幕 平板 (≥768px)	|中等屏幕 桌面显示器 (≥992px)	|大屏幕 大桌面显示器 (≥1200px)
--|--|--|--|--
栅格系统行为	|总是水平排列	|开始是堆叠在一起的，当大于这些阈值时将变为水平排列C
`.container` 最大宽度	|None （自动）	|750px|	970px	|1170px
类前缀	|.col-xs-|	.col-sm-|	.col-md-|	.col-lg-
列（column）数|	12
最大列（column）宽|	自动	|~62px|	~81px	|~97px
槽（gutter）宽	|30px （每列左右均有 15px）
可嵌套|	是
偏移（Offsets）|	是
列排序	是|
******

###简述栅格系统的原理？
1. 创建栅格系统的容器，容器的类名有两种 container和container-fluid `container是固定宽度，居中显示, container-fluid宽度为100%`
2. 给栅格系统合适的排列，容器内部要定义行，类名是row，每一个row代表一行
3. 行的内部定义单元格，单元格用col-类前缀-数字表示，数字从 1-12中取，数字等于几，就占几份，
>Bootstrap中的栅格系统是通过一系列的行（row）与列（column）的组合创建页面布局，然后你的内容就可以放入到你创建好的布局当中。栅格系统的工作原理： 
>网格系统的实现原理，仅仅是通过定义容器大小，平分12份(也有平分成24份或32份，但12份是最常见的)，再调整内外边距，最后结合媒体查询，就制作出了强大的响应式网格系统


### 编辑技巧
响应式布局：针对不同屏幕尺寸隐藏或显示页面内容
visiable-a-b 可见类
a 类前缀 xs sm md lg
b 状态 block inline inline-block

> hidden-a 隐藏类
>> hidden-md 在中等屏幕下隐藏

> pull-left 浮动
> affix 定位

> 字体图标 Glyphicons
>> 1.减少请求 2.容易控制样式，当做字体

预定义样式 	|	(颜色预设)
--|--
primary 	|	首选项(暗蓝)
success 	|	成功(暗绿)
warning 	|	警告(澄粉)
danger 		|	危险(淡紫)
info 		|	信息(淡蓝)

> 用法 ：a-danger 
>> a 类型 bg--标签背景 btn--按钮 text--字体
>>> btn-xs 设置大小 最小


> 列偏移 col-lg-offset-3
>> 将某列向右侧偏移
> 列嵌套
>>可以把某一列当做一个行，内部再写列
> 列排序
>>col-md-push (向后走)或 col-md-pull (向前走)
- 都需单独写