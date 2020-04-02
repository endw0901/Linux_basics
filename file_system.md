# ファイルシステム 

## File Systems

* ext = Extended file system (デフォルトのfile system)
* その他・・ReiserFS, JFS, XFS, ZFS, Btrfs

## mkfs ：ファイルシステムの作成

```
// ext3タイプで /dev/sdb2デバイスにfile systemを作成
mkfs -t ext3 /dev/sdb2

// 
ls -l /sbin/mkfs*

// help 
man mkfs
```

## マウント

```
// デバイス「/dev/sdb3」をマウントポイント「/opt」にマウント
mount /dev/sdb3 /opt

```

## 関連コマンド

* mkfs
* mount
* umount
* df
* mkswap
* swapon

* /etc/fstab
* UUID and labelsを見る, label作成
