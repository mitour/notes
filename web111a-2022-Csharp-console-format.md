# C# 程式架構

###### tags: `程式筆記` `web111a` `C#`

* **老師：戴德仁**
* 時間：2022/4/1、4/7
* 配合投影片02，版權問題不放

## console 類別常用方法

* `White`
* `WhiteLine`
* `Read`
* `ReadLine`

### 練習題

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

## 格式化輸出

從 `Write`、`WriteLine`著手

### string

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

#### 實戰

```csharp=
//.NET string format
Console.WriteLine("12345678901234567890");
Console.WriteLine(string.Format("{0, 0 :C}   {1, 0 :c3}\n{2, 15 :c3}\n{3, -15 :c3}", 5, -5, -5, -5));
// 完整寫法
Console.WriteLine("{0, 0 :C}   {1, 0 :c3}\n{2, 15 :c3}\n{3, -15 :c3}", 5, -5, -5, -5);
// 字串加值的寫法
Console.WriteLine($"{5,0:c}   {-5,0:c3}\n{-5,15:c3}\n{-5,-15:c3}");
```

### 數值(int, float)

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

## 預告：隨堂小考

* 紙本考試
* 可看memo，不可以看書

## 跳脫字元

* `\n`:newline
* `\r`:return
  * 游標到最前面
* `\t`:tab
  * 字首8字元
  * 字間5字元
* `@"C:\cs\hw1.cs"`
  * 前綴`@`會讓後面字串全部以一般字元輸出，但如果有`""`仍需使用跳脫字元`\"`

## 型別轉換

### 隱性轉換

![btye size](https://i.imgur.com/xxdELII.png)

![隱性轉換](https://i.imgur.com/Tigxead.png)

* `大=小`才能轉換

### 明確轉換(強制轉換)

* 利用型態轉換(Type cast)方式強制轉換
* 容易有資料遺失，將8byte轉成4byte會有4btye遺失

![強制轉換資料遺失](https://i.imgur.com/kPGGBqk.png)

## 移位運算元

### 左移`<<`

> 數學意義：
> 在數字沒有溢出的前提下，對於正數和負數，左移一位都相當於乘以2的1次方，左移n位就相當於乘以2的n次方。

### 右移`>>`

> 數學意義：
> 右移一位相當於除2，右移n位相當於除以2的n次方。

## XOR(`^`)

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

### 運算（隱性轉換）

1. 先將9(ASCII)轉成57(十進位)再轉成111001(二進位)
2. 將key值11(十進位)轉成1011(二進位)
3. 111001與1011做XOR
    * 111001
    * 001011
    * \-------
    * 110010
4. 得到110010(二進位)再轉成2(ASCII)

![ASCII](https://i.imgur.com/QNMiRlY.png)

### output

```shell=
原編碼訊息：921
編碼後訊息：29:
解碼後訊息：921
```

## 列舉資料型別

### `enum`

```csharp=
enum 物件{
  屬性=值
}
```

## 結構

### `struct`

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
