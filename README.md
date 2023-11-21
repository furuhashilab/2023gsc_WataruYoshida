# 2023gsc_WataruYoshida

吉田航の2023年度ゼミ論用レポジトリ
# 【2023年度ゼミ論】PLATEAU LOD1 建物データをOSMにインポートする際の事前準備【OSMのみの妥当性検証におけるエラー・警告の事例収集】
地球社会共生学部　地球社会共生学科　4年A組188番

学籍番号：1A120189　氏名：吉田航

指導教員：古橋　大地教授

©Furuhashi Laboratory/Wataru Yoshida, CC BY 4.0

## Abstract

本研究では、国土交通省主導の日本全国の3D都市モデルの整備・活用・オープンデータ化を目指すプロジェクト[PLATEAU](https://www.mlit.go.jp/plateau/)のLOD1の建物データを誰でも編集可能な地図[OpenStreetMap](https://www.openstreetmap.org/#map=15/35.7449/139.4576) (以下OSM)にインポートする作業の効率化を目的とし、事前準備のマニュアル作成に向けた作業及び建物のインポート作業を行う。

## インポートする際の手順
1. インポートする際のOS・Java実行環境の調査

2. [Tasking Manager](https://tasks.teachosm.org/projects/1499/tasks/?page=1)、JOSMを用いたOSMの妥当性検証、エラー・警告の修正

3. OSMの妥当性検証で表示されたエラー・警告の事例収集([Googole Spredsheet](https://docs.google.com/spreadsheets/d/1g_SA-b3N3m7rKWzYLOa16hlr8yBpsMljPL22gAJN4FQ/edit?usp=sharing)にまとめる)

4. まとめたエラー・警告をOpenStreetMapの方、古橋教授などの上級者マッパーに見てもらい、各項目の対処法を定める

5. 定めた対処法をもとにマニュアル作成

* 妥当性検証を実施する地域は[JA:MLIT PLATEAU/imports list](https://wiki.openstreetmap.org/wiki/JA:MLIT_PLATEAU/imports_list)を参考とし、**埼玉県新座市**とした。

## Introduction
2022年10月に行われた[UN/EC Open Source Software for SDG (OSS4SDG) Hakcathon](https://github.com/furuhashilab/README/issues/33#issuecomment-1281762516)にて青山学院大学　地球社会共生学部の古橋　大地教授及びYouthMappersAGUが中心となって取り組んだ、[PLATEAU](https://www.mlit.go.jp/plateau/)で公開されている東村山市のLOD1建物データを[OSM](https://www.openstreetmap.org/#map=15/35.7449/139.4576) にインポートする、という作業の内の一つである【妥当性検証】で、**表示されたエラー・警告がOSMによる問題なのか、PLATEAUによる問題なのかが判別できない**という問題が発生した。我々はこの問題の対処法として**インポート作業の事前準備としてOSMのみの妥当性検証を実施し、修正作業を行う**という考えに至った。この一連の作業をマニュアル化・実施することによりインポートする際の妥当性検証で表示されたエラー・警告はPLATEAUのデータによるものであると判別がつき、インポート作業の効率化が見込める。本研究では、マニュアル作成に向けた【OSM妥当性検証時のエラー・警告の事例収集】を[Tasking Manager](https://tasks.teachosm.org/projects/1499/tasks/?page=1)とJOSMを用いて行った。
事前準備マニュアル作成後は、埼玉県新座市のLOD1建物データインポートを行う。

## Methods
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

### 5.定めた対処法をもとにマニュアル作成

### 6.https://github.com/furuhashilab/2022gsc_WataruYoshida/issues/1#issuecomment-1321897743　を参考に、JOSMを用いて埼玉県新座市にLO1建物データのインポートを行う

## Results


## 謝辞
本研究を進めるにあたり地球社会共生学部の古橋大地教授をはじめ多くの方々より多大な助言を賜りました。厚く感謝を申し上げます

## 先行事例

https://github.com/yuuhayashi/citygml-osm/issues/96#issue-1429854543

https://wiki.openstreetmap.org/wiki/JA:MLIT_PLATEAU/imports_outline/manual

https://qiita.com/nyampire/items/1c10afdd36750c87154d 

https://wiki.openstreetmap.org/wiki/JA:JOSM/Validator

https://lists.openstreetmap.org/pipermail/talk-ja/


## 参考文献



## グラレコ


## 最終発表資料
* メディウム

* スライド
