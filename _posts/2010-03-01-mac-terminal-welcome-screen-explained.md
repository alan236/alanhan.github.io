---
layout: post
title: Mac Terminal欢迎界面详解
---

当你打开mac下的terminal的时候,首先你会看到这个界面,其中的文字包含了这些意义:

```bash
Last Login: Mon Mar 1, 15:55:50 on ttys000
Welcome Alan!
itd-624:~ Alan$
```

1. 第一行记录了你上次登录terminal的时间,大部分时候我都不记得上次登录的时间了…后面的ttys000代表了你所登录的terminal,这个wiki详细解释了ttys的来由.如果你打开多个terminal窗口,后面的3位数字随之增加.
2. 第二行的Welcome Alan!,称作message of the day,可以自行定义.具体方法在此.
3. 第三行,itd-624:~ Alan$,由两部分组成,前一部分的itd-624代表了你的电脑名称,可以在system preferences -> sharing 下更改.大部分情况这部分都会显示你的电脑名称,但有时候你所连接的网络会更改这个名字,在本图中就是一个例子,本身我的电脑名称是AH,学校的网络将其改为itd-624. 冒号之后的内容代表了当前使用的用户名称.如果你在使用ssh,这个名称则会改变.