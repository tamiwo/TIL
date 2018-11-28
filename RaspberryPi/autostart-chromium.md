Raspberry pi の起動時にChromiumを全画面起動する
======================================================================

マウスカーソルを消すならunclutterを入れる
```
$ sudo apt install unclutter
```


~/.config/lxsession/LXDE-pi/autostart を以下のように修正する 
```
@lxpanel --profile LXDE-pi
@pcmanfm --desktop --profile LXDE-pi
@xscreensaver -no-splash

@xset s off
@xset -dpms
@xset s noblank
@unclutter
@chromium-browser --noerrdialogs --kiosk --incognito http://localhost/
```

--noerrdialogs：エラーを表示しない
--kiosk：全画面モード
--incongnito：シークレットモードで起動する

kioskモードは画面がつきっぱなしなので
フルスクリーンにする
--window-size=800,600
--window-pos=0,0


Refference
----------------------------------------------------------------------
[Raspberry Pi3でキオスク端末(自動ログイン＋ブラウザ起動)を作る。](https://qiita.com/yyano/items/c08705994363b9526d07)
