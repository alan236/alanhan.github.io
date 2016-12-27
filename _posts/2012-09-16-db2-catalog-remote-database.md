---
layout: post
title: DB2 Catalog远程数据库服务器
---

在服务器上安装好DB2后,如果需要从客户端连接数据库的话,就要在客户端的机器上执行DB2的Catalog(编目)命令,具体的步骤如下(以下基于Windows):

1. 打开DB2 Command Line (需要用管理员权限打开)

2. 在DB2提示符下,输入:

   ```sql
   catalog tcpip node <node_name> remote <server_host_name> server <port_number or SVCENAME> remote_instance <db2_instance_name>   

   -- <node_name> = 节点名称,可以任意定义
   -- <server_host_name> = 数据库服务器IP地址或host name
   -- <port_number or SVCENAME> = DB2数据库监听端口
   -- <db2_instance_name> = DB2数据库实例名
   ```

3. 输入TERMINATE退出DB2提示符再重新进入,刷新DB2 Directory Cache

4. 在DB2提示符下,输入:

   ```sql
   catalog database <db_name>  at node <node_name>   

   -- <db_name> = 数据库名
   -- <node_name> = 在第二步中定义的节点名
   ```

5. 再次刷新DB2 Directory Cache

6. 在DB2提示符下,输入list node directory和list database directory,如果可以看到新的节点和数据库,证明catalog命令已经执行成功.

7. 输入以下命令连接远程DB2数据库,此处的<db_name>即是第4步定义的

   ```sql
   connect to <db_name> user <username> using <password>
   ```
