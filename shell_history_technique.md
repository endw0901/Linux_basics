# テクニック


## 複数ファイル・フォルダをまとめて処理するときに便利

```
// ３ファイル作成
touch file1 file2 file3

// 前作成した複数ファイルをまとめて表示、編集、表示、移動
ls !*
vi !*
cat !*
mv !* /tmp/

// 3フォルダ作成
cd tmp
mkdir one two three

// 前作った3フォルダまとめて権限設定、
chmod 700 !*
ls -l


```

## タイプミスをやり直すとき、修正点以外を打ち直さなくていい

```
grpe -i err /var/log/syslog

// grpe=> grepに修正。それ以外は前のコマンドラインの繰り返し
grep !*

// grep以下を、root権限で繰り返し
sudo !!





```
