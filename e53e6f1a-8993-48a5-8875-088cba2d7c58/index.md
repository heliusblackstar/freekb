# Introduction to IPv6

## Summary
IPv6 offers a publically routable address for every node, and introduces a variety of completely new concepts, mechanisms, things-that-must-be-true, and protocols.

## Source materials
If you read nothing further in this article, read this:  
You should go read RFC7368 ("IPv6 Home Networking Architecture Principles").  It's a great general introduction to IPv6 and links to many other articles that will help introduce you to how IPv6 is designed and works.  It also frames the introduction in the context of a simple-to-understand home network.

## Major features and changes in contrast to IPv4
### Ping packets (ICMPv6 Echo Requests) cannot be dropped by firewalls and all nodes MUST respond to ping
Ping is reliable again!  Hooray!

In this context, "MUST" means:
>This word, or the terms "REQUIRED" or "SHALL", mean that the definition is an absolute requirement of the specification." (RFC2119).

Doesn't mean the OS needs to include a "ping" utility, just that it is required to respond to pings per the ICMPv6 standard (RFC4443 section 4.1), and that ping packets transiting a firewall "Must Not Be Dropped" (RFC4890 section 4.2.1).
### NAT is eradicated!   
NAT was not a security feature (RFC2775 section 3.4).  
NAT was NEVER desirable but was a itself a horrible band-aid created to solve the egregious address shortage in IPv4.    
IPv6 solves both these two problems (lack of addresses and NAT).  IPv6 has plenty of addresses and therefore NAT and all the headaches it introduced are eliminated (RFC7368, section 2.2).  Addresses are NOT altered by NAT in transit thru a firewall.  Global Unicast Addresses will exist on both sides of a firewall, both the external and internal interfaces.

Note, that firewalls still exist--you can still have firewall policies that allow or deny traffic, either on the device, or at the network perimeter.

### Subnetting is gone!
The standard prefix for all networks that contain nodes is a /64.  

A /64 network prefix (which has **more than trillions of addresses** on it (specifically 2^64)) is recommended and acceptable even for networks which only have 2 devices (and this leaves plenty of room for growth later).  So whether the network will have 2 devices or more than 2 trillion, the prefix length is /64 (RFC7421):

        The de facto length of almost all IPv6 interface identifiers is therefore 64 bits.  The only documented exception is in [RFC6164], which  standardizes 127-bit prefixes for point-to-point links between routers,  among other things, to avoid a loop condition known as the ping-pong problem.

The only two valid prefix lengths for networks which contain nodes are a /64 and a /127.  Any other length violates the IPv6 standard and breaks SLAAC as well as other IPv6 protocols (RFC7421 section 4.1 actually attempts to show how many IPv6 protocols are built on the /64 prefix size).

### The IPv6 address space is mind-bogglingly expansive
To oversimply it, the size of the IPv4 address space is 2^32.  
2^33 would be twice as large as that.  2^34 would be twice as large as that.  IPv6 is 2^128.

The size difference in address space between IPv4 and IPv6 is so incredibly vast that it's actually quite difficult to convey how much larger the IPv6 address space is.  Much like we said before, we can say, "this should be enough addresses for a very long time".

### Global Unicast Addresses are abundant and everyone gets them!  
There are enough Global Unicast Addresses (similar to "Public IPs" in IPv4 parlance) for every device interface on every device.  Every server, every client, every device, there's enough for everything and everyone. 

Even home users are recommended to be assigned **at least** a /56, which is 256 networks (256 /64 prefixes), giving them 256 separate networks, each which can hold more than trillions of devices.  Home users may also be assigned a /48, which is 65,536 /64 networks, each containing more than trillions of addresses.

A single /64, has 2^64 (18,446,744,073,709,551,616) Global Unicast addresses.
The Global Unicast addresses in use are visible from the device's OS (simple!), so seeing a device's "public" address does not involve having to cross-reference a device's private IP with a firewall public/private NAT configuration like in IPv4.

