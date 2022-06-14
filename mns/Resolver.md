---
title: Resolver
description: 
published: true
date: 2022-06-12T23:59:59.057Z
tags: 
editor: markdown
dateCreated: 2022-06-12T23:59:56.286Z
---


## PublicResolver
The default public resolver.

The public resolver implements a general-purpose MNS resolver that is suitable for most standard MNS use-cases. The public resolver permits updates to MNS records by the owner of the corresponding name.

The public resolver implements the following EIPs:
- [EIP 137](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-137.md) - Contract address interface (addr()).
- [EIP 165](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-165.md) - Interface Detection (supportsInterface()).
- [EIP 181](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-181.md) - Reverse resolution (name()).
- [EIP 205](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-205.md) - ABI support (ABI()).
- [EIP 619](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-619.md) - SECP256k1 public keys (pubkey()).
- [EIP 634](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-634.md) - Text records (text()).
- [EIP 1577](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1577.md) - Content hash support (contenthash()).
- [EIP 1185](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1185.md) - DNS record support (dnsRecords())
- [EIP 2304](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-2304.md) - Multicoin support (addr()).


> While the PublicResolver provides a convenient default implementation, many resolver implementations and versions exist. Callers must not assume that a domain uses the current version of the public resolver, or that all of the methods described here are present. To check if a resolver supports a feature, see [check interface support](/mns/Resolver#check-interface-support).
{.is-info}

## DefaultReverseResolver
The default resolver used by the Reverse registrar.

The  default reverse resolver is a simple MNS resolver that is used by the reverse registrar. The reverse resolver permits updates to MNS records by the owner of the corresponding name.

The reverse resolver implments the following EIPs:
- [EIP 165](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-165.md) - Interface Detection (supportsInterface()).
- [EIP 181](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-181.md) - Reverse resolution (name())