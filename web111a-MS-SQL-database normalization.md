# 資料庫正規劃

###### tags: `程式筆記` `web111a` `MS-SQL`

* **老師：許志強**
* 時間：2022/4/6

## 目的

* 避免資料重複
* 增加查詢速度

## 作法

* 一階正規劃～六階正規劃(1NF~6NF)
* 實務上只會做到3NF

![normalization](https://i.imgur.com/KG9sLP8.png)

1. 列出所有欄位（參考網路）
2. 找出唯一值
3. 各欄位與關鍵欄位比較判定相關
   1. 1:1絕對相關
   2. 1:多相對相關
4. 相對欄位獨立出去
5. 刪除相對欄位

![3NF](https://i.imgur.com/xHFmImB.jpg)

## 課堂作業

![practice](https://i.imgur.com/eb7nndT.png)

### 欄位命名原則

#### follow the rules

#### create the rules

#### 例如

* 主檔(m_no, m_name...)
* 單據(sheet_no, sheet_name...)
* 性別(gender_code)內容會固定
  * 1(男)
  * 2(女)
  * 3(其他)

### 資料表命名

![table naming](https://i.imgur.com/D5TDbA1.png)

* (銷售類_銷售_主檔)sal_sale_master
* (基本資料_產品檔)bas_product

### 建立索引

### 外部鍵

* 資料庫圖表
  * 描述
  * 手動調整關聯線（非必要）

## SQL 語言

![sql](https://i.imgur.com/77ahXBO.png)

### 切換資料庫

```sql=
USE [master]
GO
```
