# DronecodeとROSの概要

## シミュレーション環境の概要

* Off VehicleのSimulatorsの中のSITL

### PX4プロジェクト

* 上位層はMAVLinkで通信
+ ROSで飛行指示が可能
  + MAVLink <-> ROSの通信となる

### SITL(Simulation in the loop)

+ ホストPC上で全てを行う
+ 新しいアルゴリズムのテストに向いている
* ハードウェアのタイミングやスタックサイズ制限などは考慮できない

### HITL(Hardware in the loop)

* 実機を使用
* シミュレートされたセンサ情報を流し反応をみる。

### 構成

仮想環境で構成

Ubuntu <-> Docker(Ubuntu) <-> ROS <-> Gazebo

## シミュレーション環境のセットアップ

### イントロ

+ Automated SITL setupがメイン
+ OSイメージ等はサイズが大きいので注意
* ゲストOSはTerminalで接続(Xも可)

### Dockerのインストール

* 動作確認
```
docker run hello-world
```

### Xサーバの公開

```
xhost +
```

### Docker上でubuntuを立ち上げる

* --name=SITL

  コンテナ名
* px4io/px4-ros-full*

  dockerhubで公開されているイメージをダウンロード

* bash

  bashを開く

### ビルド前に

unzip をapt-get

### ビルド実行

Githubから幾つかファイルをダウンロード

### シミュレーションの軌道

```
source devel/setup.bash
roslaunch px4 gazebo-iris-empty-world.launch
```

### コントローラの設定

* PPAからドライバーをインストール
* ドライバを再起動
```
sudo service xboxdrv stop
sudo service xboxdrv
```

### 操作方法

* ARM

  プロペラを回す-><-

* DISARM

  プロペラを止める<-<-

* 移動

### キーアサインの変更

* jstest-jdk
* launchファイルに設定を書いてアサインを変更

### その他

launchファイルを切り替える事で画面を変える事が出来る

### 終了と再会

#### 終了
* Xで閉じる
* Ctrl-Cでしばらく待つ
* Ctrl-Dでbashを閉じる
* docker stop SITL

#### 再会

docker start SITL
docker exec -it sitl bash
roslaunch px4 gazebo_iris_empty_world.launch

## ROSの概要

### ROSについて

* Robot Operating Systemの略
* ハードウェアの抽象化、デバイスドライバ、ライブラリ、メッセージ通信、パッケージ管理などを提供
* BSDライセンス

### catkin_make

* ROSのオフィシャルのビルドシステム

### roslaunch

+ launchファイルで設定された内容で起動する
* launchファイルの中身
  * XMLで記述

### 新しいコマンド

* rospack find roscpp
  * apt-getみたいなもの
* roscd roscpp
  * roscppディレクトリに移動
* rosls glog_catkin
  * glog_catkinの中身を表示

インストール先はバラバラだが、rosxxで一括して扱える。

## SITLの中身

５つのレポジトリの中身

* Firmware
  + PX4のファームウェア
* catkin_simple
  * catkinのパッケージ
* glog_catkin
  * Google glogをcat_kinで使用できるようにしたパッケージ
* mav_comm
  * MAVLinkで使用されるメッセージとサービスを程御するパッケージ
* rotors_simluator
  * MAV gazeboシミュレータの一つ
  * マルチコプターの情報
  * ジョイスティックとのI/F

※ gazebo : ROS向けシミュレータ環境  

### 依存関係の解決

* package.xmlに依存関係を記載
* unzipもここに記載されているが、他のパッケージとの依存関係によりうまう行っていない?

### Firmware

* 姿勢制御などは以下にありそう
  * Firmware/src/modules/
    * attitude_estimator_ekf
    * attitude_estimator_q
    * attitude_estimator_so3
