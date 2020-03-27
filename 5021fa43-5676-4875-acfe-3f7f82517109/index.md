# Using IPv6 autoconfiguration on Debian Linux

## Summary
On Debian 10 and later, IPv6 autoconfiguration is already enabled.   Autoconfiguration will attempt to autoconfigure addresses based on the stateful or stateless autoconfiguration methods already enabled on the network.  More information about available methods is detailed in the RFCs.

## Steps
1. Verify your system is configured for autoconfiguration.  The following lines will be present in `/etc/network/interfaces`.  If they are not present and you decide to add them, you'll need to reboot or ifdown/ifup your network interface after.

        # This is an autoconfigured IPv6 interface
        iface eth0 inet6 auto

1. Run `ip -6 address` to see your current IPv6 addresses.  You should also see a default route with `ip -6 route | grep default`:
        
        # ip -6 address
        1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 state UNKNOWN qlen 1000
        inet6 ::1/128 scope host
        valid_lft forever preferred_lft forever
        2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 state UP qlen 1000
        inet6 2001:db8::4045:4dff:fecc:bae2/64 scope global dynamic mngtmpaddr
        valid_lft 2591660sec preferred_lft 604460sec
        inet6 fd9c:c0cb:ada1:1:4045:4dff:fecc:bae2/64 scope global dynamic mngtmpaddr
        valid_lft 2591660sec preferred_lft 604460sec
        inet6 fe80::4045:4dff:fecc:bae2/64 scope link
        valid_lft forever preferred_lft forever

        # ip -6 route | grep default
        default via fe80::1622:dbff:fea0:1eed dev eth0 proto ra metric 1024 expires     1710sec hoplimit 64 pref medium

If you do not see IPv6 addresses, then your Layer 2 network does not have IPv6 enabled.  Enable it on your network.


*** 
_Mandatory_page_footer: This article and the rest of the [FreeKB](../README.md) is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._


