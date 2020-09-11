---
layout: post
title: ArchにVirtualboxをインストールした！
subtitle: ちゃんと読んでないと詰まる！！！
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [Arch, Virtualbox]
---

こんにちは！  
H.N.です。  
今回はArch LinuxにVirtualboxをインストールした話です。

## きっかけ
Windows10を使用したくなり、手元のArch LinuxにVirtualboxをインストールしたのですが、wikiをちゃんと読まなかったので少し詰まった話です。

## インストール
Arch Wikiを参照しました。  
[Virtualbox - ArchWiki](https://wiki.archlinux.jp/index.php/VirtualBox)

virtualboxパッケージとlinux-zen-headerパッケージをインストールします。  
virtualboxパッケージのインストール時にvirtualbox-host-modules-archかvirtualbox-host-dkmsを選択します。  
linuxカーネルを使用している場合はvirtualbox-host-modules-archを選択しましょう。  
linuxカーネル以外を使用している場合はvirtualbox-host-dkmsを選択しましょう。

私はzenカーネルを使用していたので、追加でlinux-zen-headerパッケージをインストールする必要がありました。

---
```Bash
pacman -S virtualbox linux-zen-header
```
---

## 感想
非常に簡単ですね！
ちゃんとWikiを読まないでvirtualboxパッケージのみをインストールした結果詰まりました。。。

以上、「ArchにVirtualboxをインストールした！」でした。
