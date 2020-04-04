# ユーザー管理

* /etc/passwd ファイルに情報は全て保存されている

## format (/etc/passwdの情報
* username:password:UID:GID:comments:home_dir:shell


* GID = group id
* password = x・・・暗号化

### formatの例
```
// root
* root:x:0:0:root:/root:/bin/bash

// 例 Joe Hendersonがコメント
joe:x:1000:1000:Joe Henderson:/home/joe:/bin/bash

```

## ユーザー名

* 8文字以下
* 一般に、小文字で、特殊文字を使用しない。数字はok

```
joehend+と表示される
ps -fu joehenderson
```

### パスワード

* /etc/passwdは誰でも読めてしまうため、/etc/shadowに現在は保存されている。
* /etc/shadowはrootのみ読める


## UID

* rootのUID = 0 (必ず0)
* ユニーク
* 1000個まで
* /etc/login.defs 

## GID

* newgrp

## commentフィールド

* 一般に、フルのユーザー名を保持
* アカウントの用途・目的を持つ場合もある
* GECOS

## Shell

* /etc/shells に使えるshell情報
* shell以外(false, nologin)を持たせてほかの用途に使う場合も

## /etc/shadow

```
// username, password, 変更なし日数、パスワード変更可能日までの日数、など・・
root:$6xaaaUICJKCD:16502:0:999999:7:::: 
```

## user追加

* useradd [] username
* option -c コメント、-m home directory作成、-sh /shell/path ユーザーのshellパス

* -g グループ追加 -G GROUP1 GROUP2 複数グループ追加

```
useradd -c "Grant Stwewart" -m -s /bin/bash grant

USERADD -C "Eddie Harris" -m -s /bin/bash -g sales -G projectx

```


## パスワード作成

```
passwd grant

// 情報
tail -l /etc/passwd
tail -l /etc/shadow
```

## Systemアカウント、Applicationアカウント

* -r systemアカウントとしてユーザー作成

```
useradd -c "Apache Web Server User" -d /opt/apache -r -s /usr/bin/nologin apache
tail -l /etc/passwd
```

## /etc/skel

* skelの内容がdefaultでhome directoryにコピーされる
* 一般に、shell config情報を持つ(.profile, .bashrc)


## useraddオプションその他
* -r ・・・systemアカウントを作成
* -d /home/dir ・・・home directoryを特別に指定

## UIDを指定

* 管理がしやすくなる

```
// -u 97 でUID 97を指定。MySQLは97で管理したい、とか
useradd -c "MySQL Server" -d /opt/mysql -u 97 -s /usr/sbin/nologin
```

## 削除

* userdel [-r] username
* -r home directoryも消す。ユーザーは消すがdirectoryの情報を残しておきたいときはつけない


## 変更

* usermod

```
grep mysql /etc/passwd

// コメント追加 => 再度確認
usermod -c "MySQL User" mysql
grep mysql /etc/passwd

```


## グループ情報

* /etc/groupに保持
* フォーマット・・・group_name:password:GID:account1, accountN
* passwordのx => /etc/shadowに保持
```
sales:x:1001:john, mary
root:x:0:
```

### groupadd,del,mod

* GID固定指定も可能

* 追加：groupadd
* 削除：groupdel
* 変更：groupmod

```

grep web /etc/group

// GID変更
groupmod -g 1234 web
grep web /etc/group

// グループ名変更(web => http
groupmod -n http web
```

## 例














