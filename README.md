# M1 Mac 上でJava環境構築（インストールから実行まで）
- 初学者/プログラミング未経験者向け

## インストールするPCの環境
- macOS BigSur 11.1
- MacBook Air(M1, 2020)
- JDK未インストール状態
  - ターミナルで `$ java -version` 叩くと、エラーメッセージ表示

### `$ java -version`のメッセージ
```
The operation couldn’t be completed. Unable to locate a Java Runtime.
Please visit http://www.java.com for information on installing Java.
```

## アジェンダ
- Step0. Eclipseを使うべきではないたった一つの理由
- Step1. VS Code インストール
- Step2. JDKインストール
- Step3. VS Codeの設定
- Step4. Hello, world!

## Step0. Eclipseを使うべきではないたった一つの理由
- Eclipseは高機能すぎて動きが遅い
- 高いPCスペックを要求する
- 初学者は挫折しがち

### Javaの文法を学びたいだけの人はコチラがおすすめ！
- ブラウザで動く環境[dokojava](https://dokojava.jp/) もある！
  - JDKインストール不要！
  - 本[『スッキリわかるJava入門 第3版』](https://amzn.to/2FzsKep)の付録。
  - 「文法学びたいだけの人」はこっちがおすすめ。

---

## Step1. VS Codeインストール
- https://code.visualstudio.com/
- 今回のバージョンは 1.52.1

### Rosettaとは
- 従来のインテル用のMacアプリを Apple Silicon Mac上で自動的に変換して実行できるようにする仕組み
- 「Rosettaを使用してひらく」チェックボックスつけてアプリ起動すると、Rosetta上で動く
  - 例) ターミナル, Xcode, iTerm2 など

### RosettaとARMアーキテクチャ使い分けよう！
#### いま Rosetta上なのかARMアーキテクチャ上なのか確認する
- 確認コマンド `$ uname -m`
  - arm64 -> ARMアーキテクチャ で実行中
  - x86_64 -> Rosetta利用 または ネイティブIntelアーキテクチャ で実行中

- オサミーの場合：
  - ARMアーキテクチャで実行したい場合「ターミナル.app」で実行
  - Rosettaで実行したい場合「iTerm2.app」で実行
  - VSCode上では適宜 `$ arch -x86_64 zsh` や `$ arch -arm64 zsh` で切り替えする

---

## Step2. JDKインストール
- [azulのサイト](https://www.azul.com/downloads/zulu-community/?os=macos&architecture=arm-64-bit&package=jdk)からJDKダウンロード
  - Appleシリコン(M1)に最適化された Java を使える

### 下記サイトからJDKインストールしないで（おすすめしない）
- [Oracleのサイト](https://www.oracle.com/java/technologies/javase-downloads.html)
- [java.com](https://java.com/ja/)

### ニュース
- [Appleシリコン搭載Mac用のJavaをAzulが公開。マイクロソフトと協力して開発](https://www.publickey1.jp/blog/20/applemacjavaazul.html)

### JDKとは
- Java Development Kit の略
- Java のプログラムの開発や実行を行うためのプログラムのかたまり

### JDKのインストールパス
- `/Library/Java/JavaVirtualMachines`

#### JDKのアンインストール方法
```
cd /Library/Java/JavaVirtualMachines
sudo rm -rf zulu-13.jdk
```
- 間違って他のJDKインストールした人は上記コマンドでアンインストール
- 上記のJDKファイル名は適宜変える

---

## Step3. VS Codeの設定
- Extension の Java Extension Pack をインストール

---

## Step4. Hello, world!
1. パレット(⌘+⇧+P)から Javaと入力し Create Java Project選ぶ
2. Locationを指定（適当でOK。今回はworkspaceフォルダつくってそこを指定）
3. プロジェクト名を決定（今回はM1JavaProject）
4. src/App.java を開く
5. Run押して実行(App.javaを右クリック>Run もしくは mainメソッドの左上のRunボタン押下)
