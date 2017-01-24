---
title: CarouselFigure
date: 2016-12-26 21:34:58
tags: 无限轮播图Demo
---
轮播图是前端页面中最常用的组件，尤其在广告页和首页中。虽然有各种各样的框架可以实现这个功能，但引入框架会使得代码不干净（强迫症。。。），还会带来一些问题，比如代码体积变大，不必要的请求等等。所以偷个懒，写个轮播Demo,可以重复利用。

```html
<div>
    <ul class="carousel-body">
    	<!--一共有14张图片，为了无限轮播，在第一张前加上最后一张。同理在最后一张后加上第一张-->
        <li>
            <img src="images/partA/part1a_03.jpg" alt="">
            <p>距离墨尔本皇家植物公园约2公里，该植物园是当今世界上设计最好的植物园之一</p>
        </li>
        <li>
            <img src="images/partA/parta14_03.jpg" alt="">
            <p>高档公寓与奢侈品店的综合体，两栋地标建筑完美展现出建筑的几何之美。</p>
        </li>
        <li>
            <img src="images/partA/parta13_03.jpg" alt="">
            <p>Capitol Grand是墨尔本首个六星级住宅项目，坐落于墨尔本著名富人区南雅拉中心地段。</p>
        </li>
        <li>
            <img src="images/partA/parta12_03.jpg" alt="">
            <p>底层规划为三个楼层的奢侈品零售区，零售区以上的楼层将设一组高端公寓套房</p>
        </li>
        <li>
            <img src="images/partA/parta11_03.jpg" alt="">
            <p>园区内设有宜人的绿化景观园林，打开窗户，园区的景观便一览无余</p>
        </li>
        <li>
            <img src="images/partA/parta10_03.jpg" alt="">
            <p>顶层私人会所拥有绝美海湾景致的无边界泳池，俯抱墨尔本令人难以置信的魅力风景</p>
        </li>
        <li>
            <img src="images/partA/parta9_03.jpg" alt="">
            <p>大厦内的公寓套房将采用精致的设计，安装落地窗，拥有宽敞明亮的空间和华丽的饰面</p>
        </li>
        <li>
            <img src="images/partA/parta8_03.jpg" alt="">
            <p>所有公寓套房均采用优质材料进行装修，装配欧式设备、高端厨具电器</p>
        </li>
        <li>
            <img src="images/partA/parta7_03.jpg" alt="">
            <p>3层时尚购物中心上盖有豪华住宅单位，格局方正、大气，尽显奢华生活</p>
        </li>
        <li>
            <img src="images/partA/parta6_03.jpg" alt="">
            <p>大楼将设有带先进设施的健身馆，让业主享受到大楼所提供的贴心服务</p>
        </li>
        <li>
            <img src="images/partA/parta5_03.jpg" alt="">
            <p>公寓套房内大面积的落地窗设计，让房间的每个角落都充满阳光</p>
        </li>
        <li>
            <img src="images/partA/parta4_03.jpg" alt="">
            <p>南雅拉提供奢华、便捷的生活，设有电车、火车和巴士服务，还有多所名校和漂亮的公园</p>
        </li>
        <li>
            <img src="images/partA/parta3_03.jpg" alt="">
            <p>Toorak路上的8号电车，可直达墨尔本大学、途径St Kilda路商业区和墨尔本CBD</p>
        </li>
        <li>
            <img src="images/partA/parta2_03.jpg" alt="">
            <p>距离雅拉河只有8分钟的路程，闲暇之余，可以和家人一起惬意的漫步雅拉河畔</p>
        </li>
        <li>
            <img src="images/partA/part1a_03.jpg" alt="">
            <p>距离墨尔本皇家植物公园约2公里，该植物园是当今世界上设计最好的植物园之一</p>
        </li>
        <li>
            <img src="images/partA/parta14_03.jpg" alt="">
            <p>高档公寓与奢侈品店的综合体，两栋地标建筑完美展现出建筑的几何之美。</p>
        </li>
    </ul>
    <div class="prew-button">&lt;</div>
    <div class="ctrls">
        <span class="active"></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
    </div>
    <div class="next-button">&gt;</div>
</div>
```
以上为html代码

