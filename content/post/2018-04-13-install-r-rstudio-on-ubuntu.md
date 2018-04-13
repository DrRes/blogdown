---
title: Install R & RStudio on Ubuntu16.04
author: ~
date: '2018-04-13'
slug: install-r-RStudio-on-Ubuntu
categories: ["Ubuntu"]
tags: []
subtitle: ''
---

## 基本


[このサイト](http://jtremblay.github.io/software_installation/2017/06/21/Install-R-3.4.0-and-RStudio-on-Ubuntu-16.04)に従うが、ハマったところがあるので書いておく。

以下、上のサイトからコマンドを引用。


```

# Install all dependencies
sudo apt-get install build-essential
sudo apt-get install fort77
sudo apt-get install xorg-dev
sudo apt-get install liblzma-dev  libblas-dev gfortran
sudo apt-get install gcc-multilib
sudo apt-get install gobjc++
sudo apt-get install aptitude
sudo aptitude install libreadline-dev
sudo aptitude install libcurl4-openssl-dev
sudo apt-get install default-jdk
sudo apt-get install texlive-latex-base
sudo apt-get install libcairo2-dev 

# Install r-base with ubuntu
sudo apt-get install r-base

# Install newest version of R from source
 wget https://cran.r-project.org/src/base/R-3/R-3.4.4.tar.gz
./configure --prefix=/home/sinnhazime/R/R-3.4.4 --with-x=yes --enable-R-shlib=yes --with-cairo=yes
make
# NEWS.pdf file is missing and will make installation crash.
touch doc/NEWS.pdf
make install

# Do not forget to update your PATH
export PATH=~/software/R/R-3.4.0/bin:$PATH
export RSTUDIO_WHICH_R=~/software/R/R-3.4.0/bin/R

# Install libjpeg62
sudo apt-get install libjpeg62
# for some reason it prompted me to do 'sudo apt-get -f install' after. I did and it worked...

# Download Rstudio and install it.
wget https://download1.rstudio.org/rstudio-1.0.143-amd64.deb
sudo dpkg -i rstudio-1.0.143-amd64.deb

## for rJava and ReporteRs installation you also need to do this:
sudo apt-get install libxml2-dev
sudo R CMD javareconf

## install fonts as well.
sudo apt-get install t1-xfree86-nonfree ttf-xfree86-nonfree ttf-xfree86-nonfree-syriac xfonts-75dpi xfonts-100dpi


# That's it type rstudio and all should be good!
```




## ハマったところ

* Rのインストールは、r-baseを`apt-get`しただけでは相当古いバージョンがインストールされてしまう。cranのサイトを`apt-get update`で確認する方法がネットに転がっていて、まだマシなバージョンがインストールされる。しかし最新版ではなかった(tidyverseが使えない。致命的！)ので、上の方法でやるべき。
* - ただし、１行目でwgetしたあとは、手動でファイルを解凍して、./configure以下を実行すること。解凍すればreadmeファイルが入っていて、「これを見てるってことは、無事解凍できたってことだな？」的なことを言ってくるので、そのファイルに従う。

* wgetでrstudioを入れるところは、[公式](https://www.rstudio.com/products/rstudio/download/#download)から探して手動でインストールすればよい。
* パスを通すのは、これでは一時的に過ぎない。
    - 永続的に通したければ、exportの２文を**~/.profile**の末尾に書き加えれば、ログインのたびによみこまれるようになる。([このサイト](https://support.rstudio.com/hc/en-us/articles/200486138-Changing-R-versions-for-RStudio-desktop)参照)
    - 書き込み方法は、 `sudo gedit ~/.profile`で開いてコピペして保存。