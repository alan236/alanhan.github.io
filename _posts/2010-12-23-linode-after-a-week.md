---
layout: post
title: 使用Linode一周小记
---

上周五linode搞了个活动,早上9点开始前100位购买服务的人都可以获得100美金的礼金,可以用来付月租,因为还有时差的关系,于是我那天一大早就起来坐在电脑前等着抢,结果成功抢到,不过最后听说差不多130分钟后才卖完.

之前我一直推崇mediatemple,主要的原因是他们有很多大公司的客户,只是他们的(dv)的价格真是vps中的劳斯莱斯,实在无法接受,只好参加了大猫的合租(顺便说一句,大猫的合租一直都很稳定,推荐!).用了linode一个星期下来,我对他们的看法大大改观,最让我惊讶和感动的就是他们support的速度,我开了5个ticket,每个都在5分钟内就收到回复,其中有两个还是凌晨1点多开的.这点很值得称赞.linode library的文章非常全面,也浅显易懂,非常适合我这样的新手.

在这里做个小广告,如果你也对linode的服务感兴趣,不妨考虑填我的referral code:
```
aba73904570c8608451f2cb9557fbba0c721038e
```
这样我也可以获得一些小的收益,两全其美.

跑了一遍unixbench,把分数贴上来
```
==============================================================
System Benchmarks Index Values BASELINE RESULT INDEX
Dhrystone 2 using register variables 116700.0 54276450.3 4650.9
Double-Precision Whetstone 55.0 9296.7 1690.3
Execl Throughput 43.0 4583.5 1065.9
File Copy 1024 bufsize 2000 maxblocks 3960.0 284893.6 719.4
File Copy 256 bufsize 500 maxblocks 1655.0 73340.2 443.1
File Copy 4096 bufsize 8000 maxblocks 5800.0 925806.9 1596.2
Pipe Throughput 12440.0 1688667.5 1357.4
Pipe-based Context Switching 4000.0 152433.9 381.1
Process Creation 126.0 7258.8 576.1
Shell Scripts (1 concurrent) 42.4 9079.2 2141.3
Shell Scripts (8 concurrent) 6.0 1190.2 1983.7
System Call Overhead 15000.0 1518083.0 1012.1
========
System Benchmarks Index Score 1152.0
```