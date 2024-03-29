# 4. フォーマット

- [4. フォーマット](#4-フォーマット)
  - [4.1. インデントは空白文字4文字を使用します](#41-インデントは空白文字4文字を使用します)
  - [4.2. `{`の後に処理を記述しないでください](#42-の後に処理を記述しないでください)
  - [4.3. 1行に2つ以上のステートメントを記述しないでください](#43-1行に2つ以上のステートメントを記述しないでください)
  - [4.4. カンマの後には空白文字を1文字分挿入します](#44-カンマの後には空白文字を1文字分挿入します)
  - [4.5. 代入演算子の前後には空白文字を挿入します](#45-代入演算子の前後には空白文字を挿入します)
  - [4.6. for 文内のセミコロンの後には空白文字を挿入します](#46-for-文内のセミコロンの後には空白文字を挿入します)
  - [4.7. ビット演算子の前後には空白文字を挿入します](#47-ビット演算子の前後には空白文字を挿入します)
  - [4.8. 論理演算子の前後には空白文字を挿入します](#48-論理演算子の前後には空白文字を挿入します)
  - [4.9. 関係演算子の前後には空白文字を挿入します](#49-関係演算子の前後には空白文字を挿入します)
  - [4.10. 算術演算子の前後には空白文字を挿入します](#410-算術演算子の前後には空白文字を挿入します)
  - [4.11. StreamAPI 記述の際の改行位置は、各中間処理・末端処理前のピリオドの前で改行する](#411-streamapi-記述の際の改行位置は各中間処理末端処理前のピリオドの前で改行する)

本章では、ソルクシーズスタンダードにおけるフォーマットの解説を行います。

フォーマッタの導入が完了していれば、基本的に読み飛ばして構いません。

## 4.1. インデントは空白文字4文字を使用します

インデントにはタブ文字ではなく、空白文字4文字分を使用します。

## 4.2. `{`の後に処理を記述しないでください

```java
//Bad
if (s == null) { return 0; }
```

```java
//Good
if (s == null) {
    return 0;
}
```

## 4.3. 1行に2つ以上のステートメントを記述しないでください

```java
//Bad
} catch (Exception e) {
    log.error("Error", e);return null;
}
```

```java
//Good
} catch (Exception e) {
    log.error("Error", e);
    return null;
}
```

## 4.4. カンマの後には空白文字を1文字分挿入します

```java
//Bad
process(x,y,z);
```

```java
//Good
process(x, y, z);
```

## 4.5. 代入演算子の前後には空白文字を挿入します

代入演算子（`=`, `+=`, `-=`, …）の前後には空白文字を挿入します。

```java
//Bad
int a=x;
a+=10;
```

```java
//Good
int a = x;
a += 10;
```

## 4.6. for 文内のセミコロンの後には空白文字を挿入します

```java
//Bad
for (int i = 0;i < array.length ;i++) {
    ...
}
```

```java
//Good
for (int i = 0; i < array.length; i++) {
    ...
}
```

## 4.7. ビット演算子の前後には空白文字を挿入します

ビット演算子（`|`、`&`、`^`、`<<`、`>>`）の前後には空白文字を挿入します。

## 4.8. 論理演算子の前後には空白文字を挿入します

論理演算子（`||`、`&&`）の前後には空白文字を挿入します。

## 4.9. 関係演算子の前後には空白文字を挿入します

関係演算子（`<`、`>`、`>=`、`<=`、`==`、`!=`）の前後には空白文字を挿入します。

## 4.10. 算術演算子の前後には空白文字を挿入します

算術演算子（`＋`、`－`、`＊`、`/`、`%`）の前後には空白文字を挿入します。

## 4.11. StreamAPI 記述の際の改行位置は、各中間処理・末端処理前のピリオドの前で改行する

```java
//Bad フォーマット不適切
List<Character> alphabetLower = list.stream().filter(Character::isAlphabetic)
    .map(Character::toLowerCase).toList();

List<Character> alphabetLower = list
    .stream()
    .filter(Character::isAlphabetic)
    .map(Character::toLowerCase)
    .toList();
```

```java
//Good
List<Character> alphabetLower = list.stream()
    .filter(Character::isAlphabetic)
    .map(Character::toLowerCase)
    .toList();
```
