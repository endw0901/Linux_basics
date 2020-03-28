# file圧縮、アーカイブ作成


## tar アーカイブ
* tar c|x|t f tarfile
*create, extract, list contents

```
// ハイフンは省略可能
tar cf file.tar
tar -cf file.tar
```

### 例

```
// directoryAをcreate tar file
tar cf xxx.tar directoryA

// 結果確認(tar内容をリスト表示)
tar tf xxx.tar

// pwdでパス確認して、パス指定
tar tf /home/xxuser/Documents/a5/a77.tar

```


## 圧縮gzip

|コマンド|内容|
|:------------:|:-----------|
|gzip|圧縮|
|gunzip|解凍|
|gzcat|圧縮ファイルの内容view|
|zcat|圧縮ファイルの内容view|
