画面の改造度を設定する
======================================================================

使用している3.5インチのモニタでは
字が読めないので解像度を落とす
ここではプリセットにない800x480を設定する

1. configファイルのバックアップ
```
$ sudo cp /boot/config.txt /boot/config.txt.bak
```

2. configに以下を追記する
```
hdmi_group=2
hdmi_mode=1
hdmi_mode=87
hdmi_cvt 800 480 60 6 0 0 0
```

右端が余っている気がするので


Refference
----------------------------------------------------------------------
[Amazon | Quimat 3.5インチタッチスクリーン HDMIモニタTFT LCDディスプレイ Raspberry Pi 3 2 Model B Rpi B B+ A A+ 映画 アーケードゲーム オーディオ入力 RPi GPIOブレークアウト拡張ボード 保護ケースキット アクリル(透明) QC35C | Quimat | マザーボード 通販](https://www.amazon.co.jp/gp/product/B075K56C12/ref=oh_aui_detailpage_o02_s00?ie=UTF8&psc=1)
[Raspberry Pi で使えるポータブルモニタの決定版が出てた（タッチスクリーン付き、GPIOを占有しない、ケース付き、約3000円） - nomolkのブログ](http://nomolk.hatenablog.com/entry/2018/02/06/223000)
