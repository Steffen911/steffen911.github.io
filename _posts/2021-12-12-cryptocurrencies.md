---
layout: post
title:  "Digital Mediums of Exchange"
date:   2021-12-12 14:16:00 +0200
categories: [crypto]
---

Initially, I wanted to start with the basics and explain how a blockchain works.
Subsequent posts would focus on their applications like cryptocurrencies, DeFi, NFTs, and DAOs.
While some people (like myself) may enjoy the intricate details of private-/public-key cryptography,
hash trees, and other fancy tech things on their own, most will probably wonder why they should even care.
Therefore, I will start with the most commonly known application of blockchains - distributed currencies.
We will first take a look at currencies in general.
What kind of currencies are there and how do we use them?
After taking a look at cryptocurrencies as well, we can actually compare the two and draw our conclusions.

## What is a currency?

Given the title and, likely, some real world exposure to multiple currencies, you will probably have a good
understanding of how you can use currencies today.
At a fundamental level currencies are a medium of exchange.
If you have a $100 bill you can exchange it for another currency, physical goods, or services.
And, as an advantage over other exchange mediums, the recipient can go ahead and do the same.
Each vendor can set a price in that common denomination, and I can decide to make a trade based on the value that
the service or good has to me compared to the amount I have to spend.

Without this central medium of exchange I might offer you a service, like writing an incredibly useful and informative
blog post, for another service, like a haircut, or a good, like a bottle of wine.
Unfortunately, there is only so much wine I can drink, and I do not fancy a haircut every other day.
I could exchange the wine for something I desire more, but would have to keep in mind how much of a thing I need to buy
another thing.
The exchange rates I'll have to keep in mind will proliferate with the number of goods and services that are on offer.

Instead, people settled on the exchange of coins or banknotes.
There are three major forms of traditional currencies in use today.

- **Representative money**: This is a claim to something valuable, e.g. a note saying that I owe you a pile of gold.
  The advantage is that it can circulate without the need to exchange the underlying commodity making it significantly
  more practical for daily use.
- **Commodity money**: Here, the medium of exchange is valuable, e.g. a gold coin.
- **Fiat money**: This represents no underlying claim and only has value, because people think it does. It is the most
  common form of money today and issues by countries and organizations. The United States Dollar and the Euro are examples
  of fiat money.

The funny thing about fiat money is that everyone could start their own coins.
If I offer you piece of paper with some numbers on it in exchange for a few bananas and you go ahead and convince your
carpenter to accept it as well, we essentially created a new currency.
As long as people believe in its value, it is valuable.

## Enter: The Internet

The system I described up until this point just works.
There is some fraud here and there by counterfeiters and scammy issuers, but overall things are nice and cosy.
I give you some money and get something in return.
A few years ago some new technology came along that removed the need for those in-person exchanges: the internet.
I can communicate and deal with people I never met.
Sometimes this involves the exchange of money.
"How can I send money over the internet?" you might wonder.
I'm glad that you asked.

Let us assume that digital money is a file on your computer, similar to a banknote.
I send such a file to you and remove it.
If everyone behaves like that we are all good and can already stop worrying.
Experience teaches us, thought, that some do not play by the rules and instead might try
to send the same file of money to multiple people.
We will call this the double-spending problem.
The following graphic illustrates the problem.
Alice has some valuable thing $\oplus$ and sends a copy to both Bill and Carla.
All three end up with the valuable thing $\oplus$.

![Naive transactions](/assets/2021-12-12-cryptocurrencies/naive-exchange.png)

Wow, that was anticlimactic.
Luckily some smart and trustworthy people came along that generously offer to verify such transactions for
a tiny fee.
Let us call them banks.
Instead of having the valuable thing $\oplus$ on her own computer Alice stores it at a bank.
She asks her bank to transfer it to Bill and the bank stores that it belongs to Bill now.
If Alice wants to send it to Carla as well the bank will reject the transactions, because Alice already transferred
the ownership.
The bank acts as a trusted third party and guarantees that we do not double spend.

![Trusted Third Party](/assets/2021-12-12-cryptocurrencies/trusted-third-party.png)

As you can imagine this gives banks a great deal of power and information about payment flows.
As you can also imagine, some people are not happy about this and want to remove the necessity of a trusted, central
authority.

## The advent of decentralized internet money

