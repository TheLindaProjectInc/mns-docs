---
title: MNS Deployments
description: 
published: true
date: 2022-06-13T16:01:38.576Z
tags: 
editor: markdown
dateCreated: 2022-06-13T00:45:54.409Z
---

If you are working with an [MNS library](/develop/library), your library will automatically find the MNS deployment you need. If for whatever reason, you need to interact with MNS directly, details for the currently supported deployments are detailed here.

# Deployed Contracts
## MainNet
|  Name |  Address | Description |
|  :---  |  :---:   |  :---  |
| MNS Registry | <a href="https://explorer.metrixcoin.com/contract/c7dfd21c0db742ea6351e5da8989df633a75fa55/" target="_blank">c7dfd21c0db742ea6351e5da8989df633a75fa55</a> | The MNS Registry contract |
| MRX Registrar | <a href="https://explorer.metrixcoin.com/contract/38ddc88dea72954a65c12756174c7ad551024f7d/" target="_blank">38ddc88dea72954a65c12756174c7ad551024f7d</a>  | An MRC721 token and controller of the '.mrx' root node |
| MRX Registrar Controller | <a href="https://explorer.metrixcoin.com/contract/adc68013c85eecb897bce76a6d0d6dce47b9977a/" target="_blank">adc68013c85eecb897bce76a6d0d6dce47b9977a</a> | A controller which allows paid registration of '.mrx' names |
| Reverse Registrar | <a href="https://explorer.metrixcoin.com/contract/1e0e17c71f77db4ccd437eec131194c83517b710/" target="_blank">1e0e17c71f77db4ccd437eec131194c83517b710</a> | A registrar which allows any adress to claim their reverse name |
| Price Oracle | <a href="https://explorer.metrixcoin.com/contract/87a3d9dbf38548cfea9e634a24381960acca9b1c/" target="_blank">87a3d9dbf38548cfea9e634a24381960acca9b1c</a> | A price oracle which returns a price in MRX for a name based on length |
| Public Resolver | <a href="https://explorer.metrixcoin.com/contract/0f34d660e34ccafac00b463fdd3a80a7437c666d/" target="_blank">0f34d660e34ccafac00b463fdd3a80a7437c666d</a> | A general purpose public resolver |
| Default Reverse Resolver | <a href="https://explorer.metrixcoin.com/contract/594679c02371634e92fb98fcb216da5e5513c261/" target="_blank">594679c02371634e92fb98fcb216da5e5513c261</a> | The name resolver used by the reverse registrar |

## TestNet
|  Name |  Address | Description |
|  :---  |  :---:   |  :---  |
|  MNS Registry | <a href="https://testnet-explorer.metrixcoin.com/contract/29f1cfcc4fbd18573eddd3b80005275ee39f5e29/" target="_blank">29f1cfcc4fbd18573eddd3b80005275ee39f5e29</a> | The MNS Registry contract |
|  MRX Registrar | <a href="https://testnet-explorer.metrixcoin.com/contract/e260f7afd549fe33b1e08ddc185d03364a4296a0/" target="_blank">e260f7afd549fe33b1e08ddc185d03364a4296a0</a> | An MRC721 token and controller of the '.mrx' root node |
|  MRX Registrar Controller | <a href="https://testnet-explorer.metrixcoin.com/contract/59d98399b6b812a34d9c64fbe0862edb77e4db5e/" target="_blank">59d98399b6b812a34d9c64fbe0862edb77e4db5e</a> | A controller which allows paid registration of '.mrx' names |
|  Reverse Registrar  | <a href="https://testnet-explorer.metrixcoin.com/contract/dadc463ba0df2e5504900ed70ffe624c7e18a190/" target="_blank">dadc463ba0df2e5504900ed70ffe624c7e18a190</a> | A registrar which allows any adress to claim their reverse name |
|  Test Registrar | <a href="https://testnet-explorer.metrixcoin.com/contract/c6652c06a92c4472c92ce3ffefe1c057cbb10200/" target="_blank">c6652c06a92c4472c92ce3ffefe1c057cbb10200</a> | A FIFO registrar which allows free registration of '.test' names |
|  Price Oracle | <a href="https://testnet-explorer.metrixcoin.com/contract/03e97aa2d7d8f16d6aee4d54ad15db08ce09937c/" target="_blank">03e97aa2d7d8f16d6aee4d54ad15db08ce09937c</a> | A price oracle which always returns a price of 200 TestNet MRX regardless of name length |
|  Public Resolver | <a href="https://testnet-explorer.metrixcoin.com/contract/e45f6870ee50d31bfedfddeb88c7c22809e8281d/" target="_blank">e45f6870ee50d31bfedfddeb88c7c22809e8281d</a> | A general purpose public resolver |
|  Default Reverse Resolver | <a href="https://testnet-explorer.metrixcoin.com/contract/609b8ea7861bdab3d79d6a050c017b9cc1d95eb5/" target="_blank">609b8ea7861bdab3d79d6a050c017b9cc1d95eb5</a> | The name resolver used by the reverse registrar |