---
layout: post
title: 在Ubuntu 10.10上安装nginx + php-fpm + mysql
---

经过两天的研究,在我的linode上安装了nginx, php-fpm和mysql.在这里记录一下整个过程,也给有需要的人分享.

1. 先安装updates

   ```bash
   sudo apt-get update
   sudo apt-get upgrade --show-upgraded
   ```

2. 然后装aptitude

   ```bash
   sudo apt-get install aptitude
   ````

3. 安装mysql,按照屏幕提示输入root密码

   ```bash
   sudo aptitude install mysql-server
   ```

4. 接着是nginx

   ```bash
   sudo aptitude install python-software-properties
   sudo add-apt-repository ppa:nginx/stable
   sudo aptitude update
   sudo aptitude install nginx
   ```

5. 创建/var/www

   ```bash
   mkdir /var/www
   ```

6. php-fpm和一些模块

   ```bash
   sudo aptitude install php5-cgi php5-mysql php5-fpm php5-curl php5-gd php5-idn php-pear php5-imagick php5-imap php5-mcrypt php5-memcache php5-mhash php5-ming php5-pspell php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl
   ```

7. 修改fastcgi_params

   ```bash
   sudo vi /etc/nginx/fastcgi_params   

   # 加入以下参数
   fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
   fastcgi_param PATH_INFO $fastcgi_script_name;
   fastcgi_connect_timeout 60;
   fastcgi_send_timeout 180;
   fastcgi_read_timeout 180;
   fastcgi_buffer_size 128k;
   fastcgi_buffers 4 256k;
   fastcgi_busy_buffers_size 256k;
   fastcgi_temp_file_write_size 256k;
   fastcgi_intercept_errors on;
   ```

8. 最后,重启nginx和php-fpm

   ```bash
   sudo /etc/init.d/nginx restart
   sudo /etc/init.d/php5-fpm reload
   ```
