# システムログ


## syslog standard 標準シスログ

* 個別のアプリでloggingを実装不要
* facilities機能とseverities重大性でカテゴライズ

### facilities

|番号|keyword|内容|
|:------------:|:-----------||:-----------|
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
