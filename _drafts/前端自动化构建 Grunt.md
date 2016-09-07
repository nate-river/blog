前端自动化构建 Grunt
===================

> 简单说，Grunt是一个自动任务运行器，会按照预先设定的顺序自动运行一系列的任务。这可以简化工作流程，减轻重复性工作带来的负担。


CMD常用命令：
-------------------------------

```sh
d:               //进入d盘
dir              //查看文件夹内容
md  aa           //创建文件夹

cd ../  cd ..    //返回上一级   
cd ../../        //返回上上级
cls              //清空命令行
start            //打开文件

ren aa bb        //重命名文件夹  aa源文件名  bb 新文件名
cd 文件夹名称      //进入指定文件夹
find 文件名       //查找某文件
rd  aa           //删除文件夹
rd/s/q 盘符:\某个文件夹   //这样整个文件夹所有的文件和文件夹都删除了

copy 路径文件名1　路径文件名2 /y  //复制文件1到指定的目录为文件2，用参数/y就同时取消确认你要改写一份现存目录文件
```

准备运行环境
---------------------------------
Grunt需要Nodejs环境，这里假设你已经安装好了Nodejs和NPM，下面的代码需要在命令行中运行。
```sh
安装：
  1. npm install -g grunt-cli // 使用NPM安装 grunt-cli
  //上述命令执行完后，grunt 命令就被加入到你的系统路径中了，以后就可以在任何目录下执行此命令了。
运行：
  1. cd ~/workspace/project/WebApp // 进入已配置Grunt模块的项目目录
  2. grunt build // 运行Grunt, 执行相应任务
```

Grunt文件介绍
---------------

创建Grunt项目中必须文件
> 一般需要在你的项目中添加两份文件：package.json 和 Gruntfile。

`package.json`应当放置于项目的根目录中，与Gruntfile.js在同一目录中，并且应该与项目的源代码一起被提交。在上述目录(package.json所在目录)中运行`npm install`将依据package.json文件中所列出的每个依赖来自动安装适当版本的依赖。
####package.json
package.json 主要用于Node.js的包管理，比如Grunt插件安装；
1. 命令 npm init 来创建默认的 **package.json**
2. 命令 npm install 是用来下载安装在 **package.json** 中指定的依赖。

你可以在此文件中列出项目依赖的grunt和Grunt插件，放置于devDependencies配置段内。

```javascript
{
  "name": "demo",         //项目名称
  "version": "1.0.0",     //版本号
  "description": "test",  //描述
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "hnz",        //作者
  "license": "ISC",       //开源许可
  "devDependencies": {    //插件列表
    "grunt-contrib-uglify": "^0.11.0"
  }
}
```

####Gruntfile.js
Gruntfile.js 是Grunt配置文件，配置任务或者自定义任务
> 这两个文件必须放在项目的根目录，并且和项目文件一起提交

-----
###Gruntfile.js主要三块代码：
1. **任务配置代码**
2. **插件加载代码**
3. **任务注册代码**

创建Gruntfile.js文件：

```javascript
module.exports = function(grunt) {     
	// 配置任务参数
	grunt.initConfig({        
		pkg: grunt.file.readJSON('package.json'),
		cssmin: {
			combine: {
				files: {
					'css/release/compress.css': ['css/*.css']
					// 指定合并的CSS文件
					['css/base.css', 'css/global.css']
				}
			},           
			minify: {
				options: {
					keepSpecialComments: 0, /* 删除所有注释 */
					banner: '/* minified css file */'                
				},
				files: {
				    'css/release/master.min.css':['css/master.css']                
				}
			}
		}
	});

	// 插件加载（加载 "cssmin" 模块）
	grunt.loadNpmTasks('grunt-contrib-cssmin');

	// 自定义任务：通过定义 default 任务，可以让Grunt默认执行一个或多个任务。    
	grunt.registerTask('default', ['cssmin']); };
```

* 任务配置代码
```javascript
 grunt.initConfig({
    pkg: grunt.file.readJSON('package.json'),
    uglify: {
      options: {
        banner: '/*! <%= pkg.name %> <%= grunt.template.today("yyyy-mm-dd") %> */\n'
      },
      build: {
        src: 'src/<%= pkg.name %>.js',
        dest: 'build/<%= pkg.name %>.min.js'
      }
    }
  });
```
* 插件加载代码
这个就超级简单了，由于上面任务需要用到 grunt-contrib-uglify，当 grunt-contrib-uglify 安装到我们的项目之后，写下下面代码即可加载：
```javascript
grunt.loadNpmTasks('grunt-contrib-uglify');
```
* 任务注册代码

插件也加载了，任务也布置了，下面我们得注册一下任务，使用一下命令来注册一个任务：
```javascript
grunt.registerTask('default', ['uglify']);
```

。上面代码意思是，你在 default 上面注册了一个 Uglify 任务，default 就是别名，它是默认的 task，当你在项目目录执行 grunt 的时候，它会执行注册到 default 上面的任务。
#####执行配置中所有的任务：
也就是说，当我们执行 grunt 命令的时候，uglify 的所有代码将会执行。我们也可以注册别的 task，例如：
#####执行某个特定的任务：
```javascript
grunt.registerTask('compress', ['uglify:build']);
```

如果想要执行这个 task，我们就不能只输入 grunt 命令了，我们需要输入 **grunt compress** 命令来执行这条 task，而这条 task 的任务是 uglify 下面的 build 任务，也就是说，我们只会执行 uglify 里面 build 定义的任务，而不会执行 uglify 里面定义的其他任务。

