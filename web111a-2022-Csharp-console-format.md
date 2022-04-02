# C# 程式架構

###### tags: `程式筆記` `web111a` `C#`

* **老師：戴德仁**
* 時間：2022/4/1
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
