---
title: Resolving Names On-chain
description: 
published: true
date: 2022-06-13T11:41:04.243Z
tags: 
editor: markdown
dateCreated: 2022-06-13T11:41:02.577Z
---

Solidity libraries for on-chain resolution are not yet available, but MNS resolution is straightforward enough it can be done trivially without a library. First, we define some pared-down interfaces containing only the methods we need:

```
abstract contract MNS {
    function resolver(bytes32 node) public virtual view returns (Resolver);
}

abstract contract Resolver {
    function addr(bytes32 node) public virtual view returns (address);
}
```

For resolution, only the resolver function in the MNS contract is required; other methods permit looking up owners and updating MNS from within a contract that owns a name.

With these definitions, looking up a name given its node hash is straightforward:

```
contract MyContract {
    // address for MainNet 0x29f1cfcc4fbd18573eddd3b80005275ee39f5e29 for TestNet
    MNS mns = MNS(0xc7dfd21c0db742ea6351e5da8989df633a75fa55);

    function resolve(bytes32 node) public view returns(address) {
        Resolver resolver = mns.resolver(node);
        return resolver.addr(node);
    }
}
```

While it is possible for a contract to process a human-readable name into a node hash, we highly recommend working with node hashes instead, as they are easier and more efficient to work with, and allow contracts to leave the complex work of normalizing the name to their callers outside the blockchain. Where a contract always resolves the same names, those names may be converted to a node hash and stored in the contract as a constant.