---
title: Registry
description: 
published: true
date: 2022-06-12T23:37:15.862Z
tags: 
editor: markdown
dateCreated: 2022-06-12T23:37:14.033Z
---

# MNS Registry
The MNS registry, which is based on the ENS registry is the core smart contract that lies at the heart of MNS resolution. All MNS lookups start by querying the registry. The registry maintains a list of domains, recording the owner, resolver, and TTL for each, and allows the owner of a domain to make changes to that data. 

The ENS registry is specified in [EIP 137](https://eips.ethereum.org/EIPS/eip-137).