# LVM_Logical_Volume_Manager

* 複数のstorage デバイス50GB*3を /var で1つのLVM 150GBで管理できる
* FILEの利用・アクセスを維持したまま拡張できる
* オンラインのデータrelocationが簡単
* 使いやすい名前にリネームできる
* 複数のデバイスを1つにしているので、パラレルで読むことで高速化できる
* data Redundancy / Mirroringができる
* Snapshotをとってバックアップにできる


## 階層
ストレージデバイス => PV(Physical Volume) => VG(volume group) => LV(logical volume) => file systems

## 作成例

```
// 1.アカウント切り替え
su -

// 2.storage表示（複数方法あり) (1)がいい？
// 2(1)使えるstorage deviceを確認
lvmdiskscan

// 2(2)partition,mountも表示  / -pはfull path表示
lsblk -p

// 2(3)みやすいフォーマット -h
df -h

// 2(4)Linuxにアタッチされているstorage表示
fdisk -l

// 3.PV作成 physical volume=> 確認
pvcreate /dev/sdb
pvs

// 4.VG作成 (VG名、PVを指定)=> 確認
vgcreate vg_app /dev/sdb
vgs
pvs

// 5.LV作成 (GB, name, VGを指定) => 確認
lvcreate -L 20G -n lv_data vg_app
lvs
lvdisplay

// LVPATH = /dev/vg_app/lv_data (PV/VG/LV)
// 

// 6.LV上にfile system作成し、fsをマウント
// 6(1) FS作成
mkfs -t ext4 /dev/vg_app/lv_data

// 6(2)directory(mount point)作成
mkdir /data

// 6(3)mount(LVのPATH, MOUNT POINT)
mount /dev/vg_app/lv_data /data

// 6(4)結果確認(mount pointのdirectory配下のFS情報)
df -h /data

// 7.LVを追加作成 (GB, name, VGを指定) => 確認
lvcreate -L 5G -n lv_app vg_app
lvs

// 8.LV上にfile system作成し、fsをマウント
// 8(1) FS作成
mkfs -t ext4 /dev/vg_app/lv_app

// 8(2)directory(mount point)作成
mkdir /app

// 8(3)mount(LVのPATHはfstabで指定し, MOUNT POINTのみでmountコマンド)
vi /etc/fstab
/dev/vg_app/lv_app /app ext4 defaults 0 0

mount /app

// 8(4)結果確認(mount pointのdirectory配下のFS情報)
df -h 


// 9. VGに残ったdisk space確認 => VFreeに記載
vgs

// VFreeぎりぎりでLV作成 => 容量不足エラー
lvcreate -L 25G -n lv_logs vg_app
```

* LV PATHはlvdisplayで表示できる


