# 災害援助ナビゲーターカスタマイズHOWTO

tomoiida@gmail.com



## 目的

このドキュメントは袖ケ浦市の災害支援ナビゲーター(http://civictechsodegaura.org/saigai)の内容を別の市町村や別の目的のために使用できるようカスタマイズするための設定・ビルド方法を説明します。

## 準備

以下のツールが必要です。

* yarn (パッケージツール)
* vue-cli （WebUIライブラリ）

```
# yarnのインストール
npm install -g yarn

# vue-cliのインストール
npm install -g @vue/cli

# ライブラリのアップデート
yarn install
```

## 設定ファイルの更新

### サブフォルダの指定

サービスをドメインのサブフォルダ（http://xxx.xxx/path/to/）に配置する場合、vue.config.jsのpublicPathを書き換えます。

```
module.exports = {
  publicPath: '/path/to/',
  "transpileDependencies": [
    "vuetify"
  ]
}
```

### 質問ファイル(src/data/QData.js)の更新

下記サービスファイルで紹介する各種制度から、どのような質問を立てれば分類できるか書き出す。

### サービスファイル(src/data/Services.js)の更新

内閣府 防災情報のページ（http://www.bousai.go.jp/taisaku/hisaisyagyousei/seido.html)にある「被災者支援に関する各種制度の概要(PDF）」を参照し、災害救助法適用の有無や各実施主体での実施の有無を確認しながら当該自治体で適用可能性のある制度をピックアップする。また、市町村、都道府県での独自措置や国での特別措置などがある可能性があるため、それらも確認して加える。

# デプロイ方法

## ビルド

以下のコマンドでビルドします。

```
yarn build
```

## デプロイ

./distフォルダの内容をサーバーのフォルダ（vue.config.jsで指定した場所）にアップロードしてください。
