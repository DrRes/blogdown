---
title: MACでUbuntu
author: ~
date: '2018-05-09'
slug: ubuntu-in-mac
categories: ["Ubuntu"]
tags: []
---

## 設定ファイルのメモ

### ~/.profileに記載

```
export PATH=/opt/google/chrome/:~/R-3.4.4/bin:$PATH
export RSTUDIO_WHICH_R=~/R-3.4.4/bin/R

!may not work in ~/.profile but in ~/.bushrc
xmodmap ~/.Xmodmap
```

### ~/.Xmodmapに記載

```
!enable eisuu & kana
!must modify mozc property
keycode 130 = Hiragana
keycode 131 = Muhenkan

!exchange control & command
clear control
clear mod4

keycode 37 = Super_L NoSymbol Super_L
keycode 133 = Control_L NoSymbol Control_L

add control = Control_L Control_R
add mod4 = Super_L

!reverse scroll
pointer = 1 2 3 5 4 7 6 8 9 10 11 12
```