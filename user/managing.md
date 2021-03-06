---
title: Managing a Name
description: 
published: true
date: 2022-06-16T15:52:00.212Z
tags: user guides
editor: markdown
dateCreated: 2022-06-13T12:10:35.806Z
---

# Updating Records
To change the resources an address resolves to, it's necessary to update that name's records in its resolver.

Each resolver may specify its own mechanism for updating records, but a standard method is implemented by the public resolver.

Most commonly this is accomplished via a user-interface such as the [MNS App](https://metrix.domains/app).

Resolver data can be set by the owner of a name from the name's detail page.

![publicresolver.png](/publicresolver.png)

## Setting a Text Record
Text records map an abirtrary key to an arbitrary value. Setting a text record can be useful if DApps or users want to get the record for a given MNS name. 

A list of commonly used text records is provided to choose from, but any string can be provided as a key. A value can be any string, in many cases it is a username, but it can be anything and is dependent on how the service a MNS name holder is using has implemented usage of the record.

![txt_record.png](/txt_record.png)

# Configuring Reverse Resolution
While 'regular' resolution involves mapping from a name to an address, reverse resolution maps from an address back to a name - or other metadata. MNS supports reverse resolution to allow applications to display MNS names in place of hexadecimal or MetrixCoin addresses.

![reverse-address.png](/reverse-address.png)

Before this can be done, the owner of the address has to configure reverse resolution for their address. This is done by searching for the MetrixCoin or hexadecimal address to find the reverse name, and [registering the .addr.reverse name](/user/registration#addrreverse).





