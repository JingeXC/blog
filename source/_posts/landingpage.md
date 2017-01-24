---
title: landingpage
date: 2017-01-04 20:59:24
tags: yeoman,gulp,bower,landingpage
---

最近一直都在写着陆页(landingpage)，写多了也就烦了，每次新建项目都需要复制文件或者去下载各种各样的包。这纯粹是体力活，没有技术含量，在浪费时间。之前有在webapp的项目中看到，可以用自动化的工具来新建项目，所以突发奇想，想用自动化工具来写着陆页。所幸，在yeoman上找到了相应的generator,安装完成，终于从石器时代进化到现代啦！

0
---
既然用到了自动化那就肯定得要有node环境啦，这是我本地的环境。
```code
C:\Users\jinge>node -v
v6.9.1
C:\Users\jinge>npm -v
3.10.8
```

1
---
第一步安装yeoman，bower和gulp
```code
npm install -g yo bower gulp
```
安装完检查
```code
C:\Users\jinge>gulp -v
[21:20:47] CLI version 3.9.1

C:\Users\jinge>bower -v
1.8.0

C:\Users\jinge>yo doctor

Yeoman Doctor
Running sanity checks on your system

√ Global configuration file is valid
√ NODE_PATH matches the npm root
√ Node.js version
√ No .bowerrc file in home directory
√ No .yo-rc.json file in home directory
√ npm version

Everything looks all right!
```

2
---
安装完成没有问题后，下载generator
```code
npm install -g generator-yeomify-landing
```
安装完成后
```code
yo yeomify-landing
```
创建项目
```code
C:\Users\jinge\work\landing>yo yeomify-landing

     _-----_     ╭──────────────────────────╮
    |       |    │   Yeoman generator for   │
    |--(o)--|    │  landing project powered │
   `---------´   │         by Gulp!         │
    ( _´U`_ )    ╰──────────────────────────╯
    /___A___\   /
     |  ~  |
   __'.___.'__
 ´   `  |° ´ Y `

? What is your app's name? landing
? What is your app's description? landing
? Would you install pug as template engine? No
? What css preprocessor would you use? stylus
? Would you install modernizr and normalize libraries? Yes
```
然后输入
```code
npm install
```
在bower.js中设置所需的jquery版本和其他包版本。
再用bower安装这些包
```code
bower install
```

3
---
<code>gulp watch</code> 在app文件夹下面启动一个watcher;
<code>gulp build</code> 将项目导出到dist文件夹下;
<code>gulp build --abspaths</code> 使用绝对路径把项目文件导出到dist文件夹中(css and js files);
<code>gulp build:watch</code> 在dist文件夹下面启动一个watcher;
<code>gulp build:clean</code> 删除dist和.tmp两个文件夹。（dist为输出文件夹，.tmp为watch产生的临时文件夹）

watch项目后，就可以在浏览器中访问项目，默认的端口是3000

最后附上generator的github[地址](https://github.com/helloilya/generator-yeomify-landing)
