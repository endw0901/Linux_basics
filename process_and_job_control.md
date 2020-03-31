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
```


|コマンド|内容|
|:------------:|:-----------|
|||
|||
