# Setting a static IPv6 address on Debian Linux

## Summary
There are a variety of methods in IPv6 to assign an address to a server.   Manually configuring the address is one method.

## Steps
1. Edit `/etc/network/interfaces` and add the following lines.  **Set the `address` line to the appropriate IPv6 address.**  You do not need to specify the default gateway, it will be grabbed automatically from Router Advertisements.

        iface eth0 inet6 static
        address 2001:db8::1234
        netmask 64

1. Run the following commands.  Alternatively, you can simply reboot.   **Either of these will disrupt connectivity to the machine!** 
        
        screen -S ipv6
        ifdown eth0
        ifup eth0

1. Run `ip -6 address` to see your current IPv6 addresses.  You should also see a default route with `ip -6 route | grep default`:

        # ip -6 address
        1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 state UNKNOWN qlen 1000
        inet6 ::1/128 scope host
        valid_lft forever preferred_lft forever
        2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 state UP qlen 1000
        inet6 2001:db8::1234/64 scope global
        valid_lft forever preferred_lft forever
        inet6 fe80::8cce:51ff:fe4d:b584/64 scope link
        valid_lft forever preferred_lft forever
        
        # ip -6 route | grep default
        default via fe80::209:fff:fed8:6703 dev eth0 proto ra metric 1024 expires 1757sec pref medium


***
_Mandatory_page_footer: This article and the rest of the FreeKB is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._

