### 微信小程序开发

1. 注册账号
   https://mp.weixin.qq.com/wxopen/waregister?action=step1
2. appid
   https://mp.weixin.qq.com/ 登录里面的开发设置能看到 appid
3. 小程序配置 app.json  

- pages 页面的集合，每一条对应了一个页面,每个页面对应了一个文件夹
- 每一个页面文件夹下面的文件 wxml ->html wxss ->css js 当前页面的 js json 当前页面的配置 建页面的时 wxml wxss js json 的名字要相同
- window —— 定义小程序所有页面的顶部背景颜色，文字颜色定义等
- 小程序全局配置的文档 https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html
4. 一个应用都叫做app  
app.js 和app.json 是全局配置  
#### 小程序的标签
- text 文本标签
- view 视图容器（div）
- image 图片标签
- block 无语义标签 不会编译出dom元素
- 其他标签 button input 
### 小程序页面
页面对应的js 
data ->表示数据
用法  ->{{}}
- wx:if 和hidden 的区别 频繁切换的时候用hidden 
- wxml语法参考 
https://developers.weixin.qq.com/miniprogram/dev/reference/wxml/data.html
