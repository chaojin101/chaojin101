---
title: Computer Network CS144 Packet Switching
categories: ["Computer Network CS144"]
tags: ["Computer Network CS144"]
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
- Dedicated circuit within the wire.
- Fixed data rate on the dedicated circuit.
- Isolated from end-to-end.

Lecture summary:
- Each call has its own private, guaranteed, isolated data rate from end-to-end.
- A call has three phases:
    1. Establish circuit from end-to-end ("dialing")
    2. Communicate
    3. Close circuit ("tear down")
- Originally, a circuit was an end-to-end physical wire.
- Nowadays, a circuit is like a virtual private wire.