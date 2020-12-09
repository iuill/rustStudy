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

Rustのネーミングルールはこれ。  
スネークケースだったりキャメルケースだったり。  
https://github.com/rust-lang/rfcs/blob/master/text/0430-finalizing-naming-conventions.md

## Rust/WinRT

言語の各機能を試していくだけだとモチベーション保てないので、何かツールを作ろうかと思い、いきなりRust/WinRTを触ってみることにする。（WinRT自体も初めて）

現在、Rust/WinRTはプレビュー版。  
https://github.com/microsoft/winrt-rs

ただし上記ページの "Getting started" は、記述がかなり不親切で以下コードの部分でドハマリ。（Rustそのものをわかってる前提？）  
>include_bindings!();


このコードはなくてもビルドは通る。  
入れる必要があるのかはよくわかってない。入れるのであればmacro.rs内のinclude_bindingsマクロの定義を参照。

そしてビルドが遅い。  
依存するWinRTコンポーネントのチェックのたびにgithubと通信してるぽい。

### Cargo.tomlで謎エラー

ビルドが通ってるのかよくわからない状態に。原因不明。  
👇これか。。。  
https://github.com/microsoft/winrt-rs/issues/381  
https://github.com/microsoft/winrt-rs/pull/382  


