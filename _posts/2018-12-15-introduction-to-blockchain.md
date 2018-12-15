---
layout: post
date:   2018-12-15 17:00:00 +0200
title: "Introduction to the Blockchain (Cryptocurrencies)"
categories:
    - Blockchain
    - Cryptocurrencies
tags:
    - Blockchain
    - Cryptocurrencies
    - Bitcoin
---

So... I wanted to write this article since 6 weeks ago, when I started to delve
into cryptocurrencies development, and today is the day :) .

**Disclaimer:** First and foremost, I'm not a blockchain and/or cryptocurrencies
fanboy, neither a hater. I think the right way to approach this topic is through
highly critical thinking, a lot of patience and will to learn.

There's a lot of potential on this field, yet a lot of empty promises too, and
to discern what's serious from what's not one needs to dig deep... and believe
me, it's a tough task. The field is deeper than one could imagine without having
previous exposition: the number of open questions & open problems is high, and
this is in part due to its interdisciplinary nature (cryptography, distributed
systems, networking, software & networks security, economics...).

My aim here is not to write a tutorial, but to explain my own learning process,
and in order to do that I'll continue writing more articles to talk about very
specific topics in almost self-contained texts.

Having said that, I'll center my attention on the cryptocurrencies landscape
rather than focusing on the more fuzzy "blockchain" term, because that's what
I'm working on, and that's where my learning experience is mostly focused.

Let's start then ☺. The story doesn't really start with Bitcoin, but that will
be our first stop because it's where all the pieces where put together for the
first time.

Knowing about the following concepts is a pre-condition to advance through the
next steps without problems:
*   [Hash function](https://en.wikipedia.org/wiki/Hash_function)
*   [Asymmetric cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography)
*   [Digital signature](https://en.wikipedia.org/wiki/Digital_signature)
*   [Merkle tree](https://en.wikipedia.org/wiki/Merkle_tree)
*   [P2P Network](https://en.wikipedia.org/wiki/Peer-to-peer)

I truly recommend to read this two articles in order:

*   [Hashcash - A Denial of Service Counter-Measure, 2002, Adam Back](http://www.hashcash.org/papers/hashcash.pdf)
*   [Bitcoin: A Peer-to-Peer Electronic Cash System, 2008, Satoshi Nakamoto](https://bitcoin.org/bitcoin.pdf)

The first one introduces what's nowadays commonly known as "Proof of Work", and
it was mainly designed to make spamming more difficult, using it for electronic
currencies was a novel idea at the time (but introduced prior to the Bitcoin's
outbreak).

The second article is considered the foundational article of the blockchain &
cryptocurrencies fields. It introduces the "Nakamoto consensus" idea (consensus
between nodes achieved through "proof of work") and the "blockchain" idea. It's
worth to say that the word "blockchain" is not used in that paper,
[Satoshi Nakamoto](https://en.wikipedia.org/wiki/Satoshi_Nakamoto) used
"proof-of-work chain" instead.

The first Bitcoin implementation arrived some months after the article
publication, and it was done applying other relatively new inventions that were
not explicitly mentioned in the foundational article:
*[smart contracts](https://en.wikipedia.org/wiki/Smart_contract)*, an
[idea proposed by Nick Szabo in 1994](http://www.fon.hum.uva.nl/rob/Courses/InformationInSpeech/CDROM/Literature/LOTwinterschool2006/szabo.best.vwh.net/smart.contracts.html)
and extended in
[1996](http://www.fon.hum.uva.nl/rob/Courses/InformationInSpeech/CDROM/Literature/LOTwinterschool2006/szabo.best.vwh.net/smart_contracts_2.html).

I have to say that the "smart contracts" concept was for me one of the hardest
points to understand when I started. I had previous knowledge about how the
blocks were chained, about the proof of work... but not about that. And it's
easy to see why: it's not mentioned at all in the Bitcoin paper, Nick Szabo's
didn't give too many clues about how they should work, and it's difficult to
find good explanations about what they really are and how they work (most of
what you'll find in the Internet is pure bullshit, empty words).

One book where I found a pretty good explanation is
[*"Mastering Bitcoin, 2nd Edition"*](http://shop.oreilly.com/product/0636920049524.do),
written by *Andreas Antonopoulos*. You can find an online and free version in
Github: [bitcoinbook/bitcoinbook](https://github.com/bitcoinbook/bitcoinbook),
I truly recommend to read it if you're just starting.

**Notice:** Might be the case that at this point you are surprised, could be
that you read somewhere, or that somebody told you that the smart contracts were
introduced in *[Ethereum](https://en.wikipedia.org/wiki/Ethereum)*... but that's
plainly wrong. Bitcoin also allows to implement smart contracts, and in fact it
uses them all the time.

The key difference is on the capabilities that the scripts have in one platform
or another. While in Bitcoin the scripting capabilities were limited on purpose
to be non-Turing complete for security reasons,
[Vitalik Butterin](https://en.wikipedia.org/wiki/Vitalik_Buterin) proposed a way
to securely execute smart contracts in without limiting their capabilities (it's
worth to say that this came at a price, but I'll leave this point for some
future article).

Here I end my first and very brief post, but as a bonus I'll link two
interesting articles about who could be the mysterious Satoshi Nakamoto:
*   [Why I think Nick Szabo is Satoshi Nakamoto](https://medium.com/@altcoinbuzz/why-i-think-nick-szabo-is-satoshi-nakamoto-even-though-he-denies-it-8c999841fbbb)
*   [Nakamoto's Neighbor](https://www.forbes.com/sites/andygreenberg/2014/03/25/satoshi-nakamotos-neighbor-the-bitcoin-ghostwriter-who-wasnt/#f3c0e4c4a37d)
