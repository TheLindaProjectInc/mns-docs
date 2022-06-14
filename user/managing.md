---
title: Managing a Name
description: 
published: true
date: 2022-06-13T17:06:42.252Z
tags: 
editor: markdown
dateCreated: 2022-06-13T12:10:35.806Z
---

# Creating Subdomains
The owner of any domain can configure subdomains as desired. This is achieved by creating a subdomain and setting its owner to the desired address - this can be the same as the owner of the parent domain, or any other address.

```
await mns.name('alice.mrx').createSubdomain('iam');
```
---
# Setting a Resolver
Before a newly created domain or subdomain can be used, a resolver address must be set. You may also want to do this if an updated resolver implementation is available that supports features that you want to make use of.

Most commonly, names are set to use a 'standard' resolver called the public resolver, which provides commonly-used functionality, but anyone may write and deploy their own special-purpose resolver; see the resolver interface definition for details.

```
await mns.name('iam.alice.mrx').setResolver('0x1234...');
```

Note that changing the resolver for a name will not automatically migrate records from the old resolver over; to do this you will need to follow the process outlined below for updating records.

---
# Updating Records
To change the resources an address resolves to, it's necessary to update that name's records in its resolver.

Each resolver may specify its own mechanism for updating records, but a standard method is implemented by the public resolver and many others. Some libraries provide functionality for updating a resolver's records using this interface.


Most records can be updated using the [MNS App](https://metrix.domains/app).
![publicresolver.png](/publicresolver.png)

## Updating the Address Record
If the resolver supports Muticoin Address resoltion, the name can be set or updated:
```
await mns.name('iam.alice.mrx').setAddr('MRX', '0x1234...');
```

## Updating the Name Record
If the resolver supports Name resoltion, the name can be set or updated:

```
await mns.name('iam.alice.mrx').setName('Alice');
```

## Updating Other Records
Some libraries - presently only mnslib - support updating other record types, such as content hashes and text records, using the same pattern.
```
await mns.name('iam.alice.mrx').setText('test', 'Test Record');
```

## Updating multiple records in one transaction
Public Resolver has multicall that permits users to set multiple records in a single operation. Read the [PublicResolver section](/mns/Resolver#publicresolver) for more detail.

---
# Configuring Reverse Resolution
While 'regular' resolution involves mapping from a name to an address, reverse resolution maps from an address back to a name - or other metadata. MNS supports reverse resolution to allow applications to display MNS names in place of hexadecimal addresses.

Before this can be done, the owner of the address has to configure reverse resolution for their address. This is done by calling the claim() method on the reverse resolver, found at the special name 'addr.reverse'.

Most commonly this is accomplished via a user-interface such as the [MNS App](https://metrix.domains/app).