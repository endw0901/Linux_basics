# Shell Scripting

* Scripts = interpreterが実行する複数のコマンドラインのまとまり

## 例

```
// ファイル作成
// shebang = #!
#! /bin/bash
echo "Scripting is fun!"

// 権限変更　rwx（7）r-x（5）r-x（5）＝ 755
chmod 755 script.sh

// 実行
./script.sh

```

### Shebang

* shebang = #!
* shebang 以下はそのスクリプトとして解釈される
* shebang無しの場合は自分の設定shellとして解釈される

```
#! /bin/bash
echo "Scripting is fun!"

#! /bin/csh
echo "Scripting is fun!"

#! /bin/ksh
echo "Scripting is fun!"

#! /bin/zsh
echo "Scripting is fun!"
```

### Shebang:スクリプト以外(python)


```
// ファイル作成
// shebang = #!
#! /bin/python
echo "Scripting is fun!"

// 権限変更　rwx（7）r-x（5）r-x（5）＝ 755
chmod 755 hi.py

// 実行
./hi.py

```

## 変数を使う variables

* 数字で始まる変数や、- @等特殊文字を含む変数は無効
* 大文字小文字数字混在、_はok。
* アルファベットで始まる

```

#! /bin/bash
MY_SHELL="bash"
echo "I am ${MY_SEHLL}ing on my keyboard."

```

## test

* -d FILE ・・・fileがdirectoryかテスト

### -x FILE testその他

* -e existするかどうか
* -f 通常のfileとして存在するかどうか
* -r readableかどうか
* -s existsするかどうか＋empyでないかどうか
* -w 書き込み可能かどうか
* -x 実行可能かどうか（このtestを実行したあなたにとって)


### -x String test

* -z String stringがemptyならtrue
* -n String stringがemptyでないならtrue

* String1 = String2 同じならtrue
* String1 != String2 違うならtrue


## 演算子

* arg1 -eq arg2
* arg1 -ne arg2

* arg1 -lt arg2   ・・・arg1 is less than arg2 then true   /  arg1 < arg2 ならture
* arg1 -le arg2   ・・・less than or equal to

* arg1 -gt arg2   ・・・greater than
* arg1 -ge arg2   ・・・greater than or equal to


## if文


```
touch script.sh
vi script.sh

// 編集
#! /bin/bash
MY_SHELL="bash"

if [ "$MY_SHELL" = "bash" ]
then
  echo "you like the bash shell"
fi


// 権限変更　rwx（7）r-x（5）r-x（5）＝ 755
chmod 755 script.sh

// 実行
./script.sh

```










