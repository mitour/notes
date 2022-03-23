# MS-SQL 環境建置及基本操作I

###### tags: `程式筆記` `web111a` `MS-SQL`

* **老師：許志強**
* 時間：2022/3/22

## SQL server 2019

### for windows

* 參考老師影片

#### 資料庫驗證

![資料庫驗證](https://i.imgur.com/iKuyYpw.jpg)

* windows 驗證：使用登入 windows 的帳號、密碼
* ==建議使用== 混合模式：自己在設定 DB user 的帳號、密碼
  * 預設請使用：**教室wifi密碼**以方邊除錯用

#### SQL Server 管理員

* 請使用 administrator 作為一但忘記驗證密碼的備案

### [install SQL server on Mac](https://leburger.gitlab.io/posts/mssql-2019-azure-data-studio-mac/)

#### Homebrew

是一款自由及開放原始碼的軟體套件管理系統，用以簡化macOS系統上的軟體安裝過程

#### Docker

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

##### Pull Image

```bash=
sudo docker pull mcr.microsoft.com/mssql/server:2019-latest
```

##### Run the container

透過容器，應用程式不需要再另外安裝作業系統（Guest OS）也可以執行。

```bash=
docker run -d --name sql_server_demo -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=<PASSWORD>' -p 1433:1433 mcr.microsoft.com/mssql/server:2019-latest
```

##### sql-cli

* npm（全稱 Node Package Manager，即「node套件管理器」）是Node.js預設的、用JavaScript編寫的軟體套件管理系統。

```bash=
npm install -g sql-cli
```

##### connect to SQL server

```bash=
mssql -u sa -p <PASSWORD>
```

##### 參考影片

{%youtube glxE7w4D8v8 %}

## SSMS

連線時使用 localhost/127.0.0.1 有可能連不到，因為會被判定為遠端連線，而被防火牆擋住

![connect issue](https://i.imgur.com/4Mr8Dbf.png)

### 設定防火牆

* 參考老師影片

1. 開 port 1433
2. 允許 sqlserver.exe
3. 允許 sqlbrowser.exe
4. 允許 ssms.exe
5. 設定網路組態

### for Mac

> 在 SSMS 沒有支援 Mac 的情況下，我們可以微軟開發的 Azure Data Studio 進行連結。

```bash=
brew cask install azure-data-studio
```

* 中文介面：cmd+shift+P，輸入 configure display language

## 資料庫操作

### 移動資料庫

* 資料庫及log需存在同一路徑
* 如想要移動資料庫檔案，需
  * 工具>卸離資料庫，要用再資料庫>附加回去
  * ==建議使用==工具>離線工作
  * stop server
* 移動資料庫遇到存取被拒問題
  * ![存取被拒](https://i.imgur.com/eJpDlid.jpg)
  * 手動加權限，內容>安全性>群組或使用者>編輯>新增Everyone
  * 或手動啟用繼承，內容>安全性>Everyone的權限>進階>變更權限>取用繼承

### 正式資料庫與測試用資料庫

* 同名不可以同時掛，需將測試用資料庫**附加為**別的名字，例如：demo_alpha

### 重新命名資料庫（資料庫複製）

* 都需要SQL Server Agent執行中
* 工作>複製資料庫>改名>重新掛，再將舊的刪掉

#### 卸離與附加

#### 使用 SQL 物件管理方法

### 備份還原

#### 離線備份

卸離、離線工作屬於離線備份

#### 線上備份

一般而言都是線上備份

* 工作>備份
* 備份類型：完整、差異、交易紀錄(log)

#### 還原

* 工作>還原>裝置>
  * 一般>檔案位置
  * 檔案>確認路徑
  * 選項>覆寫
    * 完整：restore with recovery
    * 差異：restore with standby

## 下堂預告

### 排程備份

* 異常 alert
  * email
  * line

### 異地備援

雲端
