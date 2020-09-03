---
layout: post
title: ScalaのListで使う基本の関数！
subtitle: バリュエーションが多くて覚えられない！！！
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [template]
---

こんにちは！  
H.N.です。  
今回はScalaのListで使う基本の関数をまとめたいと思います。

## きっかけ
最近は情報処理安全確保支援士試験の勉強に偏っているのですが、同じような記事ばかり書いても面白くないと思ったので違うテーマで書こうと思いました。  
今読んでいるScalaの本（コップ本）で読んだところがちょうどCollectionについてだったので記事にしようと思いました。  
ArrayやSet、Mapでシリーズ化したら面白そうですね。

## List

ListはArrayとよく似ていますが、Arrayはミュータブルなのに対してListは基本的にはイミュータブルです。  
また、ランダムアクセスが可能なのでインデックスによるアクセスが高速に行えます。

Arrayは非変なので、以下のコードを許容しません。

---
```Scala
val anyAry: Array[Any] = Array(1, 2, 3)
```
---

しかしListは共変なので、以下のコードを許容します。

---
```Scala
val anyList: Array[Any] = List(1, 2, 3)
```
---

等質的な点は共通です。  
Array[T]の要素はすべてTになります。  
同じようにList[T]の要素はすべてTになります。  

### apply

---
```Scala
val list = List()
```
---

上記のような呼出し方をします。  
引数を渡さなければ空リストになります。

### Nilと::と:::
始めてこれらを使っているプログラムを見たときは面食らいましたね。

Nilは空リストを表します。  
::（コンス）は x :: xs で x の後に xs のリストが続くことを表します。  
::: （連結）は xs ::: ys は xs と ys の連結を表す。

## 感想
まだまだ便利な関数はたくさんあるけど、基本的なのはここら辺でしょうか？  
Javaにある関数は全部ありますし、かゆいところに手が届く関数が多くて書いていてワクワクする言語ですね！

以上、「ScalaのListで使う基本の関数！」でした。
