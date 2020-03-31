# 環境変数

|コマンド|内容|
|:------------:|:-----------|
|printenv|環境変数をすべて表示|
|printenv xxx|xxxに関する環境変数をリスト表示|
|echo $xxx|xxxに関する環境変数をリスト表示|

* 慣習として、大文字(HOMEなど

```
// HOME directoryの環境変数を表示
printenv HOME
echo $HOME

// pagingへpipe
printenv | less

```

## 環境変数の作成

|コマンド|内容|
|:------------:|:-----------|
|export VAR="value"|環境変数(VAR)を作成(valueに設定値)|

* 既存の変数の場合は上書きとなる

```
// HOME directoryの環境変数を表示
export EDITOR="vi"
export TZ="US/Pasific"
```

## 環境変数の削除

|コマンド|内容|
|:------------:|:-----------|
|unset VAR|環境変数(VAR)を削除|


```
// TZ削除
unset TZ
```


## ログイン時にpersistさせる

```
// HOME directoryの環境変数を表示=> .bash_profileに環境変数の作成を追記
cat ~/.bash_profile
export TZ="US/Central"

// 現在時刻 => UTC表示
date

// タイムゾーン環境変数を変更 => dateでPDT表示
export TZ="US/Pacific"
date

// 環境変数を削除してリセット => dateでUTC表示
unset TZ
date

```
