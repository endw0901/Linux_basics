# cron

* スケジュール処理を実行できるサービス
* crontabコマンドでcronjobを操作できる

## Crontab format

* 1 2 3 4 5 command

* 1 Minute(0-59)
* 2 Hour(0-23)
* 3 Day of the Month(1-31)
* 4 Month of the Year(1-12)
* 5 Day of the Week(0-6) 0：日曜日

### 例

```
// 毎週月曜日朝7時に実行する(年月は*のためすべてにマッチ）
0 7 * * 1 /opt/sales/bin/weekly-report

// 毎日2:00起動し、log fileに出力
0 2 * * * /root/backupdb > /tmp/db.log 2>&1
```

### 複数指定できる

```
// 複数指定する例：30分毎(0,30)
0,30 * * * * /opt/bin/report
```

### 演算で指定できる

```
// 30分毎(60/2)
*/2 * * * * /opt/bin/report 
```

### 範囲指定

```
// hann0-5分の間、毎分実行
0-4 * * * * /opt/bin/report
```

## ショートカットコマンド

|コマンド|内容|
|:------------|:-----------|
|@yearly|0 0 1 1 *|
|@annualy|0 0 1 1 *|
|@monthly|0 0 1 * *|
|@weekly|0 0 * * 0|
|@daily|0 0 * * *|
|@midnight|0 0 * * *|
|@hourly|0 * * * *|


## Crontabコマンド

|コマンド|内容|
|:------------|:-----------|
|crontab file|新しいcrontabをfileからインストール|
|crontab -l|cron jobをリスト表示|
|crontab -e|cron jobsを編集edit|
|crontab -r|removeすべてのcron jobsを削除|


## cron job作成例

```
// cronファイル作成
vi my-cron

0 7 * * 1 /opt/report

// crontabで登録、登録後確認
crontab my-cron
crontab -l

// 環境変数に指定したviエディタでcrontab編集=>コメントアウトでcronjob削除
EDITOR=vi
crontab -e

#0 7 * * 1 /opt/report

// cronjob削除
crontab -r
crontab -l

```




