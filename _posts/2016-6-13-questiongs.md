---
layout: post
title:  "一些题目"
---
# 面/笔试准备方向

## html

* 访问一个网页的时候发生了什么事情
* 标签语义

## css

* 盒模型 浮动 定位 图片精灵 文档流 小的布局原理

## javascript

* 闭包 原型链  作用域  函数作用域链  new
* 函数 bind  call apply
* this的指向
* 函数 字符串 正则 常用方法
* Dom对象中的方法
* 事件对象  事件流 事件委托

## jQuery

* 选择器及其应用场景（10个例子）
* ready()和 window.onload的区别（）
* 过滤器 jQuery对象和 dom对象 dom集合
* 动画参数 用法 队列
* $.extend()  $.fn.extend()  jQuery插件
* $.contais  $.inArray  $.proxy()
* $.ajax 用法 及其知识点
* jQuery 中数据缓存机制
* jQuery 版本号之间的区别
* jQuery $函数可接受的参数 和涉及到节点操作的函数的用法
* remove detach区别
* 回调函数 链式调用
* 一些内置工具函数的实现方法

## angularjs

* 数据双向绑定及其好处
* 作用域
* 服务  指令  过滤器
* 路由
* 依赖注入
* 常见指令参数
* $http promise
* 组件化开发及其好处
* 模块的概念及其在angular中的表现形式及其好处

## html5

* localStorage cookie Session
* audio/video
* canvas用途 编程模式
* 其他API

## css3

* 预编译scss等的语法和好处
* 响应式 rem  @media  12柵格
* 设备关键分辨率
* 变形和动画
* 以类逻辑的变动来和javascript配合呈现页面

## 移动端开发

* nativeAPP  webApp HybirdApp的区别
* 移动开发中的注意事项
* zepto.js和jQuery的一些差别
* 移动开发解决方案

## 大型实际项目

* node.js + yoman +  bower + grunt|gulp 三个小软件的使用 实现前端自动化
* require.js
* 前端项目的优化
* yahho十二条军规




# 一些笔试题


## 第一组

* h5为什么只需写<!doctype html>     
  >  不基于标准通用标记语言  不需要文档类型定义
  sgml dtd

* 描述cookies，sessionStorage，localStorage的区别？
  > 都是在本地存储数据
  > cookie 存储数据量小 8k  localStorage 10M
  > sessionStorage 会话期间有效  localStorage本地持久存储
  > cookie 可设置过期时间  会附在http头部发给服务器

* Html5的form如何关闭自动完成功能
  > autocomplete = "off"
  ```html
  <form action="" method="post" id="reg" autocomplete="on"></form>
  姓名：<input type="text" name="auto" list="movie">
  <datalist id="movie">
  <option>古惑仔</option>
  <option>中国</option>
  <option>古仔</option>
  </datalist>
  ```
* 如何实现浏览器内多个标签页之间的通信

  > localStorage

  ```JavaScript
  window.addEventListener('storage', fn)
  ```

* 页面可见性（Page Visibility）API可以有哪些用途

  > 切换选项卡时做一些操作
  > 统计用户留在页面的时间
  > 在线聊天离开状态
  > 切换选项卡停止动画


* Css3新增伪类有哪些
  > nth-child
  > nth-of-type


* 如果需要手动写动画，你认为最小时间间隔是多久？为什么
  > 和显示器刷新频率保持一致  
  > requestAnimationFrame()

* 什么是cookie隔离

  > 使用非主要域名存储图片或其他资源 来降低头请求的大小
  > 因为cookie不能跨域


* Css选择符有哪些，那些属性可以继承，那些属性不可以继承
  >很多
  >字体可继承 前提是没有

* Javascript有几种类型的值，你能画出他们的内存图吗
  > 引用和值
  > 引用是类似指针的东西

* [‘1’,’2’,’3’].map(parseInt)答案是多少
  [1,NaN,NaN]
  > parseInt 函数参数
  > map运行原理

