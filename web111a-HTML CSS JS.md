# HTML, CSS, JavaScript, jQuery, WoT

###### tags: `程式筆記` `web111a` `HTML & CSS & JavaScript`

* **老師：戴德仁**
* 時間：2022/4/12、13
* WoT
  * 信任網絡（英語：Web of Trust，縮寫：WoT）是密碼學中的一個概念，可以用來驗證一個公鑰的持有者身份。
  * 信任網絡用去中心化的概念，不同於依賴數字證書認證機構的公鑰基礎設施。
  * 在計算機網絡中，可以同時存在許多獨立的信任網絡，而任何用戶均可成為這些網絡中的一份子，或者不同網絡之間的連結。

## Course Intro

* 預計花費 1~2 週
  * 前端 KnowHow
  * 環境建置（build on cloud）

## 基本觀念

* Client side
* Server side
* 網站建置於 D:\htdosc\www
* 相對路徑 htdosc\123\test.png
* 絕對路徑 D:\htdosc\123\test.png

### dos基本操作

:::info
本教學以 Linux 及 Windows 為主
:::

* MAC
* Linux
  * 節點代號
    * \c
    * \d
* Windows
  * 指令、路徑名稱不分大小寫
  * 磁碟機代號
    * C:\
    * D:\

| 指令\作業系統 | Windows | Linux |
| ----------- | ------- | ----- |
| 根          |  \      |   /   |
| 切換工作目錄  | c:      | cd /c |
| 建立資料夾   | mkdir | mkdir |

