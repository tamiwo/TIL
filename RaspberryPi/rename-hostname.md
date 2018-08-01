Rename hostname
======================================================================

以下の２つのファイルに記載されている。
```
$ sudo vim /etc/hostname
$ sudo vim /etc/hots
```

hostnameはhostnameだけが書かれているので
丸ごと消して書き直せばよい
```
raspberrypi
```

hostsの方は他にも書かれているので
hostnameと同じ名前が書かれていたところを書き換えればよい
127.0.1.1のところ
```
127.0.0.1	localhost
::1		localhost ip6-localhost ip6-loopback
ff02::1		ip6-allnodes
ff02::2		ip6-allrouters

127.0.1.1	raspberrypi
```

変更後再起動する

Refference
----------------------------------------------------------------------
[Raspberry Piにホスト名の設定をしたメモ](https://www.1ft-seabass.jp/memo/2015/04/21/raspberry-pi-hostname-memo/)
