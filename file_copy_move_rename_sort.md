# file削除、コピー、移動、リネーム、sort


## file削除
```
// file削除
rm file

// directory＆内容を削除
rm -r dir

// 強制削除（確認無し）
rm -f file

```

### lsで確認してから削除する

```
ls s*
rm s*


## コピー

```
// コピー from A to B
cp fileA fileB

// 複数ファイルをdirectoryへ
cp filaA fileB fileC directoryA

// directoryコピー・・・AをBの直下にコピー(Aの内容ではなく、AフォルダごとBにコピー)
// Bが存在しない時は新規作成mkdir Bを自動で行う
cp -r directoryA directoryB

// 複数directoryコピー A,BをCへ => treeでdirectory構造の結果を検証できる
cp -r A B C


// interactive mode => AをBにコピーするか対話形式で進む
cp fileA fileB
```

## 移動

|コマンド|内容|
|:------------:|:-----------|
|mv from to|from からtoへ移動。存在するfileからfileへmvの場合、上書きする|
|mv -i from to|対話形式(上書きしますか？など聞かれる|

## sort

```
// ファイル内容をSORT表示
sort fileA

// keyソート (F:field)
-k F

// 降順sort
-r

// ユニークsort(重複行を1行にする)
-u
```

### 例
```
// 降順＆ユニークsort
sort -ru fileA

// 2列目をkeyにsort
sort -u -k2 fileA

```

