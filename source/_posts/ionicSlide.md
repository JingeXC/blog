---
title: ionicSlide
date: 2017-01-03 21:44:51
tags: ionic,angular
---
ionic+angular开发app，在ios下发现一个交换上的问题。之前我从来都不知道ios有右滑动返回的效果（当然这我不用iphone有关），这就产生了一个问题，ionic应用在iphone下，右滑会有两次页面进入动画。这严重影响了用户体验，产品也不会放过啦。开始，对这个问题毫无头绪，毕竟这是在手机上出现的问题，没办法调试，只好去搜索答案，然后一个一个地尝试。但尝试了很多方法，都没有成功。其中有一个博客给了我启发，在ios下，ionic自带了一个页面切换的动画效果，而ios也有一个动画效果，这就是问题所在了。我只需要将ionic里的动画效果禁用即可。不过，禁用的方法有好几种，只有一种是可以的（对于我的app来说）。
在app.js中加入下面这句话。
```javascript
$ionicConfigProvider.views.transition('none');
```
另外在附上其他禁用右滑返回的方法
1 在app.js中加入
```javascript
 $ionicConfigProvider.views.swipeBackEnabled(false);
```
2 在<code><ionic-view></ionic-view></code>中加入<code>can-swipe-back="false"
</code>
3 使用指令
```html
<div on-swipe-left="swipeleftAction()">
</div>
```
4 使用监控路由的方式
[链接](http://www.songliuchen.com/Article/58.aspx)
5 通过取消ionic自带动画效果
```html
<ion-view view-title="个人中心" animation="no-animation">
```
```javascript
$ionicConfigProvider.views.transition('none');
```
