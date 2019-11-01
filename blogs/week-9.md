# Week ninth

Well, the first book (RS1) was pretty much full of basic information. However, it's only halfway to finals, now I've got the second electronic book - RS2.

> Let's start our journey with chapter 1

## Chapter 1 - Routing Concepts

This chapter was surprisingly a tough one, not because of complexity (which this chapter lacks), but because of the amount of material waiting for me to study it. Overall it took me about 5 hours to read and finish Packet Tracer Labs.

Let's go ahead, and I will summarize all useful knowledge from this study.

First thing to mention is what network administrators should **discuss first when they are mentioning networks**. These points are obvious but I should mention them:
1. Topology
1. Speed
1. Cost
1. Security
1. Availability
1. Scalability
1. Reliability

I already know why and what is this, therefore let's go ahead.

Next point of this chapter was that **Routers is just a computers**. And I couldn't agree more with that. In the previous book, we learned different parts of Router's components like CPU, Memory and it's different types, ports, etc. There was an interesting sentence that got me into thinking differently about why we need routers. It was: "Routers are devices that connect networks". Anyone would say that it's obvious and shouldn't be even mentioned, however, I changed my thoughts on building networks and how it is built right now.

**Packet forwarding mechanisms** was a new one for me, but quite simple to understand:
- Process switching - is just checking all the packets.
- Fast switching - is just caching destination interfaces at a runtime, therefore it's faster than process-switching. If there is no exit interface on cache, just apply process-switching on the packet.
- Cisco Express Forwarding (CEF) - pre-calculating all the possible cases in context of this network.

A few words about the **documentation process**. A network administrator should always identify these data about his network:
1. Device names
1. Interfaces used in the Design
1. IP addresses and subnet masks
1. Default gateways

Router's main responsibilities is to **switch packets** from source interface to it's proper exit interface. To do so performs these steps:
1. De-encapsulate frame to expose it's Header and Trailer
1. Examine the destination IP address to find the best path in the routing table.
1. Encapsulate packet into new frame of exit interface.

When router searches in it's routing table, the process can end up with these results:
- Destination IP address is directly connected network
- Remote network
- No route (Default Gateway of last resort)

I learned about some **dynamic routing protocols** and their metrics:
- Routing Information Protocol (RIP) - Hop count
- Open Shortest Path First (OSPF) - Cost based on cumulative bandwidth.
- Enhanced Interior Gateway Routing Protocol (EIGRP) - Bandwidth, delay, load, reliability.

How to read routing table entries: <br>
```cli
route-src  dest-network AD metric next-hop route-timestamp out-interface
```

How to configure static routing:
```cli
ip route network mask { next-hop-ip | exit-int }
```

How to configure default route statically:
```cli
ip route 0.0.0.0 0.0.0.0 { next-hop-ip | exit-int }
```

How to configure IPv6 static route:
```cli
ipv6 route ipv6-prefix/length { ipv6-address interface-type interface-number }
```

How to configure default IPv6:
```cli
ipv6 route ::/0
```

Overall, that's all I've got for the first chapter.

## Chapter 2 - Static routing
In previous chapter we learned a bit about static routing and it's advantages/disadvantages. Now we are going deeply into static routing principles.

**What us static routing?** Routers can learn about remote networks *manually* or dynamically. Manual configuration of router's routing table is going to be discussed here.

**Why use static routing?** There is a list of advantages:
- It's not advertised (Provides more security due to the fact of not sharing router's routing table)
- Less bandwidth (no overhead information is send)
- No CPU calculations
- The path is always known

And list of disadvantages:
- Configuration is always time-consuming
- Configuration could be error-prone
- Network Administrator is always needed to maintain topology changes
- No automatic scaling
- Require the knowledge of the whole network

**When to use static routing?** Obviously, when network is small and will not grow significantly, routing to and from stub-network, when we have a single default route.

Possible **applications** could be: connect a specific network, connect a stub-router, summarize routing table entries create a backup route.

I also learned about different **types of static routing**.
1. Standard static routing is used for typical static routing configurations
1. Default static routing is used to create a default path for packets that didn't find their entry in the routing table
1. Summary static route is used to summarize a group of routing table entries into one entry
1. Floating static route is using administrative distance in order to create a backup route for packets

**Recursive-lookup** is happened when router performs multiple table searching.

Last one, I learned a new command `show ip route { static | specific-network }`

Overall, I got the idea of RS2 book and ready for a new material.
