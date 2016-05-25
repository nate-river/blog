# 利用jquery fullpage 插件制作宣传页面的流程

##  一.引入所需的文件
两种方式：
1. 引入本机的文件 （需要下载）
2. 引入cdn中的文件 （需要网络）  
```html
  <!--非必须的-->
  <link rel="stylesheet" href="path/jquery.fullpage.css">
  <link rel="stylesheet" href="index.css">
  <script src="jquery.js"></script>
  <script src="jquery.fullpage.js"></script>
```

## 二.根据插件的规定 写好基本的dom结构

```html
<div id="main">
  <div class="section">1</div>
  <div class="section">2</div>
  <div class="section">3</div>
  <div class="section">4</div>
</div>
<script>
$(function(){
  $('#main').fullpage();
})
</script>
```

## 三.开始制作页面

要制作的页面有各种各样的需求
所以需要给插件添加一些配置项

```javascript
$(function(){
    $('#main').fullpage({
      //滚动一屏的时间
      scrollingSpeed: 1440,
      //index.html#jiewei (分享给别人)
      anchors:['youxing','shiping','guanggao','jiewei'],
      fixedElements:'#fix,.heder nav',
      paddingTop:20,
      paddingBottom:30,
      // 当滚动到底部或顶部之后能不能继续滚动
      continuousVertical:true;
      // 是否出现导航小点
      navigation:true,
      navigationPosition:'left',

      // 每一个小点的提示文字
      navigationTooltips:['a','b','c','d'],
      // 到每一屏的时候是否出现提示文字
      showActiveTooltip:true;

      // 进入一屏的时候 会调用afterLoad
      afterLoad:function(name,index){
        name是当前这张的名字  index当前是第几张
      },
      // 离开一屏的时候 会调用onLeave
      onLeave:function(index,next,dir){
          if( index === 5 ){
            $("#section5 h1").addClass('animate-fei');
          }
          if( index === 1){
            // 离开失效
            return false;
          }
          // .animate-fei{
          //   animation:fei .5s ease .3s both;
          // }
          // @keyframes fei{
          //   xxxxxxxxx
          // }
          // index 从哪张离开的
          // next  去到了哪张
          // dir   up  down
      }
    });
});
```
