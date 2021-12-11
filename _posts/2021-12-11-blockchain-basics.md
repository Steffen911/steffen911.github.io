---
layout: post
title:  "Blockchain Basics"
date:   2021-12-11 16:48:00 +0200
categories: [crypto]
---

In this post we will dive into the basics of blockchains.
What are blocks? How are they chained? And who interacts with them along the way?
I'm afraid that we cannot answer the most relevant question at this point - should I even care?
But this might be the first step on the path to enlightenment.

## On the challenge of transferring digital assets

We will focus our examples on Alice who wants to transfer something she owns to Bob.
If she has a physical objects, like a coin, she might hand it to Bob and from there on everyone can agree that
Bob owns the coin.
To proof it he can show the coin while Alice cannot.
For a digital asset, an image that Alice created and that lives on her hard drive, it becomes harder.
She could send a copy to Bob and another one to Clara.
All of them would "own" a copy of the image.

![Transferring digital assets naively](/assets/2021-12-11-blockchain-basics/traditional-transfer.png)

In certain cases, like with digital currencies, it might be desirable to have exactly one owner at a time.
We refer to this as the double spending problem.
Traditionally, we solve this by a trusted third party.
If Alice sends money from her bank account to Bob she cannot send the same money to Clara.
The bank will confirm that the ownership has transferred and prevent double spending.

![Transfers with a trusted third party](/assets/2021-12-11-blockchain-basics/trusted-third-party.png)

The hype around bitcoins, blockchains, and others started with the initial [Bitcoin Whitepaper](https://bitcoin.org/bitcoin.pdf)
by the anonymous Satoshi Nakamoto in 2009.
It describes a peer-to-peer based system of electronic cash without any central authority.
If Alice transfers something to Bob it creates a record in an immutable blockchain that is verified by multiple peers.
Afterwards, Alice cannot transfer the same thing to Clara, because their peers would check the blockchain and see that
Alice already transferred it to Bob which invalidates or blocks the transaction.
How does that work?

## Blockchains to the rescue


