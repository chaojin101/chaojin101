---
title: Computer Network CS144 Subtitles Lower Layers
categories: ["Computer Network CS144"]
tags: ["Computer Network CS144"]
math: true
---

### 7-0

Phil: 

So in this unit, we are going to finally dig down below IP, answer the question what is a link and how do they work. So how does the link layer work and what are the issues that you encounter at the link layer.

So there are two basic things that this unit is going to cover. 

The first: the fundamental principles of communication, this is where the boundary of computer science networking with electrical engineering. We're going to talk about things like signal and noise and how the signal to noise ratio, in fact, determines what's the potential bit rate capacity of a link. There's a reason why today we don't have 100 terabit per second link layers because of these fundamental mathematical principles of communication. So based on that, we are going to look at things link bit errors and how link layers recover from them. Using coding, Error correcting codes. So that for example, you add a little bit of redundancy to your link layer frames such that, if there are a few bit errors down at the physical and link layer, you can recover from and still receive the frame correctly. 

Nick:

So the second thing that we are going to learn about it in this unit are how these links are actually built. You remember from unit one that the thin waste of IP allows many many physical layers and link layers to operate underneath and still use the Internet Protocol and to tie them all together. So there are two different categories of phsical links we're going to be talking about two here, two that you'll be very familiar with already.

There's wired links, for which the dominant wired linking in use today is ethernet. So we will learn how ethernet works. The original version Ethernet used a shared cable and so needed a way to share that cable. so we'll be learning about what's called the CMSA/CD and access control mechanism that allows us to share that physical cable. But we will also learn how ethernet works today, which is to use switches, which you learned a little bit about already in the previous unit, how they learn addresses, how those tables get populated. 

The second thing we'll be learning under the links is wireless links. Now wireless is quiet different from wired. More than just the fact that it's broadcasted into the air, there's many characteristics of wireless that make it fundamentally different in the way that it works and we need to be mindful of those when making practical links.

The first one is the signal itself and the channel can vary, it's not fixed over time like it is in a wired link, where it always has the same capacity operating on the same link. The channel can fade, there can be different types of interference signals can take different paths with different links and interfer itself and because it's broadcast, everybody can hear and so this introduces challenges as well, as well security challenges because everybody can hear what we're saying.

There's another problem that we'll learn about that's called the hidden terminal problem, this is when two clients that are communicating, are both happily talking to an AP, but they have no means to communicate with each other, because they don't have any direct signal contact with each other. And so there needs to be some extra level of coordination in the network to make sure that they don't interfere with each other at the access point. Also In addition to learning about these different types link we'll be learning about what are the consequences of these different links and that different links can carry packets up to a different maxinum size so-called maximum transmission unit. Ethernet for example can take packets up to 1500 bytes long but other links may take packets only upto a certain length and so you probably remember that mention IP fragmentation in the earlier parts of the class. This is necessary when you're going from a link with a large maximum transmission unit down to a smaller one, if that is not able to carry it the network will fragment it into a number of self contained fragments that don't get put back together again until they get to the end host which then reassembles the data and hands it up to the next layer. So you learn how that works and what specific mechanisms are inside IP to make that work.

The last thing we're going to be learning about is this really interesting tricky little detail of the communication channel and that is when two hosts or two ends of a link are communicating with each other they can't possibly be using exactly the same clock or how exactly the same frequency exactly the same phase, two different places at the same time, so when a sender is sending using one clock which is potentially different from the one the receiver is using. So somehow we need to indicate to the receiver what clock rate and frequency and phase that we were using in order for the far end to correctly decode the data, so we'll learn about encoding in order to recover the clock and use it correctly at the far end.