* JavaScript代码中的‘use strict’是什么意思，使用它区别是什么
  > 使用严格模式


* 如何判断一个对象是否属于某个类
  > in
  > instanceOf

* 简单写一个通用的事件帧听器函数
  >// if(document.addEventListener){
  >// attachEvent()

* 一个页面从输入url到页面加载显示完，这个过程都发生了什么（流程说的越详细越好）
  > 简写先转换全  baidu.com  https://www.baidu.com:80
  > 域名解析成ip
  > http协议发送数据
  > 得到文档
  > 开始解析文档
  > 渲染 绘制 加载脚本
  > 执行脚本



## 第二组

* Document load和ready的区别
  > load所有资源加载完才执行js代码
  > DOM树构建完成执行js代码

* 是由使用过zepto.js？简单描述下zepto和jquery的差异
  > 小
  > 有若干手势事件
  > 数据缓存处理方式的差异
  > 插件库少

*
 ```Javascript
(function(){
   var a=5
})()
console.log(a);
```
如上代码会打印什么内容？打印在哪里？

* var a=[],b={};变量a和b哪个是array哪个是object

* json与jsonp的差异
  > xmlHttpRequest请求
  > 通过script src可跨域 解决跨域问题

* 用纯css编写一个当前流行的网页选项卡
  > hover  overflow:hidden 去掉;

* Css方面使用纯css实现未知尺寸的图片（但宽度小于200px）在200px的正方形中水平和垂直居中
  ```css
  img{
    display: block;
    position: absolute;
    margin:auto;
    top:0;
    left:0;
    right:0;
    bottom:0;
  }
  div{
    background: url('img.png') no-repeat center center;
  }
  ```

* 用js实现随机选取10-100之间的10个数字，存入一个数组，并排序
  > 发牌排序


* 把两个数组合并，并删除第二个元素

  > concat  splice

* JavaScript方面请给Array本地对象增加一个原型方法，它的用途是删除数组条目中重复的条目（可能有多个），返回值是一个包含被删除的重复条目的新数组
  > 字典


## 第三组

* css选择符的优先级算法
  > .a  div  span
  > 对某一个从后往前找
  > 找出数量最少的优先级最高

* 如何居中一个浮动元素，写出具体的css和html
  > 利用 position:relative 调整

* 如何实现一个两栏布局，左侧固定宽度200px，右侧自适应。写出具体的css和html
  > 定位浮动均可

* data-属性的作用是什么
  > 在标签身上存储自定义属性

* 请解释*{box-sizing：border-box;}  
  > div最终呈现宽度 不再按照 css width + padding + border 计算
  > 而是 全盒子模型的宽度等于设置的 width

* 有一个数组array1，它的每个元素都是一个英文单词，写一段代码，对其进行排重得到一个新的数组array2
  > 字典

* 写出你所知道的所以可用于查询节点的标准dom API   
  > console.dir(document)

* 有些css属性在使用时可能需要浏览器前缀，请写出你知道的所以前缀及对应的浏览器
  > -webkit-
  > -moz-
  > -o-


## 第四组

* 前端优化知识你知道哪些
  > 图片精灵 图片尺寸 图片格式
  > js放结尾 require.js异步加载js
  > 文件压缩合并
  > 减少网络请求
  > 代码中的细节


* JavaScript里的基本数据类型有哪些

* Js中this关键字如何使用，在那些场合下使用
  > 在函数内部使用
  > 函数不调用 它什么都不是暂时
  > 函数调用时 决定它指向哪里

  > 事件注册函数中的this 构造函数中的this
  > prototype中的this
  > jquery插件扩展中的this
  > jquery回调函数中的this  dom对象
  > 一系列以回调函数作为参数的方法中的this
  > map   foreach  filter
  > apply  call


