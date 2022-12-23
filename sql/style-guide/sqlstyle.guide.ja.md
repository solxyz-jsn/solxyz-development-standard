# SQLスタイルガイド

[![sqlstyle.guide](https://img.shields.io/badge/style-sqlstyle.guide-brightgreen.svg)](https://www.sqlstyle.guide/)

## 本ガイドについて

本ガイドは[SQL style guide by Simon Holywell][original]（著者：[Simon Holywell][simon]  翻訳：[久利史之][twitter-ja] ©[クリエイティブ・コモンズ 表示-継承4.0国際ライセンス][licence-ja]）を改変して作成している。

原文の分かりづらい箇所、過剰と判断した箇所について、補足、削除等を行っている。

内容について要望等がある場合はGitHubのissueまたはpull requestを使用する。

## 目次

- [全般](#全般)
  - [推奨事項](#推奨事項)
  - [非推奨事項](#非推奨事項)
- [命名規則](#命名規則)
  - [通則](#通則)
  - [テーブル名](#テーブル名)
  - [カラム名](#カラム名)
  - [エイリアスと相関名](#エイリアスと相関名)
  - [ストアドプロシージャ](#ストアドプロシージャ)
  - [統一的接尾辞](#統一的接尾辞)
- [問合せ文](#問合せ文)
  - [予約語](#予約語)
  - [空白類](#空白類)
    - [インデントと改行](#インデントと改行)
    - [結合](#結合)
    - [副問合せ](#副問合せ)
  - [望ましい形式](#望ましい形式)
- [CREATE文](#create文)
  - [データ型の選択](#データ型の選択)
  - [デフォルト値の指定](#デフォルト値の指定)
  - [制約とキー](#制約とキー)
  - [非推奨設計](#非推奨設計)
- [付録](#付録)
  - [予約語リファレンス](#予約語リファレンス)
  - [推奨データ型](#推奨データ型)
    - [文字型](#文字型)
    - [数値型](#数値型)
    - [日付型](#日付型)
    - [バイナリ型](#バイナリ型)
    - [その他の型](#その他の型)

<div style="page-break-before:always"></div>

## 全般

### 推奨事項

プロジェクトにより利用できないことはあるが、制限がない限り、次の規則を推奨する。

- 一貫性があり説明的な識別子と名前を使用する。

  事前に用語辞書を作成するなど、プロジェクト内で共通の識別子と名前を使用する。

- スペースとインデントを慎重に使用しコードを読みやすくする。
- [ISO-8601][iso-8601]に準拠した日付時間フォーマット（`YYYY-MM-DD HH:MM:SS.SSSSS`）で格納する。
- 移植性のためベンダー固有の関数の代わりに標準のSQL関数のみを使用する。
- コードを簡潔で冗長なSQLのない状態に保つ。たとえば、不必要なクォート、括弧、他の条件と重なる `WHERE` 句は避ける。
- 必要に応じてSQLコードにコメントを挿入する。可能なら `/*` で始まり `*/` で終わるC言語スタイルのコメントを使用し、その他の場合、`--` で始まり改行で終わる行コメントを使用する。

```sql
SELECT
  file_hash  -- 格納されたSSDEEPハッシュ
FROM
  file_system
WHERE
  file_name = '.vimrc';
```

```sql
/* ファイルの書き込み後ファイルレコードを更新する */
UPDATE
  file_system
SET
  file_modified_date = '1980-02-22 13:19:01.00000',
  file_size = 209732
WHERE
  file_name = '.vimrc';
```

<div style="page-break-before:always"></div>

### 非推奨事項

プロジェクトにより制限がない限り、次の規則を非推奨とする。

- CamelCase（例：`FileSize`）
- 説明的接頭辞やハンガリアン記法（`sp_`または`tbl_`など）。

  そのような接頭辞がなくても説明可能な命名を行う。

- 複数形

  できるだけ集合体を表す用語を使用する。たとえば`employees`の代わりに`staff`、または`individuals`の代わりに`people`を使用する。

  目的は複数形の`s`を忘れることによる不具合を減らすことにある。

  用語辞書やテーブル仕様作成時に考慮されている必要がある。

- 引用符で囲まれた識別子

  使用しなければならない場合、移植性のためSQL92の二重引用符が欠かせなくなる（ベンダーによってはサーバーを構成する必要がある）。

- オブジェクト指向設計原則をSQLまたはデータベース構造に適用すべきではない。

  データベースの構造はデータベースの設計プロセスに従うべきであり、正規化などのプロセスにプログラム側のオブジェクト指向の概念を含めるべきではない。

### 推奨非推奨まとめ

  | 項目                    | 推奨                           | 非推奨                      |
  | ----------------------- | ----------------------------- | --------------------------- |
  | コメント                | 適宜付与する                   | -                           |
  | 名称フォーマット         | `file_size`（スネークケース）  | `FileSize`（キャメルケース） |
  | 名称接頭辞              | 使用しない                     | `sp_`または`tbl_`など        |
  | 日付時間フォーマット     | [ISO-8601][iso-8601]に準拠    | -                           |
  | 複数を表現する名称       | 集合体 例：`staff`            | 複数形 例：`employees`       |
  | 引用符で囲まれた識別子   | 極力使用しない                 | -                           |
  | オブジェクト指向設計原則 | 適用しない                     | -                           |
  | ベンダー固有の関数       | 利用しない                     | -                           |
  | SQLコード               | 簡潔で冗長なSQLのない状態に保つ | -                           |

<div style="page-break-before:always"></div>

## 命名規則

### 通則

- 名前が一意であり、[予約語](#予約語リファレンス)に存在しないことを確認する。
- 桁数を最大30バイトにする。実務的にはマルチバイト文字セットを除き30文字である。
- 名前は文字で始めなければならずアンダースコアでは終わらない方が良い。
- 名前には英字、数字、アンダースコアのみを使用する。
- 複数の連続したアンダースコアの使用を避ける。読取るのが難しくなる。
- 名前にスペースを含めるのが自然な場合はアンダースコアを使用する。（first nameは`first_name`）
- 略語を避ける。略語を使う必要がある場合は、一般的に通じるものであることを確認する。

```sql
SELECT
  first_name
FROM
  staff;
```

### テーブル名

- 集合名詞を使用するか、望ましくはないが、複数形を使用する。たとえば、`employees`より`staff`が望ましい。
- `tbl`などの接頭辞やハンガリアン記法による接頭辞を付けない。
- テーブルにカラムの名前と同じ名前を付けない。その逆も同様である。
- 関連付けするテーブルの名前に2つのテーブル名を連結した名前を付けないようにする。`cars_mechanics`より`services`が望ましい。

### カラム名

- 常に単数形の名前を使用する。
- 主キーに単純に`id`を使うのは極力避ける。
- テーブルと同じ名前のカラムを追加しない。逆もまた同様である。
- 固有名詞など意味のある場合を除いて、常に小文字を使用する。

テーブル名やカラム名に固有名詞を使わないといけない場合はそれ自体を再考することを検討する。

<div style="page-break-before:always"></div>

### エイリアスと相関名

- 何らかの方法でオブジェクトまたはそのエイリアスへ関連付けをすべきである。
- 大雑把な方法として相関名はオブジェクト名の先頭文字を使う。
- すでに同じ相関名がある場合は数値を追加する。
- 常に`AS`キーワードを記載する。明示的であれば読みやすくなる。
- 計算データ（`SUM()`、`AVG()`）には、それが実際のカラムにあるつもりで名付ける。

```sql
SELECT
  first_name AS fn
FROM
  staff AS s1
JOIN
  students AS s2
    ON s2.mentor_id = s1.staff_num;
```

```sql
SELECT
  SUM(s.monitor_count) AS monitor_total
FROM
  staff AS s;
```

<div style="page-break-before:always"></div>

### ストアドプロシージャ

- 名前に動詞を含める。
- `sp_`またはそのような説明的接頭辞やハンガリアン記法を含めない。

`sp_`から始まるストアド・プロシージャはなじみがある命名であるが、適切に動詞が含まれていればこの接頭辞は必要がない。

### 統一的接尾辞

以下の接尾辞は一般的意味を持ち、SQLコードからカラムを読み取り理解しやすくする。適切な箇所で正しい接尾辞を使用すること。

- `_id` - 主キーであるカラムなど一意の識別子。
- `_status` - flag値または任意のタイプの状況を表す（例: publication_status）。
- `_total` - 値の集合の合計または総計。
- `_num` - フィールドに数値が含まれていることを表す。
- `_name` - first_nameのように名前を強調する。
- `_seq` - 連続した数値を含む。
- `_date` - 何かの日付を含むカラムであることを表す。
- `_count` - カウント。
- `_size` - ファイルサイズや衣類などのサイズ。
- `_addr` - 有形無形のデータのアドレス（例: ip_addr）。

<div style="page-break-before:always"></div>

## 問合せ文

> [原文](https://www.sqlstyle.guide/)ではフォーマットについて、スペースを多用して[RIVERS（スペースによる川）][rivers]を形作ることが推奨されているが、手間とそれから受ける利益を考慮すると本ガイドでは採用しない。

### 予約語

`SELECT`や`WHERE`など[予約語](#予約語リファレンス)は常に大文字を使用する。

略語を避け利用可能な完全なキーワードを使用するのがもっとも望ましい。（`ABS`より`ABSOLUTE`が望ましい。）

同じ機能を有するANSI SQLキーワードがすでに存在する場合はデータベース固有のものは使用しない。これはコードの移植性をより高くするためである。

```sql
SELECT
  model_num
FROM
  phones AS p
WHERE
  p.release_date > '2014-09-30';
```

### 空白類

コードを読みやすくするには、適切にスペースを補完することが重要である。コードを密集させたり、自然言語にあるスペースを削除したりしてはならない。

#### インデントと改行

インデントと改行を活用して同じ階層のキーワードが一列に並ぶように記載する。

- [予約語](#予約語リファレンス)毎に改行をする（`AS`など直前の値を修飾する語は除く）
- 同じ階層のキーワードが一列に並ぶように改行する
  - `SELECT`命令などの後に記述するカラム名などは必要に応じて改行する（読みやすさを考慮する）
- 次の例のように`UNION`などで複数の問い合わせを結合する場合はカッコも独立して改行し、見やすさを確保する。

<div style="page-break-before:always"></div>

```sql
(
  SELECT
    f.species_name,
    AVG(f.height) AS average_height,
    AVG(f.diameter) AS average_diameter
  FROM
    flora AS f
  WHERE
    f.species_name = 'Banksia'
  OR
    f.species_name = 'Sheoak'
  OR
    f.species_name = 'Wattle'
  GROUP BY
    f.species_name,
    f.observation_date
)
UNION ALL
(
  SELECT
    b.species_name,
    AVG(b.height) AS average_height,
    AVG(b.diameter) AS average_diameter
  FROM
    botanic_garden_flora AS b
  WHERE
    b.species_name = 'Banksia'
  OR
    b.species_name = 'Sheoak'
  OR
    b.species_name = 'Wattle'
  GROUP BY
    b.species_name, b.observation_date
);
```

<div style="page-break-before:always"></div>

網羅していないが、以下の場合は常にスペースを入れる。

- イコール（`=`）の前後
- カンマ（`,`）の後（改行が続く場合は除く）
- アポストロフィ（`'`）の外側（括弧内またはカンマやセミコロンが後に来る場合は除く）

```sql
SELECT
  a.title,
  a.release_date,
  a.recording_date
FROM
  albums AS a
WHERE
  a.title = 'Charcoal Lane'
OR
  a.title = 'The New Danger';
```

#### 結合

`JOIN`句は、`FROM`句と同じ段落に記載し、その条件の`ON`は結合するテーブルと同じ位置に揃える。

また内部結合の場合、必ず`INNER JOIN`を利用する。（`WHERE`句内で結合条件を記述する書き方をしない。）

```sql
SELECT
  r.last_name
FROM
  riders AS r
INNER JOIN
  bikes AS b
  ON
    r.bike_vin_num = b.vin_num
  AND
    b.engine_tally > 2
INNER JOIN
  crew AS c
  ON
    r.crew_chief_last_name = c.last_name
  AND
    c.chief = 'Y';
```

<div style="page-break-before:always"></div>

#### 副問合せ

括弧で囲まれた副問合せを配置する場合、次のように記述する。

`SELECT`句の後の（1）と（2）の副問合せは等価なため、（1）の頭と（2）の頭の括弧は同じ位置から開始する。

`WHERE`句に記述されている副問合せ（3）は`IN`の内部になるため、1段インデントした位置から開始する。

副問合せがどのキーワードと等価であるかを判断し開始位置を決める。

```sql
SELECT
  r.last_name, -- （1）
  (
    SELECT
      MAX(YEAR(championship_date))
    FROM
      champions AS c
    WHERE
      c.last_name = r.last_name
    AND
      c.confirmed = 'Y'
  ) AS last_championship_year -- （2）
FROM
  riders AS r
WHERE
  r.last_name IN (
    SELECT
      c.last_name
    FROM
      champions AS c
    WHERE
      YEAR(championship_date) > '2008'
    AND
      c.confirmed = 'Y' -- （3）
  );
```

<div style="page-break-before:always"></div>

### 望ましい形式

- 複数の`AND`を組み合わせる代わりに`BETWEEN`を使用する。
- 同様に複数のOR句を使用する代わりに`IN()`句を使用する。
- 使用するデータベースに接続した状態で値を変換する必要がある場合には`CASE`式を使う。`CASE`式はネストしてより複雑な論理構造を形成することができる。
- `UNION`節および一時テーブルは極力避ける。これらの機能へ依存しないようにスキーマを最適化できる場合はそうした方が良い。

```sql
SELECT
  CASE postcode
    WHEN 'BN1' THEN 'Brighton'
    WHEN 'EH1' THEN 'Edinburgh'
  END AS city
FROM
  office_locations
WHERE
  country = 'United Kingdom'
AND
  opening_time BETWEEN 8 AND 9
AND
  postcode IN ('EH1', 'BN1', 'NN1', 'KW1');
```

<div style="page-break-before:always"></div>

## CREATE文

スキーマ情報を宣言する際も人間が読めるコードにすることが重要である。

必要に応じてカラム定義を順序付けしグループ化すると良い。

### データ型の選択

- できるだけベンダー固有のデータ型は使用しないようにする。

  これらは移植性がないだけでなく、同じベンダーのソフトウェアの古いバージョンでは使用できない可能性がある。

  [推奨データ型](#推奨データ型)

- 浮動小数点による計算がどうしても必要な場合のみ`REAL`または`FLOAT`型を使い、それ以外は常に`NUMERIC`と`DECIMAL`型が望ましい。

  浮動小数点の丸め誤差は煩わしい。

### デフォルト値の指定

- カラムのデフォルト値はカラムと同じ型でなければならない。

  カラムが`DECIMAL`型で宣言されている場合、`INTEGER`をデフォルト値としないようにする。

- デフォルト値は、データ型の宣言の後、`NOT NULL`文の前に来なければならない。

### 制約とキー

制約とそのサブセットであるキーは、データベース定義の非常に重要な要素である。それらはすぐに判別困難になる可能性がある。

だからこそ次のようなガイドラインの基準が重要である。

#### キーの選択

定義においてキーとなるカラムを決定することは、パフォーマンスとデータの整合性に影響するため、慎重に検討されるべきである。

1. キーはある程度一意でなければならない。
2. スキーマ全体を通じデータ型の一貫性があり、将来の変更可能性が低いこと。
3. 標準的なフォーマット（ISOで公開されているものなど）で値を検証できるようにする。これは項番2に通じる。
4. キーをできるだけシンプルに保つ一方で、必要に応じて複合キーを恐れずに使用する。

これはデータベース定義の時点で論理的かつ慎重に行われる作業である。

万一、将来要件が変わっても定義を変更し最新の状態に保つことを可能にする。

<div style="page-break-before:always"></div>

#### 制約の定義

キーが決まれば、フィールド値の検証とともに制約を利用してシステム上でキーを定義することができる。

##### 通則（キーの選択）

- テーブルには、完全で有用なキーが少なくとも1つ必要である。
- `UNIQUE`、`PRIMARY KEY`、`FOREIGN KEY`と言ったデータベースベンダーが自動で付与する自明のものを除き、制約には独自の名称を付与する。

##### レイアウトと順序

- `CREATE TABLE`文の直後に`PRIMARY KEY`を定める。
- 制約は、対応するカラムの直下に定義する。
- 複数カラム制約であれば、可能な限り両方のカラム定義近くに配置することを検討する。それが困難な場合は、最後の手段として`CREATE TABLE`定義の最後に含める。
- テーブル全体に適用されるテーブルレベルの制約であればそれも最後に表示する。
- アルファベット順を使用する。`ON DELETE`は`ON UPDATE`の前に来る。

##### 検証

- 文字列のフォーマットが分かっている場合は整合性を確保するために`LIKE`と`SIMILAR TO`制約を使用する。
- 数値の範囲が完全に判明している場合は、範囲を`CHECK()`として記述し、データベースへの誤った値が入力されるのを抑止するかカラムの定義に合うように大きすぎるデータの自動切り捨てを行う。多くの場合、少なくとも値が0より大きいかどうかを確認する。
- `CHECK()`制約はデバッグを容易にするため独立した節として記述する。

##### 例

```sql
CREATE TABLE staff (
    PRIMARY KEY (staff_num),
    staff_num INT NOT NULL,
    first_name VARCHAR(100) NOT NULL,
    pens_in_drawer INT NOT NULL,
      CONSTRAINT pens_in_drawer_range
        CHECK (pens_in_drawer BETWEEN 1 AND 99)
);
```

<div style="page-break-before:always"></div>

### 非推奨設計

次のような設計は行わない。

- オブジェクト指向設計原則は、リレーショナルデータベース設計へ効果的に変換されない。

- あるカラムに値を配置し、別のカラムに単位があること。

  | 単位 | 値 |
  | --- | --- |
  | kg | 68 |
  | cm | 170 |

  そのカラムの単位が自明となるようにし、アプリケーションでカラムを再度結合する必要性をなくすべきである。

  そのカラムに挿入されたデータの有効性を確保するため`CHECK()`制約を使用する。

- EAV（エンティティ・アトリビュート・バリュー）テーブル。

  ひとつ前の非推奨設計と同様の理由。

  EAVの複雑さは多くの資料が公開されているので、

  そのようなスキーマレスデータを扱うための専用製品を使用する。

- 本来1つにまとめるべきデータを時間単位のアーカイブや多国籍企業の所在地といった任意の問題により多数のテーブルに分割すること。

  1つのテーブルを照会する単純な問合せの代わりに`UNION`句により複数のテーブルにまたがった問合せを作成する必要が出てくる。

<div style="page-break-before:always"></div>

## 付録

### 予約語リファレンス

ANSI SQL（92,99および2003）、MySQL 3から5.x、PostgreSQL 8.1、MS SQL Server 2000、MS ODBCおよびOracle 10.2の予約語リスト

```sql
A
ABORT
ABS
ABSOLUTE
ACCESS
ACTION
ADA
ADD
ADMIN
AFTER
AGGREGATE
ALIAS
ALL
ALLOCATE
ALSO
ALTER
ALWAYS
ANALYSE
ANALYZE
AND
ANY
ARE
ARRAY
AS
ASC
ASENSITIVE
ASSERTION
ASSIGNMENT
ASYMMETRIC
AT
ATOMIC
ATTRIBUTE
ATTRIBUTES
AUDIT
AUTHORIZATION
AUTO_INCREMENT
AVG
AVG_ROW_LENGTH
BACKUP
BACKWARD
BEFORE
BEGIN
BERNOULLI
BETWEEN
BIGINT
BINARY
BIT
BIT_LENGTH
BITVAR
BLOB
BOOL
BOOLEAN
BOTH
BREADTH
BREAK
BROWSE
BULK
BY
C
CACHE
CALL
CALLED
CARDINALITY
CASCADE
CASCADED
CASE
CAST
CATALOG
CATALOG_NAME
CEIL
CEILING
CHAIN
CHANGE
CHAR
CHAR_LENGTH
CHARACTER
CHARACTER_LENGTH
CHARACTER_SET_CATALOG
CHARACTER_SET_NAME
CHARACTER_SET_SCHEMA
CHARACTERISTICS
CHARACTERS
CHECK
CHECKED
CHECKPOINT
CHECKSUM
CLASS
CLASS_ORIGIN
CLOB
CLOSE
CLUSTER
CLUSTERED
COALESCE
COBOL
COLLATE
COLLATION
COLLATION_CATALOG
COLLATION_NAME
COLLATION_SCHEMA
COLLECT
COLUMN
COLUMN_NAME
COLUMNS
COMMAND_FUNCTION
COMMAND_FUNCTION_CODE
COMMENT
COMMIT
COMMITTED
COMPLETION
COMPRESS
COMPUTE
CONDITION
CONDITION_NUMBER
CONNECT
CONNECTION
CONNECTION_NAME
CONSTRAINT
CONSTRAINT_CATALOG
CONSTRAINT_NAME
CONSTRAINT_SCHEMA
CONSTRAINTS
CONSTRUCTOR
CONTAINS
CONTAINSTABLE
CONTINUE
CONVERSION
CONVERT
COPY
CORR
CORRESPONDING
COUNT
COVAR_POP
COVAR_SAMP
CREATE
CREATEDB
CREATEROLE
CREATEUSER
CROSS
CSV
CUBE
CUME_DIST
CURRENT
CURRENT_DATE
CURRENT_DEFAULT_TRANSFORM_GROUP
CURRENT_PATH
CURRENT_ROLE
CURRENT_TIME
CURRENT_TIMESTAMP
CURRENT_TRANSFORM_GROUP_FOR_TYPE
CURRENT_USER
CURSOR
CURSOR_NAME
CYCLE
DATA
DATABASE
DATABASES
DATE
DATETIME
DATETIME_INTERVAL_CODE
DATETIME_INTERVAL_PRECISION
DAY
DAY_HOUR
DAY_MICROSECOND
DAY_MINUTE
DAY_SECOND
DAYOFMONTH
DAYOFWEEK
DAYOFYEAR
DBCC
DEALLOCATE
DEC
DECIMAL
DECLARE
DEFAULT
DEFAULTS
DEFERRABLE
DEFERRED
DEFINED
DEFINER
DEGREE
DELAY_KEY_WRITE
DELAYED
DELETE
DELIMITER
DELIMITERS
DENSE_RANK
DENY
DEPTH
DEREF
DERIVED
DESC
DESCRIBE
DESCRIPTOR
DESTROY
DESTRUCTOR
DETERMINISTIC
DIAGNOSTICS
DICTIONARY
DISABLE
DISCONNECT
DISK
DISPATCH
DISTINCT
DISTINCTROW
DISTRIBUTED
DIV
DO
DOMAIN
DOUBLE
DROP
DUAL
DUMMY
DUMP
DYNAMIC
DYNAMIC_FUNCTION
DYNAMIC_FUNCTION_CODE
EACH
ELEMENT
ELSE
ELSEIF
ENABLE
ENCLOSED
ENCODING
ENCRYPTED
END
END-EXEC
ENUM
EQUALS
ERRLVL
ESCAPE
ESCAPED
EVERY
EXCEPT
EXCEPTION
EXCLUDE
EXCLUDING
EXCLUSIVE
EXEC
EXECUTE
EXISTING
EXISTS
EXIT
EXP
EXPLAIN
EXTERNAL
EXTRACT
FALSE
FETCH
FIELDS
FILE
FILLFACTOR
FILTER
FINAL
FIRST
FLOAT
FLOAT4
FLOAT8
FLOOR
FLUSH
FOLLOWING
FOR
FORCE
FOREIGN
FORTRAN
FORWARD
FOUND
FREE
FREETEXT
FREETEXTTABLE
FREEZE
FROM
FULL
FULLTEXT
FUNCTION
FUSION
G
GENERAL
GENERATED
GET
GLOBAL
GO
GOTO
GRANT
GRANTED
GRANTS
GREATEST
GROUP
GROUPING
HANDLER
HAVING
HEADER
HEAP
HIERARCHY
HIGH_PRIORITY
HOLD
HOLDLOCK
HOST
HOSTS
HOUR
HOUR_MICROSECOND
HOUR_MINUTE
HOUR_SECOND
IDENTIFIED
IDENTITY
IDENTITY_INSERT
IDENTITYCOL
IF
IGNORE
ILIKE
IMMEDIATE
IMMUTABLE
IMPLEMENTATION
IMPLICIT
IN
INCLUDE
INCLUDING
INCREMENT
INDEX
INDICATOR
INFILE
INFIX
INHERIT
INHERITS
INITIAL
INITIALIZE
INITIALLY
INNER
INOUT
INPUT
INSENSITIVE
INSERT
INSERT_ID
INSTANCE
INSTANTIABLE
INSTEAD
INT
INT1
INT2
INT3
INT4
INT8
INTEGER
INTERSECT
INTERSECTION
INTERVAL
INTO
INVOKER
IS
ISAM
ISNULL
ISOLATION
ITERATE
JOIN
K
KEY
KEY_MEMBER
KEY_TYPE
KEYS
KILL
LANCOMPILER
LANGUAGE
LARGE
LAST
LAST_INSERT_ID
LATERAL
LEADING
LEAST
LEAVE
LEFT
LENGTH
LESS
LEVEL
LIKE
LIMIT
LINENO
LINES
LISTEN
LN
LOAD
LOCAL
LOCALTIME
LOCALTIMESTAMP
LOCATION
LOCATOR
LOCK
LOGIN
LOGS
LONG
LONGBLOB
LONGTEXT
LOOP
LOW_PRIORITY
LOWER
M
MAP
MATCH
MATCHED
MAX
MAX_ROWS
MAXEXTENTS
MAXVALUE
MEDIUMBLOB
MEDIUMINT
MEDIUMTEXT
MEMBER
MERGE
MESSAGE_LENGTH
MESSAGE_OCTET_LENGTH
MESSAGE_TEXT
METHOD
MIDDLEINT
MIN
MIN_ROWS
MINUS
MINUTE
MINUTE_MICROSECOND
MINUTE_SECOND
MINVALUE
MLSLABEL
MOD
MODE
MODIFIES
MODIFY
MODULE
MONTH
MONTHNAME
MORE
MOVE
MULTISET
MUMPS
MYISAM
NAME
NAMES
NATIONAL
NATURAL
NCHAR
NCLOB
NESTING
NEW
NEXT
NO
NO_WRITE_TO_BINLOG
NOAUDIT
NOCHECK
NOCOMPRESS
NOCREATEDB
NOCREATEROLE
NOCREATEUSER
NOINHERIT
NOLOGIN
NONCLUSTERED
NONE
NORMALIZE
NORMALIZED
NOSUPERUSER
NOT
NOTHING
NOTIFY
NOTNULL
NOWAIT
NULL
NULLABLE
NULLIF
NULLS
NUMBER
NUMERIC
OBJECT
OCTET_LENGTH
OCTETS
OF
OFF
OFFLINE
OFFSET
OFFSETS
OIDS
OLD
ON
ONLINE
ONLY
OPEN
OPENDATASOURCE
OPENQUERY
OPENROWSET
OPENXML
OPERATION
OPERATOR
OPTIMIZE
OPTION
OPTIONALLY
OPTIONS
OR
ORDER
ORDERING
ORDINALITY
OTHERS
OUT
OUTER
OUTFILE
OUTPUT
OVER
OVERLAPS
OVERLAY
OVERRIDING
OWNER
PACK_KEYS
PAD
PARAMETER
PARAMETER_MODE
PARAMETER_NAME
PARAMETER_ORDINAL_POSITION
PARAMETER_SPECIFIC_CATALOG
PARAMETER_SPECIFIC_NAME
PARAMETER_SPECIFIC_SCHEMA
PARAMETERS
PARTIAL
PARTITION
PASCAL
PASSWORD
PATH
PCTFREE
PERCENT
PERCENT_RANK
PERCENTILE_CONT
PERCENTILE_DISC
PLACING
PLAN
PLI
POSITION
POSTFIX
POWER
PRECEDING
PRECISION
PREFIX
PREORDER
PREPARE
PREPARED
PRESERVE
PRIMARY
PRINT
PRIOR
PRIVILEGES
PROC
PROCEDURAL
PROCEDURE
PROCESS
PROCESSLIST
PUBLIC
PURGE
QUOTE
RAID0
RAISERROR
RANGE
RANK
RAW
READ
READS
READTEXT
REAL
RECHECK
RECONFIGURE
RECURSIVE
REF
REFERENCES
REFERENCING
REGEXP
REGR_AVGX
REGR_AVGY
REGR_COUNT
REGR_INTERCEPT
REGR_R2
REGR_SLOPE
REGR_SXX
REGR_SXY
REGR_SYY
REINDEX
RELATIVE
RELEASE
RELOAD
RENAME
REPEAT
REPEATABLE
REPLACE
REPLICATION
REQUIRE
RESET
RESIGNAL
RESOURCE
RESTART
RESTORE
RESTRICT
RESULT
RETURN
RETURNED_CARDINALITY
RETURNED_LENGTH
RETURNED_OCTET_LENGTH
RETURNED_SQLSTATE
RETURNS
REVOKE
RIGHT
RLIKE
ROLE
ROLLBACK
ROLLUP
ROUTINE
ROUTINE_CATALOG
ROUTINE_NAME
ROUTINE_SCHEMA
ROW
ROW_COUNT
ROW_NUMBER
ROWCOUNT
ROWGUIDCOL
ROWID
ROWNUM
ROWS
RULE
SAVE
SAVEPOINT
SCALE
SCHEMA
SCHEMA_NAME
SCHEMAS
SCOPE
SCOPE_CATALOG
SCOPE_NAME
SCOPE_SCHEMA
SCROLL
SEARCH
SECOND
SECOND_MICROSECOND
SECTION
SECURITY
SELECT
SELF
SENSITIVE
SEPARATOR
SEQUENCE
SERIALIZABLE
SERVER_NAME
SESSION
SESSION_USER
SET
SETOF
SETS
SETUSER
SHARE
SHOW
SHUTDOWN
SIGNAL
SIMILAR
SIMPLE
SIZE
SMALLINT
SOME
SONAME
SOURCE
SPACE
SPATIAL
SPECIFIC
SPECIFIC_NAME
SPECIFICTYPE
SQL
SQL_BIG_RESULT
SQL_BIG_SELECTS
SQL_BIG_TABLES
SQL_CALC_FOUND_ROWS
SQL_LOG_OFF
SQL_LOG_UPDATE
SQL_LOW_PRIORITY_UPDATES
SQL_SELECT_LIMIT
SQL_SMALL_RESULT
SQL_WARNINGS
SQLCA
SQLCODE
SQLERROR
SQLEXCEPTION
SQLSTATE
SQLWARNING
SQRT
SSL
STABLE
START
STARTING
STATE
STATEMENT
STATIC
STATISTICS
STATUS
STDDEV_POP
STDDEV_SAMP
STDIN
STDOUT
STORAGE
STRAIGHT_JOIN
STRICT
STRING
STRUCTURE
STYLE
SUBCLASS_ORIGIN
SUBLIST
SUBMULTISET
SUBSTRING
SUCCESSFUL
SUM
SUPERUSER
SYMMETRIC
SYNONYM
SYSDATE
SYSID
SYSTEM
SYSTEM_USER
TABLE
TABLE_NAME
TABLES
TABLESAMPLE
TABLESPACE
TEMP
TEMPLATE
TEMPORARY
TERMINATE
TERMINATED
TEXT
TEXTSIZE
THAN
THEN
TIES
TIME
TIMESTAMP
TIMEZONE_HOUR
TIMEZONE_MINUTE
TINYBLOB
TINYINT
TINYTEXT
TO
TOAST
TOP
TOP_LEVEL_COUNT
TRAILING
TRAN
TRANSACTION
TRANSACTION_ACTIVE
TRANSACTIONS_COMMITTED
TRANSACTIONS_ROLLED_BACK
TRANSFORM
TRANSFORMS
TRANSLATE
TRANSLATION
TREAT
TRIGGER
TRIGGER_CATALOG
TRIGGER_NAME
TRIGGER_SCHEMA
TRIM
TRUE
TRUNCATE
TRUSTED
TSEQUAL
TYPE
UESCAPE
UID
UNBOUNDED
UNCOMMITTED
UNDER
UNDO
UNENCRYPTED
UNION
UNIQUE
UNKNOWN
UNLISTEN
UNLOCK
UNNAMED
UNNEST
UNSIGNED
UNTIL
UPDATE
UPDATETEXT
UPPER
USAGE
USE
USER
USER_DEFINED_TYPE_CATALOG
USER_DEFINED_TYPE_CODE
USER_DEFINED_TYPE_NAME
USER_DEFINED_TYPE_SCHEMA
USING
UTC_DATE
UTC_TIME
UTC_TIMESTAMP
VACUUM
VALID
VALIDATE
VALIDATOR
VALUE
VALUES
VAR_POP
VAR_SAMP
VARBINARY
VARCHAR
VARCHAR2
VARCHARACTER
VARIABLE
VARIABLES
VARYING
VERBOSE
VIEW
VOLATILE
WAITFOR
WHEN
WHENEVER
WHERE
WHILE
WIDTH_BUCKET
WINDOW
WITH
WITHIN
WITHOUT
WORK
WRITE
WRITETEXT
X509
XOR
YEAR
YEAR_MONTH
ZEROFILL
ZONE
```

<div style="page-break-before:always"></div>

### 推奨データ型

異なるデータベース製品間の互換性を最大限高めるために使用する推奨データ型。

#### 文字型

- CHAR
- CLOB
- VARCHAR

#### 数値型

##### 絶対数値型

- BIGINT
- DECIMAL
- DECFLOAT
- INTEGER
- NUMERIC
- SMALLINT

##### 近似数値型

- DOUBLE PRECISION
- FLOAT
- REAL

#### 日付型

- DATE
- TIME
- TIMESTAMP

#### バイナリ型

- BINARY
- BLOB
- VARBINARY

#### その他の型

- BOOLEAN
- INTERVAL
- XML

[simon]: https://www.simonholywell.com/?utm_source=sqlstyle.guide&utm_medium=link&utm_campaign=md-document
    "SimonHolywell.com"
[original]: https://www.sqlstyle.guide/
    "SQL style guide by Simon Holywell"
[iso-8601]: https://ja.wikipedia.org/wiki/ISO_8601
    "Wikipedia: ISO 8601"
[rivers]: https://practicaltypography.com/one-space-between-sentences.html
    "Practical Typography: one space between sentences"
[licence-ja]: https://creativecommons.org/licenses/by-sa/4.0/deed.ja
    "Creative Commons Attribution-ShareAlike 4.0 International License"
[twitter-ja]: https://twitter.com/nkuritw
