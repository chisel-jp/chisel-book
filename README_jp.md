# Digital Design with Chisel (日本語版)

- 日本語版翻訳の流れ
    - 全体を機械翻訳（全体 俯瞰）
    - 校正初回 作業（実質の翻訳作業）
        - 2021-02-01 RC 0.3
- 日本語版の変更点
    - 原文、機械翻訳、校正を同時に管理できるように変数追加
        - 原文: fshoworiginal
        - 機械翻訳: ifshowtransfirst
        - 校正初回: ifshowtranssecond
        - 現在は 校正初回 (ifshowtranssecond) のみの表示モード
    ーSection にその行番号と進捗状況と追記
        - 作業終了時に行番号と進捗状況は削除
- 翻訳作業のボランティア募集中です
    - 日本語版のソースコード https://github.com/chisel-jp/chisel-book
    - 連絡は Chisel勉強会のSlackにお願いします。
        - 登録URL https://chisel-jp-slackin.herokuapp.com/

日本語版の翻訳状況(2021-02-01)

| 章      | 機械翻訳 | 校正初回  |コメント|
|--------:|--------|---------|-----------------|
| はじめに | 完了     | 完了     |
| 序文     | 完了    | 完了     |
| 1章     | 完了     | 完了     |
| 2章     | 完了     | 完了     |
| 3章     | 完了     | 完了     |
| 4章     | 完了     | 完了     |
| 5章     | 完了     | 完了     |
| 6章     | 完了     | 完了(1/1)
| 7章     | 完了     | 完了(12/30)
| 8章     | 完了     | 完了(1/2)
| 9章     | 完了     | 完了(1/2)
| 10章    | 完了     | 完了(12/30)
| 11章    | 完了     | 完了(1/4)
| 12章    | 完了     | 完了(1/4)
| 13章    | 完了     | 完了     |
| A       | 完了     | 完了     |
| B       | 完了     | 完了     |
| C       | 完了     | 完了     |

## Latex の ビルド環境

日本語Latexのビルド環境です、いくつか選択肢があります。


| 環境      | コメント |
|----------|--------------------------------------------------------------|
| Overleaf | make gencode などは事前に実施しておく、Latex の Build は安定している
| CentOS7  |
| Ubuntu   | TBD
| OSX      | make gencode でエラー、文字コード関連のエラーが多く発生
| Windows  | TBD


Latex 環境
- TexLive 2020 - OK
- TexLive 2019 - OK


### CentOS7での環境セットアップ

Install SBT

    curl https://bintray.com/sbt/rpm/rpm | sudo tee /etc/yum.repos.d/bintray-sbt-rpm.repo
    sudo yum install sbt

Install Scala

    wget https://downloads.lightbend.com/scala/2.13.3/scala-2.13.3.rpm
    sudo yum install scala-2.13.3.rpm

Install Tex Live (https://tug.org/texlive/)

    wget http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz
    tar xvf install-tl-unx.tar.gz
    cd install-tl-20201007
    sudo ./install-tl

    export PATH=$PATH:/usr/local/texlive/2020/bin/x86_64-linux


- 既知の問題
    - OS の TexLiveパッケージは色々と足りない物がありビルドで失敗します。
    - 文字コード関連のエラーが発生しますが無視でOK

### OSXでの環境セットアップ

Install SBT

    brew install sbt

Install Latex

    brew cask install basictex
    brew install ghostscript

tlmgr で必要なコンポーネントを追加

    sudo tlmgr update --self --all
    sudo tlmgr paper a4
    sudo tlmgr install collection-langjapanese


    sudo tlmgr install multirow
    sudo tlmgr install dirtree
    sudo tlmgr install helvetic
    sudo tlmgr install zapfchan
    sudo tlmgr install standalone
    sudo tlmgr install tikz-timing
    sudo tlmgr install pgfopts

- 既知の問題
    - make gencode で code の生成に失敗します。
    - 文字コード関連のエラーが発生しますが無視でOK

### ビルド

日本語版のソースコードの準備

    git clone git@github.com:chisel-jp/chisel-book.git
    cd chisel-book
    git checkout japanese

PDFの生成

    make

chisel-book.pdf ファイルが生成されます。

### Overleaf (TexLive 2019, 2020)

code 生成後、Overleafに一式コピーしてビルド可能。


EOF