### Firewalls can be set to simply passthru incoming IPv6 traffic, allowing simple inbound connectivity for any apps or services without any extra signaling protocol or manual firewall configuration.  
As the RFCs state, do not confuse "addressability with reachability".  
To quote RFC7368:

        An IPv6-based home network architecture should embrace the transparent end-to-end communications model as described in [RFC2775].  Each device should be globally addressable, and those addresses must not be altered in transit.  However, security perimeters can be applied to restrict end-to-end communications, and thus while a host may be globally addressable, it may not be globally reachable.
        [...]
        whether devices are globally reachable or not would depend on any firewall or filtering configuration, and not, as is commonly the case with IPv4, the presence or use of NAT.  In this respect, IPv6 networks may or may not have filters applied at their borders to control such traffic, i.e., at the homenet CE router.  [RFC4864] and [RFC6092] discuss such filtering and the merits of 'default allow' against 'default deny' policies for external traffic initiated into a homenet.  This topic is discussed further in Section 3.6.1.

### Broadcast packets are gone!
But not really.  It's just more formalized and with a new name--Multicast.  Multicast packets are "broadcast" packets, in that they are broadcasted to everyone in on the link (segment).  Multicast is a broadcast intended for "any nodes listening to traffic sent to a specific multicast group address".  Multicast is used all over the place, such as for Neighbor Discovery, Router Advertisements, etc.  

The concept of a subnet's "network address" and "broadcast address" being unusable for nodes (e.g. 192.168.1.0/24 and 192.168.1.255/24) is gone too:
> In IPv6, all zeros and all ones are legal values for any field, unless specifically excluded.  Specifically, prefixes may contain, or end with, zero-valued fields. (RFC4291)

### New configuration methods for IPv6 network interfaces
IPv4 had DHCP and statically configured.  
IPv6 has DHCPv6 (which is different than DHCP for IPv4), SLAAC (no DHCP server needed), and manual configuration.

Neighbor Discovery (ND) is new family of ICMPv6 protocols, includes Router Advertisements and Router Solicitations, and also includes a mechanism to ask the network for the Layer 2 address to use to reach a Layer 3 IP (similar to IPv4 ARP).

Router Advertisements (RAs) are new in IPv6.  RAs are multicast packets sent out both periodically by routers, and in response to Router Solicitation (RS) messages from nodes on the network.  An RA lets nodes know what Link Local address to use to contact a nearby router, and what routes the router has.  RAs are how a device automatically finds a default gateway, among potentially other things.  There is an expiration timer on the information in the RAs (and therefore an expiration on a host's default route)--but RAs are usually sent on a recurring basis by routers.

Routers can communicate DNS servers for nodes to use by including that information in their RAs.  There are discussions to amend the standards to include other methods for DNS server autoconfiguration as well (see RFC4339).

DHCPv6 comes in two flavors, and neither communicates a default route!  Nodes learn their default route by listening to RAs.  
- Stateful, which is like DHCPv4 insomuch as the DHCP server needs to record the leases it has given out.  Given the scale an IPv6 network may reach, it may not be desirable to try to record all the addresses given out by a DHCPv6 server.
- Stateless, a new tasty flavor where the DHCPv6 server does not need to remember any leases.  It simply notifies clients of the appropriate /64 prefix to use, and clients autogenerate their own addresses within that /64 network prefix, avoiding IP conflicts by using Duplicate Address Detection (DAD). 

There is also DHCPv6-PD (Prefix Delegation), which is a method a router can use to request additional Global Unicast prefixes, such as for it's 'internal' interfaces.  Once a router's 'internal' network interface obtains a Global Unicast prefix, that router interface can assist nodes on the link in obtaining Global Unicast addresses, among other things.

SLAAC (Stateless Address Autoconfiguration) (RFC4862) is completely new.

SLAAC - TODO.  EUI-64, Temporary Addresses (Privacy Extension).  Example: 5021fa43-5676-4875-acfe-3f7f82517109\index.md

Manually & statically configured - TODO (such as 78aa9176-0efe-4590-9d61-d2f6bb9bf591\index.md)

## IPv6 address types
TODO
Unicast
        Global Unicast
        Unique Local
        Site Local - gone
        Link Local (fe80 etc)

## IPv6 address format
Prefix : Interface ID


Links:  
[RFC4443]: https://tools.ietf.org/html/rfc4443

***
_Mandatory_page_footer: This article and the rest of the FreeKB is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._

