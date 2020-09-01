---
layout: post
title: DockerでKali linuxをインストールした話！
subtitle: 手軽に環境作れるが本当に便利！！！
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [Docker, Kali linux]
---

こんにちは！  
H.N.です。  
今回はDockerでKali linuxをインストールした話です。

## きっかけ
Aircrack-Ngという無線LANの解析ツールを使ってみたいと思ったのですが、  
今使っているArch linuxにインストールしてしまうと無線LANのインタフェースの設定を変えてしまうので、  
DockerにKali linuxを入れようと思い、と同時に今日はなにも記事にできるようなことをできなかったので記事にしようと思いました。。。

## DockerにKali linuxをインストールする
他のディストリビューションをインストールする時と全く同じ方法でインストールできました。

---
```Shell
docker run -it kalilinux/kali-rolling /bin/bash
```
---

このコマンドでpullとexec両方やってくれるので、インストールが終わり次第コンソールにログインできます。

---
```Shell
apt install kalilinux-everything
```
---

ログイン後のコンソールで上記のコマンドでKali-linuxのパッケージ類をインストールできます。  
2時間くらいかかります。

## 感想
Dockerはやっぱり便利ですね！  
サーバを1つ1つ作っていたことが本当に馬鹿らしく感じます。。。

近いうちにAircrack-Ngの記事もあげたいと思います！
以上、「DockerでKali linuxをインストールした話！」でした。
