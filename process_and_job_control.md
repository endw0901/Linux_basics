# process and job control

* list running process
* バックグラウンドプロセスの起動
* kill the process

|コマンド|内容|
|:------------:|:-----------|
|ps|プロセスstatus表示（現在のセッション上のプロセス)|
|ps -e|全プロセス|
|ps -f|full format|
|ps -u username|該当ユーザーのプロセスのみ表示|
|ps -p PID|PIDの情報表示|

```
// display all processes
ps -e

// display all processes, full formating pipe less
ps -ef | less

// display a process tree
ps -eH

// display a process tree
ps -e --forest

// display processes in a tree format
pstree

// interactive process viewer
top
htop

// 特定ユーザー/rootの全プロセス
ps -fu user1
ps -fu root

// 全プロセスfull formatをツリー表示、lessパイプ
ps -ef --forest | less
```

## CPUリソースを使う上位表示

```
top
htop
```

## foregroundとバックグラウンドプロセス

|コマンド|内容|
|:------------:|:-----------|
|command &|コマンドをバックグランドで開始　※実行コマンドの後ろに&を付けて実行|
|ctrl + c|foregroundプロセスの終了(kill)|
|ctrl + z|foregroundプロセスの停止(suspend)|


|コマンド|内容|
|:------------:|:-----------|
|bg [%num]|停止中(suspended)foregroundプロセスをbackgroundにする|
|fg [%num]|停止中(suspended)バックグラウンドプロセスをforegroundプロセスにする|
|kill [%job番号 or PID]|プロセスをjob / PID指定でkill|
|jobs [%num]|jobをリスト表示|


## kill

|コマンド|内容|
|:------------:|:-----------|
|kill -l|プロセスに送れるsignalの一覧を表示|

* 9：SIGKILL
* 15：SIGTERM

```
// foregroundプロセスをkill
ctrl+c

// pidにsignalを送る。signalのdefaultはterminationなので、kill pidでpidをkillする
kill [-sig] pid

// signalのリスト表示
kill -l

// pid123をkill
kill 123

// pid123をkill (terminationのsignalのdefaultの数字は15)
kill -15 123

// pid123をkill (terminationのsignalを送る)
kill -TERM 123

// killシグナル(9)を送って強制終了
kill -9 123

```

## job番号
* [1]2373 ：[1]はjob番号

```
// 実行中のjob情報(job番号1)
job %1

jobs

// 現在のプロセス
%%
%+

// ひとつ前のプロセス
%-

// 現在のjob
jobs %%
jobs %+

// ひとつ前のjob
jobs %-

// job番号をjobsで確認し、job番号2をbgからfgに移動する
jobs
fg %2

// job番号1をsuspendし、ステータス確認し、bgに移動し、kill
fg 1
ctrl + z
jobs
bg %1
jobs
kill %1
jobs


```
