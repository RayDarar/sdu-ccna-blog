# Week thirteen

This week was a pretty much hard one, because of quiz we got. Configuring vlans, port security system is a pretty much easiest part of the whole. The tough one is however the ip calculations that got me well.

I'm writing this post lately for this week, because of late lab works I got. So, in this week we have got a chapter 7.

## Chapter 7 ACL
This chapter is all about the continuation of security questions. ACL stands for Access Control Lists, which defines the set of rules or I must say the configurations of these rules in order to permit or deny IP packets depending on configuration we applied. ACL has different types of it. For instance, standard ACL works only for Internet Protocol version 4.

**The main purpose of ACL** is to define a set of rules that tells the router whether drop packet or forward using information in the header of packet. From this we can learn that ACL is not a physical thing like Firewall, instead it's an abstraction that works on OSI's layer 3 and layer 4 (Transport and Network levels).

When configured, ACL performs this tasks:
- Limiting network traffic
- Provide traffic flow control. ACLs can restrict the delivery of routing updates to ensure that the updates are from a known source
- Provide a basic level of security for network access
- Filter traffic based on traffic type
- Screen hosts to permit or deny access to network services

ACL can be applied to inbound or outbound traffic.
- **Inbound ACLs** - Incoming packets are processed before they are routed to the outbound interface
- **Outbound ACLs** - Incoming packets are routed to the outbound interface, and then they are processed through the outbound ACL

A single ACL rule is called an Access Control Entry, shortly ACE.
ACEs include the use of wildcard masks. **Wildcard mask** is a string of 32 binary digits used by the router to determine which bits of the address to examine for a match. From an ordinary subnet mask it differs in the way of matching 1s and 0s.
- Wildcard mask bit 0 - match the corresponding bit value in the address
- Wildcard mask bit 1 - ignore the corresponding bit value in the address

Simply wildcard masks are just reverse for subnet mask. The reason it works like that is explained by algorithms written in routers.
Calculating wildcard masks can be difficult. However, there's a simple way: subtract subnet mask from 255.255.255.255 address

Configuring the ACL rule can be difficult, in order to simplify this process **host** and **any** keywords are included in Cisco IOS.
- `host` keyword is substitution of 0.0.0.0 wildcard mask. Which means that the whole ip address written must match
- `any` keyword is substitution of 255.255.255.255 wildcard mask. Which means to ignore or accept any ip address

RS2 book on netacad providing a **guideline** for using ACLs:
- Use ACLs in firewall routers positioned between your internal network and an external network such as the Internet
- Use ACLs on a router positioned between two parts of your network to control traffic entering or exiting a specific part of your internal network
- Configure ACLs on border routers, that is, routers situated at the edges of your networks. This provides a very basic buffer from the outside network, or between a less controlled area of your own network and a more sensitive area of your network
- Configure ACLs for each network protocol configured on the border router interfaces

And also **rules** for applying ACL:
- Configure one ACL per protocol
- Configure one ACL per direction
- Configure one ACL per interface

These rules are not strictly defining the way you should configure your networks, it depends on your network requirements.

After obtaining all the theory information required for basic ACL implementation, let's start **configuring**.

To use numbered standard ACLs on a Cisco router, you must first create a list of ACEs and then apply it to interface. Here's the few basic commands to configure the standard ACL:
- `access-list [access-list-number] { deny | permit | remark } source { source-wildcard | log }` - creating an ACL entry

`remark` keyword is used for documentation purposes.

- `no access-list [access-list-number]` - removing an ACL by number
- `show access-list` - showing access
- `ip access-group [access-list-number] { out | in }` - applying the ACL on interface for inbound or outbound traffic
- `ip access-list { standard | extended } [name]` - creating a named ACL
- `{ permit | deny | remark } { [source] [source-wildcard] } [log]` - in ACL configuration mode
- `ip access-group [access-list-name] { out | in }` - applying the ACL on interface by ACL name

Using previous commands we can create and apply ACL rules.

Now we can **modify** existing ACL rules:
- Method 1, using text editor
- Method 2, using sequence numbers using `no [sequence-number]` for removing ACE and assigning sequence-number before creating ACE.

We can apply ACL rules on VTY lines using `access-class [sequence-number] { in | out }`. Parameter *in* restricts incoming connections and parameter *out* restricts outgoing connections.

Additionally to previous commands recall how to configure the ssh on vty ports:
- `login local`
- `transport input ssh`

Overall that's all I wanted to summarize.
