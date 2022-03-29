# C# 程式架構

###### tags: `程式筆記` `web111a` `C#`

* **老師：戴德仁**
* 時間：2022/3/29

## C# 開發應用

1. window from
2. 控制台
3. web (ASP.NET, MVC) --> 另一門課

## 程式架構

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

## 資料型別

### 強型別

要定義資料類型，偏向不容忍隱性的型別轉換。例如：`java`、`C#`

  ```java=
  int x = 123 + Integer.parseInt("456");
  ```
  
### 弱型別

即便先定義的型別，也可以很直觀的轉換，例如：`php`

  ```php=
  $x = 123 + "456";
  echo $x;
  ```

### 常見資料型別

![常見資料型別](https://i.imgur.com/4sird6c.jpg)

* 8`bit` = 1`byte`

## 常數、變數

* 常數`const`：宣告初始值後，內容不可改變
* 變數`var`：內容會改變
* `public`

## 命名規則

* 大小寫有分
* 英文、底線開頭
* 有意義
* 少用中文
* 保留字或關鍵字
  * ![保留字或關鍵字](https://i.imgur.com/1UZpcy0.png)

## 函式參數引用原則

[Call By Value, Call By Reference?](https://stu98832.github.io/2020/06/26/call-by-reference/)
記憶體中紀錄的是位置（Reference）還是實質型別（Value）？

### 實值型別與參考型別

> 實值型別傳遞給其他人時是複製實值傳遞，參考型別傳遞給其他人時是複製地址傳遞。
> 實值似影印傳遞，會複製成兩份一模一樣的物件，參考傳遞似網址傳遞，會複製網址分享對方，兩人共同觀看網站同一個物件。
> [From 實值型別與參考型別](https://ithelp.ithome.com.tw/articles/10223905)

## 運算子、運算元

### 運算元

* 單元運算子，例如：`i++`
* 二元運算子，例如：`i+j`
* 三元運算子，例如：`max=(a>b)?a:b`

### 運算子

* 算術運算子，例如：`+`、`-`、`*`、`/`、`%`
* 關係運算子，例如：`==`、`!=`、`>`、`<`、`>=`、`<=`
* 邏輯運算子，例如：`&&`、`||`、`!`、`XOR`
  * ![xor](https://i.imgur.com/pZjItqf.png)
* 位元運算子
  * ![位元運算子](https://i.imgur.com/7a6PRLl.png)
* 位移運算子，例如：`>>`右移（/2）、`<<`左移（*2）
* 複合指定運算子，例如：`+=`、`-=`等等

#### 優先層級

![運算子優先層級](https://i.imgur.com/i1DeX4R.png)

## String

### 字串相連

```csharp=
Console.WriteLine("身高是"+"150")
```

### 字串格式化

```csharp=
stringFormat("身高是{0}", height)
```

### 字串插值

```csharp=
$"身高是{height}"
```

## 建立方案

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

### Debug

設定中斷點

![Debug](https://i.imgur.com/Ogr30H2.png)

## 補充：進制轉換

### 二進制 Binary, bin

* 基數 2，逢 2 進位

![binary](https://i.imgur.com/6Vsr3A6.png)

### 八進制 Octal, oct

* 基數 8，逢 8 進位

### 十進制 Decimal, dec

* 基數 10，逢 10 進位

![decimal](https://i.imgur.com/dmnBcL4.png)

### 十六進制 Hexadecimal, hex

* 基數 16，逢 16 進位
* 10(A)、11(B)、12\(C\)、13(D)、14(E)、15(F)

### 最高有效位元 MSB：最左邊

### 最低有效位元 LSB：最右邊
