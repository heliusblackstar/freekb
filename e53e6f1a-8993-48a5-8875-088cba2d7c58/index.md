# Introduction to IPv6

## Summary
IPv6 offers a publically routable address for every device interface, and solves some of the problems with IPv4.

## Source materials
If you read nothing further in this article, read this:  
You should go read RFC7368 ("IPv6 Home Networking Architecture Principles").  It's a great general introduction to IPv6 and links to many other articles that will help introduce you to how IPv6 is designed and works.  It also frames the introduction in the context of a simple-to-understand home network.

## Major features and changes in contrast to IPv4
### NAT is eradicated!   
NAT was not a security feature (RFC2775 section 3.4).  NAT was NEVER desirable but was a horrible band-aid created to solve the egregious address shortage in IPv4.    
IPv6 solves both these two problems.  IPv6 has plenty of addresses and therefore NAT and all the headaches brought are eliminated (RFC7368, section 2.2).  Addresses are NOT altered by NAT in transit thru a firewall.  Global Unicast Addresses will exist on both sides of a firewall, both the external and internal interfaces.

Note, that firewalls still exist--you can still have firewall policies that allow or deny traffic, either on the device, or at the network perimeter.

### The need for subnetting is gone!  
The standard prefix for all networks is a /64.  A /64 network prefix (which has **more than trillions of addresses** on it) is recommended and acceptable even for networks which only have 2 devices (and this leaves plenty of room for growth later).  

Even home users are recommended to be assigned **at least**  a /56, which is 256 networks (256 /64 prefixes), giving them 256 separate networks, each which can hold more than trillions of devices.  

A single /64, has 2^64 (18,446,744,073,709,551,616) Global Unicast addresses.

### Global Unicast Addresses are abundant and everyone gets them!  
There are enough publically routable addresses (also known as Global Unicast Addresses) for every device interface on every device.  Every server, every client, every device can and does have as many Global Unicast addresses as it needs.  

The Global Unicast addresses in use are visible from the device's OS (simple!), so seeing a device's "public" address does not involve having to cross-reference a device's private IP with a firewall public/private NAT configuration like in IPv4.

### The IPv6 address space is mind-bogglingly expansive
To oversimply it, the size of the IPv4 address space is 2^32.  
2^33 would be twice as large as that.  2^34 would be twice as large as that.  IPv6 is 2^128.

The size difference in address space between IPv4 and IPv6 is so incredibly vast that it's actually quite difficult to convey how much larger the IPv6 address space is.  Much like we said before, we can say, "this should be enough addresses for a very long time".

### Firewalls can be set to simply passthru incoming IPv6 traffic, allowing simple inbound connectivity for any apps or services without any extra signaling protocol or manual firewall configuration.  
As the RFCs state, do not confuse "addressability with reachability".  
To quote RFC7368:

        An IPv6-based home network architecture should embrace the transparent end-to-end communications model as described in [RFC2775].  Each device should be globally addressable, and those addresses must not be altered in transit.  However, security perimeters can be applied to restrict end-to-end communications, and thus while a host may be globally addressable, it may not be globally reachable.
        [...]
        whether devices are globally reachable or not would depend on any firewall or filtering configuration, and not, as is commonly the case with IPv4, the presence or use of NAT.  In this respect, IPv6 networks may or may not have filters applied at their borders to control such traffic, i.e., at the homenet CE router.  [RFC4864] and [RFC6092] discuss such filtering and the merits of 'default allow' against 'default deny' policies for external traffic initiated into a homenet.  This topic is discussed further in Section 3.6.1.

### Broadcast packets are gone!
But not really.  It's just more formalized and with a new name--Multicast.  Multicast packets are "broadcast" packets.  Multicast is a broadcast intended for "any nodes listening to traffic sent to a specific multicast group address".  Multicast is used all over the place, such as for Neighbor Discovery, Router Advertisements, etc.

### Configuration methods for IPv6 network interfaces
DHCP and static are no longer the only 2 options, and manually configuring network interaces can be rare.

DHCPv6 comes in two flavors, and neither communicates a default route.
- Stateful, which is like DHCPv4 insomuchas the DHCP server needs to remember the leases it has given out.
- Stateless, a new tasty flavor where the DHCPv6 server does not need to remember any leases.  It simply notifies clients of the appropriate /64 prefix to use, and clients autogenerate their own addresses within that /64 network prefix.

Router Advertisements are multicast packets sent out by routers to let nodes know what Link Local address to use to contact a nearby router, and what routes the router has.  RAs are how a device finds a default gateway.  There is an expiration timer on the information in the RAs (and therefore an expiration on a host's default route)--but RAs are sent on a recurring basis by routers.

SLAAC - TODO

Manually & statically configured - TODO

## IPv6 address types
TODO

## IPv6 address format
TODO


***
_Mandatory_page_footer: This article and the rest of the FreeKB is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._

