---
title: atom
date: 2017-01-04 22:00:29
tags: atom plug
---

从开始接触编程，就接触到了各种IDE，上学时写java用eclipse到实习用的myeclipse。这些都是后台使用的IDE，虽然也可以用来编写前端页面，但对于前端不友好。专注于前端的IDE，我刚开始就只知道Dreamwear,以为它自带提示功能太强大了。一段时间后看到了webstrom，赶脚DW弱爆了，界面丑就算啦，装插件还各种麻烦，马上投入Webstorm的怀抱。好景不长，使用Webstorm一段时间后，我发现WS及其耗内存，打开几个项目8G的内存就已经爆满啦再加上photoshop更是雪上加霜。sublimetext和atom出现在我眼前，因为sublimetext是收费的，而atom是免费哒，果断选atom。最近看到atom有一个非常绚丽的效果，但是安装过程中出现了各种问题，记录一下。

1 github下载包安装
-----
首先当然是安装atom啦，安装完成后，在atom的用户目录下，找到<code>.atom</code>文件夹，注意不是atom的安装目录。
```code
C:\Users\jinge\.atom\packages
```
用git克隆下插件的包
包的地址
```code
https://github.com/JoelBesada/activate-power-mode.git
```
克隆完成后，进入到插件的目录下
```code
cd C:\Users\jinge\.atom\packages\activate-power-mode
```
然后输入
```code
apm install
```
如果提示没有apm这个命令，就需要在系统环境变量中添加。
如果看到<code>Install modules done</code>,就说明安装成功啦
运行atom,如果没有效果，可以使用快捷键<code>Ctrl+Alt+o</code>

2 在atom中安装插件
----
打开atom，
file=>setting=>install
在选项卡中输入activate-power-mode
在插件列表中选择当前插件，然后安装即可

tips
---
查看当前系统环境，因为这个插件是使用C++写的，因此需要一些特殊的环境。可以使用<code>apm -version</code>来查看
```bash
C:\Users\jinge\.atom\packages>apm -version
apm  1.12.9
npm  3.10.5
node 4.4.5
python
git 2.11.0.windows.1
visual studio
```
