# SQLチートシート

代表的なSQLクエリとその例をまとめています。

RDBMS製品によっては利用できないものがあることに留意が必要です。

SQLの例はスペース削減のため、フォーマットを行っていません。

実装時には[SQLスタイルガイド](sqlstyle.guide.ja.md)にしたがいます。

## 目次

- [SQLチートシート](#sqlチートシート)
  - [目次](#目次)
  - [検索](#検索)
    - [**SELECT**](#select)
    - [**DISTINCT**](#distinct)
    - [**WHERE**](#where)
    - [**ORDER BY**](#order-by)
    - [**SELECT TOP**](#select-top)
    - [**LIKE**](#like)
      - [LIKE設定例](#like設定例)
    - [**IN**](#in)
    - [**BETWEEN**](#between)
    - [**NULL**](#null)
    - [**AS**](#as)
    - [**UNION**](#union)
    - [**INTERSECT**](#intersect)
    - [**EXCEPT（MINUS）**](#exceptminus)
    - [**ANY|ALL**](#anyall)
    - [**GROUP BY**](#group-by)
    - [**HAVING**](#having)
  - [更新](#更新)
    - [**INSERT INTO**](#insert-into)
    - [**UPDATE**](#update)
    - [**DELETE**](#delete)
  - [集計関数](#集計関数)
    - [**COUNT**](#count)
    - [**MIN / MAX**](#min--max)
    - [**AVG()**](#avg)
    - [**SUM()**](#sum)
  - [結合](#結合)
    - [**INNER JOIN**](#inner-join)
    - [**LEFT（OUTER）JOIN**](#leftouterjoin)
    - [**RIGHT（OUTER）JOIN**](#rightouterjoin)
    - [**FULL（OUTER）JOIN**](#fullouterjoin)
  - [ビュー](#ビュー)
    - [**CREATE VIEW**](#create-view)
    - [**DROP VIEW**](#drop-view)
  - [テーブル](#テーブル)
    - [**CREATE TABLE**](#create-table)
    - [**DROP TABLE**](#drop-table)
  - [テーブルの編集](#テーブルの編集)
    - [**ALTER TABLE ADD**](#alter-table-add)
    - [**ALTER TABLE MODIFY**](#alter-table-modify)
    - [**ALTER TABLE DROP**](#alter-table-drop)
  - [出典](#出典)

## 検索

### **SELECT**

データベースからデータを検索する。

```SQL
SELECT * FROM table_name;
```

### **DISTINCT**

重複する値を除外し、指定された列の行を検索する。

```SQL
SELECT DISTINCT column_name FROM table_name;
```

### **WHERE**

結果のフィルタリングを行う。

```SQL
SELECT column1, column2 FROM table_name WHERE column1 = X;
-- 複数の条件の論理積　AND
SELECT * FROM table_name  WHERE column1 = X AND column2 = Y;
-- 複数の条件の論理和　OR
SELECT * FROM table_name WHERE column1 = X OR column2 = Y;
-- 条件の否定　NOT
SELECT * FROM table_name WHERE NOT column1 = X;
-- 副問合せ結果の存在確認　EXISTS
SELECT * FROM table_name WHERE EXISTS (SELECT column_name FROM table_name WHERE column1 = X);
```

### **ORDER BY**

検索結果のソートを行う。

照合順序（`ASC`, `DESC`）は必ず指定する。

> 指定しない場合はデータベースの設定に依存する

```SQL
-- 降順でソートする
SELECT * FROM table_name ORDER BY column DESC;
-- column1を昇順でソート後、column2を降順でソートする
SELECT * FROM table_name ORDER BY column1 ASC, column2 DESC;
```

### **SELECT TOP**

テーブルの上位から指定された数の行を検索する。

```SQL
SELECT TOP 5 columns_names FROM table_name WHERE column1 = X;
SELECT TOP 5 percent columns_names FROM table_name WHERE column1 = X;
-- MySQLではSELECT TOPではなく、LIMITを利用する
SELECT column_names FROM table_name LIMIT 0, 5;
```

> LIMITの詳しい利用方法は[公式ドキュメント](https://dev.mysql.com/doc/refman/8.0/ja/select.html)参照

### **LIKE**

特定のカラムに対してあいまい検索を行う。

`%`は任意の0文字以上の文字列を表す。

`_`は任意の1文字を表す。

```SQL
SELECT column_names FROM table_name WHERE column_name LIKE 'a%';
```

#### LIKE設定例

- `LIKE` 'a%'（「a」から始まる文字列）
- `LIKE` '%a'（「a」で終わる文字列）
- `LIKE` '%or%'（どこかに「or」を含む文字列）
- `LIKE` '_r%'（2番目に「r」を含む文字列）
- `LIKE` 'a_%'（「a」から始まり最低2文字の長さの文字列）
- `LIKE` '[a-c]%'（「a」,「b」,「c」のいずれかから始まる文字列）

### **IN**

WHERE句で複数の値の特定をする

```SQL
SELECT * FROM table_name WHERE column_name IN (value1, value2, …);
-- 副問合せに含まれるか
SELECT * FROM table_name_1 WHERE column_name IN (SELECT column_names FROM table_name_2);
```

### **BETWEEN**

指定された範囲の値を選択する

```SQL
-- column_nameが1から10に一致する
SELECT column_names FROM table_name WHERE column_name BETWEEN 1 AND 10;
-- column_nameが1から10に一致する、かつcolumn_name2に「aaa」と「bbb」が含まれない
SELECT * FROM Products WHERE (column_name BETWEEN 1 AND 10) AND NOT column_name2 IN ('aaa', 'bbb');
-- column_nameが日時'2020-07-01 00:00:00'から'2020-07-31 23:59:59'に一致する
SELECT * FROM Products WHERE column_name BETWEEN '2020-07-01 00:00:00' AND '2020-07-31 23:59:59';
```

> 日時の扱いはデータベースの型と一致させることに注意する

### **NULL**

値が存在しないカラムを求める

**NULL**は**値**ではないことに注意する。

> 詳しくは[コラム：NULLを知り、正しく向き合う](know_what_is_null.md)を参照

```SQL
-- NULLのカラム
SELECT * FROM table_name WHERE column_name IS NULL;
-- NULL以外のカラム
SELECT * FROM table_name WHERE column_name IS NOT NULL;
```

### **AS**

テーブルやカラムにエイリアスを設定する

```SQL
-- カラム別名を設定
SELECT column_name AS alias_name FROM table_name;
-- テーブル別名を設定
SELECT column_name FROM table_name AS alias_name;
-- 複数のカラム別名を設定
SELECT column_name AS alias_name1, column_name2 AS alias_name2;
-- 結合した結果に対してカラム別名を設定
SELECT column_name1, column_name2 + `, ` + column_name3 AS alias_name;
```

### **UNION**

2つ以上の問い合わせ結果の和集合を求める

- **UNION**で接続する各**SELECT**文はカラムの数を一致させる
- 各カラムは同じデータ型である
- 各**SELECT**文のカラムの順序は同じである

```SQL
-- 重複を排除
(SELECT columns_name FROM table1) UNION (SELECT column_name FROM table2);
-- 結果に重複あり
(SELECT columns_name FROM table1) UNION ALL (SELECT column_name FROM table2);
```

重複を気にしないのであれば、パフォーマンスに優れた**UNION ALL**を利用する。

> 詳しくは[コラム：非効率なSQLを学ぶ](inefficient_query.md)を参照

### **INTERSECT**

2つの問い合わせ結果の積集合（集合の重なり部分）を求める

利用方法は**UNION**と同様。

```SQL
(SELECT columns_name FROM table1) INTERSECT (SELECT column_name FROM table2);
(SELECT columns_name FROM table1) INTERSECT ALL (SELECT column_name FROM table2);
```

> Oracle 19c以前では**ALL**は利用できない
>
> MySQLでは利用できない

### **EXCEPT（MINUS）**

2つの問い合わせ結果の差集合（1つ目の問い合わせ結果から2つ目の問い合わせ結果に存在しない部分）を求める

利用方法は**UNION**と同様。

> Oracle 19c以前では**MINUS**を利用する。また**ALL**は利用できない
>
> MySQLでは利用できない

```SQL
(SELECT columns_names FROM table1) EXCEPT (SELECT column_name FROM table2);
(SELECT columns_names FROM table1) EXCEPT ALL (SELECT column_name FROM table2);
```

### **ANY|ALL**

**WHERE**または**HAVING**句で副問合せをチェックする。

- **ANY**は副問合せのいずれかが左辺と一致した場合`true`
- **ALL**は副問合せのすべてが左辺と一致した場合`true`
- 比較演算子（`=`, `!=`, `>`, `<`, `<=`, `>=`）と共に利用する

```SQL
SELECT columns_names FROM table1 WHERE column_name >= ANY (SELECT column_name FROM table_name WHERE column1 = X);
SELECT columns_names FROM table1 WHERE column_name >= ALL (SELECT column_name FROM table_name WHERE column1 = X);
```

### **GROUP BY**

結果を1つ以上の列でグループ化する。主に集約関数（COUNT、MAX、MIN、SUM、AVG）と共に利用する。

```SQL
SELECT column_name1, COUNT(column_name2) FROM table_name WHERE column_name2 > 100 GROUP BY column_name1 ORDER BY COUNT(column_name2) DESC;
```

### **HAVING**

集計関数による集計後に絞り込みを行う。

```SQL
SELECT COUNT(column_name1), column_name2 FROM table GROUP BY column_name2 HAVING COUNT(column_name1) > 5;
```

> **HAVING**句は[リレーショナルデータベースの世界](http://mickindex.sakura.ne.jp/database/idx_database.html)でさまざまな利用方法が紹介されています。

## 更新

### **INSERT INTO**

テーブルに新しいレコードを追加する。

```SQL
INSERT INTO table_name (column1, column2) VALUES (value1, value2);
INSERT INTO table_name VALUES (value1, value2 …);
```

### **UPDATE**

テーブルの既存のレコードを更新する。

```SQL
UPDATE table_name SET column1 = value1, column2 = value2 WHERE column_name = X;
UPDATE table_name SET column_name = value1;
```

### **DELETE**

レコードを削除する。

```SQL
DELETE FROM table_name WHERE column_name = X;
DELETE * FROM table_name;
```

## 集計関数

### **COUNT**

行数をカウントする。

```SQL
SELECT COUNT (DISTINCT column_name);
```

### **MIN / MAX**

最小値／最大値を求める。

```SQL
SELECT MIN(column_names) FROM table_name WHERE condition;
SELECT MAX(column_names) FROM table_name WHERE condition;
```

### **AVG()**

数値カラムの平均値を求める。

```SQL
SELECT AVG (column_name) FROM table_name WHERE condition;
```

### **SUM()**

数値カラムの合計値を求める。

```SQL
SELECT SUM (column_name) FROM table_name WHERE condition;
```

## 結合

### **INNER JOIN**

両方のテーブルで一致する値をもつレコードを求める。

```SQL
SELECT column_names FROM table1 INNER JOIN table2 ON table1.column_name=table2.column_name;
SELECT table1.column_name1, table2.column_name2, table3.column_name3 FROM ((table1 INNER JOIN table2 ON table1.column_name=table2.column_name) INNER JOIN table3 ON table1.column_name=table3.column_name);
```

### **LEFT（OUTER）JOIN**

左のすべてのレコードと右のマッチしたレコードを検索する。

```SQL
SELECT column_names FROM table1 LEFT JOIN table2 ON table1.column_name=table2.column_name;
```

### **RIGHT（OUTER）JOIN**

右のすべてのレコードと左のマッチしたレコードを検索する。

```SQL
SELECT column_names FROM table1 RIGHT JOIN table2 ON table1.column_name=table2.column_name;
```

### **FULL（OUTER）JOIN**

お互いのテーブルのマッチするレコードをすべて検索する。

> MySQLでは利用できない

```SQL
SELECT column_names FROM table1 FULL OUTER JOIN table2 ON table1.column_name=table2.column_name;
```

## ビュー

### **CREATE VIEW**

ビューの作成。

```SQL
CREATE VIEW view_name AS SELECT column1, column2 FROM table_name WHERE column1 = X;
```

### **DROP VIEW**

ビューの削除。

```SQL
DROP VIEW view_name;
```

## テーブル

### **CREATE TABLE**

テーブルの作成。

```SQL
CREATE TABLE table_name (
   column1 datatype,
   column2 datatype,
   column3 datatype,
   column4 datatype,
   );
```

### **DROP TABLE**

テーブルの削除。

```SQL
DROP TABLE table_name;
```

## テーブルの編集

### **ALTER TABLE ADD**

カラムの追加。

```SQL
ALTER TABLE table_name ADD column_name1 VARCHAR(45) NULL;
```

### **ALTER TABLE MODIFY**

カラムのデータ型の変更。

```SQL
ALTER TABLE table_name MODIFY column_name VARCHAR(45);
```

### **ALTER TABLE DROP**

カラムの削除。

```SQL
ALTER TABLE table_name DROP COLUMN column_name;
```

## 出典

本チートシートは次を改変して作成した。

[enochtangg/quick-SQL-cheatsheet](https://github.com/enochtangg/quick-SQL-cheatsheet)

[Copyright (c) 2018 Enoch Tang](https://github.com/enochtangg/quick-SQL-cheatsheet/blob/master/LICENSE)
