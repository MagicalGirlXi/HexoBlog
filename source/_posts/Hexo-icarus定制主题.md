---
title: Hexo+icarus定制主题
date: 2020-03-06 03:52:00
tags: Hexo
toc: true
categories: 萌新入门
thumbnail: https://blog-pics-1257119641.cos.ap-beijing.myqcloud.com/cat-4803841_1280.jpg
---



## 给网页添加js代码效果😛

在html页面中添加js代码可以实现很多可爱的效果，例如添加一个点击爱心效果。

Hexo生成的静态文件页面过程中，会解析`/theme/yourtheme/layout/`目录下的页面模板文件为html，除了直接在模板中编写js代码之外，还可以添加对js脚本的引用，这样在生成的所有页面中都会引入该js文件。

```html
<script src="/js/clicklove.js"></script>
```

<!--more-->

而Hexo会把source目录下的内容拷贝到最终生成的静态网站的根目录下，因此把点击爱心的js代码编写为`clicklove.js`放置在`/source/js/`下

```javascript
!function(e,t,a){
	    function n(){
	        c(".heart{width: 10px;height: 10px;position: fixed;background: #f00;transform: rotate(45deg);-webkit-transform: rotate(45deg);-moz-transform: rotate(45deg);}.heart:after,.heart:before{content: '';width: inherit;height: inherit;background: inherit;border-radius: 50%;-webkit-border-radius: 50%;-moz-border-radius: 50%;position: fixed;}.heart:after{top: -5px;}.heart:before{left: -5px;}"),
	        o(),
	        r()
	    }
	    function r(){
	        for(var e=0;e<d.length;e++)
	            d[e].alpha<=0?(t.body.removeChild(d[e].el),d.splice(e,1)):(d[e].y--,d[e].scale+=.004,d[e].alpha-=.013,d[e].el.style.cssText="left:"+d[e].x+"px;top:"+d[e].y+"px;opacity:"+d[e].alpha+";transform:scale("+d[e].scale+","+d[e].scale+") rotate(45deg);background:"+d[e].color+";z-index:99999");
	        requestAnimationFrame(r)
	    }
	    function o(){
	        var t="function"==typeof e.onclick&&e.onclick;
	        e.onclick=function(e){
	            t&&t(),i(e)
	        }
	    }function i(e){
	            var a=t.createElement("div");
	            a.className="heart",d.push({el:a,x:e.clientX-5,y:e.clientY-5,scale:1,alpha:1,color:s()}),t.body.appendChild(a)
	    }
	    function c(e){
	        var a=t.createElement("style");a.type="text/css";
	        try{
	            a.appendChild(t.createTextNode(e))
	        }
	        catch(t){
	            a.styleSheet.cssText=e
	        }
	        t.getElementsByTagName("head")[0].appendChild(a)
	    }
	    function s(){
	        return"rgb("+~~(255*Math.random())+","+~~(255*Math.random())+","+~~(255*Math.random())+")"
	    }
	    var d=[];
	    e.requestAnimationFrame=function(){
	        return e.requestAnimationFrame||e.webkitRequestAnimationFrame||e.mozRequestAnimationFrame||e.oRequestAnimationFrame||e.msRequestAnimationFrame||function(e){
	            setTimeout(e,1e3/60)
	        }
	    }(),
	    n()
	}
	(window,document);
```

把项目重新部署，就可以看到可爱的点击爱心效果啦！😝

更多js和css的好玩效果，参见[Hexo 博客优化之博客美化系列（持续更新）](https://blog.csdn.net/qq_36759224/article/details/85420403) 

## 设置首页仅显示文件摘要的方法

### 第一种方式

手动在`front-matter`中添加的`description`的键值对

```yaml
title: Hexo+icarus定制主题
date: 2020-03-06 03:52:00
description: 这里写文章摘要，但是这里的内容在文章详情页面并不会展示。
```
### 第二种方式

在编辑markdown文档时，在内容中加入`<!--more-->`分隔，分隔符上的内容会被选为摘要，在分隔符的位置会显示 “阅读更多” 按钮

## 复杂的样式优化

[Icarus 主题自定义](https://www.alphalxy.com/2019/03/customize-icarus/) 