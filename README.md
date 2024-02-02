# 2023gsc_WataruYoshida

吉田航の2023年度ゼミ論用レポジトリ
# 【2023年度ゼミ論】埼玉県新座市におけるPLATEAU LOD1 建物データをOSMにインポートする際の事前準備及びインポート作業
地球社会共生学部　地球社会共生学科　4年A組200番

学籍番号：1A120189　氏名：吉田航

指導教員：古橋　大地教授

©Furuhashi Laboratory/Wataru Yoshida, CC BY 4.0

## Abstract

本研究では、誰でも編集可能な地図[**OpenStreetMap**](https://www.openstreetmap.org/#map=15/35.7449/139.4576) (以下OSM)の**3D建物データの量的・質的向上を目的**として、国土交通省主導の日本全国の3D都市モデルの整備・活用・オープンデータ化を目指すプロジェクト[**PLATEAU**](https://www.mlit.go.jp/plateau/)の**LOD1の建物データをOSMにインポート**するという作業を行う。インポートを実施する地域は[JA:MLIT PLATEAU/imports list](https://wiki.openstreetmap.org/wiki/JA:MLIT_PLATEAU/imports_list)を参考として**埼玉県新座市**とし、[JA:MLIT PLATEAU/imports outline/manual](https://wiki.openstreetmap.org/wiki/JA:MLIT_PLATEAU/imports_outline/manual)に基づいて、PLATEAUデータのインポート作業を行う。加えてインポート作業の前段階に当たる「事前準備」の必要性及びその手順についても考察する。

## Introduction
近年、**デジタルツイン**という概念が世界的な注目を集めている。

デジタルツインは、インターネットに接続した機器などを活用して現実空間の情報を取得し、サイバー空間内に現実空間の環境を再現する技術である。(参考：総務省「デジタルツインって何？」https://www.soumu.go.jp/hakusho-kids/use/economy/economy_11.html, 2023年12月21日情報取得)

特に中国、米国、ドイツ、英国などの国々がデジタルツイン技術の先進国として力を入れており、産業界や学術界での注目度も高くなっている。(参照：国立研究開発法人科学技術振興機構 研究開発戦略センター「デジタルツインに関する国内外の研究開発動向」https://www.jst.go.jp/crds/pdf/2021/RR/CRDS-FY2021-RR-09.pdf, 2023年12月21日情報取得)

デジタルツインによって、現実世界のリアルタイムな監視やシミュレーションが可能になり、業務の効率化、コスト削減、開発時間の短縮といった多岐にわたるメリットをもたらす。これらのメリットを踏まえると、デジタルツインの導入と発展は今後の技術革新において欠かせないものと言えるであろう。

日本においても、デジタルツイン技術の重要性は認識されており、国土交通省都市局が主導する[**PLATEAU**](https://www.mlit.go.jp/plateau/)というプロジェクトがその一例だ。

このプロジェクトは、日本全国の3D都市モデルの整備およびオープンデータ化を目指している。PLATEAUは、地理空間情報に関する国際標準化団体であるOpen Geospatial Consortium（OGC）によって策定された、3次元都市空間を記述するためのデータ交換フォーマット「CityGML」を採用しており、これにより建物や道路など都市の構成要素が、形だけでなく用途や築年数、行政計画といった都市活動情報を含む形でデジタルツイン化される。(参照：PLATEAU by MLIT「CityGML仕様及び品質評価手法についての解説」https://www.mlit.go.jp/toshi/daisei/content/001614666.pdf, 2023年12月21日情報取得)

一方で、**OpenStreetMap**（以下OSM）は、誰でも地図の編集が可能なオープンデータの共同作業プロジェクトである。OSMの特徴は、その地域に住む地元の人々が編集することで、ローカルエリアの詳細な情報が反映されている点にある。しかし、3D建物データが不足しているか、十分に拡充されていない地域が多く、課題の一つとなっている。

そこで注目されるのが、国土交通省都市局が主導し、高精度な3D建物データを提供している**PLATEAUのデータをOSMにインポート**する動きだ。この取り組みにより、OSM上の3D建物データは量的にも質的にも大きく向上する可能性がある。重要な点は、PLATEAUがOSMと互換性のあるODbLを採用していることであり、これにより両プロジェクト間でのデータの共有と活用が容易になる。

本研究では、**PLATEAUのLOD1建物データをOSMにインポートする作業及びその事前準備の方法を確立する**ことを目指している。本研究の目的は、CityGML形式のデータをOSMに実践的にインポートし、OSMの3D建物データを量的にも質的にも向上させることだ。PLATEAUのデータを活用することで、OSMが提供するデジタル地図のリアリティと詳細性が高まり、より実用的で信頼性の高い地図情報の提供が可能になることが期待される。

インポートを実施する地域は[JA:MLIT PLATEAU/imports list](https://wiki.openstreetmap.org/wiki/JA:MLIT_PLATEAU/imports_list)を参考として**埼玉県新座市**とし、[JA:MLIT PLATEAU/imports outline/manual](https://wiki.openstreetmap.org/wiki/JA:MLIT_PLATEAU/imports_outline/manual)に基づいて、PLATEAUデータのインポート作業を行う。加えてインポート作業の前段階に当たる「事前準備」の必要性及びその手順についても考察する。


## Methods

## 「事前準備」

### 1.インポートする際のJava実行環境の調査
インポート時に使用する`citygml-osm`開発者である林優氏に助言をいただきながら、Javaのバージョンを変えながらpowershellでcitygml-osmを開き、`java -Dfile.encoding=utf-8 -jar citygml-osm-jar-with-dependencies.jar 1st`のコマンドを実行

### 2.[Tasking Manager](https://tasks.teachosm.org/projects/1499/tasks/?page=1)、JOSMを用いたOSMの妥当性検証、エラー・警告の修正
[JA:MLIT PLATEAU/imports list](https://wiki.openstreetmap.org/wiki/JA:MLIT_PLATEAU/imports_list)を参考として妥当性検証を実施する地域は**埼玉県新座市**とした。

* [Tasking Manager](https://tasks.teachosm.org/projects/1499/tasks/?page=1)では以下の図のように新座市を16分割し、マッピングという名目で妥当性検証を行った。筆者の判断で修正できるエラー・警告は修正し、修正が難しい場合は事例収集としてスクリーンショットの撮影・緯度経度の記録を行った。
![IMG_7748](https://user-images.githubusercontent.com/93134160/216592576-a55161d7-e5fa-412c-93ea-ea8002377d2c.jpg)

* JOSMにおける妥当性検証では「ファイル」から「データをダウンロード」を選択し、[Tasking Manager](https://tasks.teachosm.org/projects/1499/tasks/?page=1)で分割したメッシュごとに妥当性検証を行い、エラー・警告の事例収集を行った。
<img width="740" alt="image" src="https://user-images.githubusercontent.com/93134160/216593765-83a20434-5a00-4c8b-8da7-08787bb7c7f1.png">

### 3.OSMの妥当性検証で表示されたエラー・警告の事例収集
* [Tasking Manager](https://tasks.teachosm.org/projects/1499/tasks/?page=1)、JOSMでの妥当性検証で筆者では修正不可だったエラー・警告のスクリーンショット・緯度経度を記録。
* [JA:JOSM/Validator](https://wiki.openstreetmap.org/wiki/JA:JOSM/Validator)を参考とし、「重複したノード」「重複したウェイノード」「逆転した海岸線」「結合されていない海岸線」「順序だっていない海岸線」「不完全なウェイ」「交差しているウェイ」「重なり合っている高速道路、ウェイ」「同一ウェイ内での交差」「類似した名前のウェイ」「閉じていないウェイ」「タグのつけられていないウェイ」「他の高速道路付近のウェイとノード」「合致していない外側のウェイの形成」「（マルチ）多角形と同様である内側のウェイの形成」「Fix.meリクエスト」やこれらに関するエラー・警告、その他筆者が重要であると判断したエラー・警告のスクリーンショット・緯度経度を記録した

### 4.収集したエラー・警告を[Googole Spredsheet](https://docs.google.com/spreadsheets/d/1g_SA-b3N3m7rKWzYLOa16hlr8yBpsMljPL22gAJN4FQ/edit?usp=sharing)にまとめ、各エラー・警告を古橋教授やOpenStreeaMapの上級者マッパーに見てもらい、各項目の対処法を定義する。

## PLATEAUデータインポート作業

### [JA:MLIT PLATEAU/imports outline/manual](https://wiki.openstreetmap.org/wiki/JA:MLIT_PLATEAU/imports_outline/manual)　に基づき、JOSMを用いて埼玉県新座市にLO1建物データのインポート作業を行う

## Results

### 1. インポートする際のJava実行環境の調査
検証の結果、citygml-osmで利用されている"apache camel v2.25.4"が**Java8,Java11にしかサポートされていない**ため、Java8(LTS)やJava11(LTS)をインストールしている場合であると正しく動作するが、その他のJavaのバージョンだと動作しないということが判明した。

### 2. [Tasking Manager](https://tasks.teachosm.org/projects/1499/tasks/?page=1)、JOSMを用いたOSMの妥当性検証、エラー・警告の修正
妥当性検証およびエラー・警告の修正完了

### 3. コミュニティへの事前告知
**アカウント名をfuruhashilab4plateauimportからYoshida_plateauimportに変更**
![image](https://github.com/furuhashilab/2023gsc_WataruYoshida/assets/93134160/310e4475-d5c1-491a-a6c2-722ed21f24db)
![image](https://github.com/furuhashilab/2023gsc_WataruYoshida/assets/93134160/1998fe38-08a8-45d2-bae9-67ce17a3bfcc)

## 4. コンバーターを使用して変換作業を行う際のツール
### 変換作業が、Powershellで実装されなかったが、**コマンドプロンプト**では実装できた

* Powershell
![image](https://github.com/furuhashilab/2023gsc_WataruYoshida/assets/93134160/6790c846-26c9-4317-806d-63ffb7862b71)

* コマンドプロンプト
<img width="957" alt="image" src="https://github.com/furuhashilab/2023gsc_WataruYoshida/assets/93134160/d6e20ab3-5b19-4b59-b49e-46145456b6f4">


## 5. 1st-validation(解凍したフォルダに含まれている `***.osm` の妥当性検証)、2nd-validation(コンバーターで`***.org.osm`に変更したファイルの妥当性検証)及びエラー・警告のリスト化

### 林優氏が中心となって行った、PLATEAUで公開されている各市町村の`City-gml`を`***.osm`, `***.org.osm`, `***.mrg.osm`に変換したデータファイルが[PLATEAU-BLDG import task](http://surveyor.mydns.jp/task-bldg/mesh/11230)に格納されている。そこで公開されている新座市の`**.org.osm`の一部が開けないものがある

![image](https://github.com/furuhashilab/2023gsc_WataruYoshida/assets/93134160/6359cb30-2ad9-484a-a28a-765f30b2016c)
* このような場合は**.org.osmファイル、**.mrg.osmファイルを削除し、$ java -Dfile.encoding=utf-8 -jar citygml-osm-jar-with-dependencies.jar 2ndを実行して新たに**.org.osmファイルを作成すると正しく読み込まれるようになる

### 妥当性検証時に発生したエラー・警告を収集したリスト(https://docs.google.com/spreadsheets/d/1g_SA-b3N3m7rKWzYLOa16hlr8yBpsMljPL22gAJN4FQ/edit?usp=sharing)

* 修正方法
**ウェイが同じ区間を二度含んでいる**
![妥当性検証_修正](https://github.com/furuhashilab/2023gsc_WataruYoshida/assets/93134160/1360e4a7-cce9-4803-89bc-a008a949cb27)

**outlineを削除し、飛び出したノードを隣のノードと結合させる**


## 6. データアップロード

### データをアップロードする際に帯域制限を超えたとの表示がでて、アップロードできない(2024/1/20)
![image](https://github.com/furuhashilab/2023gsc_WataruYoshida/assets/93134160/971717c8-bb62-4f88-87e0-f4d24d49520f)

* 2024/1/23前後にOSMのWebサーバーがダウンしていたため、このような状態になったと考えられる
![image](https://github.com/furuhashilab/2023gsc_WataruYoshida/assets/93134160/11429cb9-3c51-4331-b1b3-d7ae21774253)

**現在は復旧しているため、問題なくアップロードが可能**
https://uptime.openstreetmap.org/

## 7. PLATEAUインポートアカウントがFrederik Ramm([woodpeck](https://www.openstreetmap.org/user/woodpeck))によってブロックされた
<img width="738" alt="image" src="https://github.com/furuhashilab/2023gsc_WataruYoshida/assets/93134160/091659ab-82ec-44d3-bf2b-4c2600d349a0">

**@mapconcierge 先生によると、何の実績のないアカウントが急に大量のインポートを始めたので自動的にブロックされたとのこと**

その後[data@osmfoundation.org](mailto:data@osmfoundation.org)にメッセージも送ったが、未だに返信がない状況

<img width="467" alt="image" src="https://github.com/furuhashilab/2023gsc_WataruYoshida/assets/93134160/c81d578b-3df4-46e9-93a9-614a6edb0a6b">


**@mapconcierge 先生がFrederik Ramm([woodpeck](https://www.openstreetmap.org/user/woodpeck))氏に直接連絡してくれたが、返信がない**

![image](https://github.com/furuhashilab/2023gsc_WataruYoshida/assets/93134160/22177ba9-6a6c-46c3-a099-960f9ed7b1d5)

### 2/2　[data@osmfoundation.org](mailto:data@osmfoundation.org)から返信が返ってきた。

![image](https://github.com/furuhashilab/2023gsc_WataruYoshida/assets/93134160/bb263cac-421b-4a75-ae95-766b292d945e)

**新しいアカウントでいきなり大量のアップロードを行ったことが原因で、自動破壊行為防止スクリプトによってインポートアカウントがブロックされた**

* 解決法

<img width="446" alt="image" src="https://github.com/furuhashilab/2023gsc_WataruYoshida/assets/93134160/ed806988-29e2-4216-9fb0-b05abd3e6a58">

<img width="451" alt="image" src="https://github.com/furuhashilab/2023gsc_WataruYoshida/assets/93134160/c00a4445-2c44-40d8-82ec-7adfcc67b4b7">

**OSMのインポート用アカウントのプロフィール説明のところに「私のメインアカウントはこちら」「こういう活動（インポートのWikiページ）に関わっているよ」などを書く**

**→これにより、アカウントの信用度が上がる可能性が高くなる**


**建物データが少ない地域からインポートしていくのも一つの手かもしれない**


## 8. 新座市全地域のアップロード完了

### 新座市インポート前
![420690374_395962506272993_7053118599376449919_n-min](https://github.com/furuhashilab/2023gsc_WataruYoshida/assets/93134160/76ef2189-1743-4b9e-8aae-afb4c651c8ee)
![417337755_1144385293392514_1737859945341398467_n-min](https://github.com/furuhashilab/2023gsc_WataruYoshida/assets/93134160/c8502dbf-165e-41a4-9c26-0b9500b85e34)



## 謝辞
本研究を進めるにあたり地球社会共生学部の古橋大地教授をはじめ多くの方々より多大な助言を賜りました。厚く感謝を申し上げます

## 先行事例

https://github.com/yuuhayashi/citygml-osm/issues/96#issue-1429854543

https://wiki.openstreetmap.org/wiki/JA:MLIT_PLATEAU/imports_outline/manual

https://qiita.com/nyampire/items/1c10afdd36750c87154d 

https://wiki.openstreetmap.org/wiki/JA:JOSM/Validator

https://lists.openstreetmap.org/pipermail/talk-ja/


## 参考文献

* https://wiki.openstreetmap.org/wiki/JA:MLIT_PLATEAU/imports_outline/manual

* https://www.soumu.go.jp/hakusho-kids/use/economy/economy_11.html

* https://www.jst.go.jp/crds/pdf/2021/RR/CRDS-FY2021-RR-09.pdf

* https://www.mlit.go.jp/plateau/

* https://www.mlit.go.jp/toshi/daisei/content/001614666.pdf

## グラレコ


## 最終発表資料
* メディウム

* スライド
