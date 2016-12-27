---
layout: post
title: WordPress安裝后要做的事
---

當你安裝好一個全新的wordpress準備開始寫第一篇blog的時候,稍等一下!為什么不用一點時間做一些”安裝后的設置”確保所有東西都設置正確,為以后打好基礎呢?在開始介紹前,我要聲明的是:本文僅適用于在你自己空間上安裝的wordpress.當然,如果你用其他的blog程序,也可以參考本文,只是有可能你需要自己尋找有關的設置.

大部分設置都是在blog的管理面板,所以需要你用管理員帳號登錄.

1. 改變靜態鏈接的結構 – WP默認的靜態鏈接是http://www.yourdomain.com/?p=21這樣的;但是這種靜態鏈接對于搜索引擎來說過于簡單了.如果一個http://www.yourdomain.com/the_next_great_article這樣的靜態鏈接會更吸引搜索引擎.如果需要改變這項設置,打開管理面板下的options-permalink,選擇custon field然后鍵入/%postname%即可.
2. 換掉默認的主題 – 這也是為了告訴你的讀者你是一個認真持久的blogger.網上有許多免費的主題可以使用,你可以在http://themes.wordpress.net/搜索.找到心儀的主題后,將其上傳到wp-content/themes目錄下,然后打開管理面板的Presentation/Design激活新的主題即可.
3. 更新Ping服務 – 當你更新blog之后,XMLRPC服務會幫你宣傳以便讓更多人知道你的blog.所以當然越多人來知道越好.這里http://codex.wordpress.org/Update_Services有一個Ping服務的列表.在管理面板下點擊options-writing,將列表粘帖到下面update services欄內即可.記得要點save哦!
4. 激活akismet插件 – 這個插件是默認與wordpress一同安裝的.所以你只需要去管理面板下的plug-ins然后激活它就可以了.這個插件需要一個wordpress的API號碼,它會提示你如何注冊一個.這個插件會幫你阻擋許多垃圾評論.
5. 用feedburner燒錄你的feed – 讓http://www.feedburner.com幫忙burn你的feed.當你的讀者訂閱你的RSS時候就會自動更新.同時feedburner還會幫你做統計.要記得修改主題上的feed鏈接到feedburner.
6. 好啦,現在我可以說你已經準備開始寫一個wordpress blog了!當然還有其他一些小技巧,以后的文章中會繼續介紹!
