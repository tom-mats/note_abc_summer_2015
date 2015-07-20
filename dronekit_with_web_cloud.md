# Dronekit cloud を利用したwebサービス開発の概要
志賀 雄太さん

## Dronekit cloudとは

* RESTベースのAPI
* 飛行中のドローン、地上のスマホアプリと連携するクラウドサービス
* クラウドサービスが直接ドローンと通信するのは難しいのでは
  * スマホとの連携がメインとなるのでは

## できるサービス

### 飛行logの保管管理

* tlog(droneの共通logフォーマット)を保存、管理する

### 飛行logの解析

* クラウドサービスを使う主要な理由
* 速度、高さなどを求めてくれる

### フォーマットの変換

* JSONなどの使いやすいフォーマットに出力してくれる
* KmzなどGoogle Earth. map に沿ったフォーマットにも変換可能
  * Google Mapなら2D
  + Google Earthならば3D+アニメーションを表示してくれる。

#### doaramaにExport

+ 人がどこを走ったか表示できるようになる。

### 飛行データのリアルタイムな中継

* WebSocket中継で飛行データをリアルタイム(ストリーミング)ネット配信
* サンプルはないが、将来的には実装されるのでは?

### ユーザー認証管理

### 機体情報管理

+ ユーザーに紐付いてる
* 機体情報の下に飛行情報が紐つくような感じ

### 写真や動画の保存と配信

* API上は存在しない?、サンプルもない?
* 将来的に実装する?

## Dronekit Cloudの始め方

### 開発者登録

### Cloudを選択

### Signupに進む

### ユーザ情報を登録

### 確認メールが届くので確認

###  Sign In

APP IDとKeyは後で使うのでメモする。

## Dronekit Cloudを使ってみる

* 基本REST APIとなる
* API仕様書は3DRにまとまっている

### Droneshare

* Dronecloudのサンプルプロジェクト
* Githubに転がっている
+ Javascriptベースで動いている(URLが遷移するけどREST APIだけで書き換えている)
  * 全部Dronekit cloud側にデータがある
  * PCからDronekit cloudに直接アクセスしている

## Dronekit Cloud API

### vechile

* 機体情報
  * ユーザ名
  * 速度(統計?)

### mission

飛行情報

* Max speed
* 位置情報
* KmzやJsonで経路情報を取り出せる。

## DroneShareをローカルで動かすためのTips

### Node.jsはnvm等で管理しつつ、最新のものへ

### npmも最新に

### gruntをインストール(グローバル)

### bowerをインストール

### grun buildで静的ファイル群が生成()

### npm install karma関連のエラーは最悪無視できる

### ローカルホストでwww.droenshare.comで書き換える

### じぶんのapikeyで動作させる場合には、AppID Keyを差し替える

dist/scripts/service/dapiServices.js の上部を自分のapiKeyに差し替える。

### 自分のapiKeyで動作させた場合、ユーザー関連の処理に制限がかかる

### 実際のAPIサーバはapi.3drobotics.comに存在する

独自ドメインを行うためには設定が必要

### 見方

自分のapikeyでアクセスすると本家DroneshareのSTATSでアクセス情報が表示される。

## サンプル

### 豊作計画

* トヨタ開発
* log情報を貯める事ができるので、将来的にはビッグデータ化する
  * それに応じた管理や最適化が可能になる
