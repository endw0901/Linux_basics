# shellヒストリーなど

## shellヒストリー

* 実行コマンドは保存される

* ~/.bash_history
* ~/.history
* ~/.histfile

```
// display the shell history
history

// historyサイズを変更
HISTSIZE
export HISTSIZE=1000
```

## !コマンド

```
// ライン番号Nを再度実行
!N

// 1つ前のコマンドを再度実行
!!

//「string」で始まるコマンドのうち最も直近のコマンドを再度実行
!string
```

### 例

```
head files.txt sorted_files.txt notes.txt

// 1つ前の行の全てのコマンドを再実行
// => head files.txt sorted_files.txt notes.txtに等しい
!!


// 1つ前の行の第2 argumentのみ実行
// => vi sorted_files.txtに等しい
vi !:2

```

### 例② 
* !^ = !:1
* !$ = 1つ前のargument


```
head files.txt sorted_files.txt notes.txt

// files.txt(1つ前の行の最初のargument
!^

// notes.txt(1つ前のargument)
!$
```

## shell historyの検索
* Ctrl + r・・・後方検索
* Enter・・実行
* Arrows・・コマンド変更
* Ctrl + g・・・検索キャンセル


## 例

```
history

// 指定した番号のコマンド実行(historyで番号が表示される)
!557

// 保存できる最大数=>もう一回
echo $HISTSIZE
!!

// hで始まるコマンド履歴
!h

// 2つめの引数(b.txt)
ls a.txt b.txt c.txt
echo !:2

// 1つ前のlつきコマンド=ls
ls a.txt b.txt c.txt
!l

// 1つ前のargumentをecho => c.txt
echo !$

// !^ = !:1 (1つ前の行の最初のargument
echo !^

echo aa bb cc
echo !^
```

## tab補完の例

* autocompletion(自動補完)

```
echo aaa.txt bbb.txt nnn.txt

echo aaa.txt bb(tabを押すと補完してくれる
echo $Hist(tabを押すと $HISTSIZEへ補完
```
