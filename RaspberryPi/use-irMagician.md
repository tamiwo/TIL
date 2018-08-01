irMagicianを使う
======================================================================

1. アプリのDL

```bash
$ git clone https://github.com/netbuffalo/irmcli.git
```

2. 必要なライブラリのインストール
```bash
 $ sudo apt-get install python-pip
 $ sudo pip install pyserial
```

すでに入っていたようだった

3. /devの下にttyACM0がないことを確認する

4. irMagicianを挿す

5. 再度/devの下を確認する
```bash
$ ls /dev/ttyACM*
/dev/ttyACM0
```
できていればよい

6. スキャンする
```bash
$ sudo python irmcli.py -h 
Capturing IR...
... 162
```

7. スキャンしたデータをファイルにする
```bash
$ sudo python irmcli.py -s -f filename.json
Saving IR data to light_on_off.json ...
Done !
```

8. データを送信してみる
```bash
$ sudo python irmcli.py -p -f filename.json
```


Refference
----------------------------------------------------------------------
[iOS10「ホーム」アプリと「Raspberry Pi + irMagician」でお手軽家電操作。](https://qiita.com/PonDad/items/a17d8b7d0be59f4c7f18)
[netbuffalo_irmcli  irMagician command line utility](https://github.com/netbuffalo/irmcli)
