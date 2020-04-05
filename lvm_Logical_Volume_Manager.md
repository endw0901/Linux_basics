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

## VGとLVの拡張

### VG拡張
```
// 空き確認
lvmdiskscan

// physical volume追加
pvcreate /dev/sdc/

// volume groupにphsycal volumeを追加 => vg_appを拡張
vgextend vg_app /dev/sdc

// 追加した分だけVFreeが増えていることを確認
vgs

// vgsを、pvごとに確認（pv別の空き容量
pvs
```

### LV拡張

```
// file sysetemのfree spaceを確認
df -h /data

// lvを5G拡張。-r = resize 、lvのPATH
// -rがないと、lvは拡張されるが、file systemのsizeは変わらない
lvextend -L +5G -r /dev/vg_app/lv_data
lvs

// Available 容量拡張を確認
df -h /data

resize2fs /dev/vg_app/lv_data
df -h /data
```

### mapping

```
// mapping
//  =>one FS が複数のLV上に分散されていることが分かる
lvdisplay -m /dev/vg_app/lv_data

// device確認して、pv作成
lvmdiskscan
pvcreate /dev/sdd /dev/sde
pvs

// pvをvgにアサイン
vgcreate vg_safe /dev/sdd /dev/sde
vgs 

// LV作成 mapping (-m 1 = 1copy => 合計で2)、LV名、元のVG
lvcreate -m 1 -L 5G -n lv_secrets vg_safe
lvs

// 
lvs -a

mkfs -t ext4 /dev/vg_safe/lv_secrets
mkdir /secrets
mount /dev/vg_safe/lv_secrets /secrets
df -h /secrets
```

