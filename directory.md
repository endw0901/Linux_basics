# Working with Directory

* ショートカット
* PATH外の操作

## directory shortcuts


|コマンド|内容|
|:------------:|:-----------|
|.|this directory(今の)|
|..|the parent directory(親）|
|cd -|chage to the previous directory（1つ前に戻る）|


|コマンド|内容|
|:------------:|:-----------|
|echo $OLDPWD | 1つ前にいたdirectoryを保持する環境変数を表示|
|cd - | １つ前に戻る（$OLDPWDのdirectoryと同じところ)|


## PATH外のコマンド
* フルパスを入れればPATH外コマンドも使える

```Linux Kernel Module
which cat
 //catコマンドのフルパスが表示される
/usr/bin/cat 
```

## directory操作

|コマンド|内容|
|:------------:|:-----------|
|mkdir directory|作成|
|rmdir directory|削除(空directoryのみ)|
|rm -rf directory|recursively 配下の内容も全部削除|

```Linux Kernel Module
mkdir -p directory1/directory2/directory3
rmdir -p directory1/directory2/directory3
3階層のdirectoryを1コマンドで作成・削除可能(1の下に2、その下にdirectory3)
```
