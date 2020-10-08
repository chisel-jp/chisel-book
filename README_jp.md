# Digital Design with Chisel (日本語版)

- 日本語版翻訳の流れ
    - 全体を機械翻訳（全体 俯瞰）
    - 校正初回 作業（実質の翻訳作業）
- 日本語版の変更点
    - 原文、機会翻訳、校正を同時に管理できるように変数追加
        - fshoworiginal
        - ifshowtransfirst
        - ifshowtranssecond
        - 現在は ifshowtranssecond のみ表示モード
    ーSection にその行番号と進捗状況と追記
        - 作業終了時に行番号と進捗状況は削除
- 翻訳作業のボランティア募集中です
    - 連絡は Chisel勉強会のSlackにお願いします。
        - 登録URL https://chisel-jp-slackin.herokuapp.com/


日本語版の翻訳状況(2020-10-08)

| 章      | 機械翻訳 | 校正初回  |コメント|
|--------:|--------|---------|-----------------|
| はじめに | 完了     | 完了     |
| 序文     | 完了    | 完了     |
| 1章     | 完了     | 完了     |
| 2章     | 完了     | 完了     |
| 3章     | 完了     | 完了     |
| 4章     | 完了     | 作業中
| 5章     | 完了     | 作業中
| 6章     | 完了     |
| 7章     | 完了     |
| 8章     | 完了     |
| 9章     | 完了     |
| 10章    | 完了     |
| 11章    | 完了     |
| 12章    | 完了     |
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

### CentOS7での環境セットアップ

Install SBT

    curl https://bintray.com/sbt/rpm/rpm | sudo tee /etc/yum.repos.d/bintray-sbt-rpm.repo
    sudo yum install sbt

Install Scala

    wget https://downloads.lightbend.com/scala/2.13.3/scala-2.13.3.rpm
    sudo yum install scala-2.13.3.rpm

Install Latex

    wget http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz
    tar xvf install-tl-unx.tar.gz
    cd install-tl-20201007
    sudo ./install-tl

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
    - 文字コード関連のエラーが多く発生します

### ビルド

日本語版のソースコードの準備

    git clone git@github.com:chisel-jp/chisel-book.git
    cd chisel-book
    git checkout japanese

PDFの生成

    make


chisel-book.pdf ファイルが生成されます。


EOF