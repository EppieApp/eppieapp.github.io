+++
title = 'Sending Emails from Gmail to Bitcoin'
date = 2025-10-20T18:55:01+04:00
draft = false
summary = 'How Eppie bridges the gap between decentralized finance and digital communication.'
+++

{{< figure src="/btc_addr/main.png" >}}

The convergence of financial transactions and digital communication is a natural step in the evolution of decentralized systems. In Eppie, we explore this intersection by enabling Bitcoin addresses to function not only as wallets but also as communication endpoints.

Recently, decentralized addresses went live in our test network. You can read an overview [here](https://blog.eppie.io/post/addresses/). In short: an address in Eppie is a cryptographic public key, and the private key gives the user exclusive full control over their mailbox.

And since an address is just a public key, nothing stops us from integrating existing decentralized networks with compatible cryptography – like Bitcoin or Ethereum. That’s exactly what we’re doing. Please welcome a major new feature in Eppie: your crypto identity can now double as an inbox. Create a new address or import an existing one and start receiving emails at it. Both Bitcoin and Ethereum are already working on our Testnet, more networks to be added later. And it is what we’ll be talking about today, with Bitcoin as an example.

By the way, we’re aiming to launch an open test later this year. [Sign up](https://eppie.io/) if you’d like to join.
 

## Why does Bitcoin need messaging?

Money doesn’t exist without communication – any deal must be negotiated. And today Bitcoin doesn’t have its own tool for communication inside its decentralized network. Of course, you can chat on Discord, Gmail, or Telegram. But as soon as you have to turn to centralized services, the decentralized ecosystem stops being truly decentralized. By integrating Bitcoin addresses we want to solve this problem.

There’s another benefit: lowering the entry barrier for newcomers. A Bitcoin address in Eppie is essentially a “light wallet.” Which means that an email user automatically gets their own crypto wallet, only presented in the familiar terminology of an email address. For millions of people, this can be a natural and simple way to get started with crypto.

{{< figure src="/btc_addr/userflow_1.jpg" >}}

Integration also makes it possible to exchange messages between regular email accounts and Bitcoin addresses. It works like this:

* A user writes from their Gmail to an address like `<bitcoin-address>@bridge.com`
* The email arrives at a bridge server, which accepts regular mail, encrypts it, and forwards it into the decentralized network.
* The bridge routes it to Eppie, and the recipient gets the message at their Bitcoin address inside Eppie.

{{< figure src="/btc_addr/userflow_2.jpg" >}}

In the future, we’ll release an Eppie library for wallet integration – so you’ll be able to receive emails directly in your wallet without even installing Eppie.

Expect a whole lot of neat features: like the ability to attach payments to emails, or new email notifications right in your crypto wallet.

{{< figure src="/btc_addr/userflow_3.jpg" >}}


## How it looks in Eppie

In Eppie, the address looks like this:

```
<bitcoin-address>@bitcoin
```

For example:

```
1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa@bitcoin
```

Compatibility with traditional email is preserved: you can also use `<bitcoin-address>@domain.com` or hybrid `email+<bitcoin-address>@domain.com`. All modern Bitcoin address types are supported, from old Legacy (`1…`) to Taproot (`bc1p…`). And once post-quantum addresses are introduced, we’ll support those too.

{{< figure src="/btc_addr/success.png" >}}
Our very first successful attempt to send an email to a Bitcoin address.

To use a Bitcoin address as a mailbox, you need to prove that it’s really yours. This is done via a blockchain transaction: the address must have “spent” coins at least once. In practice, the minimum transfer today is around 25 cents. You can send a transaction to yourself. Or you can import any existing address that has already spent funds – in that case, the public key has already been revealed, and no separate action is needed.

In the transaction, the full public key is revealed, and that’s what becomes the cryptographic basis for message encryption. Depending on the address type there are differences: for Legacy the key is revealed in scriptSig, for SegWit – in witness, and for Taproot – in the script-path. But the idea is always the same: only the holder of the private key can decrypt incoming messages.

Right now, registering a Bitcoin address requires some knowledge of how the network works. But we’re exploring ways to make this easier. For example, one user could invite another to create a Bitcoin address in Eppie, initiating a delayed transaction that only gets broadcast if the other user accepts. That way, more experienced users can help newcomers.

After that, everything works just like with native Eppie addresses: messages are encrypted end-to-end, each conversation uses ephemeral keys, and emails are signed with ECDSA so the recipient can be sure the sender is genuine. We’ll publish more technical details in upcoming posts.

There’s one caveat: once a public key is revealed on the blockchain, it stays there forever. If you reuse the same address for both transactions and email, it’s possible to link them. This is a privacy risk. That’s why it’s better to generate a new Bitcoin address for each communication channel.

🎥 Video: https://youtu.be/kE2JtnKXYoc

 

## Beyond the horizon

Bringing together cryptocurrencies and email may open the door to new user scenarios that weren’t possible before in decentralized systems.

Take advanced banking products like escrow – a deal with a conditional deposit, where funds are locked by a third party and only released to the seller once the conditions are met. Today this works only through centralized intermediaries, usually banks. In blockchain contexts, similar deals can be implemented through smart contracts. But combined with email, such services become much more accessible and understandable.

Imagine a buyer and seller negotiating a deal by email. The buyer sends funds to a multisig address and in the email describes the condition: “funds will be released once I confirm receipt of the goods.” A third party, an arbiter, included in the email thread, guarantees fairness. If everything goes smoothly, the buyer confirms by email and the funds are released to the seller. If a dispute arises, the arbiter decides. It looks like an ordinary email exchange, but in fact it functions as an escrow service. Without banks, without centralized platforms.

***

Where money and email come together, there’s room for a whole new layer of services. The potential seems huge. We probably haven’t scratched the surface yet.

Want to be among the first to test decentralized addresses and Bitcoin integration? Sign up for the waitlist on our [website](https://eppie.io/). And if you’d like to give us a star on GitHub — [here’s the link](https://github.com/Eppie-io).
