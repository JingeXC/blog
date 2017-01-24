---
title: AngularTips
date: 2016-12-26 22:18:23
tags: angular1
---
最近用angular1做了个项目，项目马上快结束了，但遇到个大问题--网站的SEO优化。按照SEO的同事的要求，需要在地址栏中输入参数就可以查询。不过我们使用的是ui-route,是使用下面这种方式来进行页面间传值:
```javascript
.state('tab.result',{
    url: '/result/:country/:city/:region/:pricerange/:room/:forsale/:type/:indoor/:outdoor',
    views:{
        'tab-dash':{
            templateUrl:'templates/result.html',
            controller:'resultCtrl'
        }
    }
})
```
这种传值方法有个很大的问题，就是参数为空时，url地址就会产生很多斜杠
```txt
result/country////////
```

后来请教大神，才得知上面这种方式是参数逼传，还有一种是参数可以选传
```javascript
.state('tab.refresh',{
    url:'/refresh/:country?/:city?/:region?/:pricerange?/:room?/:forsale?/:type?/:indoor?/:outdoor?',
    views:{
        'tab-dash':{
            templateUrl:'templates/refresh.html',
            controller:'refreshCtrl'
        }
    }
})
```
修改后的url地址就为
```txt
refresh?country=US&city=1231
```
