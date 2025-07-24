+++
title = 'A Letter to a Public Key: Rethinking Email Address Ownership'
date = 2025-07-24T17:53:30+04:00
draft = false
summary = 'A four step tutorial for using decentralized messaging in Eppie CLI'
+++

{{< figure src="/addresses.png" >}}

So, we are building a peer-to-peer email system where users truly own their addresses and data. We’ve already talked [about data](https://blog.eppie.io/post/feudal/) — today, let’s focus on addresses.

## Who owns your email address?

In traditional email, you don’t truly own your address — you rent it. There are two typical scenarios:

1. **An address on a provider’s domain** — like username@gmail.com. That address is essentially owned and controlled by the provider.
2. **An address on a “custom” domain** — like you@yourdomain.com. But even here, you're only renting the domain from a registrar.

In practice, your address seems to be under your control — until it isn’t. You might get suspended for breaking service rules. Someone could impersonate you and gain access. Your domain might expire. At the end of the day, critical decisions are made by the provider. Loss of access happens regularly — and it’s always their decision.

Some real-world examples:

- **Google** [deletes](https://support.google.com/accounts/answer/12418290?hl=en) accounts it deems inactive. You can lose your email just for not logging in.
- **X (Twitter)** has reclaimed attractive usernames for internal use here’s [a thread](https://x.com/jeremyvaught/status/1687223289482035200) about the @music account.
- **Skiff**, a privacy-first email startup with $14M in funding and 2M users, shut down in 2024 after being acquired by Notion. Users had six months to migrate — then the servers were shut down. Those who used Skiff for third-party logins were locked out. Here’s [a case](https://community.openai.com/t/changing-email-address-as-skiff-will-be-shut-down/622478) involving an OpenAI user unable to change their email address.

Email today is far more than messaging. It holds licenses, contracts, medical records. It’s the backbone of your online identity — and gateway to hundreds of services. Losing it can be a digital nightmare.

One could argue that running your own email server is a solution — but this setup still depends on domain registrars, hosting providers, and certificate authorities. If any of them decide to revoke your domain or certificate, you lose access. That’s still not true ownership. We believe ownership should mean ownership — not renting from providers, registrars, or certificate authorities.

That’s why we’re building a third model. In **Eppie**, your address isn’t rented. It is **created** by you — and you fully own it. Even if Eppie were to shut down like Skiff, your address would stay active on the decentralized network. No central authority, no provider lock-in.

Here’s how it works.

## How does Eppie handle addresses?

In Eppie, you generate your address **yourself**, on your own device, **in a single click** — as a **cryptographic public key**. Only you hold the private key needed to read and sign messages. Eppie connects to the decentralized network, fetches messages addressed to your key, and decrypts them. The ability to decrypt proves ownership. Concepts like login or authentication are irrelevant — there’s no gatekeeper.

While managing cryptographic keys may sound daunting, Eppie is designed to handle this complexity for you. Key management happens behind the scenes – securely and seamlessly. Whether it's generating, storing, or using your private key across multiple devices, Eppie takes care of it in a way that feels natural and intuitive. You get the benefits of strong encryption and ownership – without having to become a cryptography expert.

The transport layer is built on DHT and SBBS, storage — on IPFS. More on these in future posts. Or explore our [GitHub](https://github.com/Eppie-io/) if you're curious.

### Address format

Eppie addresses are based on compressed **secp256k1 public keys** (33 bytes). They’re used for ECIES encryption and ECDSA signature verification.

To make addresses human-friendly, they’re encoded in custom **Base32** (alphabet: abcdefghijkmnpqrstuvwxyz23456789, excluding `o`, `l`, `0`, `1` to reduce ambiguity).

Example:

`ahejyckdjrciwq9dkdgqmemu26pr5qsmbwhfk4vf65w6sw9ivinig@eppie`

This fits standard formats like address@domain and hybrid ones like email+address@domain.

Supported formats:

- `address@eppie` — for peer-to-peer communication inside the network.
- `address@domain`, e.g. `ahejy...@bridge.com` — enables bridging from external mail systems.
- `email+address@domain`, e.g. `alice+ahejy...@gmail.com` — hybrid format usable for both web3 and traditional emails.

### Why hybrid addresses matter

One of Eppie’s core strengths is flexibility. The hybrid `email+address@domain` model enables seamless communication between legacy email and decentralized networks.

Hybrid format allows you to use the same address within Eppie and in traditional email. When a message is sent through SMTP, it is delivered to your normal email address. However, when a message is sent from the decentralized network, it skips centralized servers entirely.

For those wondering how hybrid addresses work with traditional email servers — formats like `alice+ahejy...@gmail.com` rely on the subaddressing standard (RFC 5233), widely supported by email providers. This allows seamless delivery into your regular inbox. Basically, traditional email just ignores everything after `+` sign, which allows us to encode additional information within the address without breaking compatibility.

You can even register your Bitcoin address as an email identity — e.g.: 

`bc1qar0srrr7xfkvy5l643lydnw9re59gtzzwf5mdq@eppie`. 

This address can be used for communication within Eppie, and even to receive emails from classic email.

Once you sign a transaction from that address, it’s verified as yours and ready for use.

Other supported formats (coming soon):

- `bc1qar0...@bitcoin`
- `0xd8dA6B...@ethereum`
- `npub1v93...@nostr`

**Human-readable aliases** through ENS and DNS will be available soon after launch. Their job is to map a nice name like `alice.epp` to a cryptographic address. It’s easy to remember, like a traditional email address.

For ENS, the address will look like this: `alice.eth`.

For DNS — `alice.com` or `alice.site.com`, if it's a second-level domain.

And for our decentralized name service, which we also plan to launch — `alice.epp` or `alice@eppie`.

We’re developing open-source bridges anyone can host, allowing messages to flow from SMTP into Eppie. Two-way bridges are technically challenging (especially spam protection), but we welcome community initiatives here.

## How is this beneficial to you?

- An Eppie address is a personal, sovereign digital identifier.
- You can use it anywhere a standard email format is required.
- Eppie acts as a bridge between Web2 and Web3 — you can exchange messages between p2p and traditional email.
- It can serve as a universal tool for Web2 and Web3 authentication. You can create unique addresses for each service (which also works as anti-spam).
- It’s fully portable — you can carry your address across platforms and generations.
- If both you and your contact use Eppie, you can communicate using regular email addresses without losing encryption benefits.
- You can sign documents and conversations — no PDFs or DocuSign needed, just your address.
- We recently introduced AI into Eppie — addresses can now be used for communication between autonomous AI agents.
- Eppie addresses enable connections to DAOs, NFTs, and on-chain identities, receiving blockchain contract notifications, and building in-game messaging in metaverses or DAOs.
- You fully control who can reach     you — using whitelists, sender validation, proof-of-work filters, or     custom rules. Unlike traditional email, no message reaches your inbox     unless you allow it. 
- You can generate unlimited     addresses for different purposes — making targeted spam almost impossible.

***

Email address is your entry point into digital communication. Today, users don’t control it: you either rent a name from an email provider or rent a domain from a registrar.

The address system in Eppie is generated directly on your device, independent of any servers, and cannot be taken away. You can have one address, several, or even a whole hierarchy for different purposes. And no one can tell you what you can or cannot do with them.

We believe that with the right tools and UX, true ownership can be simple. That’s the challenge we’re embracing.

[Join the waitlist](https://eppie.io/?ref=hackernoon.com) and give us a [star GitHub](https://github.com/Eppie-io/Eppie-App?ref=hackernoon.com) — your support helps us grow. Thank you!