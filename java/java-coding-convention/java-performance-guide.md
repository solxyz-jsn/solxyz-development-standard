# 5. パフォーマンスガイド

- [5. パフォーマンスガイド](#5-パフォーマンスガイド)
  - [5.1. stream vs for](#51-stream-vs-for)
    - [5.1.1. 用いたソースコード](#511-用いたソースコード)

## 5.1. stream vs for

ループ処理を記述する際によく用いられる構文は`for`です。

しかし、`for`は`stream`に比べ、パフォーマンスに劣ることが知られています。（Javaのバージョンによってパフォーマンスの差が違います）

ここでは、Java 17を用いた際にどれほどの差が出るのか見ていきます。

100万回の反復処理をした際にかかる時間を次の表に示します。

| 反復処理方式 | 処理時間 |
|:--|:--|
| for |75756834 ns|
| stream | 22058458 ns |
| parallel stream| 73585833 ns |

処理はMacBook Pro（2021）Apple M1 Proを用いて計測しています。

`for`による反復処理は`stream`に比べ3倍ほどパフォーマンスに劣ることがデータからも明らかです。

しかし、時間に換算すると0.05秒ほどの差しかありません。（今回は処理が単純ということもあり、差が出づらい点は留意してください）

そのため、単純な反復処理では`stream`は非常に有効になりますが、酷く可読性を落とす場合は推奨しません。

可読性を落としてもパフォーマンスを追求しなければならない反復処理を行う場合、`stream`を利用し、メソッドチェーンにて実装を行ってください。

### 5.1.1. 用いたソースコード

```java
//Calculating square root of even numbers from 1 to N
int min = 1;
int max = 1000000;

List<Integer> sourceList = new ArrayList<>();
for (int i = min; i < max; i++) {
    sourceList.add(i);
}

List<Double> result = new LinkedList<>();


//Collections approach
long t0 = System.nanoTime();
long elapsed = 0;
for (Integer i : sourceList) {
    if(i % 2 == 0){
        result.add(Math.sqrt(i));
    }
}
elapsed = System.nanoTime() - t0;
System.out.printf("Collections: Elapsed time:\t %d ns \t(%f seconds)%n", elapsed, elapsed / Math.pow(10, 9));


//Stream approach
Stream<Integer> stream = sourceList.stream();
t0 = System.nanoTime();
result = stream.filter(i -> i%2 == 0).map(Math::sqrt).collect(Collectors.toList());
elapsed = System.nanoTime() - t0;
System.out.printf("Streams: Elapsed time:\t\t %d ns \t(%f seconds)%n", elapsed, elapsed / Math.pow(10, 9));


//Parallel stream approach
stream = sourceList.stream().parallel();
t0 = System.nanoTime();
result = stream.filter(i -> i%2 == 0).map(Math::sqrt).collect(Collectors.toList());
elapsed = System.nanoTime() - t0;
System.out.printf("Parallel streams: Elapsed time:\t %d ns \t(%f seconds)%n", elapsed, elapsed / Math.pow(10, 9));
```