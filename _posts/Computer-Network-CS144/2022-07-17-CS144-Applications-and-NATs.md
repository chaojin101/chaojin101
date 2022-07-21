---
title: Computer Network CS144 Applications and NATs
categories: ["Computer Network CS144"]
tags: ["Computer Network CS144"]
math: true
---

### 5-2 NATs - Types

Symmetric NAT

!['Symmetric NAT'](\assets\img\post\CS144\NATs\symmetric-NAT.png)

> Digestion: Symmetric NAT will translate the same internal IP with port to different NAT ports for different destination's IPs or ports. This may cause problems, if the server is distributed, two same source requests inside a symmetric NAT have different NAT ports. if the server uses the same source port to decide whether it is the same request, it will fails.
{: .prompt-tip}

### 5-3 Implication

Transport: No New Transport!

> Digestion: When NAT software maps an address, it will check the transport protocol, if the protocol is wrong means the packet is corrupted. If a new transport protocol comes out, the NAT software will simply assume the new protocol packet is corrupted. NAT software will not add support for a new transport protocol until it is very popular, but it will not become very popular until it works across NATs.
{: .prompt-tip}