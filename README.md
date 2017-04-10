長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
#這是R Code Chunk
##第一次使用要先安裝 install.packages("rvest")
##read_html
##html_nodes
##html_text
library(xml2)
```

    ## Warning: package 'xml2' was built under R version 3.3.3

``` r
library(rvest) 
```

    ## Warning: package 'rvest' was built under R version 3.3.3

``` r
frame = data.frame(Title=character(),
                      Author=character(),
                      PushNum=character())
for(i in 4670:4675){
PTTURL<-paste0("https://www.ptt.cc/bbs/NBA/index",i,".html") 
PTTContent <- read_html(PTTURL)
post_title <- PTTContent %>% html_nodes(".title") %>% html_text() 
post_title <- gsub("\n",replacement="",post_title)
post_title <- gsub("\t",replacement="",post_title)
post_author<- PTTContent %>% html_nodes(".author") %>% html_text()
post_pushnum <- PTTContent %>% html_nodes(".nrec") %>% html_text()
PTTframe <- data.frame(Title = post_title, Author = post_author, PushNum = post_pushnum)
frame <- rbind(frame,PTTframe)
}
```

爬蟲結果呈現
------------

``` r
#這是R Code Chunk
knitr::kable(frame) ##請將iris取代為上個步驟中產生的爬蟲資料資料框
```

| Title                                               | Author       | PushNum |
|:----------------------------------------------------|:-------------|:--------|
| \[討論\] 請問中場那首nba廣告音樂是哪首?             | Kafziel      | 25      |
| \[BOX \] Jazz 86:101 Blazers 數據                   | Rambo        | 88      |
| \[情報\] Lillard記錄之夜                            | dragon803    | 49      |
| (本文已被刪除) \[MrSatan\]                          | -            | 72      |
| \[專欄\] 林書豪瘋狂四月，2018年薪可望破表 LYS       | lovea        | XX      |
| \[BOX \] Pelicans 101:123 Warriors 數據             | Rambo        | 69      |
| Re: \[新聞\] 西河被質疑刷數據 Kobe力挺：什麼蠢問題  | shu2001      |         |
| \[閒聊\] Joe Johnson生涯得分突破20000分             | dragon803    | 43      |
| \[討論\] 老大是不是(準)名人堂球星中最帥的？         | Gogoro5566   | 73      |
| \[新聞\] NBA／杜蘭特16分10籃板 勇士奪14連勝         | HanJie       | 26      |
| \[新聞\] 林書豪原味簽名球衣！　籃網主場最終戰大     | zzzz8931     | 26      |
| Re: \[新聞\] 西河被質疑刷數據 Kobe力挺：什麼蠢問題  | nomilkman    | 5       |
| Re: \[新聞\] 林書豪原味簽名球衣！　籃網主場最終戰大 | ilovesumika  | 15      |
| \[新聞\] MVP之爭延燒到季後 火箭首輪對雷霆           | AAApower     | 15      |
| \[情報\] 小牛將與達拉斯牛仔隊傳奇托尼-羅莫簽約      | Kay731       | 18      |
| \[新聞\] 林書豪全能秀　籃網主場封關逆轉勝公牛       | sinana       | 22      |
| \[外絮\] Steve Nash breaks down the MVP race        | kendiablo    | 63      |
| Re: \[討論\] 是不是騎士季末再爛 大家還是認為會東冠  | wmigrant     |         |
| \[討論\] 東區爭奪排名，西區對戰組合大致底定         | gold97972000 | 30      |
| \[討論\] 為何不乾脆等雷霆火箭打完再選MVP?           | a11114xy     | X5      |
| \[情報\] 波波：不再輪休，是時候進入季後賽模式了     | Yui5         | 73      |
| (本文已被刪除) \[dragon803\]                        | -            | 1       |
| \[情報\] Lillard本日個人得分佔全隊58.42%            | avrild12     | 74      |
| \[情報\] TODAY                                      | Ivers        | 2       |
| \[討論\] 雷霆當年如果留哈登會奪冠嗎                 | hhll5566     |         |
| \[外絮\] Lillard賽後將比賽用球送給J. Johnson        | Ansel        | 67      |
| \[情報\] NBA Standing(2017.4.9)                     | tripleaAAA   | 52      |
| \[花邊\] 因應輪休爭議 聯盟宣布下季賽程延長1週       | adam7148     | 19      |
| \[討論\] 球員會想拿MVP還是拿新的獎                  | CurryMvp     | 47      |
| \[情報\] 打鐵積分 排行榜                            | checktime    | 19      |
| \[討論\] NBA是最愛輪休的職業運動嗎？                | Ayanami5566  |         |
| \[情報\] ★今日排名(2017.04.09)★                     | Rambo        | 3       |
| \[討論\] 買飯型球員在主客場的差異?                  | frank47147   | 23      |
| Re: \[討論\] 雷霆當年如果留哈登會奪冠嗎             | dro001       | 7       |
| \[討論\] 灰狼打湖人到底誰會坦                       | iimk0918     | 3       |
| \[新聞\] 籃網主場關門戰 林書豪難得半裸露肌肉        | ttfan        | 52      |
| \[新聞\] 希臘怪物雙十領軍 公鹿收下季後賽門票        | iam168888888 | 8       |
| \[討論\] 勇士跟拓荒對戰                             | yokann       | 14      |
| \[新聞\] 膝傷未癒恐成未爆彈？ 騎士厄文坦言近況遭    | Gotham       | 64      |
| 緯來賽後音樂                                        | teddy2261354 | X1      |
| \[討論\] 哪一隊存在感最低？                         | fantazy00077 | 爆      |
| Re: \[討論\] 哪一隊存在感最低？                     | derekhsu     | 62      |
| (本文已被刪除) \[MrSatan\]                          | -            | 24      |
| \[Live\] 暴龍 @ 尼克                                | Rambo        | 11      |
| Re: \[情報\] ESPN的MVP預測                          | hungys       | 44      |
| \[討論\] R:哪一隊存在感最低？                       | h1212123tw   | 12      |
| Re: \[討論\] 哪一隊存在感最低？                     | edison321    | 9       |
| Re: \[討論\] 哪一隊存在感最低？                     | dragon803    | 35      |
| (本文已被刪除) \[Temperboxer\]                      | -            |         |
| \[BOX \] Raptors 110:97 Knicks 數據                 | Rambo        | 16      |
| \[情報\] 騎士裁了Liggins                            | jaevastar    | 60      |
| \[Live\] 騎士 @ 老鷹                                | Rambo        | 爆      |
| \[情報\] 醫生：Rose的打法和基因是他頻繁受傷的原因   | bigDwinsch   | 18      |
| \[花邊\] Fultz：我願為尼克效力，能在三角進攻中成功  | bigDwinsch   | 31      |
| \[Live\] 雷霆 @ 金塊                                | Rambo        | 爆      |
| \[Live\] 小牛 @ 太陽                                | Rambo        | 1       |
| \[Live\] 火箭 @ 國王                                | Rambo        | 12      |
| Re: \[討論\] 哪一隊存在感最低？                     | feyako       | 5       |
| \[BOX \] Cavaliers 125:126 Hawks 數據               | Rambo        | 99      |
| \[新聞\] 輪休鼻組語出驚人　波帕維奇：不輪休了       | LIN9         | 28      |
| \[情報\] 西河破紀錄啦！！！！                       | ck0987515477 | 爆      |
| \[討論\] 恭喜龜龜破紀錄                             | ZaneTrout    | 11      |
| \[花邊\] Russell Westbrook本季42次大三元達成        | jay0601zzz   | 12      |
| \[BOX \] Thunder 106:105 Nuggets 數據               | Rambo        | 爆      |
| \[討論\] 龜龜絕殺50分超級大三元+單季42次大三元      | asonge0000   | 68      |
| \[討論\] 我到底看了三小???                          | RussellWestb | 26      |
| \[專欄\]哈登vs.衛少狹路相逢 火箭恐怕飛不起來LYS     | zzyyxx77     | X2      |
| \[心得\] 龜龜這場是雙絕殺!逆轉+對方季後賽out        | checktime    | 80      |
| \[情報\] 德佬例行賽場次超越TD                       | jay0601zzz   | 84      |
| \[討論\] 我龜MVP是不是穩了                          | kobeyoung    | 76      |
| \[BOX \] Pistons 103:90 Grizzlies 數據              | Rambo        | 6       |
| \[外絮\] Westbrook 破紀錄賽後球員推特祝賀           | hungys       | 59      |
| \[BOX \] Mavericks 111:124 Suns 數據                | Rambo        | 15      |
| \[BOX \] Rockets 135:128 Kings 數據                 | Rambo        | 95      |
| \[外絮\] CJ和Lillard感謝龜龜：你是真正的MVP         | Ansel        | 63      |
| \[討論\] KD有冠的話應該會超越Dirk吧?                | siriusc      | 11      |
| \[討論\] Westbrook破紀錄的大三元助攻影片            | pttnowash    | 23      |
| \[新聞\] 這一球被吹犯畢業 詹皇龍顏大怒              | jay0601zzz   | 29      |
| \[Live\] 灰狼 @ 湖人                                | Rambo        | 44      |
| \[閒聊\] 騎士老鷹之戰的一些記錄                     | dragon803    | 16      |
| \[情報\] 龜龜大三元次數正式超越張大帥               | sthho        | 28      |
| \[發錢\] 當代神獸雙破大三元                         | monmo        | 爆      |
| \[情報\] Russell Westbrook 大三元次數超越 Oscar     | gold97972000 | 17      |
| \[討論\] Westbrook是不是已經比KD強了                | FenixShou    | 60      |
| \[情報\] Kobe轉發西河今天的絕殺影片：還有疑問嗎?    | tmacor1      | 76      |
| Re: \[新聞\]單季2次50分大三元 哈登史上第一人        | checktime    | 23      |
| \[祭品\] 哈登MVP!                                   | konayuki     | X5      |
| \[新聞\] 詹姆斯大三元+厄文45分 騎士還是被逆轉       | KyrieIrving1 | 27      |
| \[新聞\] MVP給誰公平？布萊恩：丟硬幣決定            | zzyyxx77     | 14      |
| \[新聞\] 超遠三分絕殺幸運球？ 衛少：我不是亂投      | pneumo       | 14      |
| \[新聞\] 本季主場最終戰 太陽曬小牛圓滿收尾          | zzzz8931     | 1       |
| \[討論\] 湖人的防守還有救嗎?                        | tiffanycute  | 15      |
| \[討論\] 單季場均大三元+得分王                      | pptdog       | 21      |
| \[討論\] 冠軍跟大三元紀錄是否不可兼得?              | journeytou   | 18      |
| \[花邊\] MVP給誰公平？布萊恩：你們丟硬幣決定        | adam7148     | 6       |
| (本文已被刪除) \[ericl1234567\]                     | -            | 27      |
| \[討論\] Rose現在怎麼想？                           | sss631036    | 6       |
| Re: \[專欄\] 15項NBA最難破的紀錄                    | Howl7        | 35      |
| \[討論\] 騎士最近的比賽跟人事是不是都很謎？         | wmigrant     | 28      |
| Re: \[討論\] Rose現在怎麼想？                       | magicbook123 | X2      |
| \[情報\] MVP 賭盤風向吹更大了(鬍迷有福了)           | checktime    | 34      |
| Re: \[討論\] Westbrook是不是已經比KD強了            | ymgs1507     |         |
| \[外絮\] Gobert成1000/1000/200第12人                | monmo        | 33      |
| \[新聞\] 衛少奪MVP？　哈登：贏球才是MVP該做的事     | adam7148     | 98      |
| \[外絮\] Bleacher report將龜龜比喻成快銀            | h1212123tw   | 23      |
| \[討論\] 場均大三元是不是RW生涯顛峰了               | supereight   | 25      |
| Re: \[討論\] 場均大三元是不是RW生涯顛峰了           | djviva       | 26      |
| \[討論\] 今年的騎士二連霸霸業誰能抵抗?              | transformer8 | X1      |
| \[討論\] 場均大三元有助於招募隊友?                  | strmof22     | 9       |
| \[討論\] 如果西河拿MVP會是最弱MVP嗎？               | jessica805   | X1      |
| Re: \[討論\] 如果西河拿MVP會是最弱MVP嗎？           | sweetgold    | X1      |
| (本文已被刪除) \[MrSatan\]                          | -            | 26      |
| Re: \[討論\] Rose現在怎麼想？                       | ddrose       | 27      |
| \[討論\] 從2006/2008年MVP競爭看當季話題性的重要     | dro001       | 24      |
| \[情報\] 騎士的尷尬紀錄                             | saber154     | 22      |
| \[討論\] 重整隊伍該選Curry或Westbrook?              | lcall        | 71      |
| \[討論\] 集全隊之力，下一個可以刷的數據             | RuleAllWorld |         |
| \[討論\] 雷霆教練B.Donovan是不是很有料?             | qk56         | 16      |
| \[情報\] 小皇帝:我不覺得那是個犯規                  | scott6065    | 24      |
| Re: \[討論\] 集全隊之力，下一個可以刷的數據         | sin17        |         |

解釋爬蟲結果
------------

``` r
str(frame)
```

    ## 'data.frame':    120 obs. of  3 variables:
    ##  $ Title  : Factor w/ 113 levels "(本文已被刪除) [MrSatan]",..: 8 2 10 1 9 3 18 12 5 14 ...
    ##  $ Author : Factor w/ 81 levels "-","a11114xy",..: 9 14 4 1 12 14 15 4 5 7 ...
    ##  $ PushNum: Factor w/ 60 levels "","15","18","22",..: 5 15 9 13 17 12 1 8 14 6 ...

``` r
table(frame$Author)
```

    ## 
    ##            -     a11114xy     AAApower    dragon803   Gogoro5566 
    ##            6            1            1            4            1 
    ## gold97972000       HanJie  ilovesumika      Kafziel       Kay731 
    ##            2            1            1            1            1 
    ##    kendiablo        lovea    nomilkman        Rambo      shu2001 
    ##            1            1            1           15            1 
    ##       sinana     wmigrant     zzzz8931     adam7148        Ansel 
    ##            1            2            2            3            2 
    ##     avrild12  Ayanami5566    checktime     CurryMvp       dro001 
    ##            1            1            4            1            2 
    ##   frank47147       Gotham     hhll5566 iam168888888     iimk0918 
    ##            1            1            1            1            1 
    ##        Ivers teddy2261354   tripleaAAA        ttfan       yokann 
    ##            1            1            1            1            1 
    ##         Yui5   bigDwinsch     derekhsu    edison321 fantazy00077 
    ##            1            2            1            1            1 
    ##       feyako   h1212123tw       hungys    jaevastar         LIN9 
    ##            1            2            2            1            1 
    ##   asonge0000 ck0987515477   jay0601zzz    kobeyoung    pttnowash 
    ##            1            1            3            1            1 
    ## RussellWestb      siriusc    ZaneTrout     zzyyxx77    FenixShou 
    ##            1            1            1            2            1 
    ##        Howl7   journeytou     konayuki KyrieIrving1 magicbook123 
    ##            1            1            1            1            1 
    ##        monmo       pneumo       pptdog    sss631036        sthho 
    ##            2            1            1            1            1 
    ##  tiffanycute      tmacor1       ddrose       djviva   jessica805 
    ##            1            1            1            1            1 
    ##        lcall         qk56 RuleAllWorld     saber154    scott6065 
    ##            1            1            1            1            1 
    ##        sin17     strmof22   supereight    sweetgold transformer8 
    ##            1            1            1            1            1 
    ##     ymgs1507 
    ##            1

1 120篇 2Rambo最多

``` r
#這是R Code Chunk
```

覺得爬蟲很有趣很方便，可以馬上找出熱門的文章。
