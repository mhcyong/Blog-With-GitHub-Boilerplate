---
layout: post
title: 弹出DIV层自适应居中显示
slug: alert_div_by_js
date: 2020-1-12 17:50
status: publish
author: 小否先生
categories: 
  - JS代码
tags:
  - JS
  - javascript
excerpt: 弹出DIV层自适应居中显示-窗口特效-网页特效
---

[notice]弹出DIV层自适应居中显示-窗口特效-网页特效。[/notice]

```
<!DOCTYPE html>
<html>
<head>
<title>弹出DIV层自适应居中显示-窗口特效-网页特效-站长新动力-msxindl.com</title>
<meta http-equiv="content-type" content="text/html;charset=gb2312" />
<style type="text/css">
.opendiv{z-index:100;overflow:auto;position:absolute;padding:1px;border:1px solid #888;background:#fff;border-radius:5px;visibility:hidden;}
#bgdiv{z-index:99;width:100%;height:100%;position:absolute;top:0;left:0;filter:alpha(opacity=30);-moz-opacity:0.3;opacity:0.3;;visibility:hidden;background:#000;}
</style>
<script type="text/javascript">
function $(id){return document.getElementById(id);}
function openDiv(obj){
	if(!$(obj)) return false;
	var b = $('bgdiv');
	var d = $(obj);
	b.style.visibility='visible';
	d.style.visibility='visible';
	var wd=window.top.document.documentElement.clientWidth-d.offsetWidth;
	var ht=window.top.document.documentElement.clientHeight-d.offsetHeight;
	d.style.left=(wd/2)+'px';
	d.style.top=(ht/2)+'px';
	window.onresize=function(){openDiv(obj);};
	b.onclick=function(){closeDiv(obj);window.onresize=null;};  //点击背景关闭弹出层
}
//关闭弹出层
function closeDiv(obj){
	var b = $('bgdiv');
	var d = $(obj);
	b.style.visibility='hidden';
	d.style.visibility='hidden';
}
</script>
</head>
<body>
<input type="button" onclick="openDiv('div1')" value="点击弹出层1" />
<div id="div1" class="opendiv">
	弹出DIV层居中显示，自适应弹出层的高度和宽度，窗口大小改变时也能自适应保持居中<br />
	弹出DIV层居中显示，自适应弹出层的高度和宽度，窗口大小改变时也能自适应保持居中<br />
	弹出DIV层居中显示，自适应弹出层的高度和宽度，窗口大小改变时也能自适应保持居中<br />
	弹出DIV层居中显示，自适应弹出层的高度和宽度，窗口大小改变时也能自适应保持居中<br />
</div>
<div id="bgdiv"></div>
</body>
</html>
```
