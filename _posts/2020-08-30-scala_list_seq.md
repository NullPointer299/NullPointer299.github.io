---
layout: post
title: ScalaのListとSeqの連結について！
subtitle: Scalaは初見殺しが多い！！！
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [Scala, プログラム]
---

こんにちは！  
H.N.です。  
今回はScalaのSeqとListの連結についての話です。

## きっかけ
最近はScalaでプログラムを書くことが多いのですが、  
Listの連結とSeqの連結が違う関数を呼び出さなければいけないのを知らなくて迷ったので記事にしようと思いました。

## Listの連結
Listの連結は:::関数と++関数で行うことができます。  

---
```Scala:Main.scala
object Main extends App {
  
  val list123 = List(1, 2, 3)
  val list456 = List(4, 5, 6)

  val list1to6 = list123 ++ list456 // List(1, 2, 3, 4, 5, 6)

  val listAbc = List("a","b","c")
  val listDef = List("d","e","f")

  val listAtoF = listAbc ::: listDef // List("a", "b", "c", "d", "e", "f")
}
```
---

## Seqの連結
Listでは:::関数と++関数を使用して連結することができましたが、  
Seqの連結では:::関数を使うことはできません。

---
```Scala:Main.scala
object Main extends App {

  val seq123 = Seq(1, 2, 3)
  val seq456 = Seq(4, 5, 6)

  val seq1to6 = seq123 ++ seq456
  
  val seqAbc = Seq("a", "b", "c")
  val seqDef = Seq("d", "e", "f")
  
  val seqAtoF = seqAbc ::: seqDef // Compile error!
}
```
---

これを知らなくて:::関数で連結できない。。。と10分近く悩んでしまいました。

## 感想
Scalaは書いていてとても楽しいのですが、まだまだ書き方に慣れていないので頻繁に止まってしまいます。  
今まで命令型言語しか書いてこなかったので、関数型言語に触れることによってさらに視野が広がった気がします！  
Javaと同じくらい書けるようになったときどんな成長が感じられるか楽しみです！

以上、「ScalaのListとSeqの連結について！」でした。
