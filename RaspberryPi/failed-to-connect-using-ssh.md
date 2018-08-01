SSH接続での接続に失敗する
======================================================================

以下のエラーが出る場合
```shell
$ ssh 192.168.0.33
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ECDSA key sent by the remote host is
SHA256:TpIEOUWa+GCZT+CP0MDkuGifwPMOSgrcXDwav5niBVk.
Please contact your system administrator.
Add correct host key in /Users/xxxxx/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /Users/xxxxx/.ssh/known_hosts:10
ECDSA host key for 192.168.0.33 has changed and you have requested strict checking.
Host key verification failed.
```

以前に192.168.0.33で接続したあと、
OSを再インストールして、サーバ情報が変わってしまったため
WARNNIGが出ている。

原因がわかっているので
```shell
$ ssh-keygen -R raspberrypi.local
# Host rasperrypi.local found: line N
/Users/xxxxx/.ssh/known_hosts updated.
Original contents retained as /Users/xxxxx/.ssh/known_hosts.old
```
としてサーバ情報を削除する。



Refference
----------------------------------------------------------------------
[SSH接続エラー回避方法：.ssh/known_hostsから特定のホストを削除する/削除しないで対処する3つの方法](https://qiita.com/grgrjnjn/items/8ca33b64ea0406e12938)
