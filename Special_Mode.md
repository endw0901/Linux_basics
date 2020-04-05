# Special Mode

* Setuid = 実行時のSet User ID
* Setguid

## 設定

```
// fileにUID設定
chmod u+s /path/to/file
chmod 4755 /path/to/file

// fileにGID設定
chmod g+s /path/to/file
chmod 2755 /path/to/file

// 両方設定
chmod ug+s /path/to/file
chmod 6755 /path/to/file

// 設定解除
chmod g-s /path/to/file
```


## 設定ファイル検索

```
// UIDが設定されたファイル検索
find / -perm /4000 -ls

// GIDが設定されたファイル検索
find / -perm /2000 -ls

```

## directoryにSetgid

* directoryに設定すると、その配下の新規fileやdirectoryに継承される
* 既存file, directoryには継承されない

|コマンド|内容|
|:------------:|:-----------|
|||
|||
