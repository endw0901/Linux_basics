# 入出力


|I/O Name|略|File Descriptor|
|:------------|:-----------|:-----------:|
|Standard Input|stdin|0|
|Standard Output|stdout|1|
|Standard Error|stderr|2|


## Redirection

|コマンド|内容|
|:------------:|:-----------|
|>|stdout to file, コンテンツの上書き・truncate|
|>>|stdout to file, コンテンツのappend|
|<|stdin to file|

* & : file descriptorの使用

```
// stderr to stdout
2>&1
// stderr to file
2>file
```

## Null Device

* 画面表示やファイルへの書き込みを避けたいときに使う

```
// redirect output to nowhere
>/dev/null

ls here not-here 2> /dev/null

```

## 例

```
// ls結果をfileに書き込み
ls -l > files.txt

// file descriptorを使っても上記と同じ
ls -l 1> files.txt

// ls結果をfileにappend(末尾に挿入)
ls -l >> files.txt

// file内容を画面にsort表示
sort < filea

// sortしたfileをsortfileに書き込む ※redirectの組み合わせ
sort < filea > sortfile


// fileAのみ存在するとき、Bのみエラーとなる => outCにはfileAのみ出力され、エラーはスクリーン表示される
ls fileA fileB > outC 

// fileAのみ存在するとき、Bのみエラーとなる => outCにはエラーのみが出力される
ls fileA fileB 2> outC
```

* file descriptorを使う時は スペースを入れないこと 2>
