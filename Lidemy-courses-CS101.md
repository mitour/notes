# 胡立課程心得-[CS101] 初心者的計概與 coding 火球術

###### tags:`程式筆記` `Lidemy` `Coding 火球術`

## 為什麼要寫程式？

1. 叫電腦做事：下指令
1. 標準化：因為電腦很笨，只懂機器語言
    * C、Ruby、JAVA... ==翻譯官=> 機器語言
1. 邏輯思考：把自己的解法轉變成更「標準化」的格式

* 給你一個亂數的數列，例如說：1, 8, 9, 2, 5 ,4，你能想出什麼步驟把這些數字由小到大排好嗎？

    1. 取出1，小於8, 9, 2, 5 ,4，把1拉出排第一
    1. 取出8，小於9但不小於2
    1. 取出2，小於8, 9, 5 ,4，把2拉出排第二
    1. 取出5，小於8, 9但不小於4
    1. 取出4，小於8, 9, 5，把4拉出排第三
    1. 取出8，小於9但不小於5
    1. 取出9，不小於8
    1. 取出5，小於8, 9，把5拉出排第四
    1. 取出8，小於9，把8拉出排第五
    1. 把9拉出排第六

## 解決問題

1. 逐步拆解
1. 把解法寫成條列式
1. 設立重複點
1. 設立結束點，返回解答
1. 帶入變數

* 把上述問題再試一次
    1. 比較第一個是否比第二個小，如果不是排最後，跳到第7步
    2. 比較是否比第三個小，如果不是排最後，跳到第7步
    3. 比較是否比第四個小，如果不是排最後，跳到第7步
    4. 比較是否比第五個小，如果不是排最後，跳到第7步
    5. 比較是否比第六個小，如果不是排最後，跳到第7步
    6. 將第一個取出，放入新陣列
    7. 重複步驟

* 並進一步運用，目前想到最好的解法：

    1. 假設n是第1個，i是第n+1個，length是陣列長度
    2. 如果n=0跳到第七步
    3. 比較n是否小於等於i，如果不是排最後
    4. 把i+1
    5. 重複第二步，如果i大於（等於）length，跳到第六步
    6. 把n取出放新陣列，重複第二步
    7. 結束

