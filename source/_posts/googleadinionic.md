---
title: googleadinionic
date: 2017-01-03 22:22:15
tags: ionic,angular,googleAD
---
广告是开发app的一大收入来源，所以讲广告加入app变得很重要。本文只描述在angular+ionic的app中如何加入广告。

1 在html中加入谷歌广告代码，这是最简单的方式。但是这有局限性，不能根据内容的多少来加载广告。

2 使用指令的方式，在需要的位置添加，还可以repeat多条广告。
```javascript
.directive('googlead', function ($parse, $rootScope, $compile) {
        return {
            restrict: "AE",
            scope: false,
            link: function (scope, elem, attr) {
                var gpt=sessionStorage.getItem('gpt');
                if(gpt==undefined){
                    gpt=0;
                }
                var index=parseInt(gpt) + 1;
                sessionStorage.setItem("gpt",index);
                elem[0].setAttribute('id', 'div-gpt-ad-xxxxxxxxxxxx-' + index);
                var dom = '<script>googletag.cmd.push(function() {googletag.defineSlot("/xxxxxxxx/MS_StripAd_A", [320, 50], "div-gpt-ad-xxxxxxxxxxxx-' + index + '").addService(googletag.pubads()).setCollapseEmptyDiv(true, true);googletag.pubads().enableSingleRequest();googletag.enableServices();});googletag.cmd.push(function() {googletag.display("div-gpt-ad-xxxxxxxxxxxx-' + index + '"); });</script>';
                $(elem).append($compile(dom)(scope));
            }
        }
    })
```
先生成广告序列，然后拼装js代码，最后将代码注入到app中运行。
