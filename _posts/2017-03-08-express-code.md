---
layout: post
title:  "express web开发常用代码"
tags:
categories:
---

## 处理普通post请求


```javascript
const bodyParser = require('body-parser');
// parse application/x-www-form-urlencoded
app.use(bodyParser.urlencoded({extended: false}));
// parse application/json
app.use(bodyParser.json());
app.post('/',(req,res)=>{
  console.log(req.body);
})
```

## 处理session

```javascript
const session = require('express-session');
app.use(session({
  secret: 'keyboard cat',
  resave: false,
  saveUninitialized: true
}));
app.get('/logincheck',(req,res)=>{
  req.session.login = true;
})
// 中间件
app.use('/admin',(req,res,next)=>{
  if(req.seesion.login){
    next();
  }else{
    res.redirct('/login');
  }
})
```

## 上传文件

```javascript
const fs = require('fs');
const async = require('async');
const multer = require('multer');
const upload = multer({dest: 'uploads/'});
app.post('/upload', upload.single('wangEditorH5File'), function (req, res) {
  async.series([
    function (callback) {
      fs.createReadStream(req.file.path).pipe(fs.createWriteStream('public/imgs/' + req.file.originalname));
      callback(null);
    },
    function (callback) {
      fs.unlink(path.resolve(req.file.path));
      callback(null);
    }
  ], function () {
    res.end('/imgs/' + req.file.originalname);
  });

});
```

## react富文本编辑器组件

```html
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <link rel="stylesheet" href="/css/wangEditor.min.css">
</head>
<body>
<div id="page"></div>
<script src="js/jquery-2.2.1.js"></script>
<script src="js/wangEditor.js"></script>
<script src="/js/admin.js"></script>
</body>
</html>
```

```javascript
const React = require('react');
const ReactDOM = require('react-dom');
class Editor extends React.Component {
  constructor(props) {
    super(props);
    this.getContents = this.getContents.bind(this);
  }

  componentDidMount() {
    this.editor = new window.wangEditor(this.el);
    this.editor.config.uploadImgUrl = '/upload';
    this.editor.create();
    // 初始化内容
    this.editor.$txt.html('<div>this is a a</div>');
  }

  getContents() {
    console.log(this.editor.$txt.html());
  }

  render() {
    return (
      <div>
        <div contentEditable="true" style={{height:300}} ref={(el)=>{this.el = el}}></div>
        <div onClick={this.getContents}>获取内容</div>
      </div>
    );
  }
}
ReactDOM.render(<Editor/>, document.querySelector('#page'));
```


## 创建md5

```javascript
const crypto = require('crypto');
const hash = crypto.createHash('md5');
hash.update('123456');
console.log(hash.digest('hex'));
```

## mysql封装

```javascript
const mysql = require('mysql');
const pool = mysql.createPool({
  connectionLimit: 1000,
  host: 'localhost',
  user: 'root',
  password: 'root',
  database: 'music'
});
function query(sql, arr, fn) {
  pool.getConnection((err, con)=> {
    con.query(sql, arr, (err, res)=> {
      con.release();
      fn(err, res);
    })
  })
}
module.exports = {
  query: query
};
```

## 防止意外退出

```javascript
process.on('uncaughtException', (ex)=> {
  console.log('error');
});
```

## react项目中使用fetch

```javascript
// npm install whatwg-fetch --save
// 在html页面中引入whatwg-fetch.js

// fetch上传文件
var input = document.querySelector('input[type="file"]')

var data = new FormData()
data.append('file', input.files[0])
data.append('user', 'hubot')

fetch('/avatars', {
  method: 'POST',
  body: data
})
// fetch提交表单
var form = document.querySelector('form')

fetch('/users', {
  method: 'POST',
  body: new FormData(form)
})
```
