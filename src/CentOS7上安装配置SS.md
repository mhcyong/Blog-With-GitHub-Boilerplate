---
layout: post
title: CentOS7上安装配置SS
slug: centos7_ss
date: 2020-1-12 17:50
status: publish
author: 小否先生
categories: 
  - 网络技术
tags:
  - CentOS
  - 网络
excerpt: 因为最近回归原生评论，所以评论头像如果单纯的引用gravatar头像，会有一部分low bee们头像会变成gravatar默认头像，为了解决这个问题，我想对于qq号@qq.com这样的邮箱地址就行个处理来提取QQ头像，然后问题是怎么获取QQ头像地址。
---

[notice]因为最近回归原生评论，所以评论头像如果单纯的引用gravatar头像，会有一部分low bee们头像会变成gravatar默认头像，为了解决这个问题，我想对于qq号@qq.com这样的邮箱地址就行个处理来提取QQ头像，然后问题是怎么获取QQ头像地址。[/notice]

使用pip安装，分别执行以下命令：  
```
yum install m2crypto python-setuptools
easy_install pip
pip install shadowsocks
```
安装完成后，新建一个shadowsocks的配置json文件  
```
vi /etc/shadowsocks.json
```
然后在文件里编写配置内容
```
{
"server": "your_server_ip",  
"server_port": 8388, 
"local_port": 1080,             
"password": "your_passwd", 
"timeout": 300,
"method": "aes-256-cfb" 
}
```
your_server_ip ：替换成自己服务器的IP   
your_passwd：替换成自己想设置的密码串     

其他参数保持不变即可      

注意：输入完成后按 Esc键然后依次输入 :wq 回车键来保存配置信息  
保存成功后，启动shadowsocks服务
```
ssserver -c /etc/shadowsocks.json -d start
```
