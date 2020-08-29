---
layout: post
title: AtCoder Beginners Selectionを解いた！
subtitle: 競プロって楽しいけど難しい！！！
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [Scala, プログラム]
---

こんにちは！  
H.N.です。  
今回はAtCoderのBeginners SelectionのABC085C OtoshidamaとABC049C 白昼夢を解いた話です。

## きっかけ
競プロってあんまりやったことないんですが、Scalaの勉強になるかなと思い、AtCoderの問題に挑戦しました。  
初心者向けの簡単な問題のようなのですが、アルゴリズム考える力がないと苦戦しますね。。。

## ABC085C Otoshidama
この問題はお年玉のお札の枚数Nと合計金額Yが渡されるので、10000円札と5000円札と1000円札で組み合わせを出力する問題です。  
条件が 1 < N < 2000 と全網羅しても十分制限時間内に収まるので、ループで全件検索する方法をとりました。

```scala:ABC085C_Otoshidama.scala
import scala.io.StdIn.readLine

object ABC085C_Otoshidama extends App {

  val NY = readLine.split(' ').map(_.toInt)
  val (x, y, z) = findPattern(NY(0), NY(1))
  println(s"$x $y $z")

  def findPattern(N: Int, Y: Int): (Int, Int, Int) = {
    for (t10 <- 0 to N; t5 <- 0 to N - t10)
      if (10000 * t10 + 5000 * t5 + 1000 * (N - t10 - t5) == Y)
        return (t10, t5, N - t10 - t5)
    (-1, -1, -1)
  }
}
```
思った以上に考えがまとまらなくて時間かかりました。。。  
他の方の解かれているコードも似たようなアルゴリズムだったので安心しました。

## ABC049C 白昼夢
この問題は文字列Sが与えられ、Sが'dream' 'dreamer' 'erase' 'eraser'で構成されているかを判定する問題です。  
Stringのreplace関数を使用して、対象の文字を空文字に置き換えて最終的に空文字であるかを判定するようにしました。

```scala:ABC0049C_Hakuchumu.scala
import scala.annotation.tailrec
import scala.io.StdIn.readLine

object ABC0049C_Hakuchumu extends App {

  val S = readLine()

  replacePattern(S, Seq("eraser", "erase", "dreamer", "dream")) match {
    case "" => println("YES")
    case _ => println("NO")
  }

  @tailrec
  def replacePattern(string: String, pattern: Seq[String]): String = {
    if (pattern.isEmpty) string
    else replacePattern(string.replace(pattern.head, ""), 
                          pattern.filterNot(_ == pattern.head))
  }
```

この方法でも問題なく正解を出せるのですが、ネットで他の解答を調べてみると正規表現のほうがスマートにできそうでした。
```scala:RegexVersion.scala
val S = readLine()
val regex = "^(dream|dreamer|erase|eraser)+$".r

regex.findFirstIn(S) match {
  case Some(_) => println("YES")
  case _ => println("NO")
}
```
とてもわかりやすく簡潔ですね！！！  
無駄に再起関数書くよりこちらのほうが断然見やすいです。

それにしても正規表現がすっかり頭から抜けていました。。。  
正規表現もいざ書こうと思うと末尾を表す記号なんだっけ？となったりしちゃうのでまだまだ勉強しなくちゃいけないですね。

## 感想
スムーズにアルゴリズムが言語化できるととても楽しいのですが、まだまだ未熟なので詰まることが多いですね。。。  
ですが解けた時の達成感は癖になるものがありますね！  
AtCoderにはランクシステムがあるので、高いランクを目指して頑張りたいと思います！

以上、「AtCoder Beginners Selectionを解いた！」でした。
