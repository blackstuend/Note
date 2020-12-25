# Cookie Session localStorage SessionStorage 差別


## Cookie
* 稱為小餅乾，大小只能存取4KB以內，存在於瀏覽器，每一次client發送request會順便將cookie也發送到伺服器，每個瀏覽器的cookie不共用
* 通常都會設定何時過期失效


## Session
* Session是另一種記錄客戶狀態的機制，不同的是Cookie保存在客戶端瀏覽器中，而Session保存在伺服器上。客戶端瀏覽器訪問伺服器的時候，伺服器把客戶端信息以某種形式記錄在伺服器上
* 每一次有不同的client端發送請求則會在伺服器先產生一個sessionid來記錄，然後在回應這個sessionid給client端，client則會將session存在cookie內
* 因為session存在於cookie，所以當cookie被client禁用時，則session也會跟著失效，需要特別注意
* 當client越來越多，Session也會越多，所以建議設定過期時間，或是使用redis存在別的地方，而不是單純存在server上，會使得速度越來越慢

## LocalStorage
* localStorage 是 HTML5 提供的一個 API，他本質上是一個hash（哈希表），是一個存在於瀏覽器上的 hash（哈希表）
* 生命週期為永久的，只存在於client端，大小為5MB


## SessionStorage
* 跟localStorage極為相似，最大也是為5MB，差在生命週期為關閉瀏覽器即消失
* 跟上面的Session不同，Session是存在於cookie，之前一直看一些文章，一直看到session存在於cookie，想不透sessionstorage名字都有session為何不是存session，結果他是不一樣的東西!!

基於網路上常見的表

特性          | Cookie  | localStorage | SessionStorage
--------------|:-----:|----------------:| ------------:
生命週期   | 自行設定失效時間 |  永久 |    關閉頁面或是瀏覽器 
大小    | 4KB |  5MB  | 5MB
與SERVER溝通  | 每一次發送request | 僅存在client端 | 僅存在client端  

參考資料:https://kknews.cc/zh-tw/code/e6zebry.html<br>
參考資料:https://jerryzou.com/posts/cookie-and-web-storage/