---
layout: post
title: Hands-on Sybase SQLAnywhere 12.0.1 Installation on Linux
permalink: /hands-on-sybase-sqlanywhere-12-0-1-installation-on-linux/
---

Environment: Red Hat or SUSE Linux

**Installation Steps:**

1. On your linux machine, create a new user ‘sybase’

2. Switch to this new user, create the database installation directory (e.g. /databases/sybase)

3. Create another folder for the installer (e.g. /databases/installation)

4. Upload and unzip the installer

   ```bash
   $ unzip sqla1201linux3264_advanced.zip
   ```

5. Folder structure after unzip

   ```bash
   $ ls -al
   total 421004
   drwxr-xr-x 4 root root 4096 Jan 25 11:00 .
   drwxr-xr-x 6 sybase dba 4096 Jan 25 10:59 ..
   -r--r--r-- 1 root root 0 Feb 1 2011 linux-x86-x64
   dr-xr-xr-x 8 root root 4096 Feb 1 2011 monitor
   -r--r--r-- 1 root root 387 Feb 1 2011 readme.txt
   -rw-r--r-- 1 root root 431087213 Jan 25 11:00 sqla1201linux3264_advanced.zip
   dr-xr-xr-x 8 root root 4096 Feb 1 2011 sqlanywhere
   ```

6. Under the ‘Sybase’ user, start the installer

   ```bash
   $ ./sqlanywhere/setup
   ```

7. Follow the on-screen instruction  
    1. Press ENTER  
    2. Select the country you are in  
    3. In the terms of license screen, click q to skip, then type Y to agree  
    4. Type 1 for new installation  
    5. Enter license key  
    6. Select the components you’d like to install  
    7. Once everything is selected, type S to continue  
    8. Enter your desired installation directory (the one you created in step 2)  
    9. Finally, confirm and start the installation

8. After the installation is completed, go to the installation directory, you should see the following files and folders:

   ```bash
   $ ls
   bin32     demo.db                    java      readme_de.txt  res           selinux          tix
   bin32s    demo.log                   lib32     readme_en.txt  samonitor.db  sun              ultralite
   bin64     deployment                 lib64     readme_ja.txt  samples       support          uninstall.sh
   bin64s    install_20130125-1107.log  mobilink  readme_zh.txt  scripts       vcsagent
   charsets  installed.ini              readme    relayserver    sdk           thirdpartylegal
   ```

**New Database Configuration Steps:**

1. Under the new ‘sybase’ user, edit .bash_profile

   ```bash
   $ vim ~/.bash_profile
   # add the following lines:
   LD_LIBRARY_PATH=/databases/sybase/SQLAnywhere/12.01/lib64 export LD_LIBRARY_PATH
   export LANG=en_US.utf8
   ```

2. Logout from Sybase user and log in again to apply new profile

3. Check that the new environment variables are added

   ```bash
   $ env | grep LANG
   LANG=en_US.utf8
   $ env | grep LD
   LD_LIBRARY_PATH=/databases/sybase/SQLAnywhere/12.01/lib64
   ```

4. In your SQL Anywhere installation directory, create a new folder for your new database

   ```bash
   $ mkdir <database_name>
   ```

5. Create temp folder in database directory

   ```bash
   $ cd <dir_from_step_4>
   $ mkdir tmp
   ```

6. Source SQLAnywhere environment

   ```bash
   $ source <installation_dir>/bin64/sa_config.sh
   ```

7. Learn dbinit options

   ```bash
   $ </installation_dir><installation_dir>/bin64/dbinit -h
   ```

8. Go to your new database folder, create startup script

   ```bash
   $ vim init.conf
   # copy and paste the following lines:
       -p 8192
       -ze utf8
       -dba <admin_username>,<password>
       -dbs 2G
       -o <dir_from_step_4>/output_msg.trc
       -t </dir_from_step_4><dir_from_step_4>/transaction.log
       -m </dir_from_step_4><dir_from_step_4>/transaction_mirror.log
       </dir_from_step_4><dir_from_step_4>/data.db
   ```

9. Initialize new database

   ```bash
   $ <installation_dir>/bin64/dbinit @<dir_from_step_4>/init.conf
   ```

10. Learn dbsrv12 options

    ```bash
    $ <installation_dir>/bin64/dbsrv12 -h
    ```

11. Create new database configuration parameters file

    ```bash
    $ vim <dir_from_step_4>/db.conf
    # copy and paste the following lines:
        -ud
        -n <new_db_name>
        -x "tcpip (PORT=65000)"
        -gm 64
        -c 128M
        -ch 512M
        -dt <dir_from_step_5>
        -gn 10
        -o <dir_from_step_4>/sysa12d01.trc
        -os 10M
        -ze
        -zl
        -zp
        -zt
        -cs
        </dir_from_step_4><dir_from_step_4>/data.db
    ```

12. Start db server

    ```bash
    $ <installation_dir>/bin64/dbsrv12 @<dir_from_step_4>/db.conf &
    ```

13. Stop db server

    ```bash
    $ <installation_dir>/bin64/dbstop –y –c “eng=<new_db_name>;uid=<admin_username>;pwd=<password>”
    ```
