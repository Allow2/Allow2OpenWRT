allow2 for openwrt
==================

This is a first build demonstrating one way to incorporate Allow2 into a router firmware.

This was built and tested with OpenWRT on a Netgear WNDR3700.

Architecture
------------

The solution has been built with 3 primary components.

1.  **allow2d** - daemon process

    User-space daemon responsible for managing the cached settings via the allow2deviceAPI and responding to requests from the kernel module.

2.  **allow2** - kernel module 

    Kernel module responsible for intercepting packets and requesting directions from the userspace component

3.  **liballow2**

    *(under development) - extracted library for leveraging the allow2 platform within other processes*

---

To use the allow2 packages
--------------------------

1.  download and configure the **OpenWrt Buildroot**

    Follow the instructions:

    http://wiki.openwrt.org/doc/howto/build

    (This will be the &lt;openWRTBuildroot> directory)

2.  clone this repo

```sh
    git clone https://github.com/Allow2CEO/allow2openwrt.git
```

    into a suitable location outside of the openwrt home directory.

    (This will be the &lt;Allow2OpenWRT> directory)

3.  link the allow2 packages into the openwrt/packages directory

```sh
      cd &lt;openWRTBuildroot>/Packages

      ln -s &lt;Allow2OpenWRT>/allow2/ .
      ln -s &lt;Allow2OpenWRT>/allow2d/ .
      ln -s &lt;Allow2OpenWRT>/liballow2/ .
```


4.  follow the instructions for building OpenWrt or individual packages

    Use "make menuconfig" to configure the allow2 packages to build:

    * Kernel Modules -> Netfilter Extensions -> kmod-allow2
    * Libraries -> liballow2
    * Utilities -> allow2d

    Alternately, making individual packages would be:

```sh
      make package/allow2/compile
      make package/allow2d/compile
```

5.  Install on your router

3) install luci-allow2

TBA - write this bit

4) add openWRT packages

5) compile

make V=99

6) install on your router

