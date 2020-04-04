# ユーザー・グループ作成例

## グループ・ユーザー作成
```
// グループ作成 => GIDは自動採番
su
group add writers
group add tv
group add movie
tail -3 /etc/group

// user作成 -Gは追加グループ、最後はloginid
useradd -c "Carlton Cuse" -g writers -G tv -m -s /bin/bash ccuse

// password変更
passwd ccuse

// userのグループ確認(writers, tv)
groups ccuse

// 別のユーザー追加
useradd -c "David Fury" -g writers -G tv -m -s /bin/bash dfury
passwd dfury
groups dfury

useradd -c "Matt Dameon" -g writers -G movie -m -s /bin/bash mdamon
passwd mdamon
groups mdamon

useradd -c "Ben Affleck" -g writers -G movie,tv -m -s /bin/bash bafflec
passwd bafflec
groups bafflec

// /etc/groupの最後の3行を表示（追加したので)
tail -3 /etc/group

```

## グループメンバーリスト情報表示

* /etc/group・・・グループ情報を持つ

```
// /etc/groupの最後の3行を表示（追加したので)
tail -3 /etc/group

// writersに所属userがいない？ccuseはwriterグループに所属していることを確認
groups ccuse

// writerのGUID 1001を含む行検索
grep 1001 /etc/passwd
```


