# Working with Directory

* ショートカットコマンド
* PATH外の操作

## directory shortcuts
* .：this directory(今の)
* ..：the parent directory(親）
* cd：chage to the previous directory（1つ前に戻る）

|コマンド|内容|
|:------------:|:-----------|
|.|this directory(今の)|
|..|the parent directory(親）|
|cd -|chage to the previous directory（1つ前に戻る）|

|コマンド|内容|
|echo $OLDPWD|1つ前にいたdirectoryを保持する環境変数を表示|
|cd -|１つ前に戻る（$OLDPWDのdirectoryと同じところ)|


## PATH外のコマンド
* フルパスを入れればPATH外コマンドも使える

```Linux Kernel Module
which cat
 //catコマンドのフルパスが表示される
/usr/bin/cat 
```
