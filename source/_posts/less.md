---
title: less
date: 2016-12-29 22:19:28
tags: less base
---

开始工作到现在写了几个静态页面，尝试使用Less来编写样式。原本是想使用less来减少样式代码量，可能是水平有限，写出来的less比css还要多，但less还是使我提高了效率。
毕竟自动编译出来的代码，不用再去格式化，来迎合代码规范。记录一下使用的心得。

1 定义常量
--------
less可以使用<code>@常量名</code>来存储页面上元素信息。
这就可以在切图时，将页面的页面宽度和背景颜色，等等信息先存储起来，不用在码代码时，再去psd中取色，量长度等等。

```code
@pagewidth:980px;
@bgcolor:#999999
```
还有一种方式就是使用class类来存储
```css
.title{
    font-size:16px;
    color:#666;
    font-family:"Microsoft YaHei";
    font-weight:normal;
}
```
引用的时候
```code
.element{
    width:@pagewidth;
    background:@bgcolor;
    .title;
}
```

2 css的混入
------
在css中编写父元素和子元素需要写两个选择器写在两个{}中，其层级关系也没不明显。
在less中就可以混入css，就是在父元素的样式{}中，再使用选择器来选择子元素，如下代码

```code
.father{
    width:@pagewidth;
    height:200px;
    .child{
        width:100px;
        height:200px;
    }
}
```
输出成css代码就是
```css
.father{
    width:980px;
    height:200px;
}
.father .child{
    width:100px;
    height:200px;
}
```
在css中可以<code>.father>div</code>来获取子元素，在less中就可以使用&符号来链接混入代码的选择器
```code
.father{
    width:@pagewidth;
    &>div{
        height:200px;
    }
}
```
输出css
```css
.father{
    width:980px;
}
.father>div{
    height:200px;
}
```

3 运算
-----
在less中任何数字（包括颜色）是可以进行运算的，比如高度宽度等等。运算是支持+-x/等等的
```code
@color:#111;
.elem{
    width:100 + 30px;
    height:100 * 2 px;
    color:@color*2;
}
```
css输出
```css
.elem{
    width:130px;
    height:200px;
    color:#222;
}
```

4 函数
----------
在less中你可以定义一个函数，然后再调用它。
```code
.setborderradius(@px){
    border-radius:@px;
    -webkit-border-radius:@px;
    -moz-border-radius:@px;
    -o-border-radius:@px;
}
.elem{
    .setborderradius(5px);
}
```
css输出
```css
.elem{
    border-raidus:5px;
    -webkit-border-radius:5px;
    -moz-border-radius:5px;
    -o-border-radius:5px;
}
```