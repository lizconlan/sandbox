---
layout: post
title: Inserting a Couch into OS X
categories: 
- mac os
- couchdb
- tech
description: Install CouchDB on Mac OS X
keywords: couchdb,database,installation,mac os,howto,guide,couch
---


(or how to install CouchDB on Mac OS X from source if you prefer)

First things first - your best (and simplest) bet is to use [CouchDB X](http://janl.github.com/couchdbx/ "CouchDB X")

Only come back here and do the boring thing if, like what happened to me, that doesn't work on your machine

(oh and where you see make `-j2` the 2 refers to the number of cores available, mine has 2 - adjust your command string to suit)

### Install Spidermonkey

Download [the Spidermonkey js source](http://ftp.mozilla.org/pub/mozilla.org/js/js-1.7.0.tar.gz "Spidermonkey tarball")
Untar/zip and navigate to the src subdirectory in Terminal

```
make -f Makefile.ref
sudo cp Darwin_DBG.OBJ/js /usr/local/bin
sudo mkdir -p /usr/include/smjs/
sudo cp *.{h,tbl} /usr/include/smjs/
cd Darwin_DBG.OBJ
sudo cp *.h /usr/include/smjs/
sudo cp js /usr/local/bin/
sudo cp libjs.dylib /usr/local/lib/
```

### Install Erlang

Download [the Erlang source](http://erlang.org/download/otp_src_R13B04.tar.gz "Erlang tarball")
Untar/zip and navigate to the relevant directory in Terminal

```
./configure --enable-hipe
make -j2
sudo make install
```

### Install ICU

Download [the ICU source (ICU tarball)](http://download.icu-project.org/files/icu4c/4.4/icu4c-4_4-src.tgz)
Untar/zip and navigate to the source subdirectory in Terminal

```
chmod +x runConfigureICU configure install-sh
./runConfigureICU MacOSX
make -j2
sudo make install
```

### Install CouchDB

Download [the CouchDB source (CouchDB tarball)](http://www.apache.org/dyn/closer.cgi?path=/couchdb/0.11.0/apache-couchdb-0.11.0.tar.gz)
Untar/zip and navigate to the relevant directory in Terminal

```
./configure --with-js-include=/usr/include/smjs --with-js-lib=/usr/local/lib
make -j2
sudo make install
```

### Configure

To be honest, I haven't managed to get this bit to work so if (when?) all else fails just use this whenever you want to spin up couch:

```
sudo couchdb -b
```

Proper configuration for autoload **should** be something like:

```
sudo cp ~/src/org.apache.couchdb.plist /Library/LaunchDaemons
sudo chown root /Library/LaunchDaemons/org.apache.couchdb.plist
sudo launchctl load -w /Library/LaunchDaemons/org.apache.couchdb.plist
```