---
title: Frequently Asked Questions
description: 
published: true
date: 2022-06-13T15:49:04.647Z
tags: 
editor: markdown
dateCreated: 2022-06-13T12:12:38.493Z
---

## Why are names registered as hashes?
Hashes provide a fixed length identifier that can easily be passed around between contracts with fixed overhead and no issues passing around variable-length strings.

## Which wallets and dapps support MNS so far?
Currently there are no wallets that fully support the MNS, however full support is planed for both MetriMask and desktop wallets (QT and Altitude).

## Once I own a name, can I create my own subdomains?
Yes. You can create whatever subdomains you wish and assign ownership of them to other people if you desire. You can even set up your own registrar for your domain.

## Can I change the address my name points to after I’ve bought it?
Yes, you can update the addresses and other resources pointed to by your name at any time.

## Can I register a TLD of my own in the MNS?
No. We consider MNS to be part of the 'global namespace' inhabited by DNS, and so we do our best not to pollute that namespace. MNS-specific TLDs are restricted to only .mrx (on MainNet), or .mrx and .test (on TestNet), plus any special purpose TLDs such as .addr.reverse which is required to permit reverse lookups.

## Who owns the MNS rootnode? What powers does that grant them?
The root node is owned by a multisig contract, with keys held by trustworthy individuals in the MetrixCoin community. We expect that this will be hands-off, with the root ownership only used to effect administrative changes, such as the introduction of a new TLD, or to recover from an emergency such as a critical vulnerability in a TLD registrar.

The keyholders are drawn from respected members of the community. We ask and expect them to exercise their individual judgement acting in the interests of the MNS community, rather than rubber-stamping requests made to them by MNS developers.

Since the owner of a node can change ownership of a subnode (unless they have otherwise locked it from their control), the owner of the root can change any node in the MNS tree. This means that the keyholders can replace the contracts that govern issuing and managing domains, giving them ultimate control over the structure of the MNS system and the names registered in it. However, the root key holders have locked control of the .mrx registrar contract, which means that even keyholders cannot affect the ownership of .mrx domains.

The keyholders are still capable of doing the followings:
- Control allocation and replacement of TLDs other than .mrx - this is required to implement DNSSEC integration.
- Enable and disable controllers for the .mrx registrar, which affect registration and renewal policies for .mrx names.
- Update the pricing for .mrx names.
- Receive and manage registration revenue.

Over time, we plan to reduce and decentralise human control over the system. Powers still held by the MNS root, such as those to set pricing and renewal conditions for domains, will be decentralised as robust systems become available to permit doing so.

## What about foreign characters? What about upper case letters? Is any unicode character valid?
Since the MNS contracts only deal with hashes, they have no direct way to enforce limits on what can be registered; character length restrictions are implemented by allowing users to challenge a short name by providing its preimage to prove it’s too short.

This means that you can in theory register both ‘foo.mrx’ and ‘FOO.mrx’, or even \<picture of my cat>.mrx. However, resolvers such as browsers and wallets should apply the nameprep algorithm to any names users enter before resolving; as a result, names that are not valid outputs of nameprep will not be resolvable by standard resolvers, making them effectively useless. Dapps that assist users with registering names should prevent users from registering unresolvable names by using nameprep to preprocess names being requested for registration.

## Nameprep isn’t enforced in the MNS system. Is this a security/spoofing/phishing concern?
It’s not enforced by the MNS contracts, but, as described above, resolvers are expected to use it before resolving names. This means that non-nameprep names will not be resolvable.

## What are the differences between MNS and other naming services such as Namecoin and Handshake?
MNS complements and extends the usefulness of DNS with decentralised, trustworthy name resolution for web3 resources such as blockchain addresses and distributed content, while Namecoin and Handshake are efforts to replace all or part of DNS with a blockchain-based alternative.

## About the .mrx Registrar
### What does it cost to register a .mrx domain?
Currently, registration costs are set at the following prices:
- 5+ character .mrx names: $5 in MRX per year.
- 4 character .mrx names: $80 in MRX per year.
- 3 character .mrx names $320 in MRX per year.

3 and 4 character names have higher pricing to reflect the small number of these names available.

### What happens if I forget to extend the registration of a name?
After your name expires, there is a 90 day grace period in which the owner can't edit the records but can still re-register the name. After the grace period, the name is released for registration by anyone. The released name continues to resolve your MRX address until the new owner overwrites it.

### What kinds of behaviours are likely to result in losing ownership of a name?
The .mrx registrar is structured such that names, once issued, cannot be revoked so long as an active registration is maintained.