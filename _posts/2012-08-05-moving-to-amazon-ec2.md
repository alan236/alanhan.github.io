---
layout: post
title: 搬家到Amazon EC2
---

这几天再次把这个blog折腾了一遍,从用了快两年的Linode迁移到Amazon EC2,用的是Micro Instance,可以免费使用一年.Region选的是US West Oregon,装了ubuntu.试用一两天下来,暂时感觉比Linode要稍微慢那么一些些,基本上是无法察觉的.Micro Instance的内存就已达到613MB,这点比Linode的512MB要好多了.

这次搬家我选择了LAMP的环境,没有选择nginx的原因很简单,因为之前没有认真的玩过Apache,所以这次想学习一下.总的来说,从最初的deploy instance到最后成功运行wordpress的过程还是比较容易的,网上的教程中英文的已有很多,我也是新手所以在这里我也不多分享了,不想误导了他人.在这里仅记一下我遇到的几个tricky point:

1. 如需将自己的域名绑定到EC2 instance,需要先建立一个elastic IP,在EC2 Management Console里就可以找到.切记在建立IP之后要associate到你的instance,如果放着不associate是要收费的
2. wordpress permalink需要a2enmod rewrite
