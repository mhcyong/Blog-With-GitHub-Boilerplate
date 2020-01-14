---
layout: post
title: 获取QQ头像地址，并且不暴露QQ号
slug: get_qq_avatar
date: 2020-1-12 16:50
status: publish
author: 小否先生
categories: 
  - PHP代码
tags:
  - PHP
  - QQ
excerpt: 因为最近回归原生评论，所以评论头像如果单纯的引用gravatar头像，会有一部分low bee们头像会变成gravatar默认头像，为了解决这个问题，我想对于qq号@qq.com这样的邮箱地址就行个处理来提取QQ头像，然后问题是怎么获取QQ头像地址。
---

[notice]因为最近回归原生评论，所以评论头像如果单纯的引用gravatar头像，会有一部分low bee们头像会变成gravatar默认头像，为了解决这个问题，我想对于qq号@qq.com这样的邮箱地址就行个处理来提取QQ头像，然后问题是怎么获取QQ头像地址。[/notice]

## 尝试
最初想到获取QQ头像地址就是下面这样
```
https://q.qlogo.cn/g?b=qq&nk=QQ号码&s=100
```
当随之而来的问题就是暴露了别人的QQ号码，这点对于保护他人隐私上来说不太好。  
于是想到了这样的QQ头像地址  
```
https://q1.qlogo.cn/g?b=qq&k=0n5AZ9Ne4h3em8iboKu3sHg&s=100
```
上面的地址，中没有QQ号，却获取了某人的qq头像，里面的重要参数就是K的值，那么如何获取K值呢？  

## 解决
```
$qq = '你的扣扣号码';
$geturl = 'http://ptlogin2.qq.com/getface?&imgtype=1&uin='.$qq;
$qquser = file_get_contents($geturl);
$str1 = explode('&k=', $qquser);
$str2 = explode('&s=', $str1[1]);
$k = $str2[0];
$qqimg = 'https://q1.qlogo.cn/g?b=qq&k='.$k.'&s=100';
echo $qqimg
```
