---
layout: post
title: WordPress+nginx rewrite规则
---

今天研究了一下wordpress在nginx上的rewrite规则,在这里记录一下,也分享给有需要的人.

在站点的nginx配置文件中加入如下配置,选择是否要在域名中加入www,两者必须选择一项  


```Nginx
# enforce www (exclude certain subdomains)
if ($host !~* ^(www|subdomain))  
{  
    rewrite ^/(.*)$ $scheme://www.$host/$1 permanent;  
}
```  

或者  

```Nginx
# enforce NO www
if ($host ~* ^www\.(.*))  
{  
    set $host_without_www $1;  
    rewrite ^/(.*)$ $scheme://$host_without_www/$1 permanent;  
}
```

再加入  

```Nginx
# unless the request is for a valid file, send to bootstrap
if (!-e $request_filename)  
{  
    rewrite ^(.+)$ /index.php?q=$1 last;  
}
```

重启nginx即可.在wordpress后台Settings – Permalinks里更改你的设置.
