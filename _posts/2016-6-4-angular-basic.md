---
  layout: post
  title:  angularjs基础
  tags:
  categories:
---

## 1.安装引用

```sh
bower install angular
```

```html
<script src="pathto/angular.js"></script>
```

## 2.简单使用

```html
<!DOCTYPE html>
<!-- 这里使用 ng-app 指令  -->
<html  ng-app="reminder">
  <head>
    <meta charset="utf-8">
    <title></title>
    <script src="angualr.js" charset="utf-8"></script>
  </head>
  <!-- 这里使用 ng-controller -->
  <body ng-controller="mainControler">
    <!-- ng-model指令 会在作用域中的 $scope 上 放置一个 info 的属性  值为input的值 -->
    <input type="text" name="name" value="" ng-model="info">
    <!-- 双花括号中可以写 angular 表达式  下面写法为取出 $scope上的 info 属性的值-->
    <p>{{info}}</p>
  </body>
  <!-- controller的作用域范围在这里结束-->
</html>
```

## 3.以模块化的方式来开发自己的应用 和 依赖注入

```html
<!DOCTYPE html>
<html  ng-app="reminder">
  <head>
    <meta charset="utf-8">
    <title></title>
    <script src="angular.js"></script>
    <script src="index.js"></script>
  </head>
  <body ng-controller="mainControler">
    <table>
      <thead>
          <th>
              <td>姓名</td>
              <td>学号</td>
              <td>性别</td>
          </th>
      </thead>
      <tbody>
          <!-- ng-repeat 指令能从作用的$scopes身上取到数据，帮我们完成渲染-->
          <!-- 他会在每次数据变动的时候帮我们重新渲染 -->
          <tr ng-repeat="v in students">
              <td>{{v.name}} </td>
              <td>{{v.id}} </td>
              <td>{{v.sex}} </td>
          </tr>
          <tr>
              <td ng-click="addStudent()">+</td>
          </tr>
      </tbody>
    </table>
  </body>
</html>
```

```javascript
  // 把我们的应用作用单独的一个模块 和系统中的其他模块解耦
  var reminder = angular.module('reminder',[]);

  // 在我们的模块上创建一个控制器  来控制本模块中某个局部的可见数据
  reminder.controller('mainControler',['$scope',function($scope){
    $socpe.students = [
      {id:1001,name:'A',sex:'nan'},
      {id:1002,name:'B',sex:'nv'},
      {id:1003,name:'C',sex:'nan'},
    ]
    $scope.addStudent = function(){
      this.stuents.push({id:Math.random(),name:'new man', sex:'nan'});
    }
  }]);
```

##  4.常用的装饰型指令

装饰性指令用来在 view 和 controler 之间协调运作