* Ajax是什么？ajax的交互模型？如何解决跨域问题
  > 异步发送http请求
  > 发送 监听  返回

  > 不能解决，通过后台转换成同域问题

  > 不再采用 xmlHttpRequest 采用  jsonp协议 已经不再是ajax
  > 不再采用 xmlHttpRequest 采用 加载iframe 分析数据 也已经不再是ajax


* 怎样添加、移除、复制、创建和查找节点
  > dom API

## 第五组

* 浏览器标准模式和怪异模式的区别
  > document.body   document.docmentElement.scrollTop

* 你用过媒体查询，或针对移动端的布局/css吗
  >

* 如果设计中使用的非标准字体，你如何去实现
  > `@font-face`

* 请解释下inline和inline-block区别
  > 宽高 margin

* 请解释relative，fixed，absolute，static元素的区别
  > 除 static 均浮起 且高于浮动
  > relative 有假身占位 看着假身移动
  > absolute 要和祖先们商量
  > fixed 直接找最高领导

* 用css分别实现某个div元素上下居中和左右居中

  ```
  margin: 0 auto;
  ```
* 用div+css实现三栏布局（左右固定200px，中间自适应）
  > width:200  f   f margin-left:200  margin-right:200 height:200px r

* 为什么响应式设计和自适应式设计不同
  > 响应式由浏览器控制
  > 自适应加载不同的代码

* 写出下列代码的区别
    function Person（）{}
    var person = Person（）；
    var person= new Person（）；

  >  undifined 函数调用表达式求值
  >  得到一个对象 且对象原型指到Person.prototype

* 你使用过JavaScript模板系统吗？如果使用过请谈谈你都用过哪些库

  > angularjs ng-bind指令

* Js延迟加载的方式有哪些

  > async=true
  > require.js


* 哪些操作会造成内存泄漏
  > dom 操作 jquery是如何解决dom操作的内存泄漏问题
  www.imooc.com   jquery原理解析  dom操作


## 第六组

* 前端页面由哪三层构成，分别是什么，作用是什么
* 清除浮动的方法
* 有没有关注html5和css3？如果有请简单说一些您对他们的了解情况
* 你做的页面用那些浏览器测试过，经常遇到的浏览器兼容性有哪些，解决办法是什么

* 如何来管理所有的css文件、js和图片
* 列举同步与异步的区别，ajax的交互模型（原理）
* 尽可能列举jquery常用选择器，文档处理函数，筛选、事件，效果函数，ajax
* 用过哪些js框架，对于jquery列举工作中自己常用的插件
* 工作中遇到问题会怎么解决
* 有看过哪些比较喜欢的书籍、网站


## 第七组

* js表单弹出对话框函数是？获得输入焦点函数是？
  > confirm()  focus()

* 请列举一下常用的js字符串操作和数组函数，以及他们的功能、
  > .. split  slice  indexOf  trim()
  >    push  pop shift()

* Js中如何定义class，如何扩展prototype
  >  new

* Jquery中如何获取和设置css样式？
  > css

* Jquery中如何使用ajax
  > $.ajax

* 请列举几个您经常光顾的it网站或博客，最近看的一篇js的文章是
  > www.github.com  www.stackoverflow.com  www.leetcode.com

* 绘制一个标准的盒子模型，并用文字标注说明

* 输出对象中值大于2的key的数组
  Var data={a:1,b:2,c:3,d:4}
  Object keys(data).filter(function(){
    return                （补全代码）
  })
  期待输出[‘c’,’d’]

  > filter用法

## 第八组

* 对web标准以及w3c的理解和认识
  > 必须有标准   

* 行元素和块元素有哪些
  > xxx

* Css引入方式有哪些，区别是什么
  > style

* 解释css sprite，如何使用
  > 图片精灵

* Ajax请求时get和post方式的区别
  > get url传参  ?a=1&b=2&c=3

* 事件委托是什么
  > 利用事件流 冒泡 通过事件对象 e.target 捕捉 要分发函数的 小元素

