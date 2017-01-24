---
title: jsclosure
date: 2016-12-31 11:58:22
tags: javascript
---
闭包
-----
```javascript
function outfun(){
    var num=1;
    return function infun(){
        console.log(num++);
    }
}
var getnum=outfun();
getnum();
console.log(num);
```
首先先声明一个函数outfun，在在其中定义一个变量num和一个函数infun,再将infun返回到函数外面（暴露到外部）。新声明个函数用来保存outfun的结果，也就是得到infun。此时的getnum方法就为
```javascript
getnum=function(){
    console.log(num++);
}
```
注意这里的num是outfun中的私有变量，在outfun函数外是访问不到的。可以在outfun函数打印一下num，结果是undefined;

这时候就形成了闭包，只有getnum才能访问到num这个变量。
也就是闭包的好处，可以保护变量不被后面的代码影响，其缺点也显而易见了，js垃圾回收机制就无法回收内存了。