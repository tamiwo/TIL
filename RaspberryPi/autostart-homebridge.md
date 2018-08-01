homebridgeの自動起動
======================================================================

Raspberri piの起動と同時にhomebridgeも起動するようにするため
systemdに登録する

新しく以下のファイルをつくる
```
$ sudo vim /etc/systemd/system/homebridge.service
```

```
[Unit]
Description=run homebridge
After=syslog.target network-online.target

[Service]
Type=simple
User=pi
ExecStart=/home/pi/App/homebridgeStart.sh
Restart=on-failure
RestartSec=10
KillMode=process

[Install]
WantedBy=multi-user.target
```

Description:説明
After:syslogが有効になったあと（多分）
      ネットワークが有効になったあと
User:参考ページでは専用のユーザを作ったりしているが、ここではつくってないのでpi
ExecStart:起動するプログラムのパス。コマンドではない
          ここではスクリプトを指定している

スクリプトの中身
```
#!/bin/bash

sudo homebridge -I
```

スクリプトに実行権限を与えとかないと起動に失敗する
```
$ sudo chmod 755 /home/pi/App/homebridgeStart.sh
```

有効にする
```
$ sudo systemctl daemon-reload
$ sudo systemctl enable homebridge
```

再起動するか、そのまま
```
$ sudo systemctl start homebridge
```
とやれば起動する

起動したかは
```
$ sudo systemctl status homebridge
```
でそれっぽいログが出ているかをみる。もしくはプロセスがいるか探す

```
$ ps -el | grep home
4 S  1000   293     1  0  80   0 -  1017 wait   ?        00:00:00 homebridgeStart
4 S     0   360   332  0  80   0 - 41319 -      ?        00:00:07 homebridge
```

でてこなかったら起動してないのでsyslogを確認する

```
$ less /var/log/syslog
```

Refference
----------------------------------------------------------------------
[homebridge on Raspberry Pi + Siriで家電コントロール](http://yorino.hatenablog.com/entry/2017/09/02/180440)
[Raspberry Pi 3 にhomebridgeを導入してsiriから家電操作できるようにした際の覚書](https://qiita.com/udon242/items/25e09769196cbbe397e3)
[systemdを用いたプログラムの自動起動](https://qiita.com/tkato/items/6a227e7c2c2bde19521c)
