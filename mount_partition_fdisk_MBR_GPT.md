# Disk management


## Partitions

* home directoryを使いすぎてユーザーがosのspaceなどをくわないかなど、partitionを分けてシステムをoutageから守る

## MBR

* Master Boot Record
* GPTに徐々に置き換えられている

## GPT

* MBRを徐々に置き換えている（古いOSではサポートされない)
* GUID Partition Table
* 4つまでの主要なPartition + 拡張partition(無制限)

* UEFIの一部 (Unified Extensible Firmware Interface) 
* UEFIはBIOSに取って代わろうとしている


## Mount Point

* Mount Point = directory。partition上のdataにアクセスするのにつかわれるdirectoryのこと
* /(slash)がMount Point

```
//  「/home」にマウントされたpartition
/home/masaya

// mountする前に作られた /home/sarahはアクセスできない => unmountでアクセス可能になる
mkdir /home/sarah
mount /dev/sdb2 /home

unmount /home/
//

```

## paritioning tool

* fdisk (古いバージョンでは、GPTをサポートしない)
* gdiskやpartedはfdiskの代替ツール


### fdiskでpartition作成


```
fdisk -l | less
fdisk /dev/sdb

// Command m for help
m

// n:add a new partition
n

// primary or extended partition
p or enter

// 以下略。interactiveに進めていく。確認はfdisk -l
```
