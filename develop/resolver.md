---
title: Writing a Resolver
description: 
published: true
date: 2022-06-23T15:43:42.793Z
tags: developer guides
editor: markdown
dateCreated: 2022-06-13T11:28:44.514Z
---

Resolvers are specified in [EIP137](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-137.md). A resolver must implement the following method:
```
function supportsInterface(bytes4 interfaceID) constant returns (bool);
```
`supportsInterface` is defined in [EIP165](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-165.md), and allows callers to determine if a resolver supports a particular record type. Record types are specified as a set of one or more methods that a resolver must implement together. Currently defined record types include:

| Record Type | Function(s) | Interface ID | Definition |
| :--- | :--- | :---: | :---: |
| EVM Address | addr | 0x3b3b57de | [EIP137](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-137.md) |
| MNS Name | name | 0x691f3431 | [EIP181](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-181.md) |
| ABI Specification | ABI | 0x2203ab56 | [EIP205](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-205.md) |
| Public Key | pubkey | 0xc8690233 | [EIP619](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-619.md) |
| Text Records | text | 0x59d1d43c | [EIP634](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-634.md) |
| DNS Records | dnsRecord | 0xa8fa5682 | [EIP1185](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1185.md) |
| Contenthash | contenthash | 0xbc1c58d1 | [EIP1577](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1577.md) |
| Interface Discovery |interfaceImplementer | 0x01ffc9a7 | [EIP1844](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1844.md) |
| Multicoin | addr | 0xf1cb7e06 | [EIP2304](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-2304.md) |

`supportsInterface` must also return true for the interfaceID value 0x01ffc9a7, which is the interface ID of `supportsInterface` itself.

Additionally, the content interface was used as a defacto standard for Swarm hashes, and has an interface ID of 0xd8389dc5. New implementations should use contenthash instead.

## Example Resolver
A simple resolver that supports only the addr type might look something like this:

```
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.4;


contract HelloResolver  {
    
    function supportsInterface(bytes4 interfaceID) public pure returns (bool) {
        return interfaceID == 0x3b3b57de;
    }

    function addr(bytes32 /*nodeID*/) public view returns (address) {
        return address(this);
    }
}
```
This trivial resolver always returns its own address as answer to all queries. Practical resolvers may use any mechanism they wish to determine what results to return, though they should be constant, and should minimise gas usage wherever possible.