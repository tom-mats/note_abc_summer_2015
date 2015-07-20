# ABC Summer 2015

## 概要

ABC summer 2015のDrone関連の勉強会に参加してきた。

その時のメモ。

## タイムテーブル

### オープンソース によるドローンの開発の概要 講師：himamura

【概要】オープンソースによるドローンの開発が注目されています。
その中心になるであろう「Dronecode」におけるオープンソースソフトウェアとオープンソースハードウェアの紹介を行います。

* オープンソースによるドローンのコントローラーの歴史と概要
* Linux系フライトコントローラと非Linux系コントローラの紹介
* Linux Foundationによるオープンソース「Dronecode」の概要
* オープンソースハードウェアの紹介と概要
* ドローンアプリ開発の「Dronekit」の紹介

### DronekitによるAndroid APIの概要 講師：moguriso

【概要】Dronecodeプロジェクトの一つであるDronekitの紹介（1）

「Dronekitを使用したAndroidアプリの開発」
* Dronekit for Androidの概要
* Dronekit for Android開発環境の構築
* Dronekit for Android APIの概要
* Dronekit for Android APIを使用したアプリの概要

### Dronekitによる Python APIとアプリ開発の概要 講師：ogochan

【概要】Dronecodeプロジェクトの一つであるDronekitの紹介（2）

「DronekitのPython APIを使ったアプリの開発」
* Dronekit for Python APIの概要
* Dronekit for Python APIの開発環境の構築
* Dronekit for Python APIの概要
* Dronekit for Pumping APIを使用したアプリの概要
* Dronekit for Cloudの概要

### Dronekitクラウドを利用したwebサービス開発の概要 講師：DRONE.BAR 志賀雄太

【概要】Dronecodeプロジェクトの一つであるDronekitの紹介（3）

「DronekitのCloud APIを使ったwebサービス開発」
* Dronekit for Cloudの概要
* Dronekit for Cloudの開発環境の構築
* Dronekit for Cloud を利用したwebサービスの紹介

### DronecodeとROSの概要（仮） 講師：くまだす

【概要】LinuxベースのフライトコントローラのオープンソースであるDronecodeにはROS（Robot Operating System）が使用されています。

+ ROSって何？なぜROSを使うの？
+ ROSで何ができるの？
+ ROSでによるフライトコントローラの制御例
* Drone用のROSのパッケージの概要
+ サンプル

### Linuxベースのオープンソース フライトコントローラの概要 講師：hsgucci

【概要】ドローンのフライトコントローラの内部構造の説明と制御の概要
* Linuxベースのドローン用フライトコントローラの紹介（NAVIO+とErle Brain）
* フライトコントローラのソフト構成
* マルチコプターの制御方法
* フィルター処理と応用

## 備考

Redmineのtextileにするにはpandocで叩けば良いようだ

```
pandoc -s -S input.md, -t textile -o output.textile
```

* FacebookにDronecodeのグループがあるので、そこでアナウンス
