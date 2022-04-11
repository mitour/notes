# C# 程式語言

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

---

## C# 程式架構

* **老師：戴德仁**
* 時間：2022/3/29

### C# 開發應用

1. window from
2. 控制台
3. web (ASP.NET, MVC) --> 另一門課

### 主要架構

* 入口函數：`Main()`
* 預設類別名稱 class：`Program.cs`
* 命名空間通常放最外層：`namespace`，幫助不同命名空間中有相同函數時可用來分類，類似於資料夾

![C#程式架構](https://i.imgur.com/m1sAVDF.png)

### 註解

* `// 單行`
* `/* 多行 */`

### Main()

![Main()](https://i.imgur.com/JsQilUk.png)

* static 靜態：讓程式在執行時，先在記憶體佔位置
* 程式執行三階段
  * coding 編輯
  * compile 編譯
  * linking 連結：將函式庫、外部程式作連結
  * build 成執行檔，一般存於 bin/debug 或 bin/Release 資料夾中

### void

當方法沒有回傳值時

### Read()

```csharp=
console.Read(); // 僅抓取使用者輸入第一個字元
console.ReadLine(); // 抓取多行使用者輸入
```

### 資料型別

#### 強型別

要定義資料類型，偏向不容忍隱性的型別轉換。例如：`java`、`C#`

  ```java=
  int x = 123 + Integer.parseInt("456");
  ```
  
#### 弱型別

即便先定義的型別，也可以很直觀的轉換，例如：`php`

  ```php=
  $x = 123 + "456";
  echo $x;
  ```

#### 常見資料型別

![常見資料型別](https://i.imgur.com/4sird6c.jpg)

* 8`bit` = 1`byte`

### 常數、變數

* 常數`const`：宣告初始值後，內容不可改變
* 變數`var`：內容會改變
* `public`

### 命名規則

* 大小寫有分
* 英文、底線開頭
* 有意義
* 少用中文
* 保留字或關鍵字
  * ![保留字或關鍵字](https://i.imgur.com/1UZpcy0.png)

### 函式參數引用原則

[Call By Value, Call By Reference?](https://stu98832.github.io/2020/06/26/call-by-reference/)
記憶體中紀錄的是位置（Reference）還是實質型別（Value）？

#### 實值型別與參考型別

> 實值型別傳遞給其他人時是複製實值傳遞，參考型別傳遞給其他人時是複製地址傳遞。
> 實值似影印傳遞，會複製成兩份一模一樣的物件，參考傳遞似網址傳遞，會複製網址分享對方，兩人共同觀看網站同一個物件。
> [From 實值型別與參考型別](https://ithelp.ithome.com.tw/articles/10223905)

### 運算子、運算元

#### 運算元

* 單元運算子，例如：`i++`
* 二元運算子，例如：`i+j`
* 三元運算子，例如：`max=(a>b)?a:b`

#### 運算子

* 算術運算子，例如：`+`、`-`、`*`、`/`、`%`
* 關係運算子，例如：`==`、`!=`、`>`、`<`、`>=`、`<=`
* 邏輯運算子，例如：`&&`、`||`、`!`、`XOR`
  * ![xor](https://i.imgur.com/pZjItqf.png)
* 位元運算子
  * ![位元運算子](https://i.imgur.com/7a6PRLl.png)
* 位移運算子，例如：`>>`右移（/2）、`<<`左移（*2）
* 複合指定運算子，例如：`+=`、`-=`等等

##### 優先層級

![運算子優先層級](https://i.imgur.com/i1DeX4R.png)

### String

#### 字串相連

```csharp=
Console.WriteLine("身高是"+"150")
```

#### 字串格式化

```csharp=
stringFormat("身高是{0}", height)
```

#### 字串插值

```csharp=
$"身高是{height}"
```

### 建立方案

* 方案(.sln)
  * 專案1(.csproj)
  * 專案2(.csproj)
  * ...
* 如果沒有載入 System 函式庫，console 需要指名從 System 函式庫

```csharp=
System.Console.writeLine("world");
```

* `white` v.s. `whiteLine`

```csharp=
Console.white("hello, ");
Console.writeLine("world"); //執行完會跳下一行
```

![white / whiteLine](https://i.imgur.com/AmM01iP.png)

#### Debug

設定中斷點

![Debug](https://i.imgur.com/Ogr30H2.png)

### 補充：進制轉換

#### 二進制 Binary, bin

* 基數 2，逢 2 進位

![binary](https://i.imgur.com/6Vsr3A6.png)

#### 八進制 Octal, oct

* 基數 8，逢 8 進位

#### 十進制 Decimal, dec

* 基數 10，逢 10 進位

![decimal](https://i.imgur.com/dmnBcL4.png)

#### 十六進制 Hexadecimal, hex

* 基數 16，逢 16 進位
* 10(A)、11(B)、12\(C\)、13(D)、14(E)、15(F)

#### 最高有效位元 MSB：最左邊

#### 最低有效位元 LSB：最右邊

---

* **老師：戴德仁**
* 時間：2022/4/1、4/7
* 配合投影片02，版權問題不放

### console 類別常用方法

* `White`
* `WhiteLine`
* `Read`
* `ReadLine`

#### 練習題

![console exercise](https://i.imgur.com/OYXXHiL.png)

```csharp=
using System;

namespace ConsoleEx1
{
    class Program
    {
        static void Main(string[] args)
        {
            string name;
            int price;
            Console.Write("請輸入品名：");
            name = Console.ReadLine();
            Console.Write("請輸入單價：");
            price = int.Parse(Console.ReadLine());
            Console.WriteLine($"品名：{name} 單價：{price} 記錄儲存成功");
        }
    }
}

```

### 格式化輸出

從 `Write`、`WriteLine`著手

#### string

```csharp=
{index[,alignment][:formatChar]}
```

* `index` 索引值
* `,alignment` 對齊
  * 為正數往右對齊，為負數則往左
  * 數字大小決定欄位寬度
  * 為0則維持字串原先長度
* `:formatChar` 格式化字元
  * C[n]：貨幣[小數點後幾位]，預設取小數點後兩位
    * 會自動四捨五入

![formatChar](https://i.imgur.com/hxzFrAW.png)

![formatChar](https://i.imgur.com/MNyF1vb.png)

##### 實戰

```csharp=
//.NET string format
Console.WriteLine("12345678901234567890");
Console.WriteLine(string.Format("{0, 0 :C}   {1, 0 :c3}\n{2, 15 :c3}\n{3, -15 :c3}", 5, -5, -5, -5));
// 完整寫法
Console.WriteLine("{0, 0 :C}   {1, 0 :c3}\n{2, 15 :c3}\n{3, -15 :c3}", 5, -5, -5, -5);
// 字串加值的寫法
Console.WriteLine($"{5,0:c}   {-5,0:c3}\n{-5,15:c3}\n{-5,-15:c3}");
```

#### 數值(int, float)

從`ToString`著手

* 0
  * 向右對齊
  * 空位補0
* \#
  * 向左對其
  * 空未補空格

```csharp=
double i = 0801234567;
Console.WriteLine(i.ToString("(0##) ###-####"));

// 輸出結果 (080) 123-4567
```

![數值format](https://i.imgur.com/xieoPru.png)

![數值format](https://i.imgur.com/cMOmr7J.png)

### 預告：隨堂小考

* 紙本考試
* 可看memo，不可以看書

### 跳脫字元

* `\n`:newline
* `\r`:return
  * 游標到最前面
* `\t`:tab
  * 字首8字元
  * 字間5字元
* `@"C:\cs\hw1.cs"`
  * 前綴`@`會讓後面字串全部以一般字元輸出，但如果有`""`仍需使用跳脫字元`\"`

### 型別轉換

#### 隱性轉換

![btye size](https://i.imgur.com/xxdELII.png)

![隱性轉換](https://i.imgur.com/Tigxead.png)

* `大=小`才能轉換

#### 明確轉換(強制轉換)

* 利用型態轉換(Type cast)方式強制轉換
* 容易有資料遺失，將8byte轉成4byte會有4btye遺失

![強制轉換資料遺失](https://i.imgur.com/kPGGBqk.png)

### 移位運算元

#### 左移`<<`

> 數學意義：
> 在數字沒有溢出的前提下，對於正數和負數，左移一位都相當於乘以2的1次方，左移n位就相當於乘以2的n次方。

#### 右移`>>`

> 數學意義：
> 右移一位相當於除2，右移n位相當於除以2的n次方。

### XOR(`^`)

兩個條件中有一個條件不成立時，就等於條件成立了

```csharp=
char c1 = '9';
char c2 = '2';
char c3 = '1';
Console.WriteLine($"原編碼訊息：{c1}{c2}{c3}");
int key = 11;

c1 = (char)(c1 ^ key);
c2 = (char)(c2 ^ key);
c3 = (char)(c3 ^ key);
Console.WriteLine($"編碼後訊息：{c1}{c2}{c3}");

c1 = (char)(c1 ^ key);
c2 = (char)(c2 ^ key);
c3 = (char)(c3 ^ key);
Console.WriteLine($"解碼後訊息：{c1}{c2}{c3}");
```

#### 運算（隱性轉換）

1. 先將9(ASCII)轉成57(十進位)再轉成111001(二進位)
2. 將key值11(十進位)轉成1011(二進位)
3. 111001與1011做XOR
    * 111001
    * 001011
    * \-------
    * 110010
4. 得到110010(二進位)再轉成2(ASCII)

![ASCII](https://i.imgur.com/QNMiRlY.png)

#### output

```shell=
原編碼訊息：921
編碼後訊息：29:
解碼後訊息：921
```

### 列舉資料型別

#### `enum`

```csharp=
enum 物件{
  屬性=值
}
```

### 結構

#### `struct`

```csharp=
struct 物件{
  屬性=值
}
```

```csharp=
struct Product
{
  public string No, Name;
  public int Price;
}
static void Main(string[] args)
{
  // 宣告一個自定義物件Product，名叫xbox，則xbox一定會有三個欄位No, Name, Price
  Product xbox, ps4;
  xbox.No = "TVGame001";
  xbox.Name = "Xbox One(含Kinect)";
  xbox.Price = 17200;
  
  Console.WriteLine("\n===== 產品單價清單 =====\n");
  Console.WriteLine($"產品編號：{xbox.No}");
  Console.WriteLine($"產品名稱：{xbox.Name}");
  Console.WriteLine($"產品單價：{(int)xbox.Price}");
}
```

---

## C# workflow

* **老師：戴德仁**
* 時間：2022/4/7
* 配合投影片03，版權問題不放
* 預計4/8考試

### 結構化程式設計

1. 循序
2. 選擇性
   1. if/else
   2. switch
3. 重複性
   1. for
   2. while

### if/else

* 單選
* 雙選
* 巢狀

### else if

* 多選

```csharp=
if (ans == "4")
{
    Console.WriteLine("=== 答對了，真不愧是 .NET 達人....");
}
else if (ans == "1" || ans == "2" || ans == "3")
{
    Console.WriteLine("=== 答錯了，正確答案是4.");
}
else
{
    Console.WriteLine("=== 無此選項....");
}
```

### switch

* 多選

```csharp=
switch(ans)
{
    case "1":
        Console.WriteLine("=== 答錯了，正確答案是4.");
        break;
    case "2":
        Console.WriteLine("=== 答錯了，正確答案是4.");
        break;
    case "3":
        Console.WriteLine("=== 答錯了，正確答案是4.");
        break;
    case "4":
        Console.WriteLine("=== 答對了，真不愧是 .NET 達人....");
        break;
    default:
        Console.WriteLine("=== 無此選項....");
        break;
}
```

其中`case`輸出內容若相同亦可精簡為：

```csharp=
switch(ans)
{
    case "1":
    case "2":
    case "3":
        Console.WriteLine("=== 答錯了，正確答案是4.");
        break;
    ...
}
```

#### 選擇困難：用`if/else`還是`switch`?

> 1. 當分支較多時，當時用switch的效率是很高的。因為switch是隨機訪問的，就是確定了選擇值之後直接跳轉到那個特定的分支
> 但是if/else是遍歷所以得可能值，知道找到符合條件的分支。
> 如此看來，switch的效率確實比ifelse要高的多。
> 2. 由彙編程式碼可知道，switch佔用較多的程式碼空間，因為它要生成跳錶，特別是當case常量分佈範圍很大但實際有效值又比較少的情況，switch的空間利用率將變得很低。
> 3. switch只能處理case為常量的情況，對非常量的情況是無能為力的。例如 if (a > 1 && a < 100)，是無法使用switch來處理的。
> 所以，switch只能是在常量選擇分支時比if/else效率高，但是if/else能應用於更多的場合，if/else比較靈活。

### 三元運算子

```csharp=
max = a>b ? a:b;
```

### for

```csharp=
for(初值;條件示;增值){
  
}
```

* 全域變數：變數存活於程式碼執行到結束
* 區域變數：變數僅存活於特定區塊內
  * 例如`for(int i = 0; i <= 9; i++)`中的`i`

### while

```csharp=
while(條件示){
  
}
```

### do...while

```csharp=
do{
  // 至少執行一次才去判斷條件示
}while(條件示);
```

### break

終止程式，例如：印出1~10但3之後不要印

```csharp=
for(...){
  if(i==3) break
  ...
}
```

### continue

結束當下的迴圈，例如：印出1~10但不要印出3

```csharp=
for(...){
  if(i==3) continue
  ...
}
```

### 防呆

限定輸入數字，使用者輸入英文怎麼辦？

#### C#內建

```csharp=
// 原型：Boolean = 預期資料型態.TryParse(輸入, out 變數)
// 轉換成功回傳true及變數
// 轉換失敗回傳false
if(int.TryParse(Console.ReadLine(), out input)) {
  
}else{
  Console.WriteLine("輸入錯誤");
}
```

[實際應用](https://github.com/mitour/web111a_crouse_demo/blob/main/Workflow/While/Program.cs#L14)

#### try/catch
