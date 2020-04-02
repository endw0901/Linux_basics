# システムログ


## syslog standard 標準シスログ

* 個別のアプリでloggingを実装不要
* facilities機能とseverities重大性でカテゴライズ

### facilities

|番号|keyword|内容|
|:------------:|:-----------|:-----------|
|0|kern|カーネルメッセージ|
|1|user|userレベルmessage|
|2|mail|mail system|
|3|daemon|システムデーモンズ|
|4||auth|security / authorizationメッセージ
|5|syslog|syslogで生成されたmessage|
|6|lpr|line printer subsystem|
|7|news|network news subsystem|
|8|uucp|UUCP subsystem|
|9|clock|daemon|
|10|authpriv|security / authorization messages|
|11|ftp|FTP daemon|
|12|-|NTP subsystem|
|13|-|log audit|
|14|-|log alert|
|15|cron|clock daemon|
|16|local10|local use 0|
|17|local11|local use 0|
|18|local12|local use 0|
|23|local17|local use 7|


### severities 

* 0:emergency
* 1:Alert
* 2:critical
* 3:Error
* 4:Warning
* 5:Notice
* 6:Info
* 7:Debug


## Syslog servers

* ruleにもとづきsyslogを処理する
* syslogd (syslog-daemon) がruleを補完するのが伝統的
* rsyslog, syslog-ngがsyslogdを代替（最近のLinux Distribution)

### rsyslog

* /etc/rsyslog.conf:

```
// コンフィグ追加するとき
IncludeConfig /etc/rsyslog.d/*.conf
// 

```

## Logging  Rules

* Selector field・・・・facilitiesなど
* Action field・・・メッセージの処理方法を決める（例：ログファイルに書き出す）


```
// Selector fieldの例：/var/log/mail.logなどにfacilitiesがマッチする
mail.*

// 例：cronとauthpriv以外のメッセージをlog/messagesに書き出す
*.info;mail.none;authpriv.non;cron.none /var/log/messages
```

## キャッシュモード

* Cashing modeではクラッシュ時にログを一部失う可能性あり
* キャッシュを使うことでI/O処理パフォーマンス改善


```
// PATHがハイフンで始まるものがキャッシュモード
mail.info -/var/log/mail.info


// 使い分ける：エラーのみ重要なためNon-Cashing modeとし、他はパフォーマンス重視でCash mode
mail.info -/var/log/mail.info
mail.warn -/var/log/mail.warn
mail.err /var/log/mail.err
```

## logger

* syslog messagesを生成するコマンド
* 自分でsyslogを出したいときに使う

### logger option
* -p ：FACILITY.SEVERITY
* -t ：TAG

```
logger -p mail.info -t mailtest "Test."
sudo tail -l /var/log/mail.log
```

## logrotate

* logがdisk spaceを使いすぎないよう他に移すとかなどに使う


```
/etc/logrotate.conf:
include /etc/logrotate.d
```

### logrotate.confの例

* logrotate -fv /etc/logrotate.conf　・・・・　configをテストしたいとき(-f:full ??, -v:verbose)

```
// 週次でrotate
weekly

// 4week保存
rotate 4

// rotate後に新しい空ファイルを作る
create
```

```
// Ubuntuの設定例(rsyslogの処理) ・・・/etc/logrotate.d/rsyslogのファイル
/var/log/debug
/var/log/messages
{
    rotate 4
    weekly
    missingok
    notifempty
    compress
    sharedscripts
    postrotate
      reload rsyslog >/dev/null 2>&1 || true
    endscript
}
```
* rotate 4 ・・・ログ削除前に4回rotate (?一応調べる)
* missingok・・・missingログをignore
* not if empty・・・emptyならrotateしない
* compress・・・rotateしたlog fileを圧縮

* postrotate ～ endscriptの間は、rotationの後に実行される

https://qiita.com/ritukiii/items/b3d91e97b71ecd41d4ea
* /dev/nullというのはunixのスペシャルファイルの事で、空ファイルのこと（出力結果を捨てている）
* >&{ファイルディスクリプタ}・・・・{ファイルディスクリプタ}に結果をマージするという意味
* 2>&1・・・・標準エラー出力を標準出力にマージする

```
// 標準出力を標準エラー出力にマージする場合

1>&2

// 逆に標準エラー出力を標準出力にマージする場合
2>&1
```
このように使
