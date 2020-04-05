# ネットワークトラブルシューティング 

## ping コネクションテスト

```
ping google.com
ping -c 3 google.com
```

* エラー発生 => 他のサイトではokなら、ローカルネット側の問題かも

## traceroute

* それぞれホップを表示 このip => 次のip => 3つめのアクセスにとても時間がかかっている = 問題かも

```
// -n dns変換をスキップ
traceroute -n google.com
```

## tracepath

* root権限が必要
* tracepathはレスポンスごとに1行、tracerouteは１ホップごとに1行

```
tracepath -n googl.com
```

## netstat

* たくさんのオプションがある

## tcpdump

* パケットのペイロードを確認

* -nオプションは、DSNクエリをスキップして直接数字で処理できる


```
// root権限が必要
sudo tcpdump
```

## telnet

* telnetはSSHに取って代わられているが、トラブルシューティングには使われる
* port connectivityをテスト

```
telnet google.com 80

// GET HOMEPAGE
GET /

// プロンプト表示させてquit
^]
quit
```


