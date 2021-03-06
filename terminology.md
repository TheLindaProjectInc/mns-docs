---
title: Terminology
description: 
published: true
date: 2022-06-13T00:24:40.356Z
tags: 
editor: markdown
dateCreated: 2022-06-13T00:15:31.786Z
---

## Controller
The account that may edit the records of a name. The Controller may be changed by the Registrant or Controller.

## Label
An individual component of a name, such as 'alice'.

## Labelhash
The keccak256 hash of an individual label.

## Name
An MNS identifier such as 'alice.mrx'. Names may consist of multiple parts, called labels, separated by dots.

## Namehash
The algorithm used to process an MNS name and return a cryptographic hash uniquely identifying that name. Namehash takes a name as input and produces a node.

## Node
A cryptographic hash uniquely identifying a name.

## Owner
The owner of a name is the entity referenced in the MNS registry's owner field. An owner may transfer ownership, set a resolver or TTL, and create or reassign subdomains.

## Registrar
A registrar is a contract responsible for allocating subdomains. Registrars can be configured at any level of MNS, and are pointed to by the owner field of the registry.

## Registration
A registration is a registrar's record of a user's ownership of a name. This is distinct from the owner field in the Registry; registrations are maintained in the registrar contract and additionally store information on expiry date, fees paid, etc.

## Registrant
The owner of a registration. The registrant may transfer the registration, set the Controller, and reclaim ownership of the name in the registry if required.

## Registry
The core contract of MNS, the registry maintains a mapping from domain name (at any level - x, y.x, z.y.x etc) to owner, resolver, and time-to-live.

## Resolver
A resolver is a contract that maps from name to the resource (e.g., cryptocurrency addresses, content hash, etc). Resolvers are pointed to by the resolver field of the registry.