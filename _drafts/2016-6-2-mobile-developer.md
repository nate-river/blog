---
  layout: post
  title:  移动端开发流程
  tags:
  categories:
---


## 基本的知识储备

移动端的常见浏览器

* Android内置浏览器  
* 各大厂商基于Android内置浏览器开发的浏览器
* chrome  firefox  uc
* safari

在移动端可以放心使用 [`html5`](https://developer.mozilla.org/zh-CN/docs/Web/Guide/HTML/HTML5) [`css3`](http://nate-river.github.io/css3);

Css3中的重点(工程)

* 自定义字体 字体图标的使用
* @mediea 响应式
* transform  transition  animation

html5中的重点

* socket.io
* 离线*存储   localstorage  offline
* 多媒体
* historyAPI   拖放
* requestAnimationFrame


## 移动开发的解决方案

零散型的解决方案

1. bootstrap ( materialize )
2. jquery.js + swiper.js  + touch.js
3. zepto.js  (www.zeptojs.cn)
4. 专门针对移动端的meta标签
5. 开发中两个重要的概念  百分比 ：rem;
6. 前端自动化
7. 版本控制

框架型的解决方案

angular + ionic(移动APP) + sass + 前端自动化
+ 版本控制

前端自动化

node.js   七天学会node.js淘宝
bower + gulp + yoman


开始布局

1.  先把字体图标定好  (设计师给，自己去找)

    iconfont.cn


2.  利用rem处理等比例缩放的布局

    常见逻辑像素 320 360 375 385 414 480  

    需要在@mediea中处理html标签的根字体  

    html{ font-size:100px }

    320px      width:0.3rem  height:0.3rem;

    360px      width:60px    height:60px;  html: 200px;

3. bootstrap 百分比布局

```html
<div class="container-fluid">
  <div class="row">
    <div class="col-xs-8"></div>
    <div class="col-xs-4">
      <div class="row">
        <div class="col-xs-12"></div>
        <div class="col-xs-6"></div>
        <div class="col-xs-6"></div>
      </div>
    </div>
  </div>
</div>
```
