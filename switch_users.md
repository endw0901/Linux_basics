# ユーザーの切り替え、他のユーザーとしてコマンド実行

* su・・・スイッチユーザー
* sudo・・・ほかのユーザーとしてコマンド実行
* sudo -s / sudo su・・・sudoに切り替え
* visudo・・・sudoファイルをvi編集

|コマンド|内容|
|:------------|:-----------|
|su [username]|userIDを変更する。NO OPTIONはsuper userになる(=su root)|
|-|そのユーザーだったらの表示をする|
|whoami-|今のユーザー名を表示(switch後のuser)|


```
// 環境変数TEST
export TEST=1

// user1になりきる=>環境変数は表示される
su user1
echo $TEST
whoami
exit

// user1の環境で実行する=>環境変数は表示されない(user1の環境では存在しないため)
su - user1
echo $TEST

// su - user1の後なので、user1のhome directoryが表示される
pwd


// ハイフン無しのときは表示されないが、ハイフンありのときは user1環境のuser1ホームdirectoryが表示される
su -c 'echo $USER1_HOME' user1
su -c 'echo $USER1_HOME' - user1
```

## sudoコマンド

|コマンド|内容|
|:------------|:-----------|
|su [username]|userIDを変更する。NO OPTIONはsuper userになる(=su root)|
|sudo|典型例：superuserとしてコマンド実行|

* sudoコマンドは、管理者権限でしか止められないjobを止めるときなどに使う
* sudoコマンドでは、パスワードを知ることなくそのユーザーの実行確認が可能
* 一般に、システム管理者やrootユーザーが設定する

|コマンド|内容|
|:------------|:-----------|
|sudo -l|コマンドリスト表示|
|sudo command|rootとしてコマンド実行|
|sudo -u root command|同上|
|sudo -u user command|userとしてコマンド実行|


### sudoコマンド

|コマンド|内容|
|:------------|:-----------|
|sudo su|superuserにスイッチ|
|sudo su -|root環境としてsuperuserにスイッチ|
|sudo su - username|user環境としてsuperuserにスイッチ|
|sudo -s|rootとしてshellを起動|
|sudo -u root -s|同上|
|sudo -u user -s|userとしてshellを起動|

## sudoコンフィグ変更

* visudo・・・edit /etc/sudoersファイル

