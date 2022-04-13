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

## 上課影片

### 4/12 環境建置與虛擬主機架設

{%youtube kntn6ZsPy4c %}

### 4/13 環境建置與虛擬主機架設

{%youtube eGET6v_Cu1M %}
