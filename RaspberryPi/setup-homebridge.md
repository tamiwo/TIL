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
sudo npm cache clean
sudo npm install npm n -g
```
WARNIGが結構でたがインストールはできたようす

```
$ sudo npm cache clean
(node:20616) [DEP0022] DeprecationWarning: os.tmpDir() is deprecated. Use os.tmpdir() instead.
pi@raspberrypi:~ $ sudo npm install npm n -g
(node:20633) [DEP0022] DeprecationWarning: os.tmpDir() is deprecated. Use os.tmpdir() instead.
/usr/local/bin/n -> /usr/local/lib/node_modules/n/bin/n
npm WARN package.json path-is-inside@1.0.2 No README data
npm WARN package.json sorted-object@2.0.1 No README data
/usr/local/bin/npm -> /usr/local/lib/node_modules/npm/bin/npm-cli.js
/usr/local/bin/npx -> /usr/local/lib/node_modules/npm/bin/npx-cli.js
npm WARN package.json config-chain@1.1.11 No license field.
npm WARN package.json cyclist@0.2.2 No license field.
npm WARN package.json json-schema@0.2.3 No license field.
npm WARN package.json jsonify@0.0.0 license should be a valid SPDX license expression
npm WARN package.json punycode@1.4.1 punycode is also the name of a node core module.
npm WARN package.json qrcode-terminal@0.12.0 No license field.
npm WARN package.json sntp@1.0.9 No license field.
npm WARN package.json string_decoder@1.1.1 string_decoder is also the name of a node core module.
n@2.1.12 /usr/local/lib/node_modules/n
```

```
$ npm -v
6.2.0
```

で、そのあと

```
$ sudo n lts
```

を実行したので

```
$ node -v
v8.11.3
```

となった

再度
```
$ sudo npm install -g --unsafe-perm homebridge hap-nodejs node-gyp
```

```
$ cd /usr/lib/node_modules/homebridge/
-bash: cd: /usr/lib/node_modules/homebridge/: No such file or directory
```

ない。

その前のinstallで

```
pi@raspberrypi:~ $ sudo npm install -g --unsafe-perm homebridge hap-nodejs node-gyp
npm WARN notice [SECURITY] hoek has the following vulnerability: 1 moderate. Go here for more details: https://nodesecurity.io/advisories?search=hoek&version=2.16.3 - Run `npm i npm@latest -g` to upgrade your npm version, and then `npm audit` to get more info.
/usr/local/bin/homebridge -> /usr/local/lib/node_modules/homebridge/bin/homebridge
```

というログが出ていたので
```
$ cd /usr/local/lib/node_modules/homebridge/
```

として進める



```
$ sudo npm install --unsafe-perm bignum

> bignum@0.13.0 install /usr/local/lib/node_modules/homebridge/node_modules/bignum
> prebuild-install || node-gyp rebuild

prebuild-install WARN install No prebuilt binaries found (target=8.11.3 runtime=node arch=arm platform=linux)
make: Entering directory '/usr/local/lib/node_modules/homebridge/node_modules/bignum/build'
  CXX(target) Release/obj.target/bignum/bignum.o
  SOLINK_MODULE(target) Release/obj.target/bignum.node
  COPY Release/bignum.node
make: Leaving directory '/usr/local/lib/node_modules/homebridge/node_modules/bignum/build'
npm notice created a lockfile as package-lock.json. You should commit this file.
+ bignum@0.13.0
added 64 packages in 28.177s
pi@raspberrypi:/usr/local/lib/node_modules/homebridge $ cd /usr/local/lib/node_modules/hap-nodejs/node_modules/mdns
-bash: cd: /usr/local/lib/node_modules/hap-nodejs/node_modules/mdns: No such file or directory
```

またない。

http://blog.mogmet.com/hey-siri-turning-on-light-with-rasberry-pi-zero-w-homebridge-remo/

の記事を見て
	
```
$ sudo npm install --unsafe-perm mdns
$ sudo npm rebuild --unsafe-perm
```

を実施。失敗。

```
pi@raspberrypi:/usr/local/lib/node_modules/homebridge $ sudo npm install --unsafe-perm mdns

> mdns@2.4.0 install /usr/local/lib/node_modules/homebridge/node_modules/mdns
> node-gyp rebuild

make: Entering directory '/usr/local/lib/node_modules/homebridge/node_modules/mdns/build'
  CXX(target) Release/obj.target/dns_sd_bindings/src/dns_sd.o
In file included from ../src/dns_sd.cpp:1:0:
../src/mdns.hpp:32:20: fatal error: dns_sd.h: No such file or directory
 #include <dns_sd.h>
                    ^
