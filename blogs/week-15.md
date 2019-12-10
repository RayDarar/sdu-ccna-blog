# Week Fifteen

On this week we've got a final chapter, let's not wait any longer but just jump into it.

# Chapter 9 - NAT

NAT stands for Network Address Translation and was a short-time solution to the problem of ending number of IPv4 addresses. Let's firstly define what is NAT. In a nutshell NAT is dividing the whole WEB into internal networks and The Internet by defining private and public addresses.

NAT can be configured on routers. With such configurations router will have a pool of public IP addresses. In such manner, routers will hide the private IP address of an end-device translating each packet's private IPv4 address to a public IPv4 address.

NAT includes four types of addresses:

- Inside local address
- Inside global address
- Outside local address
- Outside global address

**Inside address** is the address of the device which is being translated by NAT
**Outside address** is the address of the destination device

**Local address** is any address that appears to be on the inside portion of the network
**Global address** is any address that appears to be on the outside portion of the network

After defining the purposes of NAT, let's get deep into the types of it and processes that are happening under the hood.

Types of NAT:

- **Static NAT** - one-to-one address mapping between local and global addresses
- **Dynamic NAT** - many-to-many address mapping between local and global addresses
- **Port Nat (PAT)** - many-to-one address mapping. This is also known as _NAT overloading_

Static NAT is configured manually by network administrator and is never changed.

Dynamic NAT uses a pool of public addresses and maps them to the private addresses on first-come, first-served basis.

PAT uses a different TCP ports to map different private addresses to a single one.

After discovering the types of NAT, I'm gonna try to configure them starting from static NAT.

Book says that there's a two basic tasks to configure NAT:

1. Create a mapping between a private and global addresses
1. Configure interface for NAT inside or outside translations

Commands to apply previous steps:

- `ip nat inside source static [local-ip] [global-ip]` - establishing static translations
- `ip nat { inside | outside }` - mark the interface as the inside or outside

Verifying commands:

- `show ip nat translations`
- `show ip nat statistics`
- `clear ip nat statistics`

Commands to configure dynamic NAT on cisco IOS:

- `ip nat pool [name] [start-ip] [end-ip] { netmask [netmask] | prefix-length [prefix-length] }` - define public pool
- next step is to configure access-list rules to define addresses that need to be translated
- `ip nat inside source list [access-list-number] pool [name]` - establish dynamic source translations
- `ip nat { inside | outside }` - apply it on interface

Verifying commands:

- `show ip nat translations verbose`
- `ip nat translation timeout [timeout-seconds]`
- `clear ip nat translation *` - clear all the entries

Commands to configure PAT (pool):

- `ip nat pool [name] [start-ip] [end-ip] { netmask [netmask] | prefix-length [prefix-length] }` - define public pool
- next step is to configure access-list rules to define addresses that need to be translated
- `ip nat inside source list [access-list-number] pool [name]` - establish dynamic source translations
- `ip nat { inside | outside }` - apply it on interface

Commands to configure PAT with single public address:

- configure access-list rules to define addresses that need to be translated
- `ip nat inside source list [access-list-number] interface [number] overload` - establish dynamic source translations
- `ip nat { inside | outside }` - apply it on interface

- `ip nat inside source list [list] pool [name] overload` - associate access-list with NAT pool and creating PAT

Command for configuring port forwarding:

- `ip nat inside source static { tcp | udp [local-ip] [local-port] [global-ip] [global-port] } [extendable]` - note that extendable is applied automatically

Overall that's all I wanted to tell you about NAT
