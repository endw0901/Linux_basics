# シェルプロンプトをカスタマイズ　

## format

### その他

|コマンド|内容|
|:------------:|:-----------|
|\d|Tue May26 format|
|\h|host name 最初のピリオドまで|
|\H|host name|
|\n|改行|

### 時間

|コマンド|内容|
|:------------:|:-----------|
|\t|HH:MM:SS 現在時刻24h|
|\T|HH:MM:SS 現在時刻12h|
|\@|現在時刻 am/pm|
|\A|現在時刻 HH:MM 24h|

### ユーザー・directory

|コマンド|内容|
|:------------:|:-----------|
|\u|現在のユーザー|
|\w|現在のworking directory(フルパス)|
|\W|Basename of the 現在のworking directory(パスでなくベースのdirectory名)|
|\\$|有効なUID=0(root user)のときa#、通常ユーザーなら a$|

## PS1(プロンプト)の変更

* 多くはPS1環境変数を使う。他のシェルはprompt?など。個別に調べる

```
// 現在の設定：[\u@\h \W]\$　→ [ユーザーネーム@ホスト名最初のピリオドまで 現在のworking directoryのbasename] #か$(通常ユーザーは$)
echo $PS1

// 設定の変更：ユーザーネーム@ホスト名最初のピリオドまで #か$(通常ユーザーは$)
PS1="\u@\h \$ "

// 設定の変更 現在時刻 ユーザーネーム@ホスト名最初のピリオドまで フルパスcurrent working directory #か$(通常ユーザーは$)
PS1="<\t \u@\h \w>\$ "
  
// \wはフルパス ~/Documents/a5 => pwdで~が /home/adminuserを表す(home directory)ことを確認できる
pwd

// 
PS1="\d \t \h \W>\$ "

```


## .bash_profileの変更

```
// home directoryに戻る => .bash_profileをvi editor編集
cd
vi .bash_profile

// User specific environmentの下に追記
PATH=$PATH:$HOME/bin

export PATH

# My custome prompt
export PS1="[persist \u@\h \w]\$ "

// その後、ssh localhostログイン→promptがログインで上記の設定に変わる
ssh localhost

// 現在時刻・改行、[ホスト名、working directory basename] #か$(通常ユーザーは$)
PS1="\t\n[\h \w]\$ "

```
