## Ubuntu 编译
```
apt install -y libcurl4-openssl-dev libevent-dev \
                ca-certificates libssl-dev pkg-config \
                build-essential intltool libgcrypt-dev \
                libssl-dev libxml2-dev \
                libc-ares-dev  libssl-dev libsqlite3-dev \
                libssh2-1-dev \
                lzma liblzma-dev libicu-dev zlib1g-dev 

apt-get install autopoint -y && apt-get install libtool -y && pip install sphinx


git clone https://github.com/362227/aria2-build-msys2
cd aria2-build-msys2 && bash build-aria2.sh

chmod +x /root/aria2-build-msys2/aria2/src/aria2c
mv /root/aria2-build-msys2/aria2/src/aria2c /usr/bin/
```



## Readme
aria2 build scripts for `msys2` with custom patches.

### Build Status
[![Build status](https://ci.appveyor.com/api/projects/status/fndjci8g5f71gf6l?svg=true)](https://ci.appveyor.com/project/myfreeer/aria2-build-msys2)

### License
[![GitHub license](https://img.shields.io/github/license/myfreeer/aria2-build-msys2.svg)](LICENSE) 

### Changes
* option `max-connection-per-server`: change maximum value to `*`, default value to `16`
* option `min-split-size`: change minimum value to `1K`, default value to `1M`
* option `piece-length`: change minimum value to `1K`, default value to `1M`
* option `connect-timeout`: change default value to `30`
* option `split`: change default value to `128`
* option `continue`: change default value to `true`
* option `retry-wait`: change default value to `1`
* option `max-concurrent-downloads`: change default value to `16`
* option `netrc-path` `conf-path` `dht-file-path` `dht-file-path6`: change default value to sub-folder of current directory
* option `deamon`: make use of it on mingw
* download: retry on slow speed and connection close
* download: add option `retry-on-400` to retry on http 400 bad request, which only effective if retry-wait > 0
* download: add option `retry-on-403` to retry on http 403 forbidden, which only effective if retry-wait > 0
* download: add option `retry-on-406` to retry on http 406 not acceptable, which only effective if retry-wait > 0
* http: add option `http-want-digest` to choose whether to send the generated `Want-Digest` HTTP header or not ([#10](https://github.com/myfreeer/aria2-build-msys2/issues/10)

### Environment 
[MSYS2](http://www.msys2.org/)
Should be set up with commands below:
```sh
pacman -Syyuu --noconfirm
pacman -Su --noconfirm
pacman -S --noconfirm --needed base-devel zlib-devel sqlite git unzip zip tar gmp gmp-devel libssh2 libssh2-devel openssl-devel
```

### Artifacts
* x86_64 (64-bits) version: [![aria2c.7z](https://img.shields.io/badge/download-aria2c.7z-brightgreen.svg)](https://ci.appveyor.com/api/projects/myfreeer/aria2-build-msys2/artifacts/aria2c.7z)
* x86 (32-bits) version: [![aria2c_x86.7z](https://img.shields.io/badge/download-aria2c_x86.7z-brightgreen.svg)](https://ci.appveyor.com/api/projects/myfreeer/aria2-build-msys2/artifacts/aria2c_x86.7z)

### Credits
* https://github.com/aria2/aria2
* https://gist.github.com/zhangyubaka/fb56f6bf9be50dbd28e64809cdc659be
* https://github.com/jb-alvarado/media-autobuild_suite
