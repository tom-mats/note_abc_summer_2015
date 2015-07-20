# DronekitによるAndroid APIの概要

## 概要

* ３DRが開発
* AndroidスマホからDroneへの制御コマンド
* DroneからAndroidスマホへのデータ送信
  * リアルタイムな受診には対応していないん

### 構成

* Andoroid <-> Dronekit <-> 3DR Service <-> Drone
* 最終的には3DRサービスが直接ドローンと通信
* 様々な規格を3DR Serviceがラッパーしている。
* Simulator(Ubuntu)がある

## 開発環境の構築

+ Ubuntu 14
* Andoroid

### Simulator Ardupilot

+  Githubから取ってくるだけでオッケー

### Simulator JSBSim

+ Makeが必要

### 環境変数の設定

### Simulatorの起動

shellがあるフォルダーで実行する必要がある。

### 3D Servicesのインストール

### Sample Appの入手

## APIの概要

### Android <-> Dronekit

+ TowerListner
   * 3DR Servieとのデータやりとり
* DroneListner
   * Droneとの通信

### DroneEvent

* 接続中
* 接続完了
* 切断
* Vechlemode
* 状態更新
* キャリブレーション
* エラー取得

### Controltower

* 3DR Serviceとのデータやりとりそのもの

### Drone

* Droneとのやりとり
* 将来的には主要機能はContorlTowerに結合されてDroneクラスは非公開になるのでは

## アプリケーションの概要

### Starter

* シンプルなアプリケーション

### Tower

+ 実用的なアプリケーション
* Google play で公開済み

### その他

+ ウェアブルアプリケーションになっている
  * Jumper(テレパシー社製アイウェア)
