---
  layout: post
  title: 搭建前端自动化开发环境
  tags:
  categories:
---


>  随着`node.js`的迅猛发展,前端开发已经脱离了刀耕火种,进入蒸汽机时代。

>  这里介绍一些基于`node.js`的前端自动化开发工具:

## node.js  &&  npm

> Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient. Node.js' package ecosystem, npm, is the largest ecosystem of open source libraries in the world.

最简单的理解：

`node.js`又提供了一个javascript的运行环境,以前,javascript代码可以在浏览器中运行,现在,它可以在node.js所搭建的运行环境中运行了.

浏览器并不是一个理想的代码运行环境,浏览器在给javascript扩展API的时候,基于安全的考虑,很多功能都不能做.比如操作文件,随意的处理网络请求.所以,在以前,javascript相对于python,ruby 是一门`不完善的语言`.

在node.js这个运行环境中,并没有这样那样的限制,在这里,javascript成功变成了python,ruby,变成了一门`真正的语言`.

windows下 node.js 的安装很简单,访问[`node.js官网`](node.js-url),下载安装包,默认安装就好.

打开控制台测试是否安装成功
```sh
node -v
```

`npm` 是node.js的包管理工具, node.js以模块的方式组织代码,允许任何人提交一个模块,来扩展javascript, npm用来管理这些模块

```sh
npm -v
npm install -g bower
```

如果有的包安装不上 复制以下代码替换 `x` 为安装不上的包 (会带来一定的问题,建议翻墙)

```sh
 npm install x --registry=http://registry.npm.taobao.org
```


## bower

把git命令添加到环境变量的方法:
在c盘中搜索 git.exe  找到它所处的位置,添加到环境变量

## grunt && gulp

## yeomon


node.js-url : 'https://nodejs.org'
