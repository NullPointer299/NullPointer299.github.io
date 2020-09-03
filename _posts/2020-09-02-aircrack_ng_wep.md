---
layout: post
title: aircrack-ngでWEPパケット解析してみた！
subtitle: 思っていたより簡単！！！
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [aircrack-ng]
---

こんにちは！  
H.N.です。  
今回はaircrack-ngを使ってWEP暗号が使われているWIFIのパスワードを解析した話です。  
前回構築したkaliは結局使いませんでした。。。

## きっかけ
aircrack-ng自体は前から知っていたのですが、解説記事を読んでいると難しそうに感じてなかなか手が出せませんでした。  
kaliも構築したしいい機会だからやってみようと思ったのがきっかけです。  
kali使わなかったですが。

## インタフェースの設定
まず無線インタフェースを使っているプロセスをキルします。  
systemdなどによって管理されている場合は自動で再起動されることもあるので、管理コマンドで停止しましょう。

---
```Bash
airmon-ng check kill
```
---

プロセスのキルができたら無線インタフェースをモニタモードで立ち上げます。  
モニタモードは検出できる無線のすべての通信を受け取るモードです。  
有線LANのパケットキャプチャで使用するプロミスキャスモードの無線版と考えればわかりやすいですね。

---
```Bash
airmon-ng start $IF
```
---

## 解析対象の情報収集
解析対象についてBSSID、とChannelの情報を収集します。

---
```Bash
airodump-ng --encrypt WEP $IF
```
---

BSSIDの項目と、CHの項目をメモしておきましょう。  
airodump-ngコマンドはqを2回入力することで終了することができます。  
続いて、BSSIDとCHを指定して情報を収集します。  
-wオプションで保存ファイル名を指定します。

---
```Bash
airodump-ng --bssid $BSSID --channel $CH -w $filename $IF
```
---

Data列が30000程度になるまでパケットを収集します。  
カレントディレクトリ以下に$filenameで始まるファイルがいくつか出力されます。

## ARP-request replay
解析対象に接続している機器が頻繁に通信していればパケットを集めやすいのですが、あまり通信していない環境だと解析に時間がかかります。  
これはARP-request replayをすることで対策できます。

まず、解析対象とアソシエーションを確立します。  
アソシエーションを確立すると有線接続でいうリンクアップした状態と同じになります。

---
```Bash
aireplay-ng -1 0 -a $BSSID $IF
```
---

アソシエーションの確立が成功したら、ARP-request replayを開始します。

---
```Bash
aireplay -3 -b $BSSID $IF
```
---

取得したARP requestと送信したパケットを見ることができます。  
しかし、これだけでは接続している機器が再認証するときまで待たないといけません。（ARP requestが再認証するときでないと取得できないため）  
なので待てない時は接続している機器を強制的に切断させて再認証させます。

---
```Bash
aireplay -0 1 -a $BSSID -c $CONNECTED_DEVICE_MAC $IF
```
---

これで効率的にパケットを収集することができます。

## パケット解析
収集したパケットからWEPパスワードを計算します。

---
```Bash
aircrack-ng "${filename}-01.cap"
```
---

パケットの量が十分ならばWEPパスワードが解析できているはずです。

## 感想
こんな簡単にパスワードが解析できてしまうなんて。。。  
今の時代にWEPなんて。。。とはよく言いますが実際に5分程度で解析できてしまうのを目の当たりにすると恐ろしいですね。  
街中でふとWIFIを見るとWEP見かけたりするので、危ないな～なんて思っていましたが改めて本当に危ないですね。  
平文で通信してるようなもんですね。  
とても勉強になりました。  
WPAとかWPA2についても解析ができるようなので、また挑戦してみたいと思います！

## 参考サイト
* [gate.hatenablog.jp](http://gate.hatenablog.jp/entry/2018/02/08/aircrack-wep){:target="_blank"}
* [nvnote.com](https://nvnote.com/wep-crack-kalilinux/){:target="_blank"}

以上、「aircrack-ngでWEPパケット解析してみた！」でした。
