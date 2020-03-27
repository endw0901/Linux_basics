# ls

|コマンド|内容|
|:------------:|:-----------|
|ls -l|permission, link, filesizeなど|
|ls -a|隠しファイルも表示|
|ls -al, ls -la|上2つを同時実行|


|コマンド|内容|
|:------------:|:-----------|
|ls -F|ファイルタイプを表示|

* /：directory
* @：link
* *：実行可能


## sort

|コマンド|内容|
|:------------:|:-----------|
|ls -t|時間|
|ls -r|逆順|
|ls -latr|時間の降順で、隠しファイル含めすべてのロングリストを表示|

## ツリー表示

|コマンド|内容|
|:------------:|:-----------|
|ls -R|list recursively|
|ls --color|色つき|
|ls -d|list only directory|


* treeはよりビジュアライズ

|コマンド|内容|
|tree -d|list only directory|
|tree -C|色つき|
