---
layout: post
title: 我的wordpress搬家方法
---

之前一直在用dreamhost,用了两年之后想換地方了,其一是看到国内外很多人都推薦mediatemple,dreamhost這邊也用膩了;其二是之前的24inside.net由于沒有及時續費被別人搶走了,一度沒有什么心情打理,這幾天發現了這個24er.net,比較短也比較好記,于是就想轉過來mt這邊.整理了一下dh那邊的ftp,發現這幾年弄網站沒弄出什么名堂,除了這個用了快3年的blog其他的都是空蕩蕩沒有內容的論壇或是網店甚至還有wiki,都是之前不斷嘗鮮卻很快失去興趣所留下來的.于是決定把我的blog完完整整的搬來這邊.之前有些印象,記得是備份下ftp里所有的文件,再把數據庫全部export出來.到新的這邊把文件再重新傳上去,數據庫文件import就完事了.沒想到當中遇到兩個意料之外的問題,第一:因為我的blog中有中文,在phpmyadmin中直接導入后居然全部都是亂碼!第二:我的數據庫文件很大,在phpmyadmin當中無法直接導入.因為本人是第一次將整個wordpress搬到另外一個webhosting當中,經過了些google和無數次的失敗,終于發現了一個給wordpress搬家的整體解決方案,步驟如下:

1. 當然是備份下你舊ftp上整個wordpress的文件夾,并傳入新的ftp中.

2. 利用wordpress的 WP-DB-Backup 插件備份下數據庫.方法是:在wp后臺-manage-backup,這個插件會自動備份核心的幾個表,你還可以選其他的表一起備份上.選好之后點上download to your computer然后點backup!.你將會得到一個sql.gz的壓縮包.

3. 用winrar打開sql.gz壓縮包,將里面的sql文件解壓出來.

4. (這一步要感謝zhiqiang的這篇文章,這一步是核心步驟,非常重要!!)
    1. 在phpMyadmin中设定MySQL 字符集: UTF-8 Unicode (utf8) （一般来说默认就是这个）
    2. 在phpMyadmin中设定MySQL 连接校对: utf8_general_ci
    3. 用文本编辑器如EditPlus 打开备份的数据库文件(也就是第二步解壓出來的sql文件，查找”DEFAULT CHARSET=latin1″ 用”DEFAULT CHARSET=utf8″替换。

5. 完成第3步之后,視乎你數據庫的大小,如果小于phpmyadmin的上傳限制就直接用phpmyadmin導入sql文件,但是如過大于限制,請繼續往下看.

6. 在你的ftp中建立文件夾,例如backup,將之前第3-3步修改好的sql文件上傳到這個文件夾.

7. 下載bigdump.你將會得到一個bigdump.php的文件.按如下方法修改相應的句子,并把bigdump.php放入第5步的backup文件夾中
```
$db_server = '數據庫主機';
$db_name = '數據庫名稱';
$db_username = '使用者名稱';
$db_password = '使用者密碼';
$filename = '要備份的 sql文件名';
$linespersession = 3000; // 指每次還原幾筆
$delaypersession = 0; // 中間間隔要休息幾秒，這里是不休息
$db_connection_charset = 'utf8'; // 編碼使用的字元是哪一種,記得一定要寫utf8!!否則亂碼!
```

8. 運行bigdump.php,例如http://yourname.com/backup/bigdump.php,按照屏幕指示點選start

9. 等待一會后會提示成功,別急,還有這更重要的一步,這樣才能最終解決亂碼問題:
    * 修改wp-includes/wp-db.php內的资料连线设定。详细的修改方式是这样的：
    ```
    $this->dbh = @mysql_connect($dbhost,$dbuser,$dbpassword);
    //加上下面这行
    $this->query("SET NAMES 'utf8'" );
    ```

10. 修改wp-config.php,將新的數據庫信息填入.并在wp-config.php中,在MySQL settings下加入這句代碼: 
```
define('DB_CHARSET', 'utf8');
```

11. 大功告成!!

一天的失敗以及無數次的嘗試所總結出來的方法,希望能對需要的人有所幫助.我還很菜,所以可能會有比這方法方便許多的,大家見笑了.