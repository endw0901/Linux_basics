# ソフトウェアのインストール

* version, dependency, descriptionをまとめて含む = package


## RPM

* RPM = redhat package manager
* RedHat, CentOS, Fedora, OracleLinux, Scientific Linux = RPM Distros

## yum

* remove, installにはroot / superuser権限が必要

* yum search string
* yum info [package]
* yum install [-y] package・・・[-y]を入れると、毎回yesを自動でやってくれる
* yum remove package

## rpm

* rpm -qa・・・インストール済みpackageをすべてリスト表示
* rpm -qf /path/to/file・・・ファイルが所属するpackageをリスト表示
* rpm -ql・・・packageに所属するfileをすべてリスト表示

* rpm -rvh package.rpm・・・インストールpackage


```
// 
yum search inkscape
yum info inkscape-docs

// rootユーザーにスイッチしてinstall
//  => yum install -y inkscapeならyesを省略できる
su -
yum install inkscape
yum install -y gimp
yum remove gimp
```


## DEB Distro

* popular distribution = Debian

* Debian
* Linux Mint
* Ubuntu

### APT - Advanced Packaging Tool

* Debianの管理コマンド

* apt-cache search string
* apt-get install [-y] package
* apt-get remove package・・・コンフィグは残す
* apt-get purge package ・・・コンフィグ削除まで行う

* apt-cache show package・・・package情報表示

### dpkg

* APTのほかに使えるコマンド

* dpkg -l・・・インストール済みpackageをリスト表示
* dpkg -s /path/to/file・・・fileの属するpackageをリスト表示
* dpkg -L package・・・packageに属する全fileをリスト表示
* dpkg -i pakcage.deb・・・packageをインストール



## 例

```
apt-cache show inkscape | less

// root権限でinstall
sudo apt-get install inkscape




```
