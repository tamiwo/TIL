WiFiの設定
======================================================================
WiFiの接続設定

1. AP名(SSID)を探す場合
```
$ sudo iwlist wlan0 scan
```

2. 
```
$ sudo vi /etc/wpa_supplicant/wpa_supplicant.conf
```
以下を追記する
```
network={
        ssid="AP名"
        psk="パスワード"
        key_mgmt=WPA-PSK
}
```

3. 再起動する
ifdownがうまくいかなかったので
rebootした
```
$ sudo ifdown wlan0
ifdown: unknown interface wlan0
$ sudo reboot
```

Refference
----------------------------------------------------------------------
[](https://)
