# DNS, hostname

## IP addressの決定


// inet 127.0.0.0・・inetのところにipaddress表示
ip address
ip addr
ip a
ip address show
ip a s


* ifconfig・・・上のipコマンドより古いが残っているかも


## DNS

* FQDN ・・・ fully qualified domain name
* TLD・・・top level domain(.com, .net, .orgなど)
* Domains (TLDの左）
* sub-domain (Domainsの左)



|DNS|値|
|:------------:|:-----------|
|FQDN|webprod01.mycompany.com|
|TLD|.com|
|Domains|webprod01.mycompany|
|sub-domain|webprod01.ny.us.mycompany.com|

## hostname表示

* hostname
* uname -n
* hostname -f

### hostnameコンフィグ設定

```
// Ubuntu, Redhatでのhostname設定
hostname webprod01
echo 'webprod01' > /etc/hostname
vi /etc/sysconfig/network
HOSTNAME=webprod01
```

## resolving DNS names

* host
* dig

## /etc/hostsファイル

* format：IP FQDN alias(es)

```
10.11.12.13 webprod02.mycorp.com webprod02
```

## /etc/nsswitch.conf

* NSS = Name Service Switch
* 名前解決resolvingの検索順を制御する

```
hosts: files dns
hosts: files nis dns
```