```css

.part-style .center > div {
  position: relative;
  width: 980px;
  height: 500px;
  overflow: hidden;
}
.carousel-body {
  position: absolute;
  height: 500px;
  width: 15680px;
  left: -980px;
}
.carousel-body li {
  float: left;
  position: relative;
}
.carousel-body li img {
  vertical-align: bottom;
}
.carousel-body li p {
  width: 980px;
  background: rgba(0, 0, 0, 0.5);
  height: 34px;
  line-height: 34px;
  font-size: 16px;
  font-family: "冬青黑体简体中文 W3", "黑体";
  color: #fff;
  position: absolute;
  bottom: 0px;
  left: 0px;
}
.ctrls {
  width: 980px;
  text-align: center;
  position: absolute;
  bottom: 45px;
}
.ctrls span {
  display: inline-block;
  width: 10px;
  height: 10px;
  border-radius: 5px;
  background: #FFFFFF;
  margin: 0 6px;
}
.ctrls span.active {
  background: #363636;
}
.prew-button,
.next-button {
  background: #996636;
  position: absolute;
  width: 24px;
  height: 24px;
  border-radius: 12px;
  color: #fff;
  line-height: 24px;
  text-align: center;
  font-family: "冬青黑体简体中文 W3", "黑体";
  font-weight: normal;
  bottom: 42px;
}
.prew-button {
  left: 284px;
  z-index: 10;
  cursor: pointer;
}
.next-button {
  right: 286px;
  z-index: 10;
  cursor: pointer;
}
```

以上为css代码

```javascript
//方法主体
$(function(){
    var $content = $('.carousel-body');
    var $ctrl=$('.ctrls span');
    var index = 1;
    var timmer = null;
    var pass = false;
    var start = function(){
        clearInterval(timmer);
        timmer=setInterval(function(){
            if(!pass){
                index++;
                if(index>14){
                    index=1;
                    $content.css("left","0px");
                    $content.animate({"left":-980+"px"},500);
                }else{
                    $content.animate({"left":-980*index+"px"},500);
                }
                $ctrl.removeClass("active");
                $ctrl[index-1].className="active";
            }else{
                pass=false;
            }
        },1000)
    }
    start();
    $content.on("mouseover",function(){
        clearInterval(timmer);
    })
    $content.on("mouseout",function(){
        start();
    })
    $('.ctrls span').click(function(){
        index=$(this).index() + 1;
        update();
    });
    $('.prew-button').click(function(){
        index--;
        if(index<=0) {
            index = 14;
            $content.css("left", -980 * 15 + "px");
        }
        update();
    })
    $('.next-button').click(function(){
        index++;
        if(index>14) {
            index = 1;
            $content.css("left", -980 * 0 + "px");
        }
        update();
    })
    function update(){
        pass=true;
        clearInterval(timmer);
        $ctrl.removeClass("active");
        $ctrl[index-1].className="active";
        $content.animate({"left":-980*index+"px"},{ duration: 500, queue: false, complete: function() {start();} })
    }
});
```
以上为javascript代码

当然在同一个页面中可以不只有一个轮播，所以有必要把他封装成一个方法，然后传入一个对象，调用执行。
```javascript
var carouse=function(item){
    var $content = item.$content;
    var $ctrl = item.$ctrl;
    var $ctrlsspan = item.$ctrlsspan;
    var $prew = item.$prew;
    var $next = item.$next;
    var index = 1;
    var pages = item.pages;
    var time = item.time;
    var timmer = null;
    var pass = false;
    var start = function(){
        clearInterval(timmer);
        timmer=setInterval(function(){
            if(!pass){
                index++;
                if(index>pages){
                    index=1;
                    $content.css("left","0px");
                    $content.animate({"left":-980+"px"},500);
                }else{
                    $content.animate({"left":-980*index+"px"},500);
                }
                $ctrl.removeClass("active");
                $ctrl[index-1].className="active";
            }else{
                pass=false;
            }
        },time)
    }
    start();
    $content.on("mouseover",function(){
        clearInterval(timmer);
    })
    $content.on("mouseout",function(){
        start();
    })
    $ctrlsspan.click(function(){
        index=$(this).index() + 1;
        update();
    });
    $prew.click(function(){
        index--;
        if(index<=0) {
            index = pages;
            $content.css("left", -980 * (pages+1) + "px");
        }
        update();
    })
    $next.click(function(){
        index++;
        if(index>pages) {
            index = 1;
            $content.css("left", -980 * 0 + "px");
        }
        update();
    })
    var update = function(){
        pass=true;
        clearInterval(timmer);
        $ctrl.removeClass("active");
        $ctrl[index-1].className="active";
        $content.animate({"left":-980*index+"px"},{ duration: 500, queue: false, complete: function() {start();} })
    }
}
//传入的对象
var ALL={
    $content : $('#ALL .carousel-body'),
    $ctrl : $('#ALL .ctrls span'),
    $ctrlsspan : $('#ALL .ctrls span'),
    $prew : $('#ALL .prew-button'),
    $next : $('#ALL .next-button'),
    pages : 7,
    time : 1000
}
carouse(ALL);
```


封装成JQuery插件