:::warning
Windows 下如果在 c:\ 中下 `cd d:\` 會移動不過去，因為系統判斷 c:\ 底下沒有 d:\
  
![error](https://i.imgur.com/SfF4DCP.png)

:::

## XAMPP

:::danger
XAMPP 版本請介於 7.2 到 7.4 之間，學校雲端才能用
:::

* 執行 setup_xampp.bat 設定組態
* 確認安裝
  * `php -v`
  * 如找不到請設定環境變數
    * d:\xampp
    * d:\xampp\bin\MySQL
* Port
  * Web http(此例Apache): 80
  * https(此例Apache): 443
  * MySQL: 3306
  * FTP(此例FileZilla): 21
  :::info
  因為未來老師會教其他網頁伺服器(IIS)預設Port也是80，本課程請改為6080
  XAMPP panel 的 config 及 Apache 的 config 也要改

  * IIS->Microsoft->ASP.NET
  * XAMPP->偏Ninux->PHP
  :::

## VS Code

### 推薦套件

#### Settings Sync

* [教學](https://medium.com/%E4%B8%80%E5%80%8B%E5%B0%8F%E5%B0%8F%E5%B7%A5%E7%A8%8B%E5%B8%AB%E7%9A%84%E9%9A%A8%E6%89%8B%E7%AD%86%E8%A8%98/vscode-%E4%BD%BF%E7%94%A8-settings-sync-%E5%90%8C%E6%AD%A5-vscode-%E7%9A%84%E6%93%B4%E5%85%85%E5%8A%9F%E8%83%BD%E8%88%87%E5%90%84%E9%A0%85%E8%A8%AD%E5%AE%9A-bb24a8d141eb)
  1. 權限設定
     1. github access token
     2. gist id
  2. 依據套件設定 settings.json
  
```json=
{
  // setting sync
  "sync.gist": "[your gist id]",
  "sync.autoDownload": false,
  "sync.autoUpload": false,
  "sync.forceDownload": false,
  "sync.forceUpload": false,
  "sync.quiteSync": false,
  "sync.removeExtensions": true,
  "sync.syncEctension": true
}
```

* [ATOM on Mac](https://garfieldduck.me/atom-sync-settings/)

#### Markdown 系列

* Markdown All in One：支援 markdown
* Markdown Preview Enhanced：外觀
* Markdown PDF：轉檔
* markdownlint：偵錯
* Markdown Preview Github Styling：外觀
* Markdown Theme Kit：主題
* Markdown Emoji：特殊字元
* Markdown Shortcut：簡稱
* Markdown Table Formatter：表格
* Markdown TOC：分類

#### Picgo

* 圖片上傳
* 需先安裝[Picgo](#Picgo1)

## [Picgo](https://github.com/Molunerfinn/PicGo)

* 快速圖片上傳
* 支援多方雲端

### install

* 安裝穩定版本：2.3.0
* 設定選擇 Github
* Github 圖層 > Github 設置
  * 設定repo, branch, token
* setting.json

```json=
//PicGo
"picgo.picBed.current" : "github",
"picgo.picBed.github.branch": "main",
"picgo.picBed.github.token" : "[your token]",
"picgo.picBed.github.repo": "[yourname/picgo]",
"picgo.picBed.github.path": "img/", 
```

## Git

### command

* `>`：複寫
* `>>`：appand

```shell=
echo "# reponame" >> README.md
```

## XAMPP Virual host

![note](https://i.imgur.com/SbYymsC.png)

1. httpd.conf：改port
2. httpd-vhost：設定檔案路徑及網域名稱
3. host：將網域連結到IP

### DNS

* 內網(Intranet)
  * LAN: Local Area Network
* 外網(Internet)
  * 協定 TCP/IP

## 虛擬機

### 安裝Virtual Box

1. 下載 [Portable-VirtualBox](https://www.vbox.me/)
   * Win10
2. 啟用虛擬化(BIOS)
3. 手動更改設定檔(.ini)
   1. data/language
      1. 語系簡轉繁
   2. data/settings/vboxinstall.ini
      1. vbox 版本請選 6.0.24
      2. extension pack 版本請選 6.0.24
4. 初次安裝會出現錯誤，先點選確定，請手動安裝驅動(.inf)右鍵點選安裝
   1. 網路卡驅動：app64/drivers/network
   2. USB 驅動：app64/drivers/USB
   3. 核心驅動：app64/drivers/vboxdrv
5. 執行後看到小企鵝就成功囉

### 安裝 OS

1. 新增機器
2. 掛載iso
   1. 預設開機 SATA 埠為 0
3. win10 登入方式：本機
4. 建立使用者帳戶
5. 記得把開機順序調回來

### 初始設定

#### 建立D槽

1. 開機前：存放裝置>建立虛擬硬碟
2. 開機後：電腦管理>存放裝置>磁碟管理>初始化D槽

#### Guest Additions

> VirtualBox Guest Additions are a collection of device drivers and system applications designed to achieve closer integration between the host and guest operating systems. They help to enhance the overall interactive performance and usability of guest systems.

1. 裝置>掛載 Guest Additions
2. 重新開機後就可以調整畫面解析度
3. 之後就可以卸載 Guest Additions 囉

#### 建立虛擬機與本機共享

* 裝置>共用資料夾>:ballot_box_with_check:自動掛載、:ballot_box_with_check:永久
* 裝置>共用剪貼簿>雙向
* 裝置>拖放>雙向

#### 網路卡

* bridge 橋接介面卡
  * 在本機端幫虛擬機接上網卡：
    1. 網際網路設定
    1. 變更介面卡選項
    1. 乙太網路2
    1. 內容
    1. 安裝
    1. 服務
    1. 新增
    1. 從磁片安裝
    1. 虛擬主機目錄下
       1. drivers
       1. network
       1. netlwf
       1. (.inf)
  * 之後可以看到 VitrtualBox NDIS6 Bridged Networking Driver 被安裝好囉
  * 虛擬機>裝置>網路>介面卡
* 查詢虛擬機 IP

### 本機端用 SSH 登入虛擬機

:::info
需將 Windows 更新
:::

* 設定>應用程式>選用功能
  * OpenSSH 用戶端(預設安裝)
  * OpenSSH 伺服器(需手動安裝)
* 服務>設為自動並啟用
  * OpenSSH Authentication Agent
  * OpenSSH Server
* 連線

  ```shell=
  ssh <username>@<host ip>
  # 例如本例 ssh web111a@127.0.0.1
  ```

* 查詢通訊埠(預設開啟)，有在監聽(TCP/IP)才能用SSH連線

  ```shell=
  netstat -an | findstr :22
  ```

* 防火牆(預設開啟)

#### 設定免密碼連線

設定檔位置：C:/ProgramData/ssh/sshd.config

可以用免密碼連線(預設開啟)，如有註解需拿掉

```shell=
AuthorizeKeyFile .ssh/authorized_keys
```

讓管理員可以連線，將最下面兩行註解

```shell=
# Match Group administrators
#         AuthorizedKeysFile __PROGRAMDATA__/ssh/administrators_authorized_keys
```

:::warning
因為教室電腦將`user`改成`web111a`的，ssh登入時會找不到，他會找預設的`user`

* 控制台>系統管理工具>電腦管理>`web111a`改回`user`
  * 使用者名稱
  * 全名
  * 密碼
* 新增`web111a`使用者
  * 群組加入`administrator`
:::

#### add key

將本機公鑰(.pub)加到虛擬機(authorized_keys)

#### 主機別名

在`.ssh`底下建立`config`

```shell=
Host allen
Hostname 127.0.0.1
Port 22
User allen
identityfile ~/.ssh/id_rsa_allen
```

登入

```shell=
ssh allen
```

#### 補充說明：nano

* Linux 文字編輯器
* 放在 D:/tools/nano
* 記得加環境變數

#### 補充說明：遠端複製

```shell=
scp <filename> -r[recursive] <username>@<host>:<filepath>
# 本例 scp id_rsa.pub web111a@127.0.0.1:~/.ssh/authorized_keys
```

## 上課影片

### 4/12 環境建置與虛擬主機架設（直播）

{%youtube kntn6ZsPy4c %}

### 4/13 環境建置與虛擬主機架設（直播）

{%youtube eGET6v_Cu1M %}

### 4/15 後影片參照[老師 YT](https://www.youtube.com/channel/UC6c3un6c2FyZrLr0cAuG9LQ)
