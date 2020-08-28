---
layout: post
title: Jekyllを使ってブログを始めてみた！
subtitle: 事前知識ゼロでできる！！！
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [jekyll]
---

こんにちは！  
H.N.です。  
記念すべき初回の記事はこのブログを作成したことについて書こうと思います。

ずっとブログを始めてみたいと思っていたけど、なかなか腰が上がらなくてタイミングを逃していました。  
いざやってみると、ものの数時間で体裁整えるところまで終わったので驚きました。  
自分で一からコード書くのなんてもうこのご時世あほらしくなっちゃいますね。  

初回は、Jekyllを使って公開されたテーマからブログを始めた記事を書きます。

私が使用した方法はgithubが使えれば事前知識は一切**必要ありません。**  
使えなくてもチュートリアルを見れば誰でもできると思います。

## テーマを選ぶ

今回使ったテーマはこちら  
* [beautiful-jekyll](https://github.com/daattali/beautiful-jekyll){:target="_blank"}

シンプルで見やすいのが気に入ったので選びました。

テーマは以下のサイトで探しました。  
* [jekyllthemes.io](https://jekyllthemes.io/free){:target="_blank"}

どれも良さそうで、目移りしちゃいますね。

テーマを選んだ当初は気づかなかったのですが、beautiful-jekyllでは  
リポジトリをforkして、リポジトリ名を変更するだけで即github.ioにデプロイできます。

すごいです。（他のもそうなのかな？）

## 設定を変更する

ここまで出来たらあとはREADME.MD読みながら設定を変更していくだけです。

全体的な設定は_config.ymlで変更できます。  

新しく記事を作成したいときは、postsディレクトリの中にyyyy-mm-dd-blog_titleのようにファイルを作成することで記事を作成できます。

スムーズにやれば体裁整えても1時間もかからなそうですね。

以上、「Jekyllを使ってブログを始めてみた」でした。
