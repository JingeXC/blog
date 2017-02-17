---
title: gulp
date: 2017-02-16 22:42:47
tags: 前端自动化
---

1 写在前面的废话
----
开始接触到前端自动化，感觉这个东西好省力，好神奇，只要在命令行里敲入代码就能省去以前手动引入包，打包等等工作。所以花了很多精力去学习它。学习么，总要有点收获和总结么，这里就描述一个常用的gulp任务。
2 用gulp启动一个服务器容器
----
以前编写网页，总是需要安装各种容器像TOMCAT，XAMPP，但是这些容器是为服务器定制的，对于前端开发来讲有点太占资源了，还会有缓存等等问题。好在nodejs的兴起，gulp.grunt等这类工具可以替代以前的臃肿的容器。

在文件目录下使用npm生成package.json,并且安装本地版本的gulp
```bash```
npm init
npm install gulp --save-dev
```
安装需要的gulp工具
这边需要的是gulp-connect
```bash```
npm install gulp-connect --save-dev
```
新建一个gulpfile.js文件
引入gulp和gulp-connect模块,新建一个task，配置服务器基本信息
```javascript```
var gulp = require("gulp");
var connect = require("gulp-connect");
//server
gulp.task('server',function(){
	connect.server({
		root:'./',
		livereload:true,
		port:8320
	})
})
```
然后就可以在命令行下输入"gulp server"来启动服务
![服务启动效果](http://ojioqa2pk.bkt.clouddn.com/QQ%E5%9B%BE%E7%89%8720170217112743.png)
但。。。。。
![something wrong](http://ojioqa2pk.bkt.clouddn.com/l.png)

3 用gulp来自动刷新页面
---
如果gulp就仅仅能起一个服务器容器的作用，那就错啦。grunt可以写一个功能就是在每次保存文件后，页面自动刷新，所以猜想gulp一样也能够达到相同的效果。

在2的基础上，继续引入gulp-livereload模块(请事先安装模块)
```bast```
npm install gulp-livereload --save-dev
```
```javascript```
var livereload = require("gulp-livereload");
```
创建html/css/javascript的task,每个task调用livereload方法
```javascript```
//html
gulp.task('html', function () {
  gulp.src('./*.html')
    .pipe(livereload());
});
//css
gulp.task('css',function(){
	gulp.src('./css/*.css')
	.pipe(livereload());
})
//javascript
gulp.task('js',function(){
	gulp.src('./js/*.js')
	.pipe(livereload());
})
```
再使用gulp的watch来监视文件的变动，这里再写一个监视的task
```javascript```
//watch
gulp.task('watch',function(){
	gulp.watch(['./*.html'],['html']);
	gulp.watch(['./css/*.css'],['css']);
	gulp.watch(['./js/*.js'],['js']);
	livereload.listen();
})
```
然后将监听task添加到start task中，使在start task启动时自动调用监听task
```javascript```
gulp.task('start',['server','watch']);
```
现在就可以实时刷新页面啦~~~
![something wrong again](http://ojioqa2pk.bkt.clouddn.com/l%20%281%29.png)

4 实时刷新与前端预处理结合
----
从前端预处理出现到现在已经有很长一段时间里，所以在用的看官老爷应该不少吧。加入预处理是必要的，但是前端预处理的语言有好几种，怎么支持几个不同的前端预处理变成了问题。

首先引入对应的gulp插件以支持预处理的自动编译,这里使用stylus,less,sass做栗子
```bash```
npm install gulp-stylus gulp-less gulp-sass --save-dev
```
在js中引入
```javascript```
var less = require("gulp-less"),
		sass = require("gulp-sass"),
		styl = require("gulp-stylus");
```
创建对应的task
```javascript```
gulp.task('styl',function(){
	gulp.src('css/*.styl')
	.pipe(stylus())
	.pipe(gulp.dest('css'));
})
gulp.task('less',function(){
	gulp.src('css/*.less')
	.pipe(less())
	.pipe(gulp.dest('css'));
})
gulp.task('sass',function(){
	gulp.src('css/*.sass')
	.pipe(sass())
	.pipe(gulp.dest('css'));
})
```
将这些task加入到watch中让gulp监视文件的改动
```javascript```
//watch
gulp.task('watch',function(){
	gulp.watch(['./*.html'],['html']);
	gulp.watch(['./css/*.sass'],['sass']);
	gulp.watch(['./css/*.less'],['less']);
	gulp.watch(['./css/*.styl'],['styl']);
	gulp.watch(['./css/*.css'],['css']);
	gulp.watch(['./js/*.js'],['js']);
	livereload.listen();
})
```
OKAY这样就和css预处理结合起来了，但。。。
没有人会同时使用多种预处理来写同一个项目吧~！
所以就需要判断一下使用的是哪一种的预处理

在package.js中加入自定义的对象
```json```
{
	"name":"gulp",
	....
	"css":"styl"
}
```
使用nodejs操作文件的模块来读取package.js文件，获取到css字符串。根据这个字符串来选择对应的预处理。
```javascript```
var fs = require("fs");
var json = JSON.parse(fs.readFileSync('./package.json'));
var cssstyle = json.css;
```
在watch的task中修改成
```javascript```
gulp.task('watch',function(){
	gulp.watch(['./*.html'],['html']);
	gulp.watch(['./css/*.'+cssstyle],[cssstyle]);
	gulp.watch(['./css/*.css'],['css']);
	gulp.watch(['./js/*.js'],['js']);
	livereload.listen();
})
```
这样就可以啦，但是还有不完美的地方。。。。

-1 写在后面的东东
----
本页用到的模块如下：
	1 gulp-connect 服务器模块
	2 gulp-livereload 自动加载模块
	3 gulp-stylus stylus模块
	4 gulp-less less模块
	5 gulp-sass sass模块
	6 fs nodejs文件操作模块


小工具

每次使用photoshop来切图，导出的图片的文件名都是凌乱的。所以查看了gulp的工具库发现了gulp-rename这个模块。
```javascript```
var rename = require("gulp-rename");
gulp.task('rename',function(){
	var i=1;
	gulp.src('./RAW/*.jpg')
	.pipe(rename(function(path){
		path.basename = i++;//basename就是文件名称但不包括扩展名
	}))
	.pipe(gulp.dest('./OUT'));
})
```
