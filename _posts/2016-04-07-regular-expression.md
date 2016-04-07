---
  layout: post
  title: 正则表达式
  tags:
  categories: jekyll update
---

一句简单的话来概括：

正则表达式本质上让我们拥有更强大的文本检索能力.

通过一些扩展函数,我们可以对检索到的结果做一些其他操作.

比如`构建程序数据`，`替换`，`拆分文本`等等.


## 测试工具

现在，我们来体验一下什么是`更强大的文本检索能力`

编辑器的搜索功能大家都很熟悉

为了调试方便 chrome source 选项卡现在已经越来越像一个编辑器了

在其中自然也有搜索替换功能

同时也支持使用正则表达式来搜索

界面如下

<!-- ![chrome调试工具 source选项卡界面](/images/chrome-source.png) -->

## 原子

First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column



### 可见原子

### 不可见原子

## 元字符之原子的筛选方式

## 元字符之原子的集合

## 量词

## 边界控制

## 模式单元


## 界定符

表示一个正则表达式的开始和结束位置,在javascript中

我们使用如下两种方式来定义一个正则表达式对象

```javascript
//1.字面量方式
var reg = /someregularexpression/;
//2.构造函数方式
var reg = new RegExp('/someregularexpression/',g);

var fn = function (x, y) {
  return x * y;
}
var num = fn(3, 4);
console.log(num);
```

其中位于 `someregularexpression` 两侧的 `/` 字符为界定符
