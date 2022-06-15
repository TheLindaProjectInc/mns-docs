---
title: Writing a Registrar
description: 
published: true
date: 2022-06-15T00:20:39.001Z
tags: 
editor: markdown
dateCreated: 2022-06-13T11:32:46.125Z
---

A registrar in MNS is simply any contract that owns a name, and allocates subdomains of it according to some set of rules defined in the contract code. A trivial first in first served contract is demonstrated below:

```
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.4;

import "@metrixnames/mns-contracts/contracts/registry/MNS.sol";

contract HelloRegistrar {
    MNS mns;
    bytes32 rootNode;

    modifier only_owner(bytes32 label) {
        address currentOwner = mns.owner(
            keccak256(abi.encodePacked(rootNode, label))
        );
        require(currentOwner == address(0x0) || currentOwner == msg.sender);
        _;
    }

    /**
     * Constructor.
     * @param mnsAddr The address of the MNS registry.
     * @param node The node that this registrar administers.
     */
    constructor(MNS mnsAddr, bytes32 node) {
        mns = mnsAddr;
        rootNode = node;
    }

    /**
     * Register a name, or change the owner of an existing registration.
     * @param label The hash of the label to register.
     * @param owner The address of the new owner.
     */
    function register(bytes32 label, address owner) public only_owner(label) {
        mns.setSubnodeOwner(rootNode, label, owner);
    }
}
```

You may wish to set custom rules for the allocation of new names to your users; the rules you set are entirely up to you.

You should also bear in mind that as long as you retain ownership of the parent name - either directly or through another contract - your users have no guarantee that you will not take back ownership of their names and change what they resolve to. You may wish to consider committing ownership of the name to a contract that restricts your ability to control it. For an example of this, see [ENSNow](https://github.com/ensdomains/subdomain-registrar).