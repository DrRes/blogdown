---
title: How to Use RStudio on SHIROKANE
author: ~
date: '2018-04-13'
slug: shirokane
categories: ["SHIROKANE"]
tags: []
subtitle: ''
---

## from Windows

### 起動方法

* XLaunch起動
* TeraTerm 起動
* 新しい接続：
  　ホスト：slogin.hgc.jp
* 次へ
  - ユーザ名：sn....
  - パスフレーズ：.........
  - RSA/...鍵を使う　秘密鍵：Document/supcom_key_secret

* `qlogin -l s_vmem=32G,mem_req=32G`
  - 32の部分は一致していればほかの数字でよい
* `rstudio`

### 初回設定
* TeraTerm　設定＞SSH転送＞リモートの(x)アプリケーションをlocalのXサーバに表示する　にチェックし、設定の保存を実行。再起動しておく

* `qlogin`後、　`vi ~/.bash_profile`　として、以下を追記。
  - export PATH=/usr/local/package/rstudio/1.1.322/bin:${PATH}
  - export RSTUDIO_WHICH_R=/usr/local/package/r/3.4.1/bin/R

* 一応、c:/Program Files(x86)/Xming/X0.hostsに
  172.27.18.122
  を追記してあるが、多分いらない

## from Ubuntu

### 起動方法