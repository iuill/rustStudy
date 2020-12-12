# Rustの学習用

## 環境構築

### Rustを入れる

https://news.mynavi.jp/article/rust-9/

「A. Windows 10 (rustc)」の方法でインストール。

インストールオプション
  1) Proceed with installation (default)


バージョン
  * rustc 1.48.0 (7eac88abb 2020-11-16)
  * cargo 1.48.0 (65cbdd2dc 2020-10-14)

### VisualStudioCode用のExtentionPack

https://news.mynavi.jp/article/rust-10/


## Hello World

ここの後半。  
https://news.mynavi.jp/article/rust-10/


ターミナル -> ビルドタスクの実行 -> cargo build xxx

で、いきなりworningが1件出る。  
> warning: crate `HelloWorld` should have a snake case name


Rustは命名にもチェック入るのか。。衝撃。  
スネークケースにしないといけない。  
https://wa3.i-3-i.info/word1180.html

## メモ書き

* Rustのネーミングルール  
https://github.com/rust-lang/rfcs/blob/master/text/0430-finalizing-naming-conventions.md

* The Rust Programming Language 日本語版  
https://doc.rust-jp.rs/book-ja/title-page.html

* TOMLの文法  
https://github.com/toml-lang/toml

* イテレータ  
C#のLINQみたいに書ける。

* 三項演算子
存在しない。if～elseでつらつら書く。

* クラスはない  
構造体にメソッドを追加はできる。

* シンタックスチェック、ビルド  
通常時はcheckですませる。
exe生成したいときにbuild。

* Cargo  
ビルド、パッケージマネージャ、ドキュメント生成等

* cargo パッケージ管理  
インストール： `cargo install cargo-update`  
パッケージアップデート： `cargo install-update -a`  

* デバッガ  
デバッガとしてCodeLLDBを入れてみた。普通に使える。  
https://qiita.com/84zume/items/377033ab6b6aee2a68d7


# Rust/WinRT

言語の各機能を試していくだけだとモチベーション保てないので、何かツールを作ろうかと思い、いきなりRust/WinRTを触ってみることにする。（WinRT自体も初めて）

現在、Rust/WinRTはプレビュー版。  
https://github.com/microsoft/winrt-rs

ただし上記ページの "Getting started" は、記述がかなり不親切で以下コードの部分でドハマリ。（Rustそのものをわかってる前提？）  
`include_bindings!();`

このコードはなくてもビルドは通る。  
入れる必要があるのかはよくわかってない。入れるのであればmacro.rs内のinclude_bindingsマクロの定義を参照。

そしてビルドが遅い。  
依存するWinRTコンポーネントのチェックのたびにgithubと通信してるぽい。  
調べてみたらシンタックスチェックはcheckで済ませるものらしい。

## Cargo.tomlで謎エラー

ビルドが通ってるのかよくわからない状態に。原因不明。  
ビルドが通らないの👇これか。。。  
https://github.com/microsoft/winrt-rs/issues/381  
https://github.com/microsoft/winrt-rs/pull/382  

上記解決済みであるものの、Cargo.tomlで「failed to run custom build command for `winrt v0.8.0 ～～」と出るのはよくわからない。
でもビルドは通るし、exeも生成されている。（拡張機能がどれかバグってる？）

Rust/WinRTの更新頻度かなり高いので、手を出すのは一旦保留。
