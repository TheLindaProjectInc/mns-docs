---
title: Transferring & Claiming Names
description: 
published: true
date: 2022-06-13T14:13:33.790Z
tags: 
editor: markdown
dateCreated: 2022-06-13T11:51:21.403Z
---

The procedure for setting the controller, claiming and/or transferring a name is dependent on which registrar controls the top level domain (TLD) of a specific name. 

**Supported TLDs**
| Registrar | TLD |
| :--- | :--- |  
| MRX Registrar |.mrx | 
| Reverse Registrar | .addr.reverse | 
| Test Registrar | .test | 

# Transferring a Name

## .mrx
The MRX Registrar is also an MRC721 token (NFT) which controls the .mrx TLD. Whichever address is transfered this token can claim control of the .mrx name in the MNS registry.
| |
| :---: |
| **Use the transfer button to get to the transfer form** |
|![transfer-1.png](/transfer-1.png)|
| **Input an address to transfer to and perform the transfer with web3 wallet** |
| ![transfer-2.png](/transfer-2.png) |

Once a .mrx name is transferred, the new owner can [claim the name](/user/transfer#mrx-1).

## .addr.reverse
The Reverse Registrar controls the .addr.reverse TLD. This registrar is used to provide reverse resolution of MetrixCoin addresses. If an address is the address in the name or an authorized controller of the name, it may transfer the name by claiming it for another address.


# Claiming a Name

## .mrx
The owner or an authorized controller of the [**Metrix Name Service(MNS) token**](https://explorer.metrixcoin.com/mrc721/38ddc88dea72954a65c12756174c7ad551024f7d/) may call the reclaim method and claim the name in the MNS registry.

| |
| :---: |
| **Use the claim tab to get to the claim section and input your MetrixCoin address** |
|![claim-mrx.png](/claim-mrx.png)|


## .addr.reverse
The owner or an authorized controller of the address can claim or reclaim the name by registering it.
| |
| :---: |
| **Use the register tab to get to the registration section and input the resolver you want to use and your MetrixCoin address** |
|![register-reverse.png](/register-reverse.png)|