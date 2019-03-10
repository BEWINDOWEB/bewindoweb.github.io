# strongswan的ipsec.conf配置

## 环境

操作系统：CentOS 7  
Strongswan：Linux strongSwan U5.5.3/K4.9.50-x86_64-linode86  
经测试支持系统：`windows 8`、`windows 10`、`ios11（iphone7 Plus）`、`ios11（ipad pro 2017）`、`mac OS X（mac air）`  
经测试未支持系统：`android（miui9）`  

## ipsec.conf内容
```
config setup
    uniqueids=never
    charondebug="cfg 2, dmn 2, ike 2, net 0"

conn %default
    left=%defaultroute
    leftsubnet=0.0.0.0/0
    leftcert=vpnHostCert.pem
    right=%any
    rightsourceip=10.0.0.0/24

conn xauth_pubkey_ikev1
    keyexchange=ikev1
    fragmentation=yes
    rightauth=pubkey
    rightauth2=xauth
    leftsendcert=always
    rekey=no
    auto=add

conn xauth_psk_ikev1
    keyexchange=ikev1
    leftauth=psk
    rightauth=psk
    rightauth2=xauth
    auto=add
    dpdaction=hold
    dpddelay=600s
    dpdtimeout=5s
    lifetime=24h
    ikelifetime=240h
    rekey=no

conn pubkey_ikev2
    keyexchange=ikev2
    leftauth=pubkey
    rightauth=pubkey
    leftsendcert=always
    auto=add

conn eap_ikev2
    keyexchange=ikev2
    ike=aes256-sha1-modp1024!
    rekey=no
    leftauth=pubkey
    leftsendcert=always
    rightauth=eap-mschapv2
    eap_identity=%any
    auto=add
```