* 闭包是什么，有什么特性，对页面有什么影响

  > 减少全局变量
  > 获取局部数据


* 如何阻止事件冒泡和默认事件

  > jquery return fasle
  > e.preventDefault
  > e.stopPropagation

* 请根据下面的描述，用json语法编写一个对象：
  “小明今年22岁，来自杭州，兴趣是看电影和旅游，他有两个姐姐，一个叫小芬，今年25岁，职业是护士，还有一个叫小芬，今年23岁，是一名小学老师”
  {
    'name':xiaoming
  }

  > json对象的格式

* 请阐述
   1）此代码功能
   2）优点和缺点
   3）listener.apply(el)在此的作用
   4）如何改进请写出，并说明理由

```Javascript
if（window.addEventListener）{
   var addlistener=function(el,type,listener,useCapture)
      el.addEventListener(type,listener,useCapture);
}else if(document.all){
     addlistener=function(el,type,listener){
       el.attachEvent(‘on’+type.function(){
       	listener.apply(el);
       })
     }
}
```
 > 解决了兼容问题的事件添加函数

## 第10组

* iframe有哪些缺点

  > 通信困难

* Js的eval是做什么的

  > 解析js代码

* 介绍js的基本数据类型
* Js如何实现继承
* 如何创建一个对象


## 第11组

* 在html5中，哪个元素用于组合标题元素
* 在html5中，onblur和onfocus是什么属性
* 在html5中，哪个方法用于获得用户当前的位置

* 新的html5全局属性，‘contenteditable’用于
* 哪个html5内建对象用于在画布上绘制
* Html5元素用于显示已知范围内的标题测量的是什么
* 在xhtml中，可以正确地标记段落的是什么？
* Js主要数据类型

* 把所有p元素的背景设置为红色的正确的jquery代码

* 用于添加或删除被选中元素的一个或多个类的jquery方法是什么？
$(':checked').addClass  removeClass
* 编写当i等于5时执行一些语句的条件语句代码
if( i === 5){
  console.log(1);
}
* 说明在网页设计中div标签的作用

* Flash、ajax各自的优缺点，在使用中如何取舍
  > 安全 兼容

## 第12组

* 如何判断jquery对象是否存在

  jQuery  $

* Dom对象与jquery对象之间如何转换
  $()
* 写出5个以上的jquery基本过滤选择器
  next  prev  parent chirden find
  map is first last eq
*  写出几个jquery的动画函数
  show hide slide
* 写出一个完整的jquery的ajax请求（要包括各种参数及回调函数）

* $(‘#someId’).clone()与$(‘#someId’).clone(true)有什么区别

* $(‘#someId’).css()方法可以接受几个参数

* 如何阻住事件对象的默认行为及事件冒泡


# 一些资源


* http://www.imooc.com/learn/425 (require.js)
* http://www.imooc.com/learn/30  (前端自动化)

* http://www.imooc.com/learn/172 (jquery原理)
* http://www.imooc.com/learn/222 (jquery原理)
* http://www.imooc.com/learn/156 (angular.js)

* http://www.leetcode.com      (换工作时打开)
* http://www.stackoverflow.com

* react

* javaScript 权威指南
* javaScript 高级程序设计
* javaScript 语言精粹
* javaScript 设计模式
* 关键字 + mdn
* 想办法使用google+stackoverflow
* 想办法英语过阅读关
* 在Github上维护自己的小项目,才能让自己有动力 `每天写代码`

* 尽早学习node.js(从给自己做小工具入手,直接写能用的东西,看没有任何用处)


# 未来的发展道路

1. 变身T字型人才,横向过关,纵向专家

2. 非常熟悉一个领域的业务流程

3. 能解决前端工程化问题 从技术选型,技术架设,到带团队等等

4. 能用node.js去处理任何其他事物

5. 培养产品思维.培养产品思维

6. 创业 去创造价值
