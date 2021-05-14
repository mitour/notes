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
