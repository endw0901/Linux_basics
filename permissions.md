# Permissions

* Symbolic permissions
* Numeric / octal permissions
* File vs directory permissions
* Changing permissions
* Working with groups
* File creation mask


## ls -l

* Symbolではじまる

|Symbol|type|
|:------------:|:-----------|
|-|通常ファイル|
|d|directory|
|l|Symbolic link|


 
|Symbol|type|
|:------------:|:-----------|
|r|Read|
|w|Write|
|x|Execute|


## Groups

|Symbol|type|
|:------------:|:-----------|
|u|user|
|g|group|
|o|other|
|a|all|


|コマンド|内容|
|:------------:|:-----------|
|groups|グループ表示|
|id -Gn|グループ表示|
|o|other|

* グループごとのパミッション：-(type)rwx(user)rwx(group)rwx(other=other all users) 


|item|meaning|
|:------------:|:-----------|
|chmod(ちゅもっど）|change mode|
|ugoa|user category(user,group,other,all)|
|+-=|add,subtract,set permissions


```Linux Kernel Module
// otherにwrite権限付与
chmod o+w aa.txt

// otherにwrite権限削除
chmod o-w aa.txt

// groupにwrite＆execute権限削除
chmod g+rx aa.txt

// 複数カテゴリにはカンマ区切り
chmod u+rwx,g-x aa.txt

// 全カテゴリ(user,group,other)にセット
chmod a=r aa.txt  // read-onlyのみとなる

// 無指定は全権限削除(o=でotherの権限すべて削除)
chmod u+rwx,g-x,o= aa.txt

```


r,w,x
0,0,0:off
1,1,1:2進数on
4,2,1:10進数 on


## octal mode (0-7)
* Octal mode 7 = 111(4+2+1)  = read and write and execute
* Octal mode 4 = 100(4+0+0)  = read only

* chmod 754 filename = 111(rwx) 101(r-x) 100(r--)

### よく使われる
* 700 userのみrwx、ほかは参照不可
* 755 全員rx、userのみw
* 664 user,groupがrw、ほかは修正不可
* 660 user,groupがrw、ほかは参照も不可
* 644 全員read、userのみwできる

*777、666は基本避ける。他の方法があるのでは？=> groupをつくって権限アサインなど

## group
* new fileはprimary groupにdefaultで属する
* chgrp:change the group

## 権限のコントロール
* 上位のdirectoryの権限に依存する。おかしいときは上位を見直す

### file creation mask
* nomaskだと => 777 for directories
* nomaskだと=>666 fpr files

* umask [-S] [mode] ：-Sはsymbolic notationを受け入れる
* Base Permission 777 => Subtract Umask -022 => Creations Permission 755

* 777 666 => 007 => 770 660(-1はないので)
