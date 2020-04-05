# 空白の除去、コメント除去

## fileからコメント行と空白行を除いた、通常の行のみ表示する

* #で始まる行、空白の行を検索し、マッチしないものを表示する(-vがあるので)

```
// -E extended enabled regular expression grepの引数のpatternが、拡張正規表現になる
// -v invert matches = マッチしない行を表示する
// ^：最初
// ^#：コメントライン (#で始まる）
// ^$：空白（終わりで始まる）
grep -Ev '^#|^$' file.txt
```