compilation terminated.
dns_sd_bindings.target.mk:150: recipe for target 'Release/obj.target/dns_sd_bindings/src/dns_sd.o' failed
make: *** [Release/obj.target/dns_sd_bindings/src/dns_sd.o] Error 1
make: Leaving directory '/usr/local/lib/node_modules/homebridge/node_modules/mdns/build'
gyp ERR! build error 
gyp ERR! stack Error: `make` failed with exit code: 2
gyp ERR! stack     at ChildProcess.onExit (/usr/local/lib/node_modules/npm/node_modules/node-gyp/lib/build.js:258:23)
gyp ERR! stack     at emitTwo (events.js:126:13)
gyp ERR! stack     at ChildProcess.emit (events.js:214:7)
gyp ERR! stack     at Process.ChildProcess._handle.onexit (internal/child_process.js:198:12)
gyp ERR! System Linux 4.14.34-v7+
gyp ERR! command "/usr/local/bin/node" "/usr/local/lib/node_modules/npm/node_modules/node-gyp/bin/node-gyp.js" "rebuild"
gyp ERR! cwd /usr/local/lib/node_modules/homebridge/node_modules/mdns
gyp ERR! node -v v8.11.3
gyp ERR! node-gyp -v v3.6.2
gyp ERR! not ok 
npm ERR! code ELIFECYCLE
npm ERR! errno 1
npm ERR! mdns@2.4.0 install: `node-gyp rebuild`
npm ERR! Exit status 1
npm ERR! 
npm ERR! Failed at the mdns@2.4.0 install script.
npm ERR! This is probably not a problem with npm. There is likely additional logging output above.

npm ERR! A complete log of this run can be found in:
npm ERR!     /root/.npm/_logs/2018-07-14T12_31_28_424Z-debug.log

```


https://stackoverflow.com/questions/19585117/error-dns-sd-h-no-such-file-or-directory
```
$ sudo apt-get install -y libavahi-compat-libdnssd-dev
```

リトライ
```
$ sudo npm install --unsafe-perm mdns

> mdns@2.4.0 install /usr/local/lib/node_modules/homebridge/node_modules/mdns
> node-gyp rebuild

make: Entering directory '/usr/local/lib/node_modules/homebridge/node_modules/mdns/build'
  CXX(target) Release/obj.target/dns_sd_bindings/src/dns_sd.o
  CXX(target) Release/obj.target/dns_sd_bindings/src/dns_service_browse.o
../src/dns_service_browse.cpp: In function ‘void node_mdns::OnServiceChanged(DNSServiceRef, DNSServiceFlags, uint32_t, DNSServiceErrorType, const char*, const char*, const char*, void*)’:
../src/dns_service_browse.cpp:39:50: warning: ‘v8::Local<v8::Value> Nan::MakeCallback(v8::Local<v8::Object>, v8::Local<v8::Function>, int, v8::Local<v8::Value>*)’ is deprecated [-Wdeprecated-declarations]
     Nan::MakeCallback(this_, callback, argc, info);
                                                  ^
In file included from ../src/mdns.hpp:12:0,
                 from ../src/dns_service_browse.cpp:1:
