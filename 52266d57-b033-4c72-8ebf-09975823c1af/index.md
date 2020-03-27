# Enabling IPv6 on CentOS

## Summary
IPv6 can be enabled by editing two files and restarting networking

## Steps
1. Open `/etc/sysctl.conf` and add these lines:

                net.ipv6.conf.default.disable_ipv6 = 0
                net.ipv6.conf.all.disable_ipv6 = 0

1. Open `/etc/sysconfig/network` and add these lines:

                NETWORKING_IPV6=yes
                IPV6_AUTOCONF=yes

1. `service network restart`
1. Run `ip addr` to see your new IPv6 addresses.




*** 
_Mandatory_page_footer: This article and the rest of the [FreeKB](../README.md) is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._


