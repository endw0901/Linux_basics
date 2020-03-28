# 比較 diff 


|コマンド|内容|
|:------------:|:-----------|
|diff|比較|
|sdiff|横に並べる|
|vimdiff|vimでハイライト　※見やすい|

### vimdiff
* Ctrl +w で隣のウィンドウへ移る
* :qを2回で2つのウィンドウを閉じて元に戻れる

## 例

```
// 行番号表示
cat -n file

// 差を作るために、ファイル末尾に行を追加
echo new last line  >> fileB
diff fileA fileB
//

## diffの結果の表示
* 4c4：fileAの4行目がfileBの4行目と異なる ※ｃ＝change
* < fileAを指す
* > fileBを指す


```
