# cmake build of TOPPERS/FMP3 for Raspberry Pi Pico

下記の TOPPERS/FMP3 for Raspberry Pi Pico を cmake でビルド出来るようにし、ターゲット非依存部を「3.3.3」に更新したものです。

<https://toppers.jp/fmp3-e-download.html#raspi_pico>

## 開発環境のインストール

Ruby と Visual Studio Code の Raspberry Pi Pico 拡張機能を使用します。

Rubyをインストールしてパスを通してください。「`.vscode/settings.json`」のパスに追加して Visual Studio Code のターミナルを使用すれば、システムの環境変数に追加する必要はありません。

下記の Raspberry Pi Pico 拡張機能をインストールしてください。

<https://marketplace.visualstudio.com/items?itemName=raspberry-pi.raspberry-pi-pico>

SDKバージョン「2.0.0」でプロジェクトを作成すると、開発環境がインストールされます。

※最新のSDKバージョンを使う場合は、「`.vscode/settings.json`」のパスを変更してください。

作成したプロジェクトはFMP3のビルドには使用しません。

## Sample1のビルド

このリポジトリを展開したフォルダで、下記のコマンドを実行します。

```bash
mkdir build
cd build
cmake -G Ninja ..
cmake --build .
```

このリポジトリの状態を起点に「CMakeLists.txt」を編集して、プロジェクトを構築してください。

## 注意

現状ビルドが出来るようになった段階で、検証は不十分ですので修正が必要になると思います。
