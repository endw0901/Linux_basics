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
