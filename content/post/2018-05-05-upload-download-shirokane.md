---
title: SHIROKANEとのデータ送受信
author: ~
date: '2018-05-05'
slug: upload-download-shirokane
categories: ["SHIROKANE"]
tags: []
---

基本は[wiki](https://supcom.hgc.jp/internal/mediawiki/ascp_%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89)に書いてあるとおりにすればOK.

### 自宅パソコンの場合を例示

`~/.aspera/connect/bin/ascp -i ~/.ssh/supcom_key_secret <元path> <先path>`


* パスには`<localpath>`または`<username>@fasp.hgc.jp:<supcompath>`を指定。
* localとsupcomのどちらを元path、先pathに入れるかでデータの送信と受信が決まる。
* <supcompath>は~以下の相対パスで記述。