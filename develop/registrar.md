---
title: Writing a Registrar
description: 
published: true
date: 2022-06-14T00:48:10.991Z
tags: 
editor: markdown
dateCreated: 2022-06-13T11:32:46.125Z
---

A registrar in MNS is simply any contract that owns a name, and allocates subdomains of it according to some set of rules defined in the contract code. A trivial first in first served contract is demonstrated below:

```
contract FIFSRegistrar {
    MNS mns;
    bytes32 rootNode;

    constructor(address mnsAddr, bytes32 node) {
        mns = MNS(mnsAddr);
        rootNode = node;
    }

    function register(bytes32 subnode, address owner) {
        var node = sha3(rootNode, subnode);
        var currentOwner = mns.owner(node);

        if (currentOwner != 0 && currentOwner != msg.sender) throw;

        mns.setSubnodeOwner(rootNode, subnode, owner);
    }
}
```

You may wish to set custom rules for the allocation of new names to your users; the rules you set are entirely up to you.

You should also bear in mind that as long as you retain ownership of the parent name - either directly or through another contract - your users have no guarantee that you will not take back ownership of their names and change what they resolve to. You may wish to consider committing ownership of the name to a contract that restricts your ability to control it. For an example of this, see [ENSNow](https://github.com/ensdomains/subdomain-registrar).