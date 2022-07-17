---
title: Computer Network CS144 Congestion Control
categories: ["Computer Network CS144"]
tags: ["Computer Network CS144"]
math: true
---

### 4-3 Dynamics of a single AIMD flow

!['Dynamics of a single AIMD flow'](\assets\img\post\CS144\congestion-control-note)

> Digestion: When the Buffer size, B = RTT x C (C = $$ \frac{WSize}{RTT} $$), that is B = WSize, the Bottleneck Link Utilization will always be 100%, this is because when a packet drop, the WSize will be halved, the packets in the buffer can ride out the time during the WSize increases.
{: .prompt-tip}

### 4-7a TCP Reno

> Digestion: When received duplicate acknowledgements , inflate the congestion window, because duplicate acknowledgements mean packets in the behind of the delay packet arrives destination, the network is not so congested. We can inflate the congestion window before we halve it. After it received acknowledgements, it correct its window size to corrected value halved the previous window size.
{: .prompt-tip}