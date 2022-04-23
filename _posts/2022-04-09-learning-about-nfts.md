---
layout: post
title:  "Learning about NFTs - The expensive way"
date:   2022-04-09 13:54:00 +0200
categories: [crypto, nft]
---

With the hype of cryptocurrencies fading a bit, I set out on a quest to learn what this was all about.
The most prominent use of blockchains, aside from crypto currencies, seems to be the creation, storage, and
exchange of pixelated images.
I remember a time after I just entered school, where everyone collected Pokémon and Yu-Gi-Oh! cards.
It was about creating the perfect collection to win every duel.
I feel like NFTs (Non-Fungible Tokens) are also about collecting things, but without the thrill of the fight.

A few days ago, I decided to launch my own NFT.
I heard about OpenSea before and took a look at their offering, but using a central marketplace did not feel right.
Instead, I wanted to interact with the network at a lower level.
[Mastering Ethereum](https://www.amazon.de/-/en/Andreas-M-Antonopoulos/dp/1491971940/ref=sr_1_4) provided a good understanding
on how to use the blockchain and a brief introduction into smart contracts.
The blogpost [How to write & deploy an NFT](https://ethereum.org/en/developers/tutorials/how-to-write-and-deploy-an-nft/)
on ethereum.org was the perfect starting point from there on.

In this post, I will walk you through the steps I took and the learnings I had a long the way.
The main takeaway is that it is surprisingly expensive to share pixelated artworks with the world.
There is always some charge for every step along the way.
Anyway, let us start at the beginning.

## Signing up for all the things

I thought avoiding OpenSea would avoid the registration at a central service.
I could not have been more wrong.
This section provides an overview of all the things I used along the way.
If you are happy with an NFT on a test network, crypto.com is optional.

As recommended by the tutorial, I opened an account at [Alchemy](https://www.alchemy.com), created a [Metamask](https://metamask.io)
wallet, and signed up for [Pinata](https://www.pinata.cloud).
My existing crypto.com account came in handy when it was time to convert some Euros into Ether.
If you create an account over at crypto.com, I would love it if you use my referral link: [Referral](https://crypto.com/app/8aj5j9hyde).

Why do we need all those services?
Excellent question.
From my understanding, we use them in the following way:

- **Alchemy**: Our gateway to the Ethereum network.
  We can call their service endpoints to create transactions.
  This alleviates us from the need to run our own Node, which seems even more expensive and cumbersome.
- **Metamask**: This will be the wallet that contains our Ether and NFTs in the end.
  We get a Private Key to access our wallet and make transactions and a Public Key that is our address on the blockchain.
- **Pinata**: Uploading pictures on a blockchain is expensive, because they contain a lot of data.
  Instead, we use an InterPlanetary File System which seems to be a fancy concept for a big hard drive that everyone can access.
- **Crypto.com**: As I teased earlier, creating NFTs is expensive, and we need to convert some real world money into fancy internet money.

## Creating my first NFT on the Ropsten Test Network

I am really glad that I have some previous experience with npm and Node.js.
Otherwise, following the tutorial would have become a lot of copy and paste and little understanding.
The programs itself are small and simple, though.

We start by getting some free money from the generous test network runners and are ready to go.

We use a library to define an ERC-721 token (the technical standard for NFTs) which should not be confused with
ERC-20 token (which seems to cover fungible tokens, i.e. crypto currencies).
That library receives a name, we compile it, and use a small script to send it to the blockchain.
Apparently, that is all there is to have the generic NFT capability available.
Now, we upload an image on Pinata, write some metadata that we also upload to Pinata, and send a transaction to our
contract.
You can view my first NFT on the test network on [etherscan.io](https://ropsten.etherscan.io/address/0xab8f53da7cdf93ad5ae48cd0322e6caed0eb6051).
It is a picture of the Siegessaeule in Berlin that you can view below or on the InterPlanetary File System (I love the name!)
on [pinata.cloud](https://gateway.pinata.cloud/ipfs/QmUQDaeiK6e1qM8HJHgKC6giRAMdqbQSPNqZJQeB75VnvG).

![NFT Siegessaeule](/assets/2022-04-09-learning-about-nfts/siegessaeule.jpeg)

Well, that was easy.
Time to do it on the real blockchain.

## Same thing, different blockchain

I already had about 100€ worth of Ether in my crypto.com wallet and naively thought that might be enough.
Getting the Ether into my Metamask wallet was the first challenge, though.
After I registered my external wallet in their app, they made me wait 24 hours before any transfer to it was possible.
As it was getting late, I called it a day and proceeded the following day.

New day, new problem.
Sending all my Ether to the wallet proved harder than expected, too.
You have to account for a small transaction fee that changes every second.
Better, to keep a small buffer around for the transaction fee.
A few minutes later my Ether minus transaction fee minus security buffer arrived in Metamask.
I ran the same steps as before, i.e. naming my contract, compiling it, uploading it...
"Insufficient funds". Welp.

Time to get out the big guns.
Back in my crypto.com app I buy Ether for another 300€ + a 2,99% markup for credit card payments.
Another transfer to my Metamask wallet with about 5€ in transaction fees later I feel ready to deploy my contract.
"Insufficient funds". Double welp.

I play with the gasPrice and gas settings in my config files and feel like in a high school physics class.
Do I have to multiply by a million or a billion to get the units right?
At some point my transaction goes through, I feel excitement, and head over to etherscan.io to view my transaction.
"Pending. Estimated time > 1h".
My pricing was off by three orders of magnitude.
Time to cancel my transaction - easier said than done.
After a small Google search and some time on YouTube I send 0 Ether to myself to front-run me.
Each transaction from my wallet gets an ID that is always incremented by one.
The money to myself became the first confirmed transaction, making the contract creation transaction obsolete.

Time to try again with a more realistic gas price.
Again, the transaction goes through, but the estimate is still over an hour.
At this point the Gas price was at about 40, and I included a maximum of 30 in my transaction.
Let me cancel it and try again - is what I thought.
All my transactions to myself get rejected, though, because I have to provide more gas than my current, pending transaction.
I check if on etherscan.io and there it hits me.
The expected transaction fee sits at about 280€, because contracts seem to be much more complex than transfers.
The only thing left for me is waiting for the transaction to happen.

About 2 hours later I get a confirmation and my contract is up and running.
Uploading images for 15-25€ a piece seems like peanuts now.
Here, I remembered last year's article in the Economist about their [NFT auction](https://www.economist.com/the-economist-explains/2021/10/21/why-we-are-selling-our-cover-as-an-nft).
They also put a price tag of about 400€ on their NFT creation.

I do not see how anyone can expect to run actually useful services on that foundation.
Deployments at big cloud vendors come significantly cheaper and one would have to rethink common practices like
continuous deployment.

## Takeaways

This post got longer than expected, but it reflects my astonishment.
I understand that people want to get paid for their services, but this seems a little out of line.
Building a service like Instagram on a blockchain where every post costs 20€ and every like 3-4€ does not seem attractive.
I feel like I understand NFTs and blockchain interactions much better now, but they leave me even less convinced of their merits.
Am I missing anything?
In the future I might try to auction off one of my newly minted NFTs to recoup some of the losses.
Stay tuned to learn more about that experience.
