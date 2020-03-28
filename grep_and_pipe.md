# grep

* grep pattern file

|コマンド|内容|
|:------------:|:-----------|
|grep -i|大文字小文字無視|
|grep -c|ヒット件数を表示|
|grep -n|行ラインを表示|
|grep -v|マッチしないものを探す(invert match)|


## Pipe

* cat file | grep pattern  => fileの内容をgrepする

## binaryファイルをgrepする

* strings
* cut 

```
// 例：mp3ファイルから文字列johnを探す
strings aaa.mp3 | grep -i john

// 結果のJohn Coletraneをcutする(空白を区切り文字として、2field目を切り取る => Coletrane
strings aaa.mp3 | grep -i john | head -l | cut -d ' ' -f2

```

## 例

```
// bobを含むファイルを探す
grep bob /etc/passwd

// bobを含むファイルを探し、コロン区切りのフィールド1と5を切り取る
grep bob /etc/passwd | cut -d: -f1,5

// bobを含むファイルを探し、コロン区切りのフィールド1と5を切り取り、ソートし、さらにコロンを空白に置き換える(translate)
grep bob /etc/passwd | cut -d: -f1,5 | sort | tr ":" " " 

// 上記に加えて、表テーブル形式で表示する ※列の位置が揃う
grep bob /etc/passwd | cut -d: -f1,5 | sort | tr ":" " " | column -t

```

## 結果が大きいときはpagerへ送る

* lessへredirect

```
// grepの結果を表示する場合は直接lessが使えない。pipeでlessへredirectする
grep bin /etc/passwd | less
```
