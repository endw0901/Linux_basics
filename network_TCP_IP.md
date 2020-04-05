# TCP/IP 

* Transmission Control Protocol・・・controls data exchange
* Internet Protocol・・・sends data from one device to another 
* Host・・・devices on a network that have an IP address

## Classful Networks

* Aクラス：17.24.88.9など
* Bクラス：183.194.46.31など
* Cクラス：199.83.131.186など


|class|Network|Subnet Mask|Broadcast|
|:------------:|:-----------:|:-----------:|:-----------:|
|A|17.0.0.0|255.0.0.0|17.255.255.255|
|B|183.194.0.0|255.255.0.0|183.194.255.255|
|C|199.83.131.0|255.255.255.0|199.83.131.255|


## CIDR：Classless Inter-Domain Routing

* classに関わらずネットワークを分割できる

* 例<classful Network>IP:121.67.198.94 

|class|Network|Subnet Mask|Broadcast|
|:------------:|:-----------:|:-----------:|:-----------:|
|A|121.0.0.0|255.0.0.0|121.255.255.255|

* 例<CIDR> IP:121.67.198.94 Subnet:255.255.255.0

|class|Network|Subnet Mask|Broadcast|
|:------------:|:-----------:|:-----------:|:-----------:|
|A|121.67.198.0|255.255.255.0|121.67.198.255|