../../nan/nan.h:929:46: note: declared here
   NAN_DEPRECATED inline v8::Local<v8::Value> MakeCallback(
                                              ^~~~~~~~~~~~
  CXX(target) Release/obj.target/dns_sd_bindings/src/dns_service_enumerate_domains.o
../src/dns_service_enumerate_domains.cpp: In function ‘void node_mdns::OnEnumeration(DNSServiceRef, DNSServiceFlags, uint32_t, DNSServiceErrorType, const char*, void*)’:
../src/dns_service_enumerate_domains.cpp:29:50: warning: ‘v8::Local<v8::Value> Nan::MakeCallback(v8::Local<v8::Object>, v8::Local<v8::Function>, int, v8::Local<v8::Value>*)’ is deprecated [-Wdeprecated-declarations]
     Nan::MakeCallback(this_, callback, argc, info);
                                                  ^
In file included from ../src/mdns.hpp:12:0,
                 from ../src/dns_service_enumerate_domains.cpp:1:
../../nan/nan.h:929:46: note: declared here
   NAN_DEPRECATED inline v8::Local<v8::Value> MakeCallback(
                                              ^~~~~~~~~~~~
  CXX(target) Release/obj.target/dns_sd_bindings/src/dns_service_get_addr_info.o
  CXX(target) Release/obj.target/dns_sd_bindings/src/dns_service_process_result.o
  CXX(target) Release/obj.target/dns_sd_bindings/src/dns_service_ref.o
  CXX(target) Release/obj.target/dns_sd_bindings/src/dns_service_ref_deallocate.o
  CXX(target) Release/obj.target/dns_sd_bindings/src/dns_service_ref_sock_fd.o
  CXX(target) Release/obj.target/dns_sd_bindings/src/dns_service_register.o
../src/dns_service_register.cpp: In function ‘void node_mdns::OnServiceRegistered(DNSServiceRef, DNSServiceFlags, DNSServiceErrorType, const char*, const char*, const char*, void*)’:
../src/dns_service_register.cpp:48:54: warning: ‘v8::Local<v8::Value> Nan::MakeCallback(v8::Local<v8::Object>, v8::Local<v8::Function>, int, v8::Local<v8::Value>*)’ is deprecated [-Wdeprecated-declarations]
         Nan::MakeCallback(this_, callback, argc, info);
                                                      ^
In file included from ../src/mdns.hpp:12:0,
                 from ../src/dns_service_register.cpp:1:
../../nan/nan.h:929:46: note: declared here
   NAN_DEPRECATED inline v8::Local<v8::Value> MakeCallback(
                                              ^~~~~~~~~~~~
  CXX(target) Release/obj.target/dns_sd_bindings/src/dns_service_resolve.o
../src/dns_service_resolve.cpp: In function ‘void node_mdns::OnResolve(DNSServiceRef, DNSServiceFlags, uint32_t, DNSServiceErrorType, const char*, const char*, uint16_t, uint16_t, const unsigned char*, void*)’:
../src/dns_service_resolve.cpp:51:50: warning: ‘v8::Local<v8::Value> Nan::MakeCallback(v8::Local<v8::Object>, v8::Local<v8::Function>, int, v8::Local<v8::Value>*)’ is deprecated [-Wdeprecated-declarations]
     Nan::MakeCallback(this_, callback, argc, info);
                                                  ^
In file included from ../src/mdns.hpp:12:0,
                 from ../src/dns_service_resolve.cpp:1:
../../nan/nan.h:929:46: note: declared here
   NAN_DEPRECATED inline v8::Local<v8::Value> MakeCallback(
                                              ^~~~~~~~~~~~
  CXX(target) Release/obj.target/dns_sd_bindings/src/dns_service_update_record.o
  CXX(target) Release/obj.target/dns_sd_bindings/src/mdns_utils.o
  CXX(target) Release/obj.target/dns_sd_bindings/src/network_interface.o
  CXX(target) Release/obj.target/dns_sd_bindings/src/socket_watcher.o
../src/socket_watcher.cpp: In static member function ‘static void node_mdns::SocketWatcher::Callback(uv_poll_t*, int, int)’:
../src/socket_watcher.cpp:100:63: warning: ‘v8::Local<v8::Value> Nan::MakeCallback(v8::Local<v8::Object>, v8::Local<v8::Function>, int, v8::Local<v8::Value>*)’ is deprecated [-Wdeprecated-declarations]
         Nan::MakeCallback(watcher->handle(), callback, 2, argv);
                                                               ^
In file included from ../src/mdns.hpp:12:0,
                 from ../src/socket_watcher.cpp:1:
../../nan/nan.h:929:46: note: declared here
   NAN_DEPRECATED inline v8::Local<v8::Value> MakeCallback(
                                              ^~~~~~~~~~~~
  CXX(target) Release/obj.target/dns_sd_bindings/src/txt_record_ref.o
  CXX(target) Release/obj.target/dns_sd_bindings/src/txt_record_create.o
  CXX(target) Release/obj.target/dns_sd_bindings/src/txt_record_deallocate.o
  CXX(target) Release/obj.target/dns_sd_bindings/src/txt_record_set_value.o
  CXX(target) Release/obj.target/dns_sd_bindings/src/txt_record_get_length.o
  CXX(target) Release/obj.target/dns_sd_bindings/src/txt_record_buffer_to_object.o
  SOLINK_MODULE(target) Release/obj.target/dns_sd_bindings.node
  COPY Release/dns_sd_bindings.node
make: Leaving directory '/usr/local/lib/node_modules/homebridge/node_modules/mdns/build'
+ mdns@2.4.0
added 2 packages in 78.434s
```

ないので
```
cd /usr/local/lib/node_modules/homebridge/node_modules/mdns
$ sudo node-gyp BUILDTYPE=Release rebuild
```

warningはでていたがいけてそう？

```
$ homebridge
```
とすると起動してQRコードがでた


いろいろためした際に
Homeへの追加時に

このアクセサリはすでに追加されています
リセットしてください

といわれた場合



Refference
----------------------------------------------------------------------
