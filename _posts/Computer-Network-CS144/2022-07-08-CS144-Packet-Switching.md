---
title: Computer Network CS144 Packet Switching
categories: ["Computer Network CS144"]
tags: ["Computer Network CS144"]
math: true
---

### 3-0 Intro

- Three main components of packet delay:
    - Packetization delay
    - Propagation delay
    - Queueing delay

### 3-1 The History of Networks and Internet

- Fire Beacons
- Carrier Pigeons
- Human Messengers
- Horse Relays
- Optical methods: reflect sun ray
- The Telegraph in France
    - Codes
    - Flow Control
    - Synchronization
    - Error correction and retransmission
    - Encryption
> Note: These concepts raised by the Telegraph in Franch are still in use today.
{: .prompt-info}
- Telephone

### 3-2 What is packet switching

Outline
1. What is Circuit Switching?
2. What is Packet Switching?
3. Why does the Internet use Packet Switching?

---

1. What is Circuit Switching?

Key characteristics:
- **Dedicated circuit** within the wire.
- **Fixed data rate** on the dedicated circuit.
- **Isolated** from end-to-end.

Lecture summary:
- Each call has its own private, guaranteed, isolated data rate from end-to-end.
- A call has three phases:
    1. Establish circuit from end-to-end ("dialing")
    2. Communicate
    3. Close circuit ("tear down")
- Originally, a circuit was an end-to-end physical wire.
- Nowadays, a circuit is like a virtual private wire.

Problems in computer communication:
- Inefficient. The dedicated circuit is idle in most of the time.
- Diverse Rates. A server streaming videos at 6Mb/s, or me typing at 1 character per second. A fixed rate circuit will not be much use.
- State management. Circuit switches maintain per-communication state, which must be managed.

---

2. What is Packet Switching?

Key characteristics
- Packets are routed **individually**, by looking up router's local forwarding table.
- All packets (from different connection) **share** the full link.
- **No per-communication state**.

---

3. Why does the Internet use Packet Switching?

- Efficient use of expensive links.
- Resilience to failure of links & routers. (high reliability)

### 3-3 End to End Delay

Defination:
- Packetization Delay, $$ t_p $$ : The time from when the first to the last of a packet is transmitted.
![packetization-delay.png](\assets\img\post\CS144\packet-switch-note\packetization-delay.png)
    - $$ t_p = \frac{p}{r} $$

> Digestion: Packetization Delay is like time to put bits of a packet into the link. 
{: .prompt-tip}

### 3-4 Playback Buffers

![playback-buffer.png](\assets\img\post\CS144\packet-switch-note\playback-buffer.png)

> Digestion: The playback buffer is between time to palyback and time to recevied, it is more likely a time buffer, of course time buffer is limited by packet buffer size, it could not extend packet buffer size.
{: .prompt-tip}

### 3-5 Simple Deterministic Queue Model

![simple-queue-model.png](\assets\img\post\CS144\packet-switch-note\simple-queue-model.png)

- Q(t) = A(t) - D(t) Cumulative number of bytes in queue until time $$ t $$. it is the vertical red line point at green line A(t) - yellow line D(t).
- d(t) a byte's queueing delay, which is departed at time $$ t $$. it is the horizatal red line point at yellow line value $$ t_d $$ - green line value $$ t_a $$.

---

![pipeline-packets.png](\assets\img\post\CS144\packet-switch-note\pipeline-packets.png)

- Pipeline. We break messages into packets because it lets us pipeline the transfer, and reduce end to end delay.

---

![statistical-multiplexing-p1.png](\assets\img\post\CS144\packet-switch-note\statistical-multiplexing-p1.png)
- A and B is linka and linkb arrival rate.
- c is departed rate
![statistical-multiplexing-p2.png](\assets\img\post\CS144\packet-switch-note\statistical-multiplexing-p2.png)

- Statistical Multiplexing Gain. Statistical multiplexing lets us carry many flows efficiently on a single link.