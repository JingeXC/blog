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
![something wrong](http://ojioqa2pk.bkt.clouddn.com/l.png)
