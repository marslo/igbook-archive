<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

    - [devops-kubernetes-02](#devops-kubernetes-02)
        - [/etc/network/interface](#etcnetworkinterface)
- [broadcast 130.147.219.127](#broadcast-130147219127)
- [network 130.147.219.0](#network-1301472190)
- [iface eno3 inet dhcp](#iface-eno3-inet-dhcp)
- [auto eno3](#auto-eno3)
- [iface eno3 inet static](#iface-eno3-inet-static)
- [address 192.168.11.121](#address-19216811121)
- [netmask 255.255.254.0](#netmask-2552552540)
- [gateway 192.168.10.1](#gateway-192168101)
- [dns-nameservers 61.139.2.69 218.6.200.139](#dns-nameservers-61139269-2186200139)
        - [network info](#network-info)
- [<pre><code>$ nmcli -p d show eno1](#precode-nmcli-p-d-show-eno1)
    - [GENERAL.DEVICE:                         eno1](#generaldevice-eno1)
    - [GENERAL.TYPE:                           ethernet](#generaltype-ethernet)
    - [GENERAL.HWADDR:                         C4:34:6B:BA:31:8C](#generalhwaddr-c4346bba318c)
    - [GENERAL.MTU:                            1500](#generalmtu-1500)
    - [GENERAL.STATE:                          10 (unmanaged)](#generalstate-10-unmanaged)
    - [GENERAL.CONNECTION:                     --](#generalconnection)
    - [GENERAL.CON-PATH:                       --](#generalcon-path)
    - [WIRED-PROPERTIES.CARRIER:               on](#wired-propertiescarrier-on)
    - [IP4.ROUTE[19]:                          dst = 161.88.0.0/16, nh = 0.0.0.0, mt = 0](#ip4route19-dst-161880016-nh-0000-mt-0)
    - [IP6.GATEWAY:                            --](#ip6gateway)
- [$ nmcli -p device show eno3](#nmcli-p-device-show-eno3)
    - [GENERAL.DEVICE:                         eno3](#generaldevice-eno3)
    - [GENERAL.TYPE:                           ethernet](#generaltype-ethernet-1)
    - [GENERAL.HWADDR:                         C4:34:6B:BA:31:8E](#generalhwaddr-c4346bba318e)
    - [GENERAL.MTU:                            1500](#generalmtu-1500-1)
    - [GENERAL.STATE:                          10 (unmanaged)](#generalstate-10-unmanaged-1)
    - [GENERAL.CONNECTION:                     --](#generalconnection-1)
    - [GENERAL.CON-PATH:                       --](#generalcon-path-1)
    - [WIRED-PROPERTIES.CARRIER:               on](#wired-propertiescarrier-on-1)
    - [IP4.GATEWAY:                            192.168.10.1](#ip4gateway-192168101)
    - [IP6.GATEWAY:                            --](#ip6gateway-1)
- [$ nmcli -p device show](#nmcli-p-device-show)
    - [GENERAL.DEVICE:                         eno2](#generaldevice-eno2)
    - [GENERAL.TYPE:                           ethernet](#generaltype-ethernet-2)
    - [GENERAL.HWADDR:                         C4:34:6B:BA:31:8D](#generalhwaddr-c4346bba318d)
    - [GENERAL.MTU:                            1500](#generalmtu-1500-2)
    - [GENERAL.STATE:                          20 (unavailable)](#generalstate-20-unavailable)
    - [GENERAL.CONNECTION:                     --](#generalconnection-2)
    - [GENERAL.CON-PATH:                       --](#generalcon-path-2)
    - [WIRED-PROPERTIES.CARRIER:               off](#wired-propertiescarrier-off)
    - [GENERAL.DEVICE:                         eno4](#generaldevice-eno4)
    - [GENERAL.TYPE:                           ethernet](#generaltype-ethernet-3)
    - [GENERAL.HWADDR:                         C4:34:6B:BA:31:8F](#generalhwaddr-c4346bba318f)
    - [GENERAL.MTU:                            1500](#generalmtu-1500-3)
    - [GENERAL.STATE:                          20 (unavailable)](#generalstate-20-unavailable-1)
    - [GENERAL.CONNECTION:                     --](#generalconnection-3)
    - [GENERAL.CON-PATH:                       --](#generalcon-path-3)
    - [WIRED-PROPERTIES.CARRIER:               off](#wired-propertiescarrier-off-1)
    - [GENERAL.DEVICE:                         eno1](#generaldevice-eno1-1)
    - [GENERAL.TYPE:                           ethernet](#generaltype-ethernet-4)
    - [GENERAL.HWADDR:                         C4:34:6B:BA:31:8C](#generalhwaddr-c4346bba318c-1)
    - [GENERAL.MTU:                            1500](#generalmtu-1500-4)
    - [GENERAL.STATE:                          10 (unmanaged)](#generalstate-10-unmanaged-2)
    - [GENERAL.CONNECTION:                     --](#generalconnection-4)
    - [GENERAL.CON-PATH:                       --](#generalcon-path-4)
    - [WIRED-PROPERTIES.CARRIER:               on](#wired-propertiescarrier-on-2)
    - [IP4.ROUTE[19]:                          dst = 161.88.0.0/16, nh = 0.0.0.0, mt = 0](#ip4route19-dst-161880016-nh-0000-mt-0-1)
    - [IP6.GATEWAY:                            --](#ip6gateway-2)
    - [GENERAL.DEVICE:                         eno3](#generaldevice-eno3-1)
    - [GENERAL.TYPE:                           ethernet](#generaltype-ethernet-5)
    - [GENERAL.HWADDR:                         C4:34:6B:BA:31:8E](#generalhwaddr-c4346bba318e-1)
    - [GENERAL.MTU:                            1500](#generalmtu-1500-5)
    - [GENERAL.STATE:                          10 (unmanaged)](#generalstate-10-unmanaged-3)
    - [GENERAL.CONNECTION:                     --](#generalconnection-5)
    - [GENERAL.CON-PATH:                       --](#generalcon-path-5)
    - [WIRED-PROPERTIES.CARRIER:               on](#wired-propertiescarrier-on-3)
    - [IP4.GATEWAY:                            192.168.10.1](#ip4gateway-192168101-1)
    - [IP6.GATEWAY:                            --](#ip6gateway-3)
    - [GENERAL.DEVICE:                         lo](#generaldevice-lo)
    - [GENERAL.TYPE:                           loopback](#generaltype-loopback)
    - [GENERAL.HWADDR:                         00:00:00:00:00:00](#generalhwaddr-000000000000)
    - [GENERAL.MTU:                            65536](#generalmtu-65536)
    - [GENERAL.STATE:                          10 (unmanaged)](#generalstate-10-unmanaged-4)
    - [GENERAL.CONNECTION:                     --](#generalconnection-6)
    - [GENERAL.CON-PATH:                       --](#generalcon-path-6)
    - [IP4.GATEWAY:                            --](#ip4gateway)
    - [IP6.GATEWAY:                            --](#ip6gateway-4)
        - [Route Details](#route-details)
    - [devops-kubernetes-03](#devops-kubernetes-03)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## devops-kubernetes-02
### /etc/network/interface

    $ cat /etc/network/interfaces
    auto lo
    iface lo inet loopback

    auto eno1
    iface eno1 inet static
      address 130.147.180.86
      netmask 255.255.255.192
      gateway 130.147.180.65
      dns-nameservers 130.147.236.5 161.92.35.78
      dns-search cn-132.lan.philips.com

    auto eno3
      iface eno3 inet static

<details><summary>Click to check details</summary>
<pre><code>$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eno1
iface eno1 inet static
  address 130.147.180.86
  netmask 255.255.255.192
  gateway 130.147.180.65
  dns-nameservers 130.147.236.5 161.92.35.78
  dns-search cn-132.lan.philips.com
  # broadcast 130.147.219.127
  # network 130.147.219.0

auto eno3
# iface eno3 inet dhcp
# auto eno3
# iface eno3 inet static
  # address 192.168.11.121
  # netmask 255.255.254.0
  # gateway 192.168.10.1
  # dns-nameservers 61.139.2.69 218.6.200.139
</code></pre>
</details>


### network info

    $ nmcli [-p] d[evice] show <interface>

<details><summary>Click to check details</summary>
<pre><code>$ nmcli -p d show eno1
===============================================================================
                             Device details (eno1)
===============================================================================
GENERAL.DEVICE:                         eno1
-------------------------------------------------------------------------------
GENERAL.TYPE:                           ethernet
-------------------------------------------------------------------------------
GENERAL.HWADDR:                         C4:34:6B:BA:31:8C
-------------------------------------------------------------------------------
GENERAL.MTU:                            1500
-------------------------------------------------------------------------------
GENERAL.STATE:                          10 (unmanaged)
-------------------------------------------------------------------------------
GENERAL.CONNECTION:                     --
-------------------------------------------------------------------------------
GENERAL.CON-PATH:                       --
-------------------------------------------------------------------------------
WIRED-PROPERTIES.CARRIER:               on
-------------------------------------------------------------------------------
IP4.ADDRESS[1]:                         130.147.180.86/26
IP4.GATEWAY:                            --
IP4.ROUTE[1]:                           dst = 161.92.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[2]:                           dst = 130.145.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[3]:                           dst = 180.166.223.190/32, nh = 130.147.180.65, mt = 0
IP4.ROUTE[4]:                           dst = 185.46.212.34/32, nh = 130.147.180.65, mt = 0
IP4.ROUTE[5]:                           dst = 130.140.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[6]:                           dst = 130.147.236.5/32, nh = 130.147.180.65, mt = 0
IP4.ROUTE[7]:                           dst = 130.147.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[8]:                           dst = 161.91.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[9]:                           dst = 161.84.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[10]:                          dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.ROUTE[11]:                          dst = 185.166.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[12]:                          dst = 130.146.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[13]:                          dst = 137.55.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[14]:                          dst = 161.83.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[15]:                          dst = 42.99.164.34/32, nh = 130.147.180.65, mt = 0
IP4.ROUTE[16]:                          dst = 161.85.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[17]:                          dst = 161.92.35.78/32, nh = 130.147.180.65, mt = 0
IP4.ROUTE[18]:                          dst = 140.207.91.234/32, nh = 130.147.180.65, mt = 0
IP4.ROUTE[19]:                          dst = 161.88.0.0/16, nh = 0.0.0.0, mt = 0
-------------------------------------------------------------------------------
IP6.ADDRESS[1]:                         fe80::c634:6bff:feba:318c/64
IP6.GATEWAY:                            --
-------------------------------------------------------------------------------

$ nmcli -p device show eno3
===============================================================================
                             Device details (eno3)
===============================================================================
GENERAL.DEVICE:                         eno3
-------------------------------------------------------------------------------
GENERAL.TYPE:                           ethernet
-------------------------------------------------------------------------------
GENERAL.HWADDR:                         C4:34:6B:BA:31:8E
-------------------------------------------------------------------------------
GENERAL.MTU:                            1500
-------------------------------------------------------------------------------
GENERAL.STATE:                          10 (unmanaged)
-------------------------------------------------------------------------------
GENERAL.CONNECTION:                     --
-------------------------------------------------------------------------------
GENERAL.CON-PATH:                       --
-------------------------------------------------------------------------------
WIRED-PROPERTIES.CARRIER:               on
-------------------------------------------------------------------------------
IP4.ADDRESS[1]:                         192.168.11.121/23
IP4.GATEWAY:                            192.168.10.1
-------------------------------------------------------------------------------
IP6.ADDRESS[1]:                         fe80::c634:6bff:feba:318e/64
IP6.GATEWAY:                            --
-------------------------------------------------------------------------------

$ nmcli -p device show
===============================================================================
                             Device details (eno2)
===============================================================================
GENERAL.DEVICE:                         eno2
-------------------------------------------------------------------------------
GENERAL.TYPE:                           ethernet
-------------------------------------------------------------------------------
GENERAL.HWADDR:                         C4:34:6B:BA:31:8D
-------------------------------------------------------------------------------
GENERAL.MTU:                            1500
-------------------------------------------------------------------------------
GENERAL.STATE:                          20 (unavailable)
-------------------------------------------------------------------------------
GENERAL.CONNECTION:                     --
-------------------------------------------------------------------------------
GENERAL.CON-PATH:                       --
-------------------------------------------------------------------------------
WIRED-PROPERTIES.CARRIER:               off
-------------------------------------------------------------------------------

===============================================================================
                             Device details (eno4)
===============================================================================
GENERAL.DEVICE:                         eno4
-------------------------------------------------------------------------------
GENERAL.TYPE:                           ethernet
-------------------------------------------------------------------------------
GENERAL.HWADDR:                         C4:34:6B:BA:31:8F
-------------------------------------------------------------------------------
GENERAL.MTU:                            1500
-------------------------------------------------------------------------------
GENERAL.STATE:                          20 (unavailable)
-------------------------------------------------------------------------------
GENERAL.CONNECTION:                     --
-------------------------------------------------------------------------------
GENERAL.CON-PATH:                       --
-------------------------------------------------------------------------------
WIRED-PROPERTIES.CARRIER:               off
-------------------------------------------------------------------------------

===============================================================================
                             Device details (eno1)
===============================================================================
GENERAL.DEVICE:                         eno1
-------------------------------------------------------------------------------
GENERAL.TYPE:                           ethernet
-------------------------------------------------------------------------------
GENERAL.HWADDR:                         C4:34:6B:BA:31:8C
-------------------------------------------------------------------------------
GENERAL.MTU:                            1500
-------------------------------------------------------------------------------
GENERAL.STATE:                          10 (unmanaged)
-------------------------------------------------------------------------------
GENERAL.CONNECTION:                     --
-------------------------------------------------------------------------------
GENERAL.CON-PATH:                       --
-------------------------------------------------------------------------------
WIRED-PROPERTIES.CARRIER:               on
-------------------------------------------------------------------------------
IP4.ADDRESS[1]:                         130.147.180.86/26
IP4.GATEWAY:                            --
IP4.ROUTE[1]:                           dst = 161.92.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[2]:                           dst = 130.145.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[3]:                           dst = 180.166.223.190/32, nh = 130.147.180.65, mt = 0
IP4.ROUTE[4]:                           dst = 185.46.212.34/32, nh = 130.147.180.65, mt = 0
IP4.ROUTE[5]:                           dst = 130.140.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[6]:                           dst = 130.147.236.5/32, nh = 130.147.180.65, mt = 0
IP4.ROUTE[7]:                           dst = 130.147.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[8]:                           dst = 161.91.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[9]:                           dst = 161.84.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[10]:                          dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.ROUTE[11]:                          dst = 185.166.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[12]:                          dst = 130.146.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[13]:                          dst = 137.55.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[14]:                          dst = 161.83.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[15]:                          dst = 42.99.164.34/32, nh = 130.147.180.65, mt = 0
IP4.ROUTE[16]:                          dst = 161.85.0.0/16, nh = 0.0.0.0, mt = 0
IP4.ROUTE[17]:                          dst = 161.92.35.78/32, nh = 130.147.180.65, mt = 0
IP4.ROUTE[18]:                          dst = 140.207.91.234/32, nh = 130.147.180.65, mt = 0
IP4.ROUTE[19]:                          dst = 161.88.0.0/16, nh = 0.0.0.0, mt = 0
-------------------------------------------------------------------------------
IP6.ADDRESS[1]:                         fe80::c634:6bff:feba:318c/64
IP6.GATEWAY:                            --
-------------------------------------------------------------------------------

===============================================================================
                             Device details (eno3)
===============================================================================
GENERAL.DEVICE:                         eno3
-------------------------------------------------------------------------------
GENERAL.TYPE:                           ethernet
-------------------------------------------------------------------------------
GENERAL.HWADDR:                         C4:34:6B:BA:31:8E
-------------------------------------------------------------------------------
GENERAL.MTU:                            1500
-------------------------------------------------------------------------------
GENERAL.STATE:                          10 (unmanaged)
-------------------------------------------------------------------------------
GENERAL.CONNECTION:                     --
-------------------------------------------------------------------------------
GENERAL.CON-PATH:                       --
-------------------------------------------------------------------------------
WIRED-PROPERTIES.CARRIER:               on
-------------------------------------------------------------------------------
IP4.ADDRESS[1]:                         192.168.11.121/23
IP4.GATEWAY:                            192.168.10.1
-------------------------------------------------------------------------------
IP6.ADDRESS[1]:                         fe80::c634:6bff:feba:318e/64
IP6.GATEWAY:                            --
-------------------------------------------------------------------------------

===============================================================================
                              Device details (lo)
===============================================================================
GENERAL.DEVICE:                         lo
-------------------------------------------------------------------------------
GENERAL.TYPE:                           loopback
-------------------------------------------------------------------------------
GENERAL.HWADDR:                         00:00:00:00:00:00
-------------------------------------------------------------------------------
GENERAL.MTU:                            65536
-------------------------------------------------------------------------------
GENERAL.STATE:                          10 (unmanaged)
-------------------------------------------------------------------------------
GENERAL.CONNECTION:                     --
-------------------------------------------------------------------------------
GENERAL.CON-PATH:                       --
-------------------------------------------------------------------------------
IP4.ADDRESS[1]:                         127.0.0.1/8
IP4.GATEWAY:                            --
-------------------------------------------------------------------------------
IP6.ADDRESS[1]:                         ::1/128
IP6.GATEWAY:                            --
-------------------------------------------------------------------------------
</code></pre>
</details>

### Route Details

    $ route -n
    Kernel IP routing table
    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
    0.0.0.0         192.168.10.1    0.0.0.0         UG    100    0        0 eno3
    42.99.164.34    130.147.180.65  255.255.255.255 UGH   0      0        0 eno1
    130.140.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eno1
    130.145.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eno1
    130.146.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eno1
    130.147.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eno1
    130.147.180.64  0.0.0.0         255.255.255.192 U     0      0        0 eno1
    130.147.236.5   130.147.180.65  255.255.255.255 UGH   0      0        0 eno1
    137.55.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eno1
    140.207.91.234  130.147.180.65  255.255.255.255 UGH   0      0        0 eno1
    161.83.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eno1
    161.84.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eno1
    161.85.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eno1
    161.88.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eno1
    161.91.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eno1
    161.92.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eno1
    161.92.35.78    130.147.180.65  255.255.255.255 UGH   0      0        0 eno1
    169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eno1
    180.166.223.190 130.147.180.65  255.255.255.255 UGH   0      0        0 eno1
    185.46.212.34   130.147.180.65  255.255.255.255 UGH   0      0        0 eno1
    185.166.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eno1
    192.168.10.0    0.0.0.0         255.255.254.0   U     100    0        0 eno3

## devops-kubernetes-03

      $ ifconfig en1
      en1: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
        ether 6c:96:cf:f2:01:0a
        inet6 fe80::81d:93a6:a4d4:32c2%en1 prefixlen 64 secured scopeid 0x6
        inet 192.168.10.124 netmask 0xfffffe00 broadcast 192.168.11.255
        nd6 options=201<PERFORMNUD,DAD>
        media: autoselect
        status: active

      $ ifconfig en0
      en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
        options=10b<RXCSUM,TXCSUM,VLAN_HWTAGGING,AV>
        ether 78:7b:8a:bc:c2:3c
        inet6 fe80::1843:dfe3:4c35:c38%en0 prefixlen 64 secured scopeid 0x5
        inet 130.147.182.248 netmask 0xfffffe00 broadcast 130.147.183.255
        nd6 options=201<PERFORMNUD,DAD>
        media: autoselect (100baseTX <full-duplex>)
        status: active


      $ ifconfig
      lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
        options=1203<RXCSUM,TXCSUM,TXSTATUS,SW_TIMESTAMP>
        inet 127.0.0.1 netmask 0xff000000
        inet6 ::1 prefixlen 128
        inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1
        nd6 options=201<PERFORMNUD,DAD>
      gif0: flags=8010<POINTOPOINT,MULTICAST> mtu 1280
      stf0: flags=0<> mtu 1280
      XHC20: flags=0<> mtu 0
      en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
        options=10b<RXCSUM,TXCSUM,VLAN_HWTAGGING,AV>
        ether 78:7b:8a:bc:c2:3c
        inet6 fe80::1843:dfe3:4c35:c38%en0 prefixlen 64 secured scopeid 0x5
        inet 130.147.182.248 netmask 0xfffffe00 broadcast 130.147.183.255
        nd6 options=201<PERFORMNUD,DAD>
        media: autoselect (100baseTX <full-duplex>)
        status: active
      en1: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
        ether 6c:96:cf:f2:01:0a
        inet6 fe80::81d:93a6:a4d4:32c2%en1 prefixlen 64 secured scopeid 0x6
        inet 192.168.10.124 netmask 0xfffffe00 broadcast 192.168.11.255
        nd6 options=201<PERFORMNUD,DAD>
        media: autoselect
        status: active
      en2: flags=8963<UP,BROADCAST,SMART,RUNNING,PROMISC,SIMPLEX,MULTICAST> mtu 1500
        options=60<TSO4,TSO6>
        ether 2a:00:02:31:1e:a0
        media: autoselect <full-duplex>
        status: inactive
      en3: flags=8963<UP,BROADCAST,SMART,RUNNING,PROMISC,SIMPLEX,MULTICAST> mtu 1500
        options=60<TSO4,TSO6>
        ether 2a:00:02:31:1e:a1
        media: autoselect <full-duplex>
        status: inactive
      bridge0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
        options=63<RXCSUM,TXCSUM,TSO4,TSO6>
        ether 2a:00:02:31:1e:a0
        Configuration:
          id 0:0:0:0:0:0 priority 0 hellotime 0 fwddelay 0
          maxage 0 holdcnt 0 proto stp maxaddr 100 timeout 1200
          root id 0:0:0:0:0:0 priority 0 ifcost 0 port 0
          ipfilter disabled flags 0x2
        member: en2 flags=3<LEARNING,DISCOVER>
                ifmaxaddr 0 port 7 priority 0 path cost 0
        member: en3 flags=3<LEARNING,DISCOVER>
                ifmaxaddr 0 port 8 priority 0 path cost 0
        nd6 options=201<PERFORMNUD,DAD>
        media: <unknown type>
        status: inactive
      p2p0: flags=8843<UP,BROADCAST,RUNNING,SIMPLEX,MULTICAST> mtu 2304
        ether 0e:96:cf:f2:01:0a
        media: autoselect
        status: inactive
      awdl0: flags=8943<UP,BROADCAST,RUNNING,PROMISC,SIMPLEX,MULTICAST> mtu 1484
        ether 6e:66:62:10:bb:fa
        inet6 fe80::6c66:62ff:fe10:bbfa%awdl0 prefixlen 64 scopeid 0xb
        nd6 options=201<PERFORMNUD,DAD>
        media: autoselect
        status: active
      utun0: flags=8051<UP,POINTOPOINT,RUNNING,MULTICAST> mtu 2000
        inet6 fe80::2c33:8275:3276:346f%utun0 prefixlen 64 scopeid 0xc
        nd6 options=201<PERFORMNUD,DAD>
