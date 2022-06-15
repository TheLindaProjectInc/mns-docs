---
title: Managing a Name
description: 
published: true
date: 2022-06-15T00:59:28.075Z
tags: user guides
editor: markdown
dateCreated: 2022-06-13T12:10:35.806Z
---

# Updating Records
To change the resources an address resolves to, it's necessary to update that name's records in its resolver.

Each resolver may specify its own mechanism for updating records, but a standard method is implemented by the public resolver and many others.

Most commonly this is accomplished via a user-interface such as the [MNS App](https://metrix.domains/app).

Resolver data can be set by the owner of a name from the name's detail page.

![publicresolver.png](/publicresolver.png)

# Configuring Reverse Resolution
While 'regular' resolution involves mapping from a name to an address, reverse resolution maps from an address back to a name - or other metadata. MNS supports reverse resolution to allow applications to display MNS names in place of hexadecimal or MetrixCoin addresses.

![reverse-address.png](/reverse-address.png)

Before this can be done, the owner of the address has to configure reverse resolution for their address. This is done by searching for the MetrixCoin or hexadecimal address to find the reverse name, and [registering the .addr.reverse name](/user/registration#addrreverse).


