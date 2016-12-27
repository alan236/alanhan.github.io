---
layout: post
title: Macbook Pro Retina外接显示器小记
---

上星期趁着Dell的12 Days of Deals，入手了一台[U2715H](http://accessories.us.dell.com/sna/productdetail.aspx?c=ca&cs=cadhs1&l=en&sku=210-ADKB)显示器。  
由于是第一次给我2012年的Macbook Pro Retina配显示器，好多东西事先都没有想到。在这里记录一下:

* 习惯视网膜屏幕显示效果的人群第一次看到外接显示器的文字显示可能会觉得发虚。这是由于OS X字体渲染的算法导致，基本没有办法解决。网上有些[方法](http://www.ireckon.net/2013/03/force-rgb-mode-in-mac-os-x-to-fix-the-picture-quality-of-an-external-monitor)可以尝试，但效果不大：
    1. 确保显示器的Color Profile是RGB（在Preferences -&gt; Display中查看）
    2. 确保OS X不要将显示器认作电视（在About This Mac -&gt; System Report -&gt; Graphics/Display查看）
    3. 可以尝试在Preferences -&gt; General中关闭”Use LCD font smoothing when available”
* U2715H支持的接口有DisplayPort, MiniDP, HDMI。从显示效果上排名应该是DisplayPort &gt; DVI &gt; HDMI &gt; VGA。如果可能尽量使用rMBP上的雷电（Thunderbolt）接口。
* 如果连接rMBP到U2715H并在显示器设置中打开DP 1.2，会导致黑屏，需要特殊方法把DP 1.2关闭：
    1. 将显示器关机
    2. 拔下所有显示输入线
    3. 显示器开机，并呼出Input Source菜单，高亮选中DP但不要点确认退出菜单
    4. 长按确认按钮15秒（绿色勾）
    5. DP 1.2重设菜单会出现。转至disabled，然后重启显示器即可

* 由于rMBP设计关系，不建议外接显示器的时候将电脑关盖，会影响散热。
