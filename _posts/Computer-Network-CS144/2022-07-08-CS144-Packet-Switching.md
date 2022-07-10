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
$$ t_p = \frac{p}{r} $$

> Digestion: Packetization Delay is like time to put bits of a packet into the link. 
{: .prompt-tip}