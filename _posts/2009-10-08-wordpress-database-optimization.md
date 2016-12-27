---
layout: post
title: Wordpress数据库瘦身
---

再次打算给这个blog搬家.进去数据库看了看,WTF,居然45MB之巨!我文章也不算很多阿,400多篇,评论更少的可怜,怎么可能这么大?再仔细一看,光wp_postmeta就有40MB,55万个entries.确定是这个表的问题.再进去看看,满眼都是meta_key =_utw_tags_0… google一下之后,才恍然大悟,原来是之前Wordpress不支持tags的时候,我用过Ultimate Tag Warrior这个插件惹得祸,自从WP原生支持tags之后,我就把UTW删掉了,可是却没管数据库.瘦身的方法如下:

```sql
DELETE FROM `wp_postmeta` WHERE meta_key = '_utw_tags_0'
DELETE FROM `wp_postmeta` WHERE meta_key = '_utw_tags_'
```

执行完这两个命令后,整个世界清净了.wp_postmeta从40MB骤减至67KB.