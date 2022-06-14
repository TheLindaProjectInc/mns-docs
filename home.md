---
title: 
description: 
published: true
date: 2022-06-13T17:14:20.593Z
tags: 
editor: markdown
dateCreated: 2022-06-12T20:47:53.978Z
---

<p align="center">
  <img width="420" height="420" src="/logo-purple-1080.png">
  <p align="center" style="font-size: 32px; font-weight: bold;">Metrix Name Service</p>
</p>

# Introduction
The Metrix Name Service (MNS) is a distributed, open, and extensible naming system built on the MetrixCoin blockchain and based on the [Ethereum Name Service (ENS)](https://github.com/ensdomains).

The main purpose of the MNS is to take human readable names like 'metroid.mrx' and convert them to machine readable identifiers such as MetrixCoin addresses, other cryptocurrency addresses, content hashes, and more.

The MNS also supports ‘reverse resolution’, making it possible to associate metadata such as canonical names or interface descriptions with MetrixCoin addresses.

The MNS has similar goals to DNS, the Internet’s Domain Name Service, but has significantly different architecture due to the capabilities and constraints provided by the EVM on the MetrixCoin blockchain. Like DNS, MNS operates on a system of dot-separated hierarchical names called domains, with the owner of a domain having full control over subdomains.

Top-level domains, like ‘.mrx’ and ‘.test’, are owned by smart contracts called registrars, which specify rules governing the allocation of their subdomains. Anyone may, by following the rules imposed by these registrar contracts, obtain ownership of a domain for their own use. 

Because of the hierarchal nature of MNS, anyone who owns a domain at any level may configure subdomains - for themselves or others - as desired. For instance, if Alice owns 'alice.mrx', she can create 'pay.alice.mrx' and configure it as she wishes.

The MNS is deployed on the MetrixCoin MainNet and TestNet. If you use a library such as the [mnslib](https://github.com/TheLindaProjectInc/mnslib) Javascript library, or an end-user application, it will automatically detect the network you are interacting with and use the MNS deployment on that network.

You can try MNS out for yourself now by using the [MNS App](https://metrix.domains/app).


## MNS Architecture
The MNS has two principal components: the [Registry](/mns/Registry), and [Resolvers](/mns/Resolver).

![mns-architecture.png](/mns-architecture.png)

The MNS registry consists of a single smart contract that maintains a list of all domains and subdomains, and stores three critical pieces of information about each:
- The owner of the domain
- The resolver for the domain
- The caching time-to-live (TTL) for all records under the domain

The owner of a domain may be either an external account (a user) or a smart contract. A registrar is simply a smart contract that owns a domain and issues subdomains of that domain to users that follow some set of rules defined in the contract.

Owners of domains in the MNS registry may:
- Set the resolver and TTL for the domain
- Transfer ownership of the domain to another address
- Change the ownership of subdomains

The MNS registry is deliberately straightforward and exists only to map from a name to the resolver responsible for it.

Resolvers are responsible for the actual process of translating names into addresses. Any contract that implements the relevant standards may act as a resolver in MNS. General-purpose resolver implementations are offered for users whose requirements are straightforward, such as serving an infrequently changed address for a name.

Each record type - cryptocurrency address, IPFS content hash, and so forth - defines a method or methods that a resolver must implement in order to provide records of that kind. New record types may be defined at any time via the EIP/MIP standardization process, with no need to make changes to the MNS registry or to existing resolvers in order to support them.

Resolving a name in MNS is a two-step process: First, ask the registry what resolver is responsible for the name, and second, ask that resolver for the answer to your query.

![resolving-steps.png](/resolving-steps.png)

In the above example, we're trying to find the MetrixCoin EVM address pointed to by 'foo.mrx'. First, we ask the registry which resolver is responsible for 'foo.mrx'. Then, we query that resolver for the address of 'foo.mrx'.


## Namehash
Resource constraints in smart contracts make interacting directly with human-readable names inefficient, so the MNS works purely with fixed length 256-bit cryptographic hashes. In order to derive the hash from a name while still preserving its hierarchal properties, a process called Namehash is used. For example, the namehash of 'alice.mrx' is 0x13f99ca63779ff0a9066f002cc875de1463c0e1d4e8ee83a6b9ea5fb33552433; this is the representation of names that is used exclusively inside MNS.

Namehash is a recursive process that can generate a unique hash for any valid domain name. Starting with the namehash of any domain - for example, 'alice.mrx' - it's possible to derive the namehash of any subdomain - for example 'iam.alice.mrx' - without having to know or handle the original human-readable name. It is this property that makes it possible for MNS to provide a hierarchal system, without having to deal with human-readable text strings internally.

Before being hashed with namehash, names are first normalized, using a process called UTS-46 normalization. This ensures that upper- and lower-case names are treated equivalently, and that invalid characters are prohibited. Anything that hashes and resolves a name must first normalize it, to ensure that all users get a consistent view of MNS.

For details on how namehash and normalization works, see the developer documentation on [https://github.com/ethereum/EIPs](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-137.md).


## Getting Started
MNS has documentation for a variety of audiences, including MetrixCoin users, dapp developers and contract developers.

### I'm a MetrixCoin holder/user and want to use the MNS
Check out the User Guides, starting with [Registering & Renewing Names](/user/registration).

### I'm a DApp developer and want to add MNS support to my DApp
Check out the dapp developer guide, starting with [MNS DApp Integration](/develop/dapp).

### I'm a contract developer and want to interact with MNS from my contract code
Check out the Contract Developer Guide, starting with [Resolving Names On-chain](/develop/resolving) You can also [write your own resolver](/develop/resolver) (to customize the process of looking up names), or your own [registrar](/develop/registrar) (to customize the process of registering new names).
