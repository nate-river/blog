---
layout: post
title:  "fullPage.js"
date:   2016-04-05 12:31:27 +0800
categories: jekyll update
---

# [fullPage.js][full-page]配置项介绍

* sectionsColor

  一个数组 规定了各个section的颜色

* controlArrows

  定义是否通过箭头来控制slide幻灯片,默认值为true
  在移动设备上可以通过滑动来操作幻灯片

* verticalCentered

  每一页的内容是否垂直居中，默认值为true

* resize

  字体大小是否随窗口缩放而缩放 默认值为false

* scrollingSpeed

  滚动速度,默认为700毫秒

* anchors

  给每个section定义锚链接

* lockAnchors

  是否锁定锚链接

* active class

  默认显示哪个section

* easing

  定义页面section滚动的动画方式
  设置这个值需要引入jquery.easings 插件

* css3

  默认为true,使用css3 transform 来实现页面滚动动画

* loopTop

  滚动到最顶部后是否连续滚动到底部，默认值为false

* loopBottom

  滚动到最底部后是否连续滚动回顶部 默认值为false

* loopHorizontal

  横向slide幻灯片是否循环滚动，默认值为true

* autoScrolling

  是否使用插件的滚动方式，默认值为true, 如果设置为false,则会出现浏览器自带的滚动条

* scrollBar

  是否包含滚动条，默认值为false
  如果设置为true,则浏览器自带的滚动条出现
  页面滚动时还是页滚动，但是滚动条的默认行为也效果

* paddingTop  paddingBottom

  设置每一个section顶部和底部的padding，默认值为0
  如果我们需要设置一个固定在顶部或者底部的菜单，导航，元素等，可以使用这两个配置项

* fixedElements

  普通方式书写的固定定位元素会被插件覆盖
  需要我们通过指定这个属性才会生效，参数为一个jquery选择器

* keyboardScrolling

  是否可以使用键盘方向键导航，默认值为true

* touchSensitivity

  在移动设备中滑动页面的敏感性，默认为5，按百分比衡量，越大则越难滑动

* continuousVertical

  是否循环滚动，默认值为false，如果设置为true,则页面会循环滚动，
  不像loopTop loopBottom那样出现跳动 这个属性和loopTop loopBottom 不兼容 不要同时设置

* animateAnchor

  锚链接是否可以控制滚动动画，默认为true。如果设置为false,则通过锚链接定位到某个页面显示不再有动画

* recordHistory

  是否记录历史,默认为true,可以记录页面滚动的地址
  通过浏览器前进和后退按钮来导航

* menu

  绑定菜单，设定的相关属性与anchors的值对应后，菜单可以控制滚动，默认值为 false
  可以设置为菜单的jquery选择器
  ```html
  <ul id="fullpageMenu">
      <li data-menuanchor="page1"></li>
      <li data-menuanchor="page2"></li>
      <li data-menuanchor="page3"></li>
      <li data-menuanchor="page4"></li>
  </ul>
  ```

* navigation

  是否显示导航，默认false 如果设置为true 会显示小圆点，作为导航

* navigationPosition

  导航小圆点位置，可以设置为left或者right

* navigationTooltips

  导航小圆点的tooltips设置，默认为[],按照顺序放置

* showActiveTooltip

  是否显示当前页面的导航的tooltip信息，默认为false

* slidesNavigation

  是否显示横向幻灯片的导航，默认值为false

* slidesNavPosition

  横向幻灯片导航的位置，默认为bottom 可以设置为top

* scrollOverflow

  内容超过满屏后是否显示滚动条，默认为false. 如果设置为true,则会显示滚动条
  如果要滚动查看内容，还需要jquery.slimscroll插件，该插件主要用于模拟传统的浏览器滚动条

* sectionSelector

  section的选择器，默认为.section

* slideSelector

  slide的选择器 默认为.slide.


# fullPage.js 方法介绍

* moveSectionUp()

* moveSectionDown()

* moveTo(section,slide)

  滚动到第几页，第几个幻灯片，注意，页面从1开始，而幻灯片从0开始

* silentMoveTo(section,slide)

  滚动到第几页，和moveTo一样，但是没有动画效果

* moveSlideRight()

  幻灯片向右滚动

* moveSlideLeft()

  幻灯片向左滚动

* setAutoScrolling()

* setLockAnchors()

* setRecordHistory()

* setScrollingSpeed()

* setAllowScrolling(boolean,[directions])

  添加或删除鼠标滚轮/滑动控制，第一个参数true为启用，false 为禁用
  后面的参数为方向，取值包含 all,up,down,left,right,可以使用多个，逗号隔开

* destory(type)

  销毁fullpage特效，type可以不写，或者使用all,不写type,fullpage给页面添加的样式和html元素还在
  如果使用all,则样式 html等全部销毁

* reBuild()

  重新更新页面和尺寸，用于通过ajax请求后改变了页面结构之后，重建效果

#  fullPage.js 回调函数

* afterLoad(anchorLink,index)

  滚动到某一section，且滚动结束后，会触发一次此回调函数，函数接收 anchorLink 和index 两个参数，
  anchorLink 是锚链接的名称 index 是序号  从1开始计算
  可以根据 anchorLink 和 index的参数值判断触发相应的事件

* onLeave(index,nextIndex,direction)

  离开一个section时触发，通过return false可以取消滚动
  离开的序号 到达的序号  滚动的方向

* afterRender()

  页面结构生成之后的回调函数

* afterResize()

  浏览器窗口尺寸改变之后的回调函数

* afterSlideLoad()

  滚动到某一个幻灯片后的回调函数

* onSlideLeave

  离开一个slide之后的回调函数


[full-page]:   https://github.com/alvarotrigo/fullPage.js
