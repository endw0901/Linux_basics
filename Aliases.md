# エイリアス

* alias [name[=value]]

* Aliases = ショートカット
* 長いコマンドや、頻繁に使うコマンドに対してエイリアスを使う
* 例：ls -l => エイリアス「ll」にする、とか


|コマンド|内容|
|:------------:|:-----------|
|alias|設定中のエイリアスをリスト表示|

## 例

```
// タイプミス対策
alias grpe='grep'

// 他のOSのコマンドをLinux風に置換
alias cls='clear'

```

## エイリアス削除

|コマンド|内容|
|:------------:|:-----------|
|unalias name|削除|
|unalias -a|全てのエイリアス削除|


## 設定を残したい(persist)とき

* .bash_profileを編集(cd => vi .bash_profile)


## 例

```
// エイリアス作成
alias ll='ls -l'
ll

// 設定を残す => ログインし直すと使える 
cd
vi .bash_profile

# My aliases
alias mycls='clear'
exit
ssh localhost


```
