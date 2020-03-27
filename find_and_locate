# find files / directories

* find [path...] [expression]

|コマンド|内容|
|:------------:|:-----------|
|find [path...] [expression]|recursively finds files in path。引数無しはcurrent directoryとその配下|

## find options

* -name pattern
* -iname pattern (大文字小文字は無視する)
* ls (見つけたるごとlsする)

* -mtime days (modification time and days)
* -size num (サイズで探す)
* -newer file (fileより新しく作成されたfileを探す)
* -exec (見つけたfileに指定コマンドのexecute)


```Linux Kernel Module
// 10日-13日以内の修正(modification time)
find . -mtime +10 -mtime -13

// sで始まるfileを探してls
find . -name s* -ls

// 1MB以上 (1K, 1M, 1G)
find . -size +1M

// xx.txtより新しいdirectory
find . -type d -newer file.txt

```


## locate (a fast find)
* queries an index
* indexができるまでのタイムラグの分、検索結果はリアルタイムではなくラグがある
