# How to see IPv4 / IPv6 routes and neighbors

## Summary
There are new commands to see neighbors and routes in IPv6.  In IPv4 ARP was a protocol that mapped Layer 3 (IP) to Layer 2 (MAC).  In IPv6 Neighbor Discovery is used.  

## Steps
### Show the ARP table / Neighbor table
#### Linux
`ip neighbor`.  This shows both IPv4 and IPv6 information.

        192.0.2.195 dev eth0 lladdr 04:d9:f5:1c:45:05 REACHABLE
        192.0.2.1 dev eth0 lladdr 00:e0:67:1f:26:c9 STALE
        192.0.2.27 dev eth0 lladdr 8e:d5:65:35:38:6b REACHABLE
        192.0.2.118 dev eth0 lladdr 3c:28:6d:14:e7:14 STALE
        2001:db8::2e0:67ff:fe1f:26c9 dev eth0 lladdr 00:e0:67:1f:26:c9 router REACHABLE
        fe80::1:1 dev eth0 lladdr 00:e0:67:1f:26:c9 router REACHABLE
        fe80::8c0c:95ff:fec3:c624 dev eth0 lladdr 8e:0c:95:c3:c6:24 STALE
        2001:db8::8c0c:95ff:fec3:c624 dev eth0 lladdr 8e:0c:95:c3:c6:24 STALE

#### Windows
`arp -a` to see v4 ARP table: 

        Interface: 192.0.2.195 --- 0xb
        Internet Address      Physical Address      Type
        192.0.2.1           00-e0-67-1f-26-c9     dynamic
        192.0.2.18          f2-d5-f2-bd-bd-5b     dynamic

`netsh interface ipv6 show neighbors` to show IPv6 neighbors:

        Interface 11: Ethernet


        Internet Address                              Physical Address   Type
        --------------------------------------------  -----------------  -----------
        2001:db8::501                                 8e-d5-65-35-38-6b  Stale
        2001:db8:::2e0:67ff:fe1f:26c9                 00-e0-67-1f-26-c9  Reachable (Router)
        2001:db8:::4045:4dff:fecc:bae2                42-45-4d-cc-ba-e2  Stale
        2001:db8:::8c0c:95ff:fec3:c624                8e-0c-95-c3-c6-24  Stale
        2001:db8:::dea6:32ff:fe17:f63f                dc-a6-32-17-f6-3f  Stale
        fe80::1:1                                     00-e0-67-1f-26-c9  Reachable (Router)
        fe80::4045:4dff:fecc:bae2                     42-45-4d-cc-ba-e2  Stale
        fe80::8c0c:95ff:fec3:c624                     8e-0c-95-c3-c6-24  Stale
        fe80::8cd5:65ff:fe35:386b                     8e-d5-65-35-38-6b  Stale
        ff02::1                                       33-33-00-00-00-01  Permanent
        ff02::2                                       33-33-00-00-00-02  Permanent
        ff02::c                                       33-33-00-00-00-0c  Permanent
        ff02::16                                      33-33-00-00-00-16  Permanent

### Show the routing table
#### Linux
IPv4: `ip route`

        default via 192.0.2.1 dev eth0
        192.0.2.0/24 dev eth0 proto kernel scope link src 192.0.2.226

IPv6: `ip -6 route`

        ::1 dev lo proto kernel metric 256 pref medium
        2001:db8::/64 dev eth0 proto kernel metric 256 expires 86388sec pref medium
        fe80::/64 dev eth0 proto kernel metric 256 pref medium
        default via fe80::1:1 dev eth0 proto ra metric 1024 expires 48sec hoplimit 64 pref medium

#### Windows
IPv4 & IPv6: `route print`
```
===========================================================================
Interface List
 11...04 d9 f5 1c 45 05 ......Realtek PCIe GbE Family Controller
  5...5c f3 70 8a 12 67 ......Bluetooth Device (Personal Area Network)
  1...........................Software Loopback Interface 1
===========================================================================

IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.0.2.1    192.0.2.195     25
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    331
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    331
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    331
        192.0.2.0    255.255.255.0         On-link       192.0.2.195    281
      192.0.2.195  255.255.255.255         On-link       192.0.2.195    281
      192.0.2.255  255.255.255.255         On-link       192.0.2.195    281
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    331
        224.0.0.0        240.0.0.0         On-link       192.0.2.195    281
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    331
  255.255.255.255  255.255.255.255         On-link       192.0.2.195    281
===========================================================================
Persistent Routes:
  None

IPv6 Route Table
===========================================================================
Active Routes:
 If Metric Network Destination      Gateway
 11    281 ::/0                     fe80::1:1
  1    331 ::1/128                  On-link
 11    281 2001:db8::/64            On-link
 11    281 2001:db8::142a:a8c1:f69b:a30b/128
                                    On-link
 11    281 2001:db8::7c2b:e56e:311f:83e2/128
                                    On-link
 11    281 fe80::/64                On-link
 11    281 fe80::142a:a8c1:f69b:a30b/128
                                    On-link
  1    331 ff00::/8                 On-link
 11    281 ff00::/8                 On-link
===========================================================================
Persistent Routes:
  None
```


*** 
_Mandatory_page_footer: This article and the rest of the [FreeKB](../README.md) is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._


