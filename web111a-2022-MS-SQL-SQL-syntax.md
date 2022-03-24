# MS-SQL

###### tags: `程式筆記` `web111a` `MS-SQL`

* **老師：洪福成**(代課)
* 時間：2022/3/24

## 案例分享

一間公司員工老是抱怨電梯太慢，老闆於是開會討論是否真的慢，因為老舊？換新的能解決？預算問題等等。
此時就有一位員工出面說：我有一個不用花很多錢的方法，也許我能試著解決看看。
老闆也就同意了。
過一陣子確實沒有再聽到抱怨電梯太慢的問題。
待老闆實際到電梯口查看，發現該員工在電梯旁裝上一面全身鏡。
原來員工等電梯的同時整理儀容，也就忘了等待的時間有多漫長。

## SQL 查詢

### 語法

```sql=
SELECT 欄位1, 欄位2
FORM table1 JOIN table2
WHERE -- 在 group by 前的條件（搭配LIKE/AND/OR）
GROUP BY -- 群組化
HAVING --在 group by 後的條件
ORDER BY --排序，永遠下在最後
```

### 範例

* 模糊查詢

```sql=
SELECT * FROM employee WHERE name LIKE '陳%'
```

* Top 10

```sql=
SELECT TOP 10 * FROM employee ORDER BY salary DESC
```

* 群組化：各縣市客戶家數

```sql=
SELECT city, COUNT(*) 家數 --通常有用count都會group by
FROM customer
GROUP BY city
ORDER BY city
```

* 欄位內容篩選，還有很多依需求去搜尋
  * LEFT(num, 3)
  * DATEADD(YEAR, 40, birthday)

```sql=
SELECT LEFT(num, 3) AS class, COUNT(*) AS amount
FROM students
GROUP BY LEFT(num, 3)
ORDER BY class
```

* 某些情況下，`HAVING` 可以放在 `WHERE` 中（用 `AND` 連接）

```sql=
SELECT LEFT(班級座號, 3) AS 班級,
  SUM(事假) AS 事假,
  SUM(病假) AS 病假,
  SUM(公假) AS 公假,
  SUM(曠課) AS 曠課
FROM RECORDS
WHERE 年月日 LIKE '9003%' AND LEFT(班級座號, 3) >= 104 AND LEFT(班級座號, 3) <= 107
GROUP BY LEFT(班級座號, 3)
-- HAVING LEFT(班級座號, 3) >= 104AND LEFT(班級座號, 3) <= 107
ORDER BY LEFT(班級座號, 3)
```

### 練習題

:::info

* 留意沒有唯一解
* 反白可以做區域執行

:::

* 找出年齡大於40歲

```sql=
SELECT 學號, 
       姓名, 
       出生年月日, 
       DateAdd(YEAR, 40, 出生年月日) AS 滿40歲生日
FROM STUDENTS
WHERE DateAdd(YEAR, 40, 出生年月日) < GETDATE()
-- 生日+40年要大於今天
ORDER BY 出生年月日
```
