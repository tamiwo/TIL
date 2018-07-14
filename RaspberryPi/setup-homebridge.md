Title Homebridgeのセットアップ
======================================================================

homebridge経由でirMagicianのコマンドを発行するまで

1. Node.jsのインストール
   8版でも動かない記事が見られたので6版で

```
$ curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
$ sudo apt-get install -y nodejs
```

いちおうログ
```
$ curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -

## Installing the NodeSource Node.js 6.x LTS Boron repo...


## Populating apt-get cache...

+ apt-get update
Get:1 http://archive.raspberrypi.org/debian stretch InRelease [25.3 kB]        
Get:2 http://raspbian.raspberrypi.org/raspbian stretch InRelease [15.0 kB]     
Get:3 http://archive.raspberrypi.org/debian stretch/main armhf Packages [166 kB]
Get:4 http://raspbian.raspberrypi.org/raspbian stretch/main armhf Packages [11.7 MB]
Get:5 http://archive.raspberrypi.org/debian stretch/ui armhf Packages [34.0 kB]
Fetched 11.9 MB in 25s (467 kB/s)                                              
Reading package lists... Done

## Confirming "stretch" is supported...

+ curl -sLf -o /dev/null 'https://deb.nodesource.com/node_6.x/dists/stretch/Release'

## Adding the NodeSource signing key to your keyring...

+ curl -s https://deb.nodesource.com/gpgkey/nodesource.gpg.key | apt-key add -
OK

## Creating apt sources list file for the NodeSource Node.js 6.x LTS Boron repo...

+ echo 'deb https://deb.nodesource.com/node_6.x stretch main' > /etc/apt/sources.list.d/nodesource.list
+ echo 'deb-src https://deb.nodesource.com/node_6.x stretch main' >> /etc/apt/sources.list.d/nodesource.list

## Running `apt-get update` for you...

+ apt-get update
Hit:1 http://archive.raspberrypi.org/debian stretch InRelease                  
Hit:2 http://raspbian.raspberrypi.org/raspbian stretch InRelease               
Get:3 https://deb.nodesource.com/node_6.x stretch InRelease [4,635 B]
Get:4 https://deb.nodesource.com/node_6.x stretch/main armhf Packages [1,008 B]
Fetched 5,643 B in 2s (2,541 B/s)
Reading package lists... Done

## Run `sudo apt-get install -y nodejs` to install Node.js 6.x LTS Boron and npm
## You may also need development tools to build native addons:
     sudo apt-get install gcc g++ make
## To install the Yarn package manager, run:
     curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
     echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
     sudo apt-get update && sudo apt-get install yarn


pi@raspberrypi:~ $ sudo apt-get install -y nodejs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libc-ares2 libhttp-parser2.8 libuv1 nodejs-doc nodered
The following packages will be REMOVED:
  nodejs-legacy
The following NEW packages will be installed:
  libc-ares2 libhttp-parser2.8 nodejs-doc
The following packages will be upgraded:
  libuv1 nodejs nodered
3 upgraded, 3 newly installed, 1 to remove and 76 not upgraded.
Need to get 10.3 MB of archives.
After this operation, 61.5 MB of additional disk space will be used.
Get:1 http://archive.raspberrypi.org/debian stretch/main armhf libc-ares2 armhf 1.14.0-1~bpo9+1 [80.7 kB]
Get:2 http://archive.raspberrypi.org/debian stretch/main armhf libhttp-parser2.8 armhf 2.8.1-1~bpo9+1 [19.3 kB]
Get:3 http://archive.raspberrypi.org/debian stretch/main armhf libuv1 armhf 1.18.0-3~bpo9+1 [86.3 kB]
Get:4 http://archive.raspberrypi.org/debian stretch/main armhf nodered armhf 0.18.7-3 [5,185 kB]
Get:5 http://archive.raspberrypi.org/debian stretch/main armhf nodejs armhf 8.11.1~dfsg-2~bpo9+1 [4,126 kB]
Get:6 http://archive.raspberrypi.org/debian stretch/main armhf nodejs-doc all 8.11.1~dfsg-2~bpo9+1 [775 kB]
Fetched 10.3 MB in 27s (379 kB/s)                                              
apt-listchanges: Reading changelogs...
Selecting previously unselected package libc-ares2:armhf.
(Reading database ... 124722 files and directories currently installed.)
Preparing to unpack .../libc-ares2_1.14.0-1~bpo9+1_armhf.deb ...
Unpacking libc-ares2:armhf (1.14.0-1~bpo9+1) ...
Selecting previously unselected package libhttp-parser2.8:armhf.
Preparing to unpack .../libhttp-parser2.8_2.8.1-1~bpo9+1_armhf.deb ...
Unpacking libhttp-parser2.8:armhf (2.8.1-1~bpo9+1) ...
Preparing to unpack .../libuv1_1.18.0-3~bpo9+1_armhf.deb ...
Unpacking libuv1:armhf (1.18.0-3~bpo9+1) over (1.9.1-3) ...
Preparing to unpack .../nodered_0.18.7-3_armhf.deb ...
Unpacking nodered (0.18.7-3) over (0.18.4-1) ...
(Reading database ... 123425 files and directories currently installed.)
Removing nodejs-legacy (4.8.2~dfsg-1) ...
(Reading database ... 123417 files and directories currently installed.)
Preparing to unpack .../nodejs_8.11.1~dfsg-2~bpo9+1_armhf.deb ...
Unpacking nodejs (8.11.1~dfsg-2~bpo9+1) over (4.8.2~dfsg-1) ...
Selecting previously unselected package nodejs-doc.
Preparing to unpack .../nodejs-doc_8.11.1~dfsg-2~bpo9+1_all.deb ...
Unpacking nodejs-doc (8.11.1~dfsg-2~bpo9+1) ...
Setting up nodejs-doc (8.11.1~dfsg-2~bpo9+1) ...
Processing triggers for mime-support (3.60) ...
Processing triggers for desktop-file-utils (0.23-1) ...
Setting up libuv1:armhf (1.18.0-3~bpo9+1) ...
Processing triggers for libc-bin (2.24-11+deb9u3) ...
Processing triggers for man-db (2.7.6.1-2) ...
Processing triggers for gnome-menus (3.13.3-9) ...
Processing triggers for hicolor-icon-theme (0.15-1) ...
Setting up libc-ares2:armhf (1.14.0-1~bpo9+1) ...
Setting up libhttp-parser2.8:armhf (2.8.1-1~bpo9+1) ...
Setting up nodejs (8.11.1~dfsg-2~bpo9+1) ...
Setting up nodered (0.18.7-3) ...
Processing triggers for libc-bin (2.24-11+deb9u3) ...
```


2. homebridgeのインストール
```
$ sudo npm install -g --unsafe-perm homebridge hap-nodejs node-gyp
$ cd /usr/lib/node_modules/homebridge/
$ sudo npm install --unsafe-perm bignum
$ cd /usr/lib/node_modules/hap-nodejs/node_modules/mdns
$ sudo node-gyp BUILDTYPE=Release rebuild
```

１行目で
```
sudo: npm: command not found
```
と言われた

https://qiita.com/mascii/items/77c685df65c4cbca9315
を参考にnpmをインストール

```
sudo apt-get install -y npm
```

Refference
----------------------------------------------------------------------
[](https://)
