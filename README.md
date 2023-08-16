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


## Results


## 謝辞
本研究を進めるにあたり地球社会共生学部の古橋大地教授をはじめ多くの方々より多大な助言を賜りました。厚く感謝を申し上げます

## 先行事例

https://github.com/yuuhayashi/citygml-osm/issues/96#issue-1429854543

https://qiita.com/nyampire/items/1c10afdd36750c87154d 

https://wiki.openstreetmap.org/wiki/JA:JOSM/Validator


## 参考文献



## グラレコ


## 最終発表資料
* メディウム

* スライド
