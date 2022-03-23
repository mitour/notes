# MS-SQL 基本操作II

###### tags: `程式筆記` `web111a` `MS-SQL`

* **老師：許志強**
* 時間：2022/3/23

## 定時排程備份

* 需確認SQL Agent是否執行中，控制台>系統管理工具>服務
* 維護計畫
  * 子計畫>頻率
  * 工具箱>維護計畫工作>備份資料庫工作
* 記得存檔、記得存檔、記得存檔

## 備份檔規劃 TSQL

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

## 備份異常alert

### Email

#### 建立操作員

* SQL Server Agent > 操作員

#### 設定gmail smtp

* 不需自架 Mail Server，運用 Gmail SMTP(寄)/POP3(收)
* 需有帳號及應用程式密碼
  * 基於資安考量，需有兩段式驗證過才能取的應用程式密碼
  * ![應用程式密碼](https://i.imgur.com/i2fLZs5.png)
* 管理>SQL Server 紀錄檔> database mail
* 記得存檔、記得存檔、記得存檔

#### 通知操作員工作

* 成功
* 失敗
* 完成

### Line

#### Line Notify

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

## 異地備援

### Google Drive

![google drive](https://i.imgur.com/8tK2Yzc.png)

* 使用 Google Drive 桌面軟體
* 將 /dbbackup 勾選與雲端硬碟保持同步

### MEGA
