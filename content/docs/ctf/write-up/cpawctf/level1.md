---
title: "Level1"
date: 2023-04-25T16:57:13+09:00
draft: false
weight: 1
---

#### [Misc] Test Problem

Flagを問題文からコピー・ペースト。

#### [Crypto] Classical Cipher

問題文のシーザー暗号をdecryptするだけ。
参考: [caesar-cipher](../../../python/cookbook/caesar-cipher/)

#### [Reversing] Can you execute

問題ページから`exec_me`をダウンロードし、Linuxの`file`コマンドでファイルの形式を調べると、x86_64アーキテクチャのプロセッサを搭載し、GNU/Linux 2.6.24以上のカーネルを実行している環境で実行できることがわかる。

```bash
> file exec_me
exec_me: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.24
```

適切な環境でexec_meを実行するとフラグを得られる。

**追加情報**

`readelf -h`を利用することでバイナリに含まれるヘッダ情報を表示することが可能。

#### [Misc] Can you open this file

問題ページから`open_me`をダウンロードし、Linuxの`file`コマンドでファイルの形式を調べると、Microsoft Office Wordで作成されたファイルであることがわかる。拡張子を`.doc`などに変更して開くとフラグを得られる。

```bash
> file open_me
open_me: Composite Document File V2 Document, Little Endian, Os: Windows, Version 10.0, Code page: 932, Author: v, Template: Normal.dotm, Last Saved By: v, Revision Number: 1, Name of Creating Application: Microsoft Office Word, Total Editing Time: 28:00, Create Time/Date: Mon Oct 12 04:27:00 2015, Last Saved Time/Date: Mon Oct 12 04:55:00 2015, Number of Pages: 1, Number of Words: 3, Number of Characters: 23, Security: 0
```

#### [Web] HTML Page

Chrome Dev Toolなどでソースコードを表示し、`cpaw`などで検索するとフラグを得られる。

#### [Forensics] River

ImageMagickのidentifyを使うと画像の詳細情報を表示できる。

```bash
$ identify --verbose river.jpg
```

表示された内容を眺めているとGPS情報が含まれていることが分かるので、あとは検索するだけ。

**追加情報**

座標の表記方法について(参考:[リンク](https://support.google.com/maps/answer/18539?hl=ja&co=GENIE.Platform%3DDesktop))
> - 度（DD）: 41.40338, 2.17403
> - 度分秒（DMS）: 41°24'12.2"N 2°10'26.5"E
> - 度分（DMM）: 41 24.2028, 2 10.4418

#### [Network]pcap

Wiresharkでpcapファイルを開き、パケットをダブルクリックで開くとバイト列が表示されるので、そのなかからフラグを探して完了。

#### [Crypto]HashHashHash!

Hash Toolkitで検索。
#### [PPC]並べ替えろ!

配列を降順ソートして連結して完了。
