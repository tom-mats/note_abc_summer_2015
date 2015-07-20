# Dronekitによる Python APIとアプリ開発の概要

+ DroneKitは元々自動車の制御がメインだったのでVechileという名前になっている。

## Dronekit-python

* DroneKit のメインのAPI
* コンパニオンコンピューター(Droneをコントールするコンピューターをコントロールするコンピュータ)上で動作する。
  * RBPi などPythonインタプリタがあるようなコンピューターのこと
  * 自立運転を高度化する。(ウェイポイントコントロールはできるという前提)
* AruduPilotと通信する
* 通信はMAVLinkだが、APIにとってはどうでも大丈夫
* 制御だけなくテレメータ(センサ、位置情報)機能もある
* OSSでGithub上に公開

## APIの機能

### 機体リストの取得

+ 複数のドローンを制御できるAPIになっている

### 機体の状態

### Waypointの作成と管理

### 指定した場所への誘導

### 機体へのメッセージ送信

### 設定済みラジコンチャンネルの書き換え

* ラジコン感覚で操作可能?

### API

* いっぱいあるけどdroneapi.lib.vehicleさえわかれば大丈夫

### droneapi.lib.Vechile

* 屋外のコントロールを前提としている。

### droneapi.lib.CommandSequence

* Drone操作のメインAPI

### 鼻腔

+ モータの制御とかは気にする必要はない。

## サンプル

### Vehichle Starter

#### 接続する
```python
api = llocal_connect()

v = api.get_cehicles()[0]
```
#### 状態表示

```python
print v.location
```

### 機体をarmedにする

```python
v.mode = Vechile("GUIDED")
v.flush() <- flushしないと、コマンドが実行されない
実行されるまで待機
print "%s" v.armed
v.armed = True
v.flush()
待機
```

#### オブザーバーを付ける

* Callbackのようなもの

#### ホームポジションの設定
```python
v.download()
```

### パラメータの設定

### RCチャンネルの上書き

* 0にすると初期値に戻る

```python
v.channel_override = {"1":900}
```

### Simple Go To

#### GPSと機体の初期化

```python
vechile.mode.name = "INITALISING"なら待機
vechile.gps_0.fix_type < 2 GPSが有効になるまで待機
GUIDEDにする(APIが制御するモード)
armedにする
takeoffする
指定する高さになるまで待機
```

### 動作命令

```
pint1 = location(xx yy, zzz, is_relativ=True)
v.command.goto(pint1)
v.flush()
time.sleep(30)
```

### Follow me

#### 初期化

自分のところのGPSと通信するようにする

#### 動作

```
自分のところのGPS情報を取得
GPSの位置をdroneへ通知
v.command.goto
v.flush
time.sleep(2)
```

### 鼻腔

* なかなか面白そう
* RBPiでできそう
* ルンバも制御できるらしい
