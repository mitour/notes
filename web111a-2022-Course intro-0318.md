# C# 程式語言 & 導師時間

###### tags: `程式筆記` `web111a` `C#`

* **老師：戴德仁**
* 時間：2022/3/18

## 導師時間

1. 請同學注意上課、點名時間8:20，逾時會記曠課
2. 班長提供請假名單
3. 課表更動請查閱共用
4. 第52屆全國技能競賽中區分區技能競賽
5. 課務用電腦不得私自安裝非授權軟體
6. 建議購買SSD/256G外接硬碟

## 專題注意事項

1. 需部署至課務伺服器
2. 1-3人

## 環境建置

1. 7-ZIP
2. notepad++
3. fastcopy
4. git
   1. 路徑C:\Git
   1. 取消勾選 Windows Explorer integration
   1. 編輯器選擇 nano
5. Cmder
6. nvm
   1. 路徑C:\nvm、C:\nvm\nodes
7. XAMPP
8. composer
   1. develop mode要勾選

## Git

### 基本設定

1. 調整 options
2. [初次設定 Git](https://git-scm.com/book/zh-tw/v2/%E9%96%8B%E5%A7%8B-%E5%88%9D%E6%AC%A1%E8%A8%AD%E5%AE%9A-Git)
   1. username
   1. email
   1. default editor

## 終端機設定

* 命令提示字元中可以設定>進階，以管理員身份執行就不用每一次都按

### Cmder

1. 控制台>系統>進階系統設定>環境變數>path
2. 新增 cmder 路徑 C:\cmder

## node設定

* 安裝

```bash=
nvm list avaiable
nvm install [版本號]
nvm use [版本號]
```

* 測試

```bash=
node
```

## SAMPP設定

1. 設定環境變數
   * D:\xampp\php
   * D:\xampp\mysql\bin

2. 設定檔
   * 檔案名稱：setup_xampp.bat

3. 確認是否設定完成

```bash=
php --version
```

![確認是否成功添加路徑php](https://i.imgur.com/wNJXbPq.png)

```bash=
mysql --version
```

![確認是否成功添加路徑mysql](https://i.imgur.com/q6gH9ac.png)

## composer

Composer是PHP的軟體包管理系統

### 指定composer根位置

1. 新增系統變數
   1. 變數名稱：COMPOSER_HOME
   1. 變數值：c:\composer
1. 設定環境變數
   1. path 增加 c:\composer\vendor\bin

## Visual Studio 2019 簡介

基本完整的開發工具集，它包括了整個軟體生命週期中所需要的大部分工具，如UML工具、程式碼管控工具、整合開發環境（IDE）等等。

* 如需新增套件，可至控制台>程式集>變更
  * ASP.NET
  * AZURE
  * .NET 桌面開發
  * 通用 Windows 平台開發
  * VS 擴充功能開發

## 延伸

### 環境變數

#### [環境變數教學](https://shaochien.gitbooks.io/command-line-and-environment-variable-tutorial/content/environment-variable.html)

> 如果沒有把軟體本身「可執行檔的路徑」設定在 PATH 環境變數中的話，則每次執行該命令必須使用以下兩種方式：
>
> * 到該程式所在的執行檔目錄底下執行
> * 輸入執行檔的完整路徑

#### 例如：command not found 就是路徑沒設定好

[zsh command not found](https://bonze.tw/mac--e8-a7-a3-e6-b1-ba-zsh-command-not-found/)

### SAMPP

允許使用者可以在自己的電腦上輕易的建立網頁伺服器。

> XAMPP的名稱來自以下組合：
> **X**（支援跨平台）
> **A**pache
> **M**ySQL或MariaDB
> **P**HP
> **P**erl

* [Mac 使用 XAMPP 建立 php 開發環境 教學](https://medium.com/@mpp21x/%E4%BD%BF%E7%94%A8-xampp-%E5%BB%BA%E7%AB%8B-php-symfony-%E9%96%8B%E7%99%BC%E7%92%B0%E5%A2%83-b5a793ab5b6b)
* Virual Host
  * 設定 VirtualHost 目的是使用同一個伺服器架設多個網站，當使用者以不同網域名稱連到該主機時， web server 會依據不同的目的網頁需求，回應不同的網頁內容。

### PHP

* scripting language
* server-side language
* creating dynamic web pages
  * ![dynamic web pages](https://content.codecademy.com/courses/introduction-to-php/php_static_dynamic.svg)

### Node.js

> Node.js 是能夠在伺服器端運行 JavaScript 的開放原始碼、跨平台執行環境。
JavaScript 通常作為使用者端程式設計語言使用，以JavaScript 寫出的程式常在使用者的瀏覽器上執行。Node.js 的出現使 JavaScript 也能用於伺服器端編程。

* nvm：node version management
