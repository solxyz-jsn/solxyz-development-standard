# 非効率なSQLを学ぶ

> サンプルは`MySQL`を利用しています。

## TL;DR

- 非効率なSQLがどんなものかを知ることで、よいSQLを書く土台とする。
- 基本に忠実な実装を意識する。
- 公式のチューニングガイドを活用する。

## 非効率なSQLとはどんなものか

非効率なSQLのすべてのパターンを羅列するのはそれこそ非効率なので、ここでは[ORACLEのチューニングガイド](https://docs.oracle.com/cd/F39414_01/tgsql/introduction-to-sql-tuning.html#GUID-ADD9B100-7FFC-4652-941A-E6FEF8FD7D7E)から抜き出してみます。

> SQL文が不要な作業を実行するように記述されている場合、パフォーマンスの改善のためにオプティマイザができることはあまりありません。非効率的な設計パターンの例を次に示します。
>
> - 結合条件が追加されていないため、デカルト結合が発生する。
>
> - ヒントによって大きな表を結合内の駆動表として指定する。
>
> - UNION ALLではなくUNIONを指定する。
>
> - 外部問合せの各行に対して副問合せを実行する。

ひとつひとつ確認してみましょう。（ヒント句については特殊な例なので割愛）

### 結合条件が追加されていないため、デカルト結合が発生する

次のようなテーブルがあります。

`item`テーブル

| id | item_name | price | staff_id |
| --- | --- | --- | --- |
| 1 | itemA | 100 | 1 |
| 2 | itemB | 80 | 2 |

`staff`テーブル

| staff_id | first_name | last_name |
| --- | --- | --- |
| 1 | 太郎 | 田中 |
| 2 | 花子 | 山田 |

これらを次のように条件なしで結合します。

```SQL
SELECT 
    *
FROM
  items AS I,
  staff AS S;
```

結果は次のようにお互いの行を総当たりで結合したものが出力されます。

| id | item_name | price | staff_id | staff_id | first_name | last_name |
| --- | --- | --- | --- | --- | --- | --- |
| 2 | itemB | 100 | 2 | 1 | 太郎 | 田中 |
| 1 | itemA | 80  | 1 | 1 | 太郎 | 田中 |
| 2 | itemB | 100 | 2 | 2 | 花子 | 山田 |
| 1 | itemA | 80  | 1 | 2 | 花子 | 山田 |

結果はテーブルAの行数×テーブルBの行数となるため、行数が多いテーブル同士では致命的な結果となります。

こんなSQL書かないよと思うかもしれませんが、副問合せでうっかり条件式を書き忘れる、誤って消してしまうかもしれません。

多くのRDBMS製品はJOIN条件の不足を指摘してくれますが、上記のようにカンマでテーブルをつないでいる場合はエラーとなりません。

結合する場合は常にJOINを利用することで防ぐことが可能です。

> ただし、MySQLでは次のようなSQLはエラーとならず、上記と同様の結果となります。
>
> ```SQL
> SELECT
>   *
> FROM
>   items AS I 
> INNER JOIN -- INNER JOINのONがない
>   staff AS S;
> ```
>
> JOINとONがセットで使われていることを常に意識しましょう。
>

### UNION ALLではなくUNIONを指定する

`UNION`を復習しましょう。

`UNION`は、複数の`SELECT`ステートメントからの結果を1つの結果セットへ結合するために使用されます。

確認のために先述の`item`テーブルと同じ構造の`new_item`テーブルを作成します。

`new_item`テーブル

| id | item_name | price | staff_id |
| --- | --- | --- | --- |
| 1 | itemA | 80 | 1 |
| 2 | itemC | 80 | 2 |

`UNION`を実行します。

```SQL
(
  SELECT 
    *
  FROM
   items
)
UNION
(
  SELECT 
    *
  FROM
    new_items
);
```

| id | item_name | price | staff_id |
| --- | --- | --- | --- |
| 1 | itemA | 80 | 1 |
| 2 | itemB | 100 | 2 |
| 2 | itemC | 80 | 2 |

2つのテーブルの重複が除去されて出力されます。

`UNION ALL`を実行します。

```SQL
(
  SELECT 
    *
  FROM
   items
)
UNION ALL
(
  SELECT 
    *
  FROM
    new_items
);
```

| id | item_name | price | staff_id |
| --- | --- | --- | --- |
| 1 | itemA | 80 | 1 |
| 2 | itemB | 100 | 2 |
| 1 | itemA | 80 | 1 |
| 2 | itemC | 80 | 2 |

重複する行はそのまま出力されます。

`UNION`実行時は**内部的に**重複排除のためにソート処理が行われ、これがクエリの効率を下げます。

重複を気にする必要がない場合は`UNION ALL`を利用しましょう。

### 外部問合せの各行に対して副問合せを実行する

たとえば、次のようなSQLを指します。

```SQL
SELECT 
  I.id,
  I.item_name,
  (
    SELECT 
      S.last_name
    FROM
      staff S
    WHERE
      I.staff_id = S.staff_id
  ) AS last_name,
  (
    SELECT 
      S.first_name
    FROM
      staff S
    WHERE
    I.staff_id = S.staff_id
  ) AS first_name
FROM
  items I;
```

各行で個別に`staff`テーブルに対して問い合わせを行っていて、明らかに非効率ですね。

こちらもこんなSQL書かないよと思うかもしれませんが、実際の現場でも見ることがあります。

内部の仕組みを意識していなければ、出力結果は求めたものになるので、違和感を覚えないかもしれません。

多くの場合は`JOIN`で解決できます。

```SQL
SELECT 
  I.id,
  I.name,
  S.last_name,
  S.first_name
FROM
  items I
INNER JOIN
  staff S
  ON 
    I.staff_id = S.staff_id;
```

## 構文の動作を理解する

それぞれの構文の動作を理解するとこれらの動作を推測し、避けることができるようになります。

書籍などを通じて、学習を深めていきましょう。

## 公式のチューニングガイドを活用する

先ほどの紹介した[ORACLEのチューニングガイド](https://docs.oracle.com/cd/F39414_01/performance.html)ように製品ごとにもガイドが用意されています。

パフォーマンスが思うように出ないときは各製品のガイドをうまく活用しましょう。
