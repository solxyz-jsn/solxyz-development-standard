# 6. 推奨事項

- [6. 推奨事項](#6-推奨事項)
  - [6.1. クラスやメソッドなどには適切なアクセス修飾子を付与してください](#61-クラスやメソッドなどには適切なアクセス修飾子を付与してください)
  - [6.2. インスタンス変数は原則 private にしてください](#62-インスタンス変数は原則-private-にしてください)
  - [6.3. ローカル変数はできるだけ狭いスコープで使用してください](#63-ローカル変数はできるだけ狭いスコープで使用してください)
  - [6.4. なるべく再代入は避けて、そのためにfinalを活用してください](#64-なるべく再代入は避けてそのためにfinalを活用してください)
  - [6.5. なるべく引数の状態を変えないでください](#65-なるべく引数の状態を変えないでください)
  - [6.6. 戻り値として null を使いたい場合、Optional の使用を検討してください](#66-戻り値として-null-を使いたい場合optional-の使用を検討してください)
  - [6.7. コレクションのように型パラメータを取るクラスを使用する場合は適切な型をバインドしてください](#67-コレクションのように型パラメータを取るクラスを使用する場合は適切な型をバインドしてください)
  - [6.8. コレクションの処理はStream APIを使用して簡潔に書くことを検討してください](#68-コレクションの処理はstream-apiを使用して簡潔に書くことを検討してください)
  - [6.9. チェック例外のスローを伴う処理はStream APIではなく拡張for文を使用して実装してください](#69-チェック例外のスローを伴う処理はstream-apiではなく拡張for文を使用して実装してください)
  - [6.10. ノーマルfor文はなるべく使用せず、Stream APIか拡張for文の使用を検討してください](#610-ノーマルfor文はなるべく使用せずstream-apiか拡張for文の使用を検討してください)
  - [6.11. 配列全体をコピーする場合はcloneメソッドを使用してください](#611-配列全体をコピーする場合はcloneメソッドを使用してください)
  - [6.12. コレクションを配列に変換する場合はtoArrayメソッドを使用してください](#612-コレクションを配列に変換する場合はtoarrayメソッドを使用してください)
  - [6.13. 配列をコレクションに変換する場合はArrays.asList、またはList.ofを使用してください](#613-配列をコレクションに変換する場合はarraysaslistまたはlistofを使用してください)
  - [6.14. メソッドをオーバーライドしたり、抽象メソッドを実装する場合はメソッドに@Overrideを付けてください](#614-メソッドをオーバーライドしたり抽象メソッドを実装する場合はメソッドにoverrideを付けてください)
  - [6.15. 使用可能なAPI](#615-使用可能なapi)
    - [6.15.1. 使用可能な標準APIを使用して実装してください](#6151-使用可能な標準apiを使用して実装してください)
  - [6.16. 代表的なプログラミング原則](#616-代表的なプログラミング原則)
    - [6.16.1. YAGNI](#6161-yagni)
      - [6.16.1.1. YAGNIに違反しているソースコード](#61611-yagniに違反しているソースコード)
    - [6.16.2. KISS](#6162-kiss)
    - [6.16.3. DRY原則](#6163-dry原則)
    - [6.16.4. 単一責任の原則](#6164-単一責任の原則)

よりよいソースコードを書くために、推奨事項を定めています。

## 6.1. クラスやメソッドなどには適切なアクセス修飾子を付与してください

クラスやメソッドなど、アクセス修飾子を付与できる場所では適切なアクセス修飾子を選択してください。

アクセス修飾子の種類と公開範囲を次に示します。

|アクセス修飾子|公開範囲|
|---|---|
|`public`|すべてのクラスからアクセス可能|
|`protected`|自分自身、同一パッケージのクラス、サブクラスからアクセス可能|
|（なし）|自分自身、同一パッケージのクラスからアクセス可能|
|`private`|自分自身のみアクセス可能|

みだりに`public`で宣言せず、必要がなければ狭い範囲になるようアクセス修飾子を付与してください。

このとき、`private`で宣言すればよいというわけではありません。

共通化できるロジックに関しては、1つのクラスにまとめて`public`で宣言してください。

共通化とは、同じ処理をしていることではなく、同じ目的を行うように実装してください。

```java
//Bad 同じ処理が別のクラスに定義されている
public class AClass {
    .
    .
    .
    private void hoge() {
        .
        .
        .
    }
}

public class BClass {
    .
    .
    .
    private void hoge() {
        .
        .
        .
    }
}
```

```java
//Good 同じ処理をまとめている
public class AClass {
    .
    .
    .
}

public class BClass {
    .
    .
    .
}

public class HogeUtils {
    public void hoge() {
        .
        .
        .
    }
}
```

## 6.2. インスタンス変数は原則 private にしてください

インスタンス変数はクラス外に露出するべきではありません。
原則`private`としてください。

例外的に、フレームワークの制約で`private`以外にしなくてはならない場合は適切なアクセス修飾子を付与してください。

また、抽象クラスを作成してサブクラスで参照させたいインスタンス変数がある場合は`protected`にしてください。
ただし、その場合でもみだりにインスタンス変数を公開するのではなく、メソッドを併用することでインスタンス変数を`private`にできないか検討してください。

このとき、`private`で宣言すればよいというわけではありません。

共通化できる変数に関しては、1つのクラスやEnumにまとめて`public`で宣言してください。

共通化とは、同じ値であるということではなく、同じ意味をもつように実装してください。


```java
//Bad 同じ定数が別のクラスに定義されている
public class AClass {
    private static final String ENDPOINT_URL = "https://example.com";
    .
    .
    .
}

public class BClass {
    private static final String ENDPOINT_URL = "https://example.com";
    .
    .
    .
}
```

```java
//Good 同じ定数を一箇所で宣言している
public class AClass {
    .
    .
    .
}

public class BClass {
    .
    .
    .
}

public class APIEndpointsConst {
    public static final String ENDPOINT_URL = "https://example.com";
    .
    .
    .
}
```

## 6.3. ローカル変数はできるだけ狭いスコープで使用してください

ローカル変数のスコープができるだけ狭くなるように利用する場所と近い位置で宣言をしてください。

ローカル変数の宣言と実際に使用する箇所が遠い場合、可読性が落ちるだけでなく、ガベージコレクションパフォーマンス低下を招く恐れがあります。

```java
//Bad
final String text = ...

callMethod1();
callMethod2();
callMethod3();
.
.
.
callMethodN();

//textを使わない処理が延々と続いた後に初めてtextを使う処理が登場
useText(text);
```

```java
//Good
callMethod1();
callMethod2();
callMethod3();
.
.
.
callMethodN();

//textを宣言してすぐに使用している
final String text = ...
useText(text);
```

また、ローカル変数のスコープはブロック単位です。
特定のブロック内でしか使用しないローカル変数は該当のブロック内で宣言してください。

```java
//Bad
//if文のブロック内でしか使用されないのにブロック外で宣言されている
final String text = ...
if (isSuccess(result)) {
    useText(text);
}
callOtherMethod();
return;
```

```java
//Good
//if文のブロック内で宣言されている
if (isSuccess(result)) {
    final String text = ...
    useText(text);
}
callOtherMethod();
return;
```

## 6.4. なるべく再代入は避けて、そのためにfinalを活用してください

ソースコードは「変更可能な状態」が少なければ少ないほど、全体の把握がしやすく理解しやすい傾向にあります。

変数を再代入するということは、知らないうちに「変更可能な状態」を作っていることになります。

```java
String value = "hello";

...

//変数の再代入をすると「変更可能な状態」となり、ソースコードを読んでいる途中で
//「今この変数の値は何か？」を常に気にする必要が出てくる
value = "world";
```

ソースコードを読むときに把握すべきことを減らしましょう。
そのために変数の再代入は避けましょう。

変数の再代入を避けるために`final`を活用してください。
変数を宣言する際に`final`を付けると、その変数は再代入不可になります。

```java
final String value1 = "hello";

...

//再代入不可なので次のコメントアウトしているソースコードはコンパイルエラーになる
//value1 = "world";

//既存の変数に再代入せずに、新しい変数を導入する
final String value2 = "world";
```

ローカル変数だけではなく、フィールドにも`final`を付けて再代入不可に出来ないか検討してみてください。
フレームワークの制約などで必ず`setter`を定義しないといけない場合もありますが、そうでない場合はなるべくフィールドも再代入不可にし、Spring Frameworkであれば[コンストラクタインジェクション](https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-constructor-injection)を検討してください。

## 6.5. なるべく引数の状態を変えないでください

ソースコードは「状態を変更する箇所」が局所的であればあるほど、全体の把握がしやすく理解しやすい傾向にあります。

引数の状態を変更してしまうと、状態を変更する箇所が広がってしまうことになります。

```java
//※これはやらない方がよい非推奨ソースコードの例
//
//消費税計算をした後に引数自身に税をセットしている
//なるべくなら消費税計算をするだけにとどめて、itemに税をセットするのは呼び出し元が行った方がよい
public BigDecimal calculateTax(final Item item) {
    BigDecimal tax = item.getPrice().multiply(taxRate);
    item.setTax(tax);
    return tax;
}
```

`private`メソッドであればクラス内に閉じているので影響範囲が限られていますが、`public`や`protected`などのクラス外に公開されるメソッドではなるべく引数の状態を変更しないことを推奨します。

## 6.6. 戻り値として null を使いたい場合、Optional の使用を検討してください

値が「ない」状態を表す手段として`null`を使う方法と、Java 8から導入された`java.util.Optional`を使う方法があります。

戻り値を`java.util.Optional`にすると、値を返さない場合があるメソッドだということをシグネチャで表現できます。

```java
//値を返さない場合があることがメソッドのシグネチャから読み取れる
public Optional<String> maybeReturnValue() {
    ...
    if (...) {
        return Optional.of(value);
    }
    return Optional.empty();
}

//（Optionalではないので）必ず値を返すことがメソッドのシグネチャから読み取れる
public String mustReturnValue() {
    ...
}
```

`null`は値がある場合と同じ型で表現できるので、値を返さない場合があるメソッドだということをシグネチャで表現できず、Javadocへの記載などで対応しなくてはいけません。

```java
//値を返さない場合があることがメソッドのシグネチャから読み取れない
public String maybeReturnValue() {
    ...
    if (...) {
        return value;
    }
    return null;
}

//必ず値を返すことがメソッドのシグネチャから読み取れない
public String mustReturnValue() {
    ...
}
```

`java.util.Optional`を使用すると、メソッドの呼び出し元で戻り値の存在チェックをするべきかどうかを型で表現できるので、コンパイラーのサポートを受けられて安全です。
値を返さない場合があるメソッドでは戻り値を`java.util.Optional`にすることを検討してみてください。

```java
//Optionalを使用したメソッドの場合
//戻り値がない場合を考慮しないといけないことが型を見れば分かる
final Optional<String> optional = maybeReturnValue();
final String value = optional.orElse(defaultValue);
```

```java
//nullを使用したメソッドの場合
//戻り値がない場合を考慮しないといけないことが型を見ても分からない
//※nullチェックが漏れていてもコンパイルエラーにならず発見が遅れる
String value = maybeReturnValue();
if (value == null) {
    value = defaultValue;
}
```

## 6.7. コレクションのように型パラメータを取るクラスを使用する場合は適切な型をバインドしてください

`java.util.List<E>`や`java.util.Map<K, V>`のようなコレクションや`java.util.Optional<T>`は、型パラメータが定義されています。
このようなクラスを使用する場合は適切な型をバインドしてください。

適切な型をバインドすることでコンパイラーによる型チェックを活かせます。

```java
//Bad
//型パラメータがバインドされていないためNG
final List raw = new ArrayList();
//バインドされた型が抽象的すぎるためNG
final List<Object> objects = new ArrayList<>();
```

```java
//Good
//具体的な型をバインドしているためOK
final List<Item> items = new ArrayList<>();

final String item = ...
items.add(item); //バインドされた型と不一致なのでコンパイルエラーになる

final Item item = ...
items.add(item); //バインドされた型と一致するのでコンパイルが通る
```

## 6.8. コレクションの処理はStream APIを使用して簡潔に書くことを検討してください

Java 8から導入されたStream APIを使用すれば`java.util.List`や`java.util.Set`などのコレクションを簡潔なソースコードで処理できる場合があります。

Stream APIは`filter`や`map`、`collect`といったメソッドを使用して各要素に対する操作を小さく設定できます。
そのため、各要素に対してどのような処理をするのかが分かりやすくなる傾向にあります。

|メソッド|説明|ソースコード例|
|---|---|---|
|`filter`|条件に合う要素だけに絞り込む|`stream.filter(x -> x % 2 == 0) //偶数だけに絞り込む`|
|`map`|要素を変換する|`stream.map(x -> x.getClass()) //Classに変換する`|
|`collect`|`Collector`によって`Stream`を変換する|`stream.collect(Collectors.joining(", ")) //要素をカンマ区切りの文字列に変換する`|

その他のメソッドは[`java.util.stream.Stream`のJavadoc](https://docs.oracle.com/javase/jp/10/docs/api/java/util/stream/Stream.html)で確認してください。

Stream APIを使用したソースコード例と拡張for文を使用したソースコード例を次に示します。
どちらも従業員のリストから職種がプログラマーの従業員だけに絞り込んで平均年齢を算出しています。

Stream APIを使用したソースコード例の方が、どのような処理を積み重ねて結果を得ているのかが分かりやすく感じないでしょうか。

```java
//Stream APIを使用したソースコード例
final List<Employee> employees = ...
final IntSummaryStatistics statistics = employees.stream()
        //職種がプログラマーだけに絞る
        .filter(emp -> emp.getJobCategory().equals(programmer))
        //年齢を抽出
        .mapToInt(emp -> emp.getAge())
        //集計する
        .summaryStatistics();
//平均を算出
final double average = statistics.getAverage();
```

```java
//拡張for文を使用したソースコード例
final List<Employee> employees = ...
double tempAge = 0;
int tempSize = 0;
for (final Employee employee : employees) {
    //職種がプログラマーだけに絞る
    if (employee.getJobCategory().equals(programmer)) {
        //年齢を抽出して一時変数へ足し込む
        tempAge += employee.getAge();
        //平均を求めるため分母となる数をインクリメント
        tempSize++;
    }
}
//平均を算出
final double average = tempAge / tempSize;
```

必ず簡潔になるとは限りませんし、ソースコードの読みやすさ・分かりやすさは主観によるものなので強制ではありませんが、コレクションを処理する際はStream APIを使用することを検討してみてください。

## 6.9. チェック例外のスローを伴う処理はStream APIではなく拡張for文を使用して実装してください

Stream APIはコレクションの操作を簡潔に書けますが、チェック例外のスローが宣言されているメソッドを呼び出す場合はラムダ式の中で`try-catch`を書かなくてはいけません。
せっかく簡潔に書けるはずのStream APIが`try-catch`によって煩雑なソースコードになってしまいます。
そのため、チェック例外のスローを伴う操作が含まれる場合は拡張`for`文を使用してください。

ファイルの入出力では多くの場合に`java.io.IOException`がスローされます。
コレクション操作に伴ってファイルを処理する場合は拡張`for`文を使用するとよいでしょう。

```java
//Bad
final List<String> heads = files.stream()
        .map(file -> {
            //readLineでIOExceptionがスローされる可能性がある
            try (BufferedReader in = openReader(file)) {
                return in.readLine();
            } catch (final IOException e) {
                throw new UncheckedIOException(e);
            }
        })
        .filter(head -> head != null)
        .collect(Collectors.toList());
```

```java
//Good
final List<Path> files = ...
final List<String> heads = new ArrayList<>();
for (Path file : files) {
    //readLineでIOExceptionがスローされる可能性がある
    try (BufferedReader in = openReader(file)) {
        final String head = in.readLine();
        if (head != null) {
            heads.add(head);
        }
    } catch (IOException e) {
        ...
    }
}
```

## 6.10. ノーマルfor文はなるべく使用せず、Stream APIか拡張for文の使用を検討してください

コレクションの要素を順次処理するにはStream APIと拡張`for`文が使えるので、ノーマル`for`文を使用する場面は通常ありません。
ノーマル`for`文はなるべく使用しないようにしてください。

※[ノーマルfor文は導入「1.4.表記ルール」参照](./java-coding-guide-introduction.md)

## 6.11. 配列全体をコピーする場合はcloneメソッドを使用してください

配列全体をコピーする場合は`clone`メソッドを使用するのがもっともシンプルです。

```java
//Good
final Item[] values = ...
final Item[] copied = values.clone();
```

`java.util.Arrays`クラスの`copyOf`メソッドを使用してもよいです。
このメソッドは第2引数でコピーする長さを指定できます。

```java
//Good
final Item[] values = ...
final Item[] copied = Arrays.copyOf(values, values.length);
```

`clone`と`Arrays.copyOf`はどちらもシャローコピーを行います。
ディープコピーをしたい場合はループしながら各要素に対してもコピー処理を行う必要があります。

[シャローコピーとディープコピーの違い](https://www.javadrive.jp/start/array/index10.html)

```java
//Good
final Item[] values = ...
final List<Item> temp = new ArrayList<>(values.length);
for (Item item : values) {
    temp.add(copyItem(item));
}
final Item[] copied = temp.toArray(new Item[0]);
```

例に示したケースではJava 8から導入されたStream APIを使用すると、より簡潔なソースコードになります。

```java
//Good
final Item[] values = ...
final Item[] copied = Arrays.stream(values)
        .map(item -> copyItem(item))
        .toArray(Item[]::new);
```

## 6.12. コレクションを配列に変換する場合はtoArrayメソッドを使用してください

コレクションには配列に変換する`toArray`メソッドが用意されています。
各要素をループして配列を作ったりせず、`toArray`メソッドを使用してください。

```java
//Bad
final List<Item> items = ...
final Item[] itemArray = new Item[items.size()];
int index = 0;
for (final Item item : items) {
    itemArray[index++] = item;
}
```

```java
//Good
final List<Item> items = ...
final Item[] itemArray = items.toArray(new Item[0]);

//Stream APIにもtoArrayメソッドが用意されている
//Streamを配列に変換したい場合はこのメソッドを使用する
final Item[] itemArray = items.stream().toArray(Item[]::new);
```

このソースコード例では`toArray`メソッドに渡す配列を長さ`0`で初期化しています。
元となるコレクションの`size`メソッドを長さに指定して初期化することも可能ですが、パフォーマンスの差はほぼありません。
そのため、どちらの初期化方法を選択してもよいですが、本規約のソースコード例では見やすさを考慮して長さ`0`で初期化しています。

## 6.13. 配列をコレクションに変換する場合はArrays.asList、またはList.ofを使用してください

配列のユーティリティである`java.util.Arrays`クラスにはリストに変換する`asList`メソッドが用意されています。
各要素をループしてリストを作ったりせず、`java.util.Arrays`クラスの`asList`メソッドを使用してください。

```java
//Bad
final Item[] itemArray = ...
final List<Item> items = new ArrayList<>(itemArray.length);
for (final Item item : itemArray) {
    items.add(item);
}
```

```java
//Good
final Item[] itemArray = ...
final List<Item> items = Arrays.asList(itemArray);
```

なお、Java 9からは`java.util.List`に`of`メソッドが追加されたので、こちらを使用しても構いません。

```java
//Good
final Item[] itemArray = ...
final List<Item> items = List.of(itemArray);
```

Java 9からは`java.util.Set`にも`of`メソッドが追加されました。
これまで配列から`java.util.Set`に変換しようとすると、いったん`java.util.List`に変換してから`java.util.Set`を生成したり、Java 8からはStream APIを使用して変換していました。
Java 9からは簡潔なソースコードで変換できるようになりました。

```java
//Java 7までの変換方法
final Set<Item> items =  new HashSet<>(Arrays.asList(itemArray));

//Java 8からはStream APIで変換できる
final Set<Item> items =  Arrays.stream(itemArray).collect(Collectors.toSet());

//Java 9からはより簡潔に変換できる
final Set<Item> items = Set.of(itemArray);
```

## 6.14. メソッドをオーバーライドしたり、抽象メソッドを実装する場合はメソッドに@Overrideを付けてください

サブクラスでスーパークラスのメソッドをオーバーライドする場合、サブクラス側のメソッドに`@Override`を付けてください。
`@Override`を付けておくと、コンパイラーが本当にオーバーライドされたメソッドであるかチェックしてくれます。

```java
//Bad
public class SuperClass {

    public void someMethod() {
        ...
    }
}

public class SubClass extends SuperClass {

    //メソッド名が間違っておりオーバーライドになっていない。
    //コンパイルは通るのでミスに気付きにくい。
    public void sameMethod() {
        ...
    }
}
```

```java
//Good
public class SuperClass {

    public void someMethod() {
        ...
    }
}

public class SubClass extends SuperClass {

    //@Overrideを付けているとオーバーライドになっていない場合はコンパイルエラーになる。
    //コンパイル時にミスに気づくことができる。
    @Override
    public void sameMethod() {
        ...
    }
}
```

Java 6からはインターフェースで宣言された抽象メソッドを実装する際にも`@Override`が使用できるようになりました。
スーパークラスのメソッドをオーバーライドする際と同様に`@Override`を付けるようにしてください。

```java
//Good
public class SomeAction implements Runnable {

    @Override
    public void run() {
        ...
    }
}
```

---

## 6.15. 使用可能なAPI

業務アプリケーションを開発するのに十分なだけのAPIを厳選することで、品質を確保するための規約です。

### 6.15.1. 使用可能な標準APIを使用して実装してください

Java標準ライブラリのうち使用可能なAPIについては、SpotBugsやSonarQubeを参照してください。

---

## 6.16. 代表的なプログラミング原則

### 6.16.1. YAGNI

YAGNI（ヤグニ）とは、You ain't gonna need itの頭文字からきています。

これは直訳すると「必要ない」という意味です。

つまるところ、現在必要のない機能を実装しても将来使うことはほとんどないということです。

昨日の実装は、その機能が必要実装を行うことで、適切な実装が可能となります。

#### 6.16.1.1. YAGNIに違反しているソースコード

- 参照されていないメソッド・変数
- コメントアウトされたソースコード

など

### 6.16.2. KISS

KISSとは、Keep it simple stupidの頭文字からきています。

これは直訳すると「バカシンプルであること」という意味です。

つまるところ、簡潔で単純な状態にしておけば、将来変更を加える際に実装が楽になるということです。

### 6.16.3. DRY原則

DRY原則とは、Don't Repeat Yourselfの頭文字からきています。

これは直訳すると「同じことを繰り返すな」という意味です。

つまるところ、同じ機能を違う場所で実装するを禁止するということです。

このとき、安直に重複した箇所をまとめることがベストではないことは意識しておかなければならないことです。

意味を共通化させ、意味が違う箇所はそれぞれまとめずに残しておきましょう。

### 6.16.4. 単一責任の原則

単一責任の原則とは、SOLIDと呼ばれるオブジェクト指向の原則のひとつで、ひとつのクラスには1つだけの責任をもつという原則です。

責任が1つとはどのようなことかというと「モジュールはたったひとつのアクターに対して責務を負うべきである」ということです。

単一責任の原則を守っていない例として、責任が多く存在しているFatコンポーネントが存在します。

Fatコンポーネントの例と単一責任の原則に則って作成された例を比較して、ソースコードの読みやすさと修正する際の楽さを見比べて見ましょう。

ここでは、ソースコードの単一責任の原則を説明するためJavaDocが正確ではないことに注意してください。

```java
//Bad 責任範囲が座席着席情報と就業情報の2つの責任範囲を包括している
/**
 * 座席着席情報を管理するクラス
 */
public class SeatingInfoManager {
    /**
     * 座席情報全件取得
     */
    public List<SatingInfo> getDataAll() {
        ...
    }

    /**
     * ユーザーID指定の座席情報取得
     */
    public SeatingInfo getDataByUserId(final String userId) {
        ...
    }

    /**
     * ユーザーID指定の着席処理
     */
    public int sitDown(final String userId) {
        ...
    }

    /**
     * ユーザーID指定の離席処理
     */
    public int leave(final String userId) {
        ...
    }

    /**
     * ユーザーID指定の始業処理
     */
    public int start(final String userId) {

    }

    /**
     * ユーザーID指定の終業処理
     */
    public int end(final String userId) {
        ...
    }

    /**
     * ユーザー存在判定
     */
    private boolean existUser(final String userId) {
        ...
    }

}
```

```java
//Good 単一責任の原則に則っている
/**
 * 座席着席情報を管理するクラス
 */
public class SeatingInfoManager {

    /**
     * 座席情報全件取得
     */
    public List<SatingInfo> getDataAll() {
        ...
    }

    /**
     * ユーザーID指定の座席情報取得
     */
    public SeatingInfo getDataByUserId(final String userId) {
        ...
    }

    /**
     * ユーザーID指定の着席処理
     */
    public int sitDown(final String userId) {
        ...
    }

    /**
     * ユーザーID指定の離席処理
     */
    public int leave(final String userId) {
        ...
    }

}

/**
 * 就業情報を管理するクラス
 */
public class WorkInfoManager {

    /**
     * ユーザーID指定の始業処理
     */
    public int startWork(final String userId) {

    }

    /**
     * ユーザーID指定の終業処理
     */
    public int endWork(final String userId) {
        ...
    }

}

/**
 *　ユーザーユーティリティ
 */
public class UserUtils {
    /**
     * ユーザー存在チェック
     */
    public boolean checkUserExistance(final String userId) {
        ...
    }
}
```

goodでは、それぞれの責任範囲を「座席着席情報管理」、「就業情報管理」、「ユーザーユーティリティ」のクラスに分けています。

このように分けることで、それぞれのクラスで何の処理を行っているのかが明確で見えやすくなります。

また、たとえばユーザー存在チェックに別の処理を加えなければならない際に、対象がUserUtilsクラスだけでよいなど品質向上にもつながります。
