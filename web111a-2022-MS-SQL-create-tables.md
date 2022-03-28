# MS-SQL 創建資料表

###### tags: `程式筆記` `web111a` `MS-SQL`

* **老師：許志強**
* 時間：2022/3/28

## Naming rules

1. 不可數字開頭，不可空格，要的話需要以`[]`包住
2. 建立新資料表要重新整理、重新整理、重新整理

### Naming styles

1. 名稱在前，分類在後
2. 簡稱
3. 駝峰式
4. 底線
5. is開頭

### Primary key

#### 流水式命名 auto-increment

1. 識別規格：是
2. 為識別：是
3. 欄位設定主索引鍵
4. 資料類型為`int`

#### GUID

> 通常表示成32個16進位數字（0－9，A－F）組成的字串，如：{21EC2020-3AEA-1069-A2DD-08002B30309D}

1. 資料類型為`uniqueidentifier`
2. 資料表設計工具>rowGUID：是
3. 欄位設定主索引鍵
4. **型別也可以改成`varchar`，重點在於預設值有call `newid()`**

* GUID 為建立資料後產生，如需立刻看到可以手動「執行SQL」

#### 選擇障礙？

|方法| 流水式 | GUID |
|--| -------- | -------- |
|用途| 多數案例使用 | 注重前後關係 |
|範例|一般主檔、交易檔 | 簽核檔 |

## 資料類型不允許儲存變更

工具>選項>設計師>取消勾選「防止儲存需要資料表重建的變更」

## 欄位資料類型

* 表格內僅列舉部分，常用部分粗體表示

| 文字 | 整數數字 | 小數數字 | 日期 |
| ---- | ------ | -------- | ---- |
| Char |**int** | **decimal** | date  |
| **VarChar**  |**bit**    | float   | time  |
| NVarChar |bigint |  money | **datetime** |

### Char

* 缺點：易出現搜尋錯誤狀況

![char](https://i.imgur.com/UDC3XYm.png)

### VarChar

![VarChar](https://i.imgur.com/u6dGegL.png)

### NVarChar

* 支援多國語系

![NVarChar](https://i.imgur.com/amMsVoj.png)

### 數字

* bit, int 不用列長度
* decimal 需要列出長度
  * decimal[ ( p[ , s] ) ]
  * p (有效位數)
  * s (小數位數)
  * 例如：25.99 --> `decimal(2, 2)`

### 時間

* datetime：日期
* smalldatetime：日期+時間

### NULL

* 必填欄位

## Import Data

以[郵遞區號 3+2 ](https://www.post.gov.tw/post/internet/Download/index.jsp?ID=2292)為例