> 實作之後發現這個最好的解法真是爛透了:cry:
![程式碼](https://i.imgur.com/U5jIi0J.png)

延伸閱讀：[淺談 JS sort() 到背後排序方法](https://medium.com/@leokao0726/%E6%B7%BA%E8%AB%87-js-sort-%E5%88%B0%E8%83%8C%E5%BE%8C%E6%8E%92%E5%BA%8F%E6%96%B9%E6%B3%95-1035f5b8cde8)

## command line

### 常用指令

* pwd我在哪
* ls
* cs
  * .. 上一層
  * . 本層
  * ~ 使用者home目錄
  * / 根目錄
* touch
* mkdir
* rm
* rmdir
* cp file copyfile
* mv
  * 移動
  * 重新命名
* man
  * q 離開
* homework:
![homework](https://i.imgur.com/EygNoEI.png)
* date
* top (table of processes):印出全部工作
* cat (catenate)連接檔案/印出檔案內容
* less 新視窗顯示檔案內容
* grep 抓取檔案關鍵字
  * grep if test.js
* echo 印出字串

### command-line 組合技

* |(pipe)
  * cat file.txt | grep hi
* \>(redirect)
  * date > time.txt

## 二進位

### 逢二進位

> 世界上只有 10 種人，懂二進位和不懂二進位的

### 16進位，逢16進位

#### rgb(R, G, B)

1. rgb(255, 0, 0)正紅，16進位表示為#FF0000
2. rgb(0, 255, 0)正綠，16進位表示為#00FF00
3. rgb(0, 0, 255)正藍，16進位表示為#0000FF

### homework

#### 試著把 27, 32, 100 轉成二進位

1. 27 = 16 + 8 + 2 + 1 = 11011
2. 32 = 32 = 100000
3. 100 = 64 + 32 + 4 = 1100100

## 儲存空間單位

* bit:最小單位，只能儲存 0 跟 1
* byte = 8 bit
* kb = 2^10 = 1024 byte
* mb = 1024 kb
* gb = 1024 mb
* tb, pb, eb...

## 數字儲存

### 正整數

通常數字用 32bit(4byte) 儲存，每 1bit 表示 0 或 1，故有 2^32 種情形

### 負整數

#### 將正數所有為元顛倒後 +1

![範例](https://i.imgur.com/BysbfA6.png)

##### 好處

* 頭一個 bit 代表正負
* 方便計算
  * 假設最多儲存 8bit 的前提下，兩數相加等於 0，多出的 1 為溢位
![二進位正負數相加](https://i.imgur.com/WI2SyPJ.jpg)
* 能表示的範圍：-2^31 到 2^31-1 之間，也就是 -2147483648 ~ 2147483647

### 小數

> 有限的空間不可能儲存無限的小數

依據 [IEEE754 標準](https://www.wikiwand.com/zh/IEEE_754)，
頭 1bit(藍區) 為符號位，後 11bit(綠區) 為指數域，餘 52bit(紅區) 為小數域，只儲存小數點後的位數
> 這邊是用 64位元精準度(double)，如果是 32位元精準度 (float)，則各佔 1, 8, 23bit

![IEEE754](https://i.imgur.com/T5JuZeq.png)
將每一小數寫成固定格式：0.00000853 = 0.853 * 10^(-5)

[延伸閱讀-使用浮點數最最基本的觀念](http://blog.dcview.com/article.php?a=VmhQNVY%2BCzo%3D)

## 網路基礎概論

* IP：由四個 0~255 數字組成，例如：203.211.0.39
* 域名：比 IP 好記，例如：google.com
* DNS(Domain name system)：就像是電話簿，紀錄 IP 對照到域名
  * 8.8.8.8 由 google 提供的免費 DNS，亦可同時搜集使用者愛好
* 前端後端
![前端後端](https://i.imgur.com/AExaGWW.jpg)

## 內網與外網

從外部看，大家的 IP 都一樣，從內部看有虛擬 IP 區分
![內網與外網](https://i.imgur.com/Q3Ny1fi.png)

### VPN

![VPN](https://i.imgur.com/q6Kblkd.png)

## session 與 cookie

session id 就是一張有期限的識別證，只認識別證，不認人
![登入流程](https://i.imgur.com/276z88H.jpg)

## 了解瀏覽器

* HTML 是框架、身體，CSS 是外觀、衣服，JavaScript 則是程式與互動
* 瀏覽器：把 HTML, CSS, JavaScript 解析成網頁
* HTML 都一樣，但 CSS 不同 [CSS 之美](http://www.csszengarden.com/)
* 實際看看：開發人員工具 > network > cookie

## 資訊安全

* DoS：有人一直發 request 讓伺服器沒辦法處理別人的 request
* DDoS：有很多人一直發 request，通常會用木馬程式
* 木馬程式：等於在你的電腦裡開了一個後門，駭客可以裝鍵盤側錄器紀錄帳號密碼、用你的電腦當跳板、DDoS
* 暴力破解：一直試
  * 字典檔，常見密碼組合

## 資料庫簡介

### Structured Query Language

* 查詢
  * **SELECT** phone **FROM** users **WHERE** name=peter
* 刪除
  * **DELETE FROM** users **WHERE** name=peter
* 更新
  * **UPDATE** users **SET** phone=123 **WHERE** name=peter
* 新增
  * **INSERT INTO** users(name,phone) **VALUES** (peter, 1234)

## 儲存密碼的正確方式

### 雜湊函數

> 哈希（Hash）算法就是单向散列算法，它把某个较大的集合P映射到另一个较小的集合Q中，假如这个算法叫H，那么就有Q = H（P）。对于P中任何一个值p都有唯一确定的q与之对应，但是一个q可以对应多个p。
> ——[密碼破解之王](http://www.ha97.com/4009.html)

* md5：將輸入的密碼加密，但無法從輸出導出輸入，一般要破解就是用暴力破解或是查字典。
* 加鹽(salting)：自動幫密碼加上一段亂數後才進行 md5 加密，確保不易被破解。
* SHA256：較 md5 更安全的雜湊函數，但也較慢。
* [線上加密/破解密碼](https://www.cmd5.com/)

## 其他常見攻擊手法

### 讓輸入變成程式碼的一部分

* SQL injection
![SQL injection](https://i.imgur.com/iOQin9L.jpg)
* XSS(cross site scripting)：運用 HTML Tag (像是`<script>`)讓其他使用者傳輸敏感資料給攻擊者
  * 小遊戲：[XSS-game](https://xss-game.appspot.com/)

### 解法：過濾使用者輸入

> 請千萬不要嘗試建立黑名單過濾，你可以參觀 [XSS Cheat Sheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet) 這個網站，就會知道有非常多形式可以讓瀏覽器去執行腳本程式。因此最簡單又保險的方式，就是全部逸出。例如將`<script>`變成`&lt;script&gt;`
> —— [Rails 實戰聖經](https://ihower.tw/rails/security.html#sec0)

* 前後端都做資料欄位過濾
  * 前端：沒必要傳送無意義請求
  * 後端：**一定要過濾**，有些工具可以跨過前端，畢竟前端 code 是公開可見的

## 參考

[[偷米騎巴哥]帶你認識XSS攻擊手法](https://www.youtube.com/watch?v=MMMkvHwqPRY)
{%youtube MMMkvHwqPRY %}

## 程式是什麼

[什麼是「組合語言」？](http://it-easy.tw/assembly-language/)

1. 機器語言：1 和 0，電腦只看得懂機器語言
1. 組合語言：需經組譯器翻成機器語言，具有機器依存性
1. 高階語言(High-Level Language)：須經由編譯器翻成組合語言，不具有機器依存性，但無法跨作業系統
   1. 程序導向語言(Procedure-Oriented Language)
   1. 物件導向語言(Object-Oriented Language)：抽象化、多次使用
1. 自然語言(Nature Language)

### 逆向工程簡介

> 既然可以從程式碼變成機器看得懂的語言，當然就可以「逆向」回來 把機器碼變成看得懂的語言，這個就叫做**逆向工程**
>
> 逆向以後你甚至可以修改程式，把某些地方改成你想要的樣子，改完之後再重新翻譯回去，就變成破解版的程式了

* 無視帳號密碼
* 序號產生器

#### 理論歸理論，實際上沒有這麼容易

* 定時驗證機制...

### 程式語言

#### 你在哪個領域，就需要會哪個領域的與言

[小測驗：我幾乎不會Orz](http://helloworldquiz.com/)

* C：能暸解程式底層運作
* C++：比 C 多了物件導向
* JAVA：跨平台
* JvaScript：近期發展到可以在瀏覽器外執行
* Python：分析、網頁、小工具，初心者友善
* ...

## 演算法 Algorithm

[人腦也可以執行演算法 - David J. Malan](https://youtu.be/6hfOvs8pY1k)
{%youtube 6hfOvs8pY1k %}

> 解決問題的方法，輸入到輸出中間的過程

### 哪一個演算法比較好？

* 時間複雜度：一個演算法要花多少時間找出答案？
* 假設一串數目為 n 數列要找出一個數字是否存在數列中，時間複雜度為 O(n)
![Big-o](https://i.imgur.com/TJ2XHYV.png)

#### 時間與空間的拉扯

* 空間換取時間：建立中繼的表格，時間複雜度較低，但須花空間儲存表格
* 如果有排序：終極密碼，從中間開始猜，也就是**二分搜尋法**

#### 不同面向的考量

* 時間花費少
* 空間花費少
* 正確率較高
* 相容率較高
* 開發成本低

##### 根據需求不同，找出其中的平衡

* 例如：美國人口普查
* 量級問題：n 的大小影響著演算法的好壞
  * 每天給你 100 元跟第一天給 2 元第二天給 4 元第三天給 8 元...
  * 即 100n 跟 2^n

## 排序演算法

* [VisuAlgo](https://visualgo.net/en)
* 選擇排序：選擇最小的往左
* 泡沫排序：兩兩比較大的往右
* 插入排序：撲克牌
* 合併排序：切割成小數列排完之後合併
* 快速排序：挑選基準點(povit)，讓基準左邊比較小，右邊比較大，在兩邊分別挑基準點

### homework

#### 你能夠寫出泡沫排序法的步驟嗎？就像我們在 1-2 介紹過的那樣，一步一步寫出來

1. 假設 n = 0, swapped = false
2. 如果 n 比 n+1 大，兩者互換位置，swapped = true
3. 把 n = n+1
4. 如果 swapped = true，重複步驟 1
5. 結束

## Scratch

![Scratch](https://i.imgur.com/LbKBJtb.png)

[均一教育平台-Scratch玩程式](https://www.junyiacademy.org/computing/programming/scratch)
