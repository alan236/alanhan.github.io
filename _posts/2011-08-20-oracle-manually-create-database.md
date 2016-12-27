---
layout: post
title: Oracle手动创建数据库
---

1. 在$ORACLE_HOME/dbs目录下，创建新数据库的pfile文件，其中至少包括以下参数(假设新数据库叫bill)，文件名为initbill.ora：

   ```sql
   *.background_dump_dest='/ocp/bill/admin/bdump'
   *.compatible='10.2.0.1.0'
   *.control_files='/bak/bill/control01.ctl','/ocp/bill/control02.ctl'
   core_dump_dest='/ocp/bill/admin/cdump'
   *.db_name=bill
   instance_name=bill
   *.job_queue_processes=10
   *.sga_max_size=419430400
   *.sga_target=423624704
   *.undo_management='AUTO'
   *.undo_tablespace='UNDOTBS1'
   *.user_dump_dest='/ocp/bill/admin/udump'
   ```

2. 根据pfile，创建所需的相应目录

3. 创建环境变量

   ```bash
   export ORACLE_SID=bill
   ```

4. sqlplus / as sysdba 登录

5. 在SQL提示符下由pfile启动数据库,输入:

   ```
   startup nomount pfile='initbill.ora';
   ```

6. 待oracle实例启动到nomount状态下通过pfile创建spfile，输入：

   ```sql
   create spfile from pfile;
   ```

7. 退出SQL提示符后创建新的密码文件，输入：

   ```sql
   orapwd file=orapwbill password=oracle
   ```

8. 在$ORACLE_HOME/dbs目录下创建手动建库的sql脚本createdb.sql，内容示例：

   ```sql
   create database bill
   maxinstances 2
   maxlogfiles 32
   maxlogmembers 5
   maxdatafiles 200
   maxloghistory 290
   user sys identified by oracle
   user system identified by oracle
   character set utf8
   national character set al16utf16
   datafile '/ocp/bill/oradata/system.dbf' size 300m
   sysaux datafile '/ocp/bill/oradata/sysaux.dbf' size 200m
   undo tablespace UNDOTBS1 datafile '/ocp/bill/oradata/undotbs1.dbf'
   size 200m
   default temporary tablespace temp tempfile '/ocp/bill/oradata/temp
   1.dbf' size 100m
   logfile
   group 1 '/ocp/bill/oradata/redo1.log' size 100m,
   group 2 '/ocp/bill/oradata/redo2.log' size 100m
   ;
   ```

9. 在SQL提示符下运行刚刚创建的脚本，输入：

   ```sql
   @createdb.sql
   ```

10. 在SQL提示符下创建users表空间，输入：

    ```sql
    create tablespace users datafile '/ocp/bill/oradata/users.dbf' size 200m;
    ```

11. 在SQL提示符下创建数据字典，输入：

    ```sql
    @?/rdbms/admin/catalog.sql
    @?/rdbms/admin/catproc.sql
    ```