这里需要注意的是，task 的命名不能与后面的任务配置同名，也就是说这里的 compress 不能命名成 uglify，这样会报错或者产生意外情况

###Grunt常用插件列表
所有插件的安装方法：进入项目所在文件夹，启动命令行工具，输入

```javascript
npm install grunt-contrib-<module> --save-dev
```
其中 --save-dev ，表示将它作为你的项目依赖添加到package.json文件中devDependencies内。如果你要安装指定版本的Grunt或者Grunt插件，只需要运行npm install grunt@VERSION --save-dev命令，其中VERSION就是你所需要的版本(指定版本号即可)。
1.  less实时编译插件

-----------------
2. css压缩 grunt-contrib-mincss
非常常用的插件，用于css压缩。

```javascript
module.exports=function(grunt){
    grunt.initConfig({
        pkg:grunt.file.readJSON('package.json'),
        //css处理
        cssmin:{
            minify: {//压缩css
                files: [{
                    expand: true,
                    cwd: 'css',//源地址
                    src: ['*.css', '!*.min.css'],//筛选css文件
                    dest: 'css/min',//目标地址
                    ext: '.min.css'//压缩后文件
                }]
            },
            combine:{//合并多个css文件
                files: {
                    //合并后指定路径文件    要合并的多个文件
                    'css/aa.css': ['css/index.css', 'css/output.css']
                }
            }
        }
    });
    grunt.loadNpmTasks('grunt-contrib-cssmin');//加载插件 cssmin
    grunt.registerTask('default', ['cssmin']);//注册任务cssmin
};
```

-----------------
3.  合并文件  grunt-contrib-concat
非常常用的grunt插件，用于合并任意文件，用法也非常简单
安装：
```javascript
npm install grunt-contrib-concat --save-dev
```
比如说你写了一个类库，有三大模块，如：
| a.js | b.js | c.js |
| :--: | :--: | :--: |

当你的项目准备发布的时候，你可能需要将这三个模块合并成一个大的模块all.js，这样做可以减少HTTP请求，增快页面的响应速度。

示例：多个文件合并成一个文件

```javascript
grunt.initConfig({
  concat: {
    options: {
      separator: ';',
      stripBanners: true,
      banner: '/*! hello - v1.0.0 - 2015-11-11 */'
    },
    dist: {
      src: ['a.js', 'b.js', 'c.js'],
      dest: 'all.js',
    }
  }
 });
```
参数介绍
 options中是一些选项，键值对方式，可以做一些简单的配置
* separator 文件连接分隔符，表示连接的文件用指定的separator分割。
* banner 出现在合并后的文件开头出现，一般做说明和注释用。
* footer 出现在合并后的文件底部出现，一般做说明和注释用。
* stripBanners 如果为true，去除代码中的块注释，默认为false
* process  如果为true，则在合并前先执行。
* src是一个数组，里面的元素是你要合并的文件，按0-n的顺序进行合并。（注意你要合并的顺序）
* dest是你生成合并文件的目录和文件名。

**多个合并任务**

```javascript
grunt.initConfig({
  concat: {
    one: {
      src: ['a.js'],
      dest: 'all.js',
    },
    two: {
      src: ['b.js', 'c.js'],
      dest: 'all-sec.js',
    },
  },});
```
这里分别定义了两个合并任务，one和two，分别生成两个合并文件 grunt concat:one 执行第一个任务， grunt concat:two 执行第二个，如果只是  grunt concat，则两个任务都会执行。

下面是另一种写法，效果同上

```javascript
grunt.initConfig({
  concat: {
    basic_and_extras: {
      files: {
        'all.js': ['a.js'],
        'all-sec': ['b.js', 'c.js']
      }
    }
  }
});
```
动态的文件名

```javascript
grunt.initConfig({
  pkg: grunt.file.readJSON('package.json'),
  concat: {
    dist: {
      src: ['a.js'],
      dest: 'dist/<%= pkg.name %>-<%= pkg.version %>.js',
    }
  }
 });
```

4. javascript代码检查  grunt-contrib-jshint
jshint用于javascript代码检查（并会给出建议），发布js代码前执行jshint任务，可以避免出现一些低级语法问题。
jshint拥有非常丰富的配置，可以自由控制检验的级别。

4.  js压缩 grunt-contrib-uglify
非常常用的插件，压缩js文件

```sh
npm install grunt-contrib-uglify --save-dev
```
任务配置：

```javascript
module.exports=function(grunt){
    grunt.initConfig({
        pkg:grunt.file.readJSON('package.json'),
        uglify:{
            options: {
                banner: '/*Author:<%= pkg.author %>  Date:<%= grunt.template.today("yyyy-mm-dd") %> */\n'
            },
            build: {
                // 动态文件映射，
                // 当任务运行时会自动在 "src/bin/" 目录下查找 "**/*.js" 并构建文件映射，
                // 添加或删除文件时不需要更新 Gruntfile。
                files: [
                    {
                        expand: true,     // 启用动态扩展
                        cwd: 'js/',      // 源文件匹配都相对此目录
                        src: ['**/*.js'], // 匹配模式
                        dest: 'js/',   // 目标路径前缀
                        ext: '.min.js',   // 目标文件路径中文件的扩展名
                        extDot: 'first'   // 扩展名始于文件名的第一个点号
                    },
                ],
            }
        }
    });
    grunt.loadNpmTasks('grunt-contrib-uglify');//加载插件 uglify
    grunt.registerTask('default', ['uglify']);//注册任务uglify
};
```
