ラズパイをAPにする
======================================================================

dash button用に別のWifiネットワークを用意する

TL-WN725Nのドライバインストール

ラズパイに挿した状態で

```
$ sudo wget http://www.fars-robotics.net/install-wifi -O /usr/bin/install-wifi
$ sudo chmod +x /usr/bin/install-wifi
$ sudo install-wifi
```
して再起動。

wlanのifができる

if設定
/etc/dhcpcd.confに以下を追記
```
interface wlan1
static ip_address=192.168.200.1/24
``` 
hostapdの導入
```
sudo apt install hostapd -y
```

上記はdriver=nl80211のときで
driver=rtl871xdrv を使うので以下でいれる
```
$ unzip adafruit_hostapd.zip 
$ sudo mv /usr/sbin/hostapd /usr/sbin/hostapd.ORIG 
$ sudo mv hostapd /usr/sbin
$ sudo chmod 755 /usr/sbin/hostapd
```


```
$ cd /etc/hostapd/
$ sudo cp /usr/share/doc/hostapd/examples/hostapd.conf.gz ./
$ sudo gzip -d hostapd.conf.gz
```

できた/etc/hostapd/hostapd.confを編集

```
interface=wlan1
driver=nl80211
#driver=rtl871xdrv  #最後に説明します
ssid=MyPi
hw_mode=g
channel=6
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2
wpa_passphrase=raspberry
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
```


Refference
----------------------------------------------------------------------
[Raspberry PiがTP-LINK製WiFiアダプタを自動認識しない場合の対処法](https://qiita.com/mmorita44/items/2f1b9798bce301aea985)
