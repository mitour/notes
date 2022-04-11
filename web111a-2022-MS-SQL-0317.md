# MS-SQL

###### tags: `程式筆記` `web111a` `MS-SQL`

* **老師：許志強**
* 時間：2022/3/17

## 課程相關軟體環境建置

* 學習重點：
  * 後端框架：[ASP.NET](https://ithelp.ithome.com.tw/questions/10000993#:~:text=%E8%87%B3%E6%96%BCASP.NET%E6%98%AF%E4%BB%80%E9%BA%BC%E6%A8%A3%E7%9A%84%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80%EF%BC%8C%E7%B0%A1%E5%96%AE%E7%9A%84%E8%AA%AA%EF%BC%8C%E4%BB%96%E6%98%AF%E7%B6%B2%E7%AB%99%E5%BE%8C%E7%AB%AF%E7%9A%84%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80%EF%BC%8C%E7%94%A8%E4%BE%86%E9%96%8B%E7%99%BC%E5%8B%95%E6%85%8B%E7%9A%84%E7%B6%B2%E9%A0%81%EF%BC%8C%E4%BE%8B%E5%A6%82%E7%95%99%E8%A8%80%E7%89%88%E3%80%81%E9%83%A8%E8%90%BD%E6%A0%BC%E9%80%99%E4%BA%9B%E9%9C%80%E8%A6%81%E5%BE%9E%E8%B3%87%E6%96%99%E5%BA%AB%E6%92%88%E5%8F%96%E8%B3%87%E6%96%99%EF%BC%8C%E7%94%A2%E7%94%9F%E5%87%BA%E5%85%A7%E5%AE%B9%E7%9A%84%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80%E3%80%82%E5%8F%A6%E5%A4%96%E5%83%8F%E6%98%AFPHP%E3%80%81JSP%E9%80%99%E4%BA%9B%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80%EF%BC%8C%E4%BB%96%E5%80%91%E7%9A%84%E6%80%A7%E8%B3%AA%E5%B0%B1%E5%92%8CASP.NET%E7%9B%B8%E4%BC%BC%EF%BC%8C%E5%8F%AA%E6%98%AF%E4%B8%8D%E5%90%8C%E7%9A%84%E9%96%8B%E7%99%BC%E5%85%AC%E5%8F%B8%E6%88%96%E7%A4%BE%E7%BE%A4%E6%89%80%E6%8F%90%E4%BE%9B%E3%80%82)
  * database: SQL server 2019
  * 程式語言：C#(OOP)
  * 開發工具：visual studio 2019, visual studio 2019 core
* 環境建置
  * 截圖：Green Shot
    * 中文支援
    * 免費
    * 輕量
    * 功能強大
  * 錄影：Camtasia Studio
    * 長期試用依記事本說明操作，版權問題不放
    * 異常：有聲音沒畫面，需透過解碼器解碼
  * 照片播放軟體：irfanview
  * 影片播放：potplayer
    * 可節錄重點、AB段
  * 電子書：Cyber article
    * 付費軟體，有教學授權，版權問題不放
    * 製作系統操作手冊用
  * 心智圖：Xmind
    * 應用廣泛：會議記錄、年度規劃、組織圖、系統架構等...
  * 流程圖：Draw.io
  * 問題反應：Trello

---

## 環境建置及基本操作

* **老師：許志強**
* 時間：2022/3/22

### SQL server 2019

#### for windows

* 參考老師影片

##### 資料庫驗證

![資料庫驗證](https://i.imgur.com/iKuyYpw.jpg)

* windows 驗證：使用登入 windows 的帳號、密碼
* ==建議使用== 混合模式：自己在設定 DB user 的帳號、密碼
  * 預設請使用：**教室wifi密碼**以方邊除錯用

##### SQL Server 管理員

* 請使用 administrator 作為一但忘記驗證密碼的備案

#### [install SQL server on Mac](https://leburger.gitlab.io/posts/mssql-2019-azure-data-studio-mac/)

##### Homebrew

是一款自由及開放原始碼的軟體套件管理系統，用以簡化macOS系統上的軟體安裝過程

##### Docker

可以將應用程式快速地部署到各種環境並加以擴展，而且知道程式碼可以執行。

Docker 包括三個基本概念：[Docker——從入門到實踐](https://philipzheng.gitbook.io/docker_practice/)
* 映像檔（Image）
* 容器（Container）
* 倉庫（Repository）

> Docker 想解決的問題：
> 改善傳統虛擬機器因為需要額外安裝作業系統（Guest OS），導致啟動慢、佔較大記憶體的問題
>  
> Docker 要提供的解法：
> 以應用程式為核心虛擬化，取代傳統需要 Guest OS 的虛擬化技術
> [from Docker 使用教學](https://cwhu.medium.com/docker-tutorial-101-c3808b899ac6)

##### Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?

[[解決方法] mac 作業系統上無法使用 docker](http://andy51002000.blogspot.com/2021/02/mac-docker.html)

:::info
~~測試不可行，似乎目前版本存在 bug...~~

```bash=
This is a known VirtualBox bug. Let's try to recover anyway...
Error creating machine: Error in driver during machine creation: Error setting up host only network on machine start: The host-only adapter we just created is not visible. This is a well known VirtualBox bug. You might want to uninstall it and reinstall at least version 5.0.12 that is is supposed to fix this issue
```
:::

:warning:3/23更新：
雖然不太理解原因，但改安裝 [docker desktop](https://www.docker.com/products/docker-desktop/)，又可行了，個人推測是sudo

###### Pull Image

```bash=
sudo docker pull mcr.microsoft.com/mssql/server:2019-latest
```

###### Run the container

透過容器，應用程式不需要再另外安裝作業系統（Guest OS）也可以執行。

```bash=
docker run -d --name sql_server_demo -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=<PASSWORD>' -p 1433:1433 mcr.microsoft.com/mssql/server:2019-latest
```

###### sql-cli

* npm（全稱 Node Package Manager，即「node套件管理器」）是Node.js預設的、用JavaScript編寫的軟體套件管理系統。

```bash=
npm install -g sql-cli
```

###### connect to SQL server

```bash=
mssql -u sa -p <PASSWORD>
```

###### 參考影片

{%youtube glxE7w4D8v8 %}

### SSMS

連線時使用 localhost/127.0.0.1 有可能連不到，因為會被判定為遠端連線，而被防火牆擋住

![connect issue](https://i.imgur.com/4Mr8Dbf.png)

#### 設定防火牆

* 參考老師影片

1. 開 port 1433
2. 允許 sqlserver.exe
3. 允許 sqlbrowser.exe
4. 允許 ssms.exe
5. 設定網路組態

#### for Mac

> 在 SSMS 沒有支援 Mac 的情況下，我們可以微軟開發的 Azure Data Studio 進行連結。

```bash=
brew cask install azure-data-studio
```

* 中文介面：cmd+shift+P，輸入 configure display language

### 資料庫操作

#### 移動資料庫

* 資料庫及log需存在同一路徑
* 如想要移動資料庫檔案，需
  * 工具>卸離資料庫，要用再資料庫>附加回去
  * ==建議使用==工具>離線工作
  * stop server
* 移動資料庫遇到存取被拒問題
  * ![存取被拒](https://i.imgur.com/eJpDlid.jpg)
  * 手動加權限，內容>安全性>群組或使用者>編輯>新增Everyone
  * 或手動啟用繼承，內容>安全性>Everyone的權限>進階>變更權限>取用繼承

#### 正式資料庫與測試用資料庫

* 同名不可以同時掛，需將測試用資料庫**附加為**別的名字，例如：demo_alpha

#### 重新命名資料庫（資料庫複製）

* 都需要SQL Server Agent執行中
* 工作>複製資料庫>改名>重新掛，再將舊的刪掉

#### 卸離與附加

#### 使用 SQL 物件管理方法

#### 備份還原

##### 離線備份

卸離、離線工作屬於離線備份

##### 線上備份

一般而言都是線上備份

* 工作>備份
* 備份類型：完整、差異、交易紀錄(log)

##### 還原

* 工作>還原>裝置>
  * 一般>檔案位置
  * 檔案>確認路徑
  * 選項>覆寫
    * 完整：restore with recovery
    * 差異：restore with standby

---

* **老師：許志強**
* 時間：2022/3/23

### 定時排程備份

* 需確認SQL Agent是否執行中，控制台>系統管理工具>服務
* 維護計畫
  * 子計畫>頻率
  * 工具箱>維護計畫工作>備份資料庫工作
* 記得存檔、記得存檔、記得存檔

### 備份檔規劃 TSQL

> Transact-SQL是具有批次與區塊特性的SQL指令集合，資料庫開發人員可以利用它來撰寫資料部份的商業邏輯（Data-based Business Logic），以強制限制前端應用程式對資料的控制能力。
> 它是用來讓應用程序與SQL Server溝通的主要語言。

* 方便找尋及管理備份檔
* 例如：dbbackup\demo\2022\03
* 使用 T-SQL，簡單來講分為以下步驟，程式碼如下
  1. 開權限 xp_cmdshell=1
  2. 備份 BACKUP DATABASE
  3. 關權限 xp_cmdshell=0
* 維護計畫
  * 子計畫>頻率
  * 工具箱>維護計畫工作>執行T-SQL陳述式
* 記得存檔、記得存檔、記得存檔

```sql=
use [master]
-- 開啟 xp_cmdshell
EXEC sp_configure 'show advanced options', 1;
GO
RECONFIGURE;
GO
EXEC sp_configure 'xp_cmdshell', 1;
GO
RECONFIGURE;
GO 

--宣告變數
DECLARE @FolderName nvarchar(250) = 'D:\dbbackup'
DECLARE @DataBaseName nvarchar(250) = 'demo'
DECLARE @JobName nvarchar(250) = 'demo 資料庫備份'
DECLARE @FileName nvarchar(250)
DECLARE @FileDate nvarchar(250)
DECLARE @Command nvarchar(250)

--取得日期變數 , 例 2013-01-01 12:30:40.001
SET @FileDate = CONVERT(NVARCHAR(250), GETDATE(), 121)

--除去日期變數中的 - : . 符號 , 例 20130101_123040_001
SET @FileDate = REPLACE( @FileDate , '-' , '' )
SET @FileDate = REPLACE( @FileDate , ':' , '' )
SET @FileDate = REPLACE( @FileDate , '.' , '_' )
SET @FileDate = REPLACE( @FileDate , ' ' , '_' )

--設定備份目錄,並自動以年、月建立目錄
SET @Command = 'mkdir ' + @FolderName
EXEC xp_cmdshell @Command, no_output

SET @FolderName = @FolderName + '\' + @DataBaseName
SET @Command = 'mkdir ' + @FolderName
EXEC xp_cmdshell @Command, no_output

SET @FolderName = @FolderName + '\' + SUBSTRING(@FileDate , 1 , 4)
SET @Command = 'mkdir ' + @FolderName
EXEC xp_cmdshell @Command, no_output

SET @FolderName = @FolderName + '\' + SUBSTRING(@FileDate , 5 , 2)
SET @Command = 'mkdir ' + @FolderName
EXEC xp_cmdshell @Command, no_output

--設定檔案名稱 , 例 D:\db\2012\dbbackup\dbtest\2013\01\20130101_123040.bak
SET @FileName = @FolderName + '\' + SUBSTRING(@FileDate , 1 , 15) + '.bak'

--執行備份作業
BACKUP DATABASE @DataBaseName TO DISK = @FileName WITH NOINIT , NOUNLOAD , NAME = @JobName , NOSKIP , STATS = 10, NOFORMAT

-- 關閉 xp_cmdshell
use [master]
EXEC sp_configure 'show advanced options', 0;
GO
EXEC sp_configure 'xp_cmdshell', 0;
GO
RECONFIGURE;
GO 
```

### 備份異常alert

#### Email

##### 建立操作員

* SQL Server Agent > 操作員

##### 設定gmail smtp

* 不需自架 Mail Server，運用 Gmail SMTP(寄)/POP3(收)
* 需有帳號及應用程式密碼
  * 基於資安考量，需有兩段式驗證過才能取的應用程式密碼
  * ![應用程式密碼](https://i.imgur.com/i2fLZs5.png)
* 管理>SQL Server 紀錄檔> database mail
* 記得存檔、記得存檔、記得存檔

##### 通知操作員工作

* 成功
* 失敗
* 完成

#### Line

##### Line Notify

* 先安裝老師自己寫的程式
* token
  * 1:1個人
  * 群組：將 Line Notify 邀請進群組，token 需要重產生一組對群組的
  * ![token](https://i.imgur.com/tMYcYrQ.png)

* 簡單流程：SQL Server > DOS > Line
* 維護計畫：大致與 email 相似，只是通知部分仍由 TSQL 陳述式，透過 DOC 讓 line 發通知，程式碼如下
  * 備份
  * 通知

```sql=
use [master]
-- 開啟 xp_cmdshell
EXEC sp_configure 'show advanced options', 1;
GO
RECONFIGURE;
GO
EXEC sp_configure 'xp_cmdshell', 1;
GO
RECONFIGURE;
GO 

--宣告變數
DECLARE @FolderName nvarchar(250) = 'C:\linenotify'
DECLARE @ExecuteName nvarchar(250) = 'LineNotify.exe'
DECLARE @TokenName nvarchar(250) = <TOKEN GOES HERE>
DECLARE @MessageName nvarchar(250) = 'demo 資料庫備份失敗'
DECLARE @Command nvarchar(500)

SET @Command = @FolderName + '\' + @ExecuteName + ' ' + @TokenName + ' "' + @MessageName + '"'
EXEC xp_cmdshell @Command, no_output


-- 關閉 xp_cmdshell
use [master]
EXEC sp_configure 'show advanced options', 0;
GO
EXEC sp_configure 'xp_cmdshell', 0;
GO
RECONFIGURE;
GO 
```

### 異地備援

#### Google Drive

![google drive](https://i.imgur.com/8tK2Yzc.png)

* 使用 Google Drive 桌面軟體
* 將 /dbbackup 勾選與雲端硬碟保持同步

#### MEGA

---

## SQL Practice

* **老師：洪福成**(代課)
* 時間：2022/3/24

:::info

### 案例分享

一間公司員工老是抱怨電梯太慢，老闆於是開會討論是否真的慢，因為老舊？換新的能解決？預算問題等等。
此時就有一位員工出面說：我有一個不用花很多錢的方法，也許我能試著解決看看。
老闆也就同意了。
過一陣子確實沒有再聽到抱怨電梯太慢的問題。
待老闆實際到電梯口查看，發現該員工在電梯旁裝上一面全身鏡。
原來員工等電梯的同時整理儀容，也就忘了等待的時間有多漫長。
:::

### SQL 查詢

#### 語法

```sql=
SELECT 欄位1, 欄位2
FORM table1 JOIN table2
WHERE -- 在 group by 前的條件（搭配LIKE/AND/OR）
GROUP BY -- 群組化
HAVING --在 group by 後的條件
ORDER BY --排序，永遠下在最後
```

#### 範例

* 模糊查詢

```sql=
SELECT * FROM employee WHERE name LIKE '陳%'
```

* Top 10

```sql=
SELECT TOP 10 * FROM employee ORDER BY salary DESC
```

* 群組化：各縣市客戶家數

```sql=
SELECT city, COUNT(*) 家數 --通常有用count都會group by
FROM customer
GROUP BY city
ORDER BY city
```

* 欄位內容篩選，還有很多依需求去搜尋
  * LEFT(num, 3)
  * DATEADD(YEAR, 40, birthday)

```sql=
SELECT LEFT(num, 3) AS class, COUNT(*) AS amount
FROM students
GROUP BY LEFT(num, 3)
ORDER BY class
```

* 某些情況下，`HAVING` 可以放在 `WHERE` 中（用 `AND` 連接）

```sql=
SELECT LEFT(班級座號, 3) AS 班級,
  SUM(事假) AS 事假,
  SUM(病假) AS 病假,
  SUM(公假) AS 公假,
  SUM(曠課) AS 曠課
FROM RECORDS
WHERE 年月日 LIKE '9003%' AND LEFT(班級座號, 3) >= 104 AND LEFT(班級座號, 3) <= 107
GROUP BY LEFT(班級座號, 3)
-- HAVING LEFT(班級座號, 3) >= 104AND LEFT(班級座號, 3) <= 107
ORDER BY LEFT(班級座號, 3)
```

### 練習題

:::info

* 留意沒有唯一解
* 反白可以做區域執行

:::

* 找出年齡大於40歲

```sql=
SELECT 學號, 
       姓名, 
       出生年月日, 
       DateAdd(YEAR, 40, 出生年月日) AS 滿40歲生日
FROM STUDENTS
WHERE DateAdd(YEAR, 40, 出生年月日) < GETDATE()
-- 生日+40年要大於今天
ORDER BY 出生年月日
```

---

* **老師：洪福成**(代課)
* 時間：2022/3/25

### Practice

* 指名要撈1180024資料庫，如果是英文開頭就可以不用`[]`，命名原則上，有會比就易懂

```sql=
use [1180024]
```

* 子查詢
* ORDER BY 不能放在子查詢中

### Addition / HW: Practice SQL

* [datacamp](https://www.datacamp.com/courses/introduction-to-sql)

{%youtube gvRXjsrpCHw %}

---

## 創建資料表

* **老師：許志強**
* 時間：2022/3/28

### Naming rules

1. 不可數字開頭，不可空格，要的話需要以`[]`包住
2. 建立新資料表要重新整理、重新整理、重新整理

#### Naming styles

1. 名稱在前，分類在後
2. 簡稱
3. 駝峰式
4. 底線
5. is開頭

#### Primary key

#### 流水式命名 auto-increment

1. 識別規格：是
2. 為識別：是
3. 欄位設定主索引鍵
4. 資料類型為`int`

#### GUID

> 通常表示成32個16進位數字（0－9，A－F）組成的字串，如：{21EC2020-3AEA-1069-A2DD-08002B30309D}

1. 資料類型為`uniqueidentifier`
2. 資料表設計工具>rowGUID：是
3. 欄位設定主索引鍵
4. **型別也可以改成`varchar`，重點在於預設值有call `newid()`**

* GUID 為建立資料後產生，如需立刻看到可以手動「執行SQL」

#### 選擇障礙？

|方法| 流水式 | GUID |
|--| -------- | -------- |
|用途| 多數案例使用 | 注重前後關係 |
|範例|一般主檔、交易檔 | 簽核檔 |

:::info
**資料類型不允許儲存變更**

工具>選項>設計師>取消勾選「防止儲存需要資料表重建的變更」
:::

### 欄位資料類型

* 表格內僅列舉部分，常用部分粗體表示

| 文字 | 整數數字 | 小數數字 | 日期 |
| ---- | ------ | -------- | ---- |
| Char |**int** | **decimal** | date  |
| **VarChar**  |**bit**    | float   | time  |
| NVarChar |bigint |  money | **datetime** |

#### Char

* 缺點：易出現搜尋錯誤狀況

![char](https://i.imgur.com/UDC3XYm.png)

#### VarChar

![VarChar](https://i.imgur.com/u6dGegL.png)

#### NVarChar

* 支援多國語系

![NVarChar](https://i.imgur.com/amMsVoj.png)

#### 數字

* bit, int 不用列長度
* decimal 需要列出長度
  * decimal[ ( p[ , s] ) ]
  * p (有效位數)
  * s (小數位數)
  * 例如：25.99 --> `decimal(2, 2)`

#### 時間

* datetime：日期
* smalldatetime：日期+時間

#### NULL

* 必填欄位

### Import Data

以[郵遞區號 3+2](https://www.post.gov.tw/post/internet/Download/index.jsp?ID=2292)為例

---

## 資料庫索引

* **老師：許志強**
* 時間：2022/3/31

### Import Data

* 以[郵遞區號 3+2](https://www.post.gov.tw/post/internet/Download/index.jsp?ID=2292)為例
* 先用 excel 做資料整理
  * copy + paste
    * 資料表不用 SELECT id
    * 不用`id`欄
  * BULK INSERT(CSV)
    * 留意`id`欄位也需要

:::info

## 肺腑之言

### 想當soho?

* domainKnowHow
  * 該領域的所有專業知識
  * 例如：會計系統需要懂稅務知識等等。
* SA/SD

### 鋪好退休之路

* 年輕人只有肝
  * 趨勢：ERP
* 斜槓
* 客座講師為例
  * $600/hr，最多 80hrs/month，粗略地說是月休四天月薪四萬
  * 責任少，不用招生又場地、設備都有了
  * 教到老
  * 可以接不只一個場
* 能力不夠要會濠洨
:::

### 目的

增加速查詢速度

![index](https://i.imgur.com/DxGnOP0.png)

### 叢集索引(Clustered Index)

* 叢集索引將資料表或檢視中的資料列**依其索引鍵值排序與儲存**
* 一個資料表只能有一個叢集索引
* 如果資料表沒有任何叢集索引，它的資料列就儲存在未排序的結構中，這個結構稱為堆積。

### 非叢集索引(NonClustered Index)

* 速度比叢集索引慢
* 哪一個欄位容易被作為查詢條件，例如：
  * :heavy_check_mark: 編號
  * :heavy_check_mark: 名稱
* 順序，以上例
  * 編號不會重複沒有必要放優先
  * 故先比對名稱如果重複，再比對編號

> 指不管資料在原本資料表中的排序，而在索引表中自己依照索引值建立排列。與叢集索引的差別是，叢集索引的排列順序就是實際上資料的排列順序，而非叢集索引的排列順序不會/無法影響到實際資料的排列順序。也因此，一個資料表中可以包含很多非叢集索引。
> [FROM Rails 效能優化](https://medium.com/@jinghua.shih/rails-%E7%B6%B2%E7%AB%99%E6%95%88%E8%83%BD%E5%84%AA%E5%8C%96-%E4%BA%8C-%E8%B3%87%E6%96%99%E5%BA%AB%E7%B4%A2%E5%BC%95-database-index-bd89fa3757a)

## 關聯式資料管理系統(RDBMS)

* 強調資料的關聯性
* Foreign key

### 誰關聯？（建議作法）

* 與主檔關聯用編號(NO.)
  * 客戶檔[客戶編號]->訂單[訂單編號]
  * 如果客戶被誤刪資料，`id` 有可能會變
* 與表單關聯用`id`
  * 訂單主檔[`id`]->訂單明細檔[訂單編號]
  * 因為訂單編號可能不是唯一，例如：分公司共用系統

### 建立關聯

* 用交易檔去關聯主檔，例如：[訂單檔]->[客戶檔]

---

## 資料庫正規化

* **老師：許志強**
* 時間：2022/4/6

### 目的

* 避免資料重複
* 增加查詢速度

### 作法

* 一階正規劃～六階正規劃(1NF~6NF)
* 實務上只會做到3NF

![normalization](https://i.imgur.com/KG9sLP8.png)

1. 列出所有欄位（參考網路）
2. 找出唯一值
3. 各欄位與關鍵欄位比較判定相關
   1. 1:1絕對相關
   2. 1:多相對相關
4. 相對欄位獨立出去
5. 刪除相對欄位

![3NF](https://i.imgur.com/xHFmImB.jpg)

### 課堂作業

![practice](https://i.imgur.com/eb7nndT.png)

### 欄位命名原則

#### follow the rules

#### create the rules

#### 例如

* 主檔(m_no, m_name...)
* 單據(sheet_no, sheet_name...)
* 性別(gender_code)內容會固定
  * 1(男)
  * 2(女)
  * 3(其他)

### 資料表命名

![table naming](https://i.imgur.com/D5TDbA1.png)

* (銷售類_銷售_主檔)sal_sale_master
* (基本資料_產品檔)bas_product

### 建立索引

### 外部鍵

* 資料庫圖表
  * 描述
  * 手動調整關聯線（非必要）

## T-SQL syntax

![sql](https://i.imgur.com/77ahXBO.png)

### 切換資料庫

```sql=
USE [master]
GO
```

---

* **老師：許志強**
* 時間：2022/4/11

### CRUD

> 增刪查改（英语：CRUD），全稱增加（Create，意為「建立」）、刪除（Delete）、查詢（Read，意為「讀取」）、改正（Update，意為「更新」）

### `SELECT`

```sql=
SELECT * FROM <database>
```

### 條件式 `WHERE`

* 當資料為連續時，用`BETWEEN/AND`效率優於`>A AND <B`

```sql=
SELECT * FROM pur_purchase_d
WHERE amt BETWEEN 200 AND 5999
```

* 複選`IN`

```sql=
...
WHERE mno IN ('D01', 'D02', 'D04')
```

* 模糊查詢`%`

```sql=
...
WHERE mname LIKE '%豬排%'
```

* 群組完後的條件`HAVING`

```sql=
...
SUM(qty) FROM pur_purchase_d
GROUP BY mno
HAVING SUM(qty) > 30
```

### 排序 `ORDER BY`

* 永遠擺最後一行
* 中文依筆畫排序

### 群組 `GROUP BY`

* 用以合計、加總、平均

### 聯集 `JOIN`

#### 搞清楚目的

* `INNER JOIN`:兩邊同時有資料才撈的到
* `LEFT (OUTER) JOIN`:保證左邊全部撈的到
* `RIGHT (OUTER) JOIN`:保證右邊資料全部撈的到
* `FULL (OUTER) JOIN`:兩邊都撈的到
* `CROSS JOIN`:左右相乘，不需關聯`ON`
  * ![CROSS JOIN](https://i.imgur.com/eU0F8Pi.png)

### 合併 `UNION`

* `UNION ALL` 不剔除重複資料
* `UNION` 剔除重複值

|     | 資料數 | 欄位數 |
| ---- | ------ | ----- |
| `JOIN`(LEFT 為例)  | 不變   | 增加   |
| `UNION` | 增加   | 不變   |

#### 限制

* 兩表欄位數量需**相同**
* 欄位型態需**相容**
* 合併前不要排序
  * 無意義
  * 浪費成本
* 合併後再做排序
* 欄位名稱以第一組為主

### 子查詢 Sub Query

* 統計

```sql=
SELECT mno, mname, 
(SELECT COUNT(*) FROM bas_product WHERE place_no = bas_place.mno) AS counts
FROM bas_place
```

### 其他

* `MAX()`
* `MIN()`
* `TOP <number>`

## 撰寫 T-SQL 程式

### 時機

1. Trigger 觸發程式
2. Store Procedure 預儲程序
3. Function 使用者自定義函數

### 用 Trigger 觸發程式實作小計

* 掛在資料庫裡面
  * 當只影響到資料，與畫面無關時
    * 欄位計算，例如：小計
* 自動攔截使用者 Insert, Update, Delete 的動作，會存在於緩衝區(Buffer)

| 動作   | Insert  | Update | Delete |
| ------ | -------- | ----- | -- |
| 緩衝區  | Inserted Buffer | Inserted Buffer(改後)<br>Deleted Buffer(改前) | Deleted Buffer |

#### 判斷

* 新增：新增緩衝區有資料、刪除緩衝區沒有資料
* 修改：新增緩衝區有資料、刪除緩衝區也有資料
* 刪除：刪除緩衝區有資料、新增緩衝區沒有資料

#### 起手式

:::info
本例為了方便理解將宣告變數部分方開寫
:::

```sql=
CREATE TRIGGER <命名>
  ON <資料表名稱>
  AFTER INSERT,DELETE, UPDATE
AS
BEGIN
  -- 如果下面有做計算，不要回應任何東西，預設開啟
  SET NOCOUNT ON;

-- ======自訂區：小計======
  -- 判斷是新增、修改、刪除
  DECLARE @command nvarchar(50) = ''
  IF EXISTS(SELECT * FROM inserted) AND NOT EXISTS(SELECT * FROM deleted) SET @command = 'INSERT'
  IF EXISTS(SELECT * FROM inserted) AND EXISTS(SELECT * FROM deleted) SET @command = 'UPDATE'
  IF EXISTS(SELECT * FROM deleted) AND NOT EXISTS(SELECT * FROM inserted) SET @command = 'DELETE'
  
  -- 欄位變數宣告
  DECLARE @rowid int = 0
  DECLARE @qty decimal(18,4) = 0
  DECLARE @price decimal(18,4) = 0
  DECLARE @amount decimal(18,4) = 0

  -- 判斷使用者新增資料或是修改資料
  IF(@commnad = 'INSERT' OR @command = 'UPDATE')
  BEGIN
    SET @rowid = (SELECT rowid FROM inserted)
    SET @qty = (SELECT qty FROM inserted)
    SET @price = (SELECT price FROM inserted)
    
    -- 防呆
    IF (@qty IS NULL) SET @qty = 0
    IF (@price IS NULL) SET @price = 0
    
    -- 計算小計並存於變數@amount
    SET @amount = @qty * @price
    
    -- 將變數@amount更新回欄位中
    UPDATE [dbo].[sal_sales_d] SET amount = @amount WHERE rowid = @rowid
  END
-- ======================
  
END
GO
```

#### 完整程式碼

:::info
執行後再做修改會看到 `CREATE TRIGGER` 變成 `ALTER TRIGGER`
:::

![TRIGGER](https://i.imgur.com/SpyZp7i.png)

* 新增：要手動「執行SQL」
* 修改：立刻看到結果

![result](https://i.imgur.com/OU1rVcW.png)

### 用 Trigger 實作自動表頭編號

1. 前置碼
   1. S_20220411001
2. 週期
   1. 年月日:20220411001
   2. 年月:202204001
   3. 年:2022001
3. 流水號
   1. 3碼:001
   2. 4碼:0001

* 對象：銷貨單表頭中的`sheet_no`

```sql=
DECLARE @command nvarchar(50) = ''
IF EXISTS (SELECT * FROM inserted)AND NOT EXISTS (SELECT * FROM deleted) SET @command = 'INSERT'
IF EXISTS (SELECT * FROM deleted)AND NOT EXISTS (SELECT * FROM inserted) SET @command = 'DELETE'
IF EXISTS (SELECT * FROM inserted)AND EXISTS (SELECT * FROM deleted) SET @command = 'UPDATE'

DECLARE @lead_code  nvarchar(50) = 'S'   -- 前置碼
DECLARE @cycle_code nvarchar(50) = 'YMD' -- 週期碼(Y/YM/YMD)
DECLARE @seq_leng   int = 3              -- 流水號長度
DECLARE @seq        int = 1              -- 目前流水號編號
DECLARE @find_no    nvarchar(50) = ''    -- 尋找編號

DECLARE @rowid      int = 0
DECLARE @sheet_no   nvarchar(50) = ''    -- 單據編號
DECLARE @sheet_date date                 -- 單據日期

-- 新增時自動編號:前置碼+日期+流水號(例如:S20220411001)
IF(@command = 'INSERT')
BEGIN
    SET @rowid = (SELECT rowid FROM inserted)

    -- 1.將表單編號冠上前置碼，空白表示沒有前置碼
    SET @sheet_no = @lead_code

    -- 2.將表單編號加上日期
    -- 判斷流水號日期
    SET @sheet_date = (SELECT sheet_date FROM inserted)
    -- 只取日期前4碼，將格式轉成 nvarchar
    IF (@cycle_code = 'Y') SET @sheet_no += CONVERT(nvarchar(4), @sheet_date, 112)
    IF (@cycle_code = 'YM') SET @sheet_no += CONVERT(nvarchar(6), @sheet_date, 112)
    IF (@cycle_code = 'YMD') SET @sheet_no += CONVERT(nvarchar(8), @sheet_date, 112)

    -- 3.將表單編號加上流水號
    -- 判斷今天是否已有資料，有的話取出流水編號最大號並接續編號
    SET @find_no = @sheet_no + '%'
    IF EXISTS (SELECT * FROM sal_sales WHERE sheet_no LIKE @find_no)
    BEGIN
        -- 找出今天最大編號
        SET @find_no = (SELECT TOP 1 sheet_no FROM sal_sales WHERE sheet_no LIKE @find_no ORDER BY sheet_no DESC)
        -- 取出最大編碼最後3碼，轉成整數之後再+1
        SET @seq = CAST(RIGHT(@find_no, @seq_leng) AS int) + 1
    END
    -- 將流水號轉成nvarchar前面補3個0，再取最後3碼，保證流水號有3碼，不足處補0
    SET @sheet_no += RIGHT(REPLICATE('0', @seq_leng) + CAST(@seq AS nvarchar), @seq_leng)

    -- 4.將表單編號寫回表單
    UPDATE sal_sales SET sheet_no = @sheet_no WHERE rowid = @rowid
END
```

#### 完整程式碼

![sourse code](https://i.imgur.com/5EhmQuf.png)
![result](https://i.imgur.com/zJe0sBI.png)

#### 應用到的函式

* 轉換型態
  * `CONVERT`(<型態>, <資料>, <格式>)
    * <格式>:本例`112`即YYYYMMDD
  * `CAST`(<資料> `AS` <型態>)
* `REPLICATE`(<數值>, <重複次數>)
* `RIGHT`(<資料>, <位數>)