[angularjs 概念介绍](http://docs.ngnice.com/guide)

[angularjs API](http://docs.ngnice.com/api)


*  ng-app
*  ng-controller

*  ng-repeat  // track by $index  可以避免同id属性报错
*  ng-model

*  ng-class
*  ng-show
*  ng-hide
*  ng-if
*  ng-switch

*  ng-[event]
*  ng-href
*  ng-init

##  5.组件型指令

`组件型指令` 用来拆分复杂的html页面

实现`组件化开发` 和一定程度的 `复用`

login.html

```html
<div id="login">
  <div class="usernam"></div>
  <div class="password"></div>
  <button class="submit">Login</button>
</div>
```

index.html

```html
<!DOCTYPE html>
<html ng-app="reminder">
  <head>
    <meta charset="utf-8">
    <title></title>
    <script src="angular.js" charset="utf-8"></script>
    <script src="index.js" charset="utf-8"></script>
  </head>
  <body ng-controller = "mainControler">
    <login></login>
  </body>
</html>
```
index.js

```javascript
var reminder = angular.module('reminder',[]);
// 在整个模块的各个控制器作用域内  login指令都可用
reminder.directive('login',[function(){
  // Runs during compile
  return {
    restrict: 'AE', // E = Element, A = Attribute, C = Class, M = Comment
    templateUrl: 'login.html',
    // name: '',
    // priority: 1,
    // terminal: true,
    // scope: {}, // {} = isolate, true = child, false/undefined = no change
    // controller: function($scope, $element, $attrs, $transclude) {},
    // require: 'ngModel', // Array = multiple requires, ? = optional, ^ = check parent elements
    // template: '<h3>Hello Angular</h3>',
    // replace: true,
    // transclude: true,
    // compile: function(tElement, tAttrs, function transclude(function(scope, cloneLinkingFn){ return function linking(scope, elm, attrs){}})),
    // link: function($scope, iElm, iAttrs, controller) {
    // }
  };
}]);
```

## 6. ng-view 指令

angular 多页面切换的方式

```html
<script src="angular-route.js"></script>
<div class="">
   <title-bar></title-bar>  
   <div ng-view></div>
   <tab-bar></tab-bar>
</div>
```

```javascript
var myapp = angular.module('myapp',[]);

myapp.controller('indexctrl',['$scope',function($scope){
  //index.html 的控制器
}]);
myapp.controller('infoctrl',['$scope','$routeParams',function($scope,$routeParams){
  //info.html 的控制器
  console.log($routeParams.id);
}]);

myapp.config(['$routeProvider',function($routeProvider) {
  $routeProvider.when('/',{
    controller:'indexctrl',
    templateUrl:'index.html'
  }).when('/view/:id',{
    controller:'infoctrl',
    templateUrl:'info.html',
    publicAccess:true
  }).otherwise({
    redirectTo:'/'
  });
}])
```


## 7. 服务

为什么需要服务?

>  多页面切换的过程中  有些数据被锁死在对应的controller内。
>  需要把这些公共的数据以服务的形式组织起来，随需随取

服务在整个页面的生命周期中可用

```javascript

var myapp = angular.module('myapp',[]);

// 可以在中括号中定义其他需要的服务
myapp.factory('$student',[ function(){
  return {
      students:[
        {...},
        {...},
        {...},
      ]
      getStudentsById:function(){
        ...
      },
      removeStudentsById:function(){

      },
      updateStudentsById:function(){

      },
      addStudent:function(id){

      }
  }
}]);

myapp.service('$copyRight',  function(){
  this.name = 'unique';
  this.date  = '2015';
  this.generatorCode = function () {
    return '<span>'+this.name+'</span><img src="erweima">';
  }
});

myapp.constant('$isLogin', {islogin:false});

myapp.value('$PI', Math.PI);

```

## 8.过滤器

有的时候一些展现在页面上的数据需要格式化

有的时候一些展现在页面上列表需要排序，过滤。

我们使用过滤器

内置过滤器参考api文档

自定义过滤器的方式

```javascript
myapp.filter('young',function(){
  return function(e,type){
    var r =  [];
    var _sex = type?'nan':'nv';
    for (var i = 0; i < e.length; i++) {
      if(e[i].age>=12 && e[i].age<=17 && e[i].sex == _sex){
        r.push(e[i]);
      }
    };
    return r;
  }
})
```
```html
  <li ng-repeat="stu in students| young:1" ></li>
```

## 9.使用动画

```html
<script src="angular-animate.js"></script>
```

```javascript
var myapp = angular.module('myapp',['ngRoute','ngAnimate']);
```

查阅文档 观察class的变化 写css样式来操控动画


## 10.使用$http服务


## 11.使用jquery

```html
<button type="button" name="button" ng-click="submit($event)"></button>
```

```javascript
$scope.toggletododetail = function($event){
  console.log($event);
  var el = angular.elements() // 得到一个JqLite对象
  console.dir(el);  //查看其中的方法，比jquery少很多
}
```

如果想使用jquery

先引入jquery 后引入angular.js

随后不用任何配置就可以在代码中使用  $

## 12.自定义指令中的配置项

> 指令之name属性
> 指令之priority属性
> 指令之terminal属性

> 指令之template属性
> 指令之templateUrl属性

> 指令之scope属性
> 指令之controller属性
> 指令之require属性

> 指令之restrict 属性
> 指令之replace属性
> 指令之transclude属性

> 指令之compile属性
> 指令之link属性

## 13.利用templateCache来缓存页面

```javascript
//会在app启动的时候运行一次
myapp.run(function($templateCache){
  $templateCache.put('cache','<h3>内容来源于缓存!</h3>');
})
myapp.directive('tsTplcache', [function(){
  // Runs during compile
  return {
    restrict:'EAC',
    templateUrl:'cache',
    replace:true
  };
}]);
```

## 14.其他注意事项

*  ng-binding 解决页面元素闪烁问题
*  一次绑定问题
* $eval $apply  $watch 解决一些监测问题
* 其他问题
