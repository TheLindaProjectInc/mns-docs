---
title: Troubleshooting
description: 
published: true
date: 2022-06-15T00:41:50.705Z
tags: user guides
editor: markdown
dateCreated: 2022-06-13T12:11:27.479Z
---

# Transaction Issues
## Contract Call Revert
Contract call reverts are caused by using incorrect parameters, lack of permission in the contract or a combination of these factors. In the case that contract calls revert, all input parameters and permissions should be checked.

## All 0 transacton hash
In some cases a transaction fails to be submitted to the network. In the case that the transaction hash is returned as all zeros, adjust the gas limit and/or gas price. This is frequently caused by dust MRX that is in the sending address. Usually increasing the gas price from 5000 to 10000 will resolve this issue.
![gas-adjustment.png](/gas-adjustment.png)
# MetriMask
## Adding Metrix Name Service(MNS) token to MetriMask 
MRC721 tokens can be added to the MetriMask web3 wallet.

**1. Go to the NFTs tab and click Add Token**
![metrimask-add-token.png](/metrimask-add-token.png)
**2. Add the token address for Metrix Name Service token ``38ddc88dea72954a65c12756174c7ad551024f7d``**
![metrimask-token-address.png](/metrimask-token-address.png)
**3. The token is now visible in MetriMask in the NFTs tab** 
![metrimask-nfts-tab.png](/metrimask-nfts-tab.png)
