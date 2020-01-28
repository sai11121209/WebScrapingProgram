# 東京ディズニーリゾート待ち時間測定アプリ
![](https://img.shields.io/badge/Pyhton-3.7.8-4169e1.svg)
![](https://img.shields.io/badge/Pyhtonista3-3.6-00fa9a.svg)
![](https://img.shields.io/badge/MySQL-5.7.27-4169e1.svg)  

## 標準ライブラリを含む使用ライブラリ
mysql.connector  
os  
time  
sshtunnel
requests
pandas  
## サードパーティライブラリのインストール
```
$ pip install mysql.connector
$ pip install sshtunnel
$ pip install requests
$ pip install pandas
```
## 内容
東京ディズニーリゾートでのアトラクション混雑を少しでも減らせるように一日の待ち時間の流れ瞬時に可視化し,現在そのアトラクションが空いているのか,混雑しているのか判断することのできるアプリを到達点に作成中です.
### 実装済み機能
1. 一日の平均待ち時間の算出
1. 現在の待ち時間の表示  
> 機能2については待ち時間データが大量に蓄積されている状態になるとデータが正常に取得できない問題があり修正中

### 実装予定機能
1. 一日の待ち時間の流れをグラフ化し表示
1. その他ピーク値検出を用いた自動混雑判定
## 動作概要
### 自宅PCでの処理の流れ  
1. タスクスケジューラーを使用し開園時刻5分前にプログラムを起動.
1. 自宅PC上でディズニー待ち時間APIのデータを取得.
1. 取得した待ち時間データをMySQLサーバに送信.
1. 閉園時刻と同時に1日の待ち時間データをMySQLサーバより取得.
1. 取得データをcsvファイルに書き出す.
1. MySQLサーバ待ち時間テーブルのデータを全消去とともにオートインクリメントをリセット.  
***これらの処理のうち2,3の処理を開園時刻から閉園時刻まで指定間隔(ex:5分)で実行しMySQLサーバにデータを蓄積させる.***  
### iPhone(Pyhtonista3)での処理の流れ  
1. 待ち時間の情報を確認したい時にアプリを起動.
1. プログラム実行と同時にMySQLサーバから1日の平均待ち時間、現在に待ち時間を取得.
1. 取得したデータをテーブル形式で画面に表示.  
## Pythonista3実行画面
### 開園時実行画面
#### 起動直後
!<img src="開園時実行画面.jpg" alt="attach:cat" title="attach:cat" width="200" height="433">  
#### アトラクション選択時
### 閉園時実行画面
!<img src="閉園時実行画面.jpg" alt="attach:cat" title="attach:cat" width="200" height="433">  
