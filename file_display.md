# file_display


|コマンド|内容|
|:------------:|:-----------|
|cat|すべてdisplay|
|more|fileをブラウズできる|
|less|moreより機能が多い|
|head|最初の10行|
|tail|終わり10行|

* more/less => spaceでページ送り、enterで行送り、qで終了 (vi editorベース)



```Linux Kernel Module
// default 10行 -> 引数で行数を変更可能
tail -15 file.txt
```

## ログなど、リアルタイムに更新されるファイルの確認
* 静的ファイルはcat

* リアルタイムに更新されるファイルはcatは向いていない


```Linux Kernel Module
// follow the file
tail -f file
```

## fileタイプを表示

* fileコマンド

```Linux Kernel Module
file fileA
```
