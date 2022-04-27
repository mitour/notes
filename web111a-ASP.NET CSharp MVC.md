# ASP.NET C# MVC

###### tags: `web111a` `程式筆記` `ASP.NET` `C#`

* 老師：許志強
* 時間：2022/04/27

## 淵源

### .NET Support Policy

* 早期是 Webform，後來改 [MVC](#補充：MVC) 架構，
* 所以 .Net Framework (目前 4.8 版)問世了，他可以寫Webform 和 .Net Framework，但是沒有跨平台支援
* 於是有 .Net Core (目前 3.1 版)
* 後來又有 .Net 6
* 之後預計還會有 .NET 7, .Net 8 ...

![.NET Support Policy](https://i.imgur.com/VRewGSo.png)

:::success
本課以 .Net Framework 為主，時間充足會帶到 .Net Core、.Net 6
:::

#### 補充：MVC

> 目的：簡化應用程式的開發與增強程式的可維護性
> 缺點：耗時

![MVC model](https://i.imgur.com/P2DPXIH.jpg)

* Model
  * 業務邏輯相關的資料以及對資料的處理方法
  * 存取資料
  * 伺服端程式語言
* View
  * 圖像製作
  * 前端程式語言
* Controller
  * 主要負責將視覺的靜態頁面轉換成嵌有程式的動態頁面
    * 將資料利用表單發送到 Model
    * 接收並轉換 Model 所回傳的資料並呈現在 View 之上

參考：[[Day 01] 什麼是MVC？能吃嗎？](https://ithelp.ithome.com.tw/articles/10191216)

### 那手機呢？

* 以前除了寫 C#，手機端還要再學 Android 以及 iOS 開發，
* 於是有了 Xamarin，讓你能用 C# 開發手機 APP
* 但微軟又双叒叕宣布之後 MAUI 將會取代 Xamarin

### 開發工具

* Visual Studio
  * 整合性較高，可以寫 .Net Framework、.Net Core
  * 比較肥大，畢竟還要能寫舊東西
  * 只能用在 Windows 平台
* Visual Studio Core
  * 特別針對跨平台，MacOS、Unix 也可以用
  * 業界趨勢，故新技術支援叫豐富

:::success
結論：小孩才做選擇。本課以 Visual Studio 為主，時間充足會帶到 Visual Studio Core
:::

#### 版本選擇

* 年份
  * 2019
  * 2022支援 .Net 6 :ballot_box_with_check:
* 版本
  * 社群版（微軟會員免費）:ballot_box_with_check:
  * 專業版
  * 企業版

## C\#

### Visual Studio 基操

### `try/catch`

```csvpreview=
try
{
  // 有可能出錯的程式碼
}
catch (Exception e)
{
  // 錯誤訊息在這邊撈
  Console.WriteLine("Error occurred from {0}. Message = {1}", path, e.Message);
}
finally
{
  // 無論如何執行這邊
}
```

### `TryParse`

比起 `try/catch` 不會讓程式中斷，可以再用迴圈讓使用者重新輸入

```csharp=
double.TryParse(str_height, out db1_height)
```
