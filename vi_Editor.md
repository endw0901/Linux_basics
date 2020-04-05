# Vi Editor

|コマンド|内容|
|:------------:|:-----------|
|vi file|edit file|
|vim file|viより多機能|
|view|read-onlyのvim|

* ファイルを間違って変更したくない時はviewを使う

## 操作
* h,j,k,l
* b, w
* ^, $


## 3つのmode
* command
* insert
* line

### mode
* i insert after the cursor
* I insert from the beggining of the line
* a append after the cursor
* A append at the end of the line


### VLine mode
* :w writes/save the file => enterで改行
* :w! force the file to be saved
* :q quit
* :q! quit without saving
* :wq! write and quit
* :x wqと同じ

#### VLine mode (操作)
* :n  n行目に移動
* :$ 最後の行へ移動
* :set nu  行数時表示
* :set nonu 行数時非表示
* :help


## 繰り返し

```Linux Kernel Module
// 5行上に移動
5k

// 80回テキスト挿入
80i text esc

// 80回 _ を挿入
80i esc 
```


## 削除

```Linux Kernel Module
// delete a charactor
x

// delete a word
dw

// delete a line
dd

// delete from the current position
D
```

## 置換

```Linux Kernel Module
// replace 文字列
r

// change the current word
cw

// change the current line
cc

// change the current text from the current position
c$
C

// 大文字小文字入れ替え
~
```

## コピーペースト

```Linux Kernel Module
// yank(copy) the current line
yy

// yank the <position>
y<position>

// paste the most recent deleted or yanked text
p

// change the current text from the current position
c$
C

// 大文字小文字入れ替え
~
```



## undo 

```Linux Kernel Module
// undo
u

// Redo
Ctr-R
```

## Serch
```
// forward serch -> nで次のwordへジャンプ,Nで前へ
/<pattern>

// reverse search
?<pattern>
```

## help
* vimtutor