Satoshi Nakamoto's [Bitcoin paper](https://bitcoin.org/bitcoin.pdf) published in 2009 proposes a solution to the
double-spending problem without a central authority.
Instead of sending each transaction to a central authority for verification we publish it publicly to many people.
They take multiple transactions and group them into a block.
Now, we arrive at the interesting part.
Creating a block is computationally expensive, meaning that you will have to do some hard mathematics that even computers
are bad at.
Also, we attach all blocks to previous blocks to create a chain - the blockchain.
Afterwards each participant in the network just accepts the longest chain of such blocks as the actual collection of
transactions.

Let us check if this solves our problem.
Can I double spend my money? No, because the participants in the network and the recipient would see that I already spent
my money in previous transactions. Therefore, my payment would be rejected.
Can I undo any transaction? Theoretically, if you control more computational power than the rest of the network.
But the chance diminishes with each block that was added on top of the initial transaction, because one has to re-do
all the hard work to recreate the blocks.
Therefore, one usually assume that a transaction is confirmed after 5-10 additional blocks on the chain.
Additionally, the system provides incentive for being honest.
It should be more lucrative to put the computing power to use in an honest way.

![Blockchain transactions](/assets/2021-12-12-cryptocurrencies/blockchain.png)

Computing hard puzzles is the way that blockchains like Bitcoin and Ethereum work.
This is called Proof-of-Work.
Another concept is Proof-of-Stake that is lighter on resources and a majority of coin-owners has to agree on a
transaction to include it in the chain.
A subsequent post on blockchains will go into more details.

We can conclude that blockchains are a technology that enables transfers between people without having a central
authority to validate transactions and prevent double spending.
Does that suffice to qualify as a currency?

## Are cryptocurrencies "currencies"?

Before we established that a currency is a medium of exchange.
I can accept it for some good or service and can easily use it to consume other goods and services.
In theory this also applies to cryptocurrencies.
It is a bit less convenient with the current technology, but you could buy a Pizza or a Tesla with your bitcoins.

Nevertheless, I would argue that cryptocurrencies are not currencies.
"Why though?" you might ask.
First and foremost, because most countries and tax codes agree that they are commodities or property.
Second, and perhaps more convincing: There are no stable or near-stable prices for cryptocurrencies.
To qualify as a currency I would argue that goods and services would need to have prices denominated in the cryptocurrency,
e.g. Bitcoin.
A Pizza could always cost 0.5 Bitcoin.
In case I want to pay in Euro I would pay the equivalent at a current exchange rate.
I'm not aware of any case where this is the case.
I assume that this is due to the tax code.
Businesses will have to pay taxes in the local currency and, therefore, have to assign a price in the local currency
to their offerings.
As long as most countries (excluding El Salvador) do not accept their taxes in cryptocurrencies businesses have little
incentive to bind their prices to a volatile cryptocurrency.
Also, most employees would be unhappy to receive a salary that, adjusted for most purchases,
fluctuates widely from month to month.

All in all, cryptocurrencies are not mainstream means of exchanges in my opinion and, therefore, do not qualify as
true currencies.

## Can we stabilize things?

If you like your crypto coins like your isotopes stablecoins might be the thing for you.
Instead of fluctuating (wildly) compared to some baseline currency they tie their value to it and keep the same
exchange rate.
How does that work out?
Let us assume that we want to create a stable coin linked to the US Dollar.
There are two main ways to produce and maintain a stable coin.
One is to have an underlying company that accepts a transfer in US Dollar via the traditional financial system.
It keeps them in a save deposit and issues a new coin that is worth exactly one US Dollar.
Also, you can ask this company to redeem your coin for a US Dollar.
This is a crypto-reinvention of the representative money we mentioned earlier.
Another, more interesting, approach is the securitization of another cryptocurrency.
I can use smart contract (watch out for a follow-up post on that) to create 1 US Dollar of worth in my stable coin
by putting something like 3 US Dollars worth of another coin, e.g. Bitcoin.
Here, we include some safety margin to still pay out 1 US Dollar if the exchange rate of Bitcoin drops.
The underlying security is sold automatically once it reaches the stable value.
What happens if many people try to redeem their stable coins at the same time?
Well, imagine the 2008 financial crisis on steroids without any regulators or central banks.
Better keep your popcorn ready.
