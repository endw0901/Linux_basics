# BIOS_boot_process 

## BIOS
* BIOS = Basic Input / Output System
* おもな役割 = boot loaderの発見と実行
* POST (Power-On Self Test)を実行する

## Boot Loader

* LILO = Linux Loader
* GRUB = Grand Unified Bootloader (replace LILO)

* Boot Loaderの役割 = OSをstartする

## initRD = initial RAM Disk

* initRD = diskからloadされ、memoryにstoreされるtemporary file system
* OS file systemを起動するために必要なmodule やhelpを格納する

## /boot Directory

* Linuxのbootに必要なfileを保持

* initRD, kernel, boot loader configuration

```
// 
ls -F /boot
```

## Kernel Ring Buffer

* Linux kernelからのmessageを保持する
* dmesgコマンド
* /var/log/dmesg

## Init

* /etc/inittab:

```
id:3:initdefault:
```

* being phased out by systemd

### Runlevels

* initに保持する（一般に）

|コマンド|内容|
|:------------:|:-----------|
|0|shut down|
|1|1, S,s：single user mode for メンテナンス|
|2|multi-user mode with GUI / Debiun, Ubuntu|
|3|multi-user text mode(RedHat, CentOS)|
|4|未定義|
|5|multi-user mode with GUI / (RedHat, CentOS)|
|6|Reboot|

### systemd

* targetsを使う（runlevelsの代わりに）

```
// 利用可能なtargetを見る
// /lib/systemd/system
cd

// runlevel 5 target -> graphical target
ls -l runlevel5.target
```

### runlevelsの変更

|コマンド|内容|
|:------------:|:-----------|
|telinit RUNLEVEL|runleveの変更|
|systemctl isolate TARGET|変更したいTARGETを指定|


```
telinit 5
systemctl isolate graphical.target
```

## リブート

```
// runlevelを直接渡す
telinit 6

// targetを使う
systemctl isolate reboot.target

// rebootコマンドで実行
reboot

// shutdownコマンド(時間指定, 5分後、今すぐnow)   shutdown -r (-rはrebootオプション)
shutdown -r 15:30 "rebooting!"
shutdown -r +5 "rebooting soon!"
shutdown -r now

```

## Power off

```
// runlevelを渡す
telinit 0

// targetを使う
systemctl isolate poweroff.target

// コマンドでpower off
poweroff
```
