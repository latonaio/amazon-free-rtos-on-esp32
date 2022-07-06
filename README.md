# amazon-free-rtos-on-esp32  
amazon-free-rtos-on-esp32 は、Amazon FreeRTOS を ESP32 上で動作させるマイクロサービスです。

## 動作環境
* Amazon FreeRTOS
* ESP32

## Amazon FreeRTOS について
Amazon FreeRTOS とはプログラミング、デプロイ、保護、接続、管理を簡単にする、アプライアンス、センサー、フィットネストラッカー、産業オートメーション、自動車などの多くのデバイスで使われているマイクロコントローラー向けの、オープンソースかつリアルタイムのオペレーティングシステムです。

## 事前準備
本マイクロサービスを使用するにあたって事前に開発環境をホストマシンの OS 別にセットアップする必要があります。  
詳細は、[FreeRTOS ユーザーガイド](https://docs.aws.amazon.com/ja_jp/freertos/latest/userguide/getting_started_espressif.html)の ESP-IDF v4.2 の開始方法 を参照してください。

## 動作方法
### submoduleのダウンロード
以下のコマンドで submodule をダウンロードします。
```
git submodule update --init --recursive
```

### submoduleのディレクトリに移動
以下のコマンドで submodule をディレクトリに移動します。
```
cd freertos
```

### ESP32の開発環境のインストール
以下のコマンドで ESP32 の開発環境をインストールします。  
```
vendors/espressif/esp-idf/install.sh
```

### 環境変数のセット
以下のコマンドで環境変数のセッティングをします。  
```
source vendors/espressif/esp-idf/export.sh
```

### プロジェクトトップに移動
以下のコマンドでプロジェクトトップに移動します。  
```
cd ../
```

### ビルド
以下のコマンドでビルドします。  
```
cmake -S . -B build -DCMAKE_TOOLCHAIN_FILE=freertos/tools/cmake/toolchains/xtensa-esp32.cmake -GNinja
```

### ESP32にフラッシュ
以下のコマンドで ESP32 にフラッシュします。  
```
cmake --build build --target flash
```

### ESP32にフラッシュしたプログラムの起動とデバッグ
以下のコマンドで ESP32 にフラッシュしてあるプログラムの起動とデバッグをします。  
```
idf.py monitor
```