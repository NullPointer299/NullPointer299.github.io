---
layout: post
title: ScalaのTupleの分解が便利！
subtitle: 痒い所に手が届く！！！
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [Scala]
---

こんにちは！  
H.N.です。  
今回はScalaでTupleを分解する話です。

## きっかけ
一日一記事って結構つらいですね。。。  
Scalaで学んだことで繋いでいきたいと思います！

## Tupleとは
Tupleは複数の違う型の要素を扱うことができるデータ構造です。  
Tuple1 ～ Tuple22までの型がScalaライブラリによって定義されており以下のように使うことができます。

---
```Scala
val tuple2 = (1, "two")
```
---

各要素へのアクセスは以下のようにできます。

---
```Scala
tuple2._1    // 1
tuple2._2    // "two"
```
---

## Tupleを変数に分解する
TupleはScalaパターンマッチの拡張でプログラム内のあらゆる場所で使用することができます。

---
```Scala
val (one, two) = tuple2    // one = 1, two = "two"
```
---

ケースクラスからの分解もすることができます。  
2次元座標を表すケースクラスPosition(x: Int, y:Int)があるとします。  
Positionクラスのオブジェクトpos(1, 5)は以下のように分解することができます。

---
```Scala
val Position(x, y) = pos    // x = 1, y = 5
```
---

## 感想
使わなくてもコードは書けますが、この記法を使えばとてもスマートになると思います！  
こういう痒い所に手が届く書き方が多くあるから学んでいて飽きませんね！

以上、「ScalaのTupleの分解が便利！」でした。
