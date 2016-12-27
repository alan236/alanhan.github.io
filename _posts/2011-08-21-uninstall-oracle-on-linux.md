---
layout: post
title: 在Linux手动卸载Oracle数据库
---

需要删除的目录及文件：

```bash
rm -rf $ORACLE_BASE
rm -rf /etc/oratab
rm -rf /etc/oracle
rm -rf /etc/inittab
rm -rf /usr/local/bin/coraenv
rm -rf /usr/local/bin/dbhome
rm -rf /usr/local/bin/oraenv
```