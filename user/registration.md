---
title: Registration & Renewal of Names
description: 
published: true
date: 2022-06-13T17:21:59.726Z
tags: 
editor: markdown
dateCreated: 2022-06-13T01:08:34.679Z
---

# Registrations
When users want to obtain a domain for the first time, they must interact with a registrar. Registrars are smart contracts that own a domain, and have a defined process for handing out subdomains. 

The registrar a user needs to interact with depends on the domain they want to obtain; for instance, a user wanting a .mrx name will have to interact with the .mrx registrar. Each registrar defines its own API for name registrations and renewals, where appropriate.

## .mrx
``.mrx`` names can be registered through the MRXRegistrarController which rents names with prices based on name length.
Registrations have a minimum duration of 28 days and no maximum duration.

**Name Pricing**
| Characters | Price(USD) per Annum |
| :---: | :---: |
| 3 | $320 |
| 4 | $80 |
| 5+ | $5 |

The controller works exclusively with plaintext labels (eg, 'alice' for 'alice.mrx').

To prevent frontrunning, the MRXRegistrarController requires a commit/reveal process for new name registrations (but not for renewals). To register a name, the user must:
| |
| :---: |
| **1. Generate a commitment hash from the desired name to register and a secret value.** |
| ![005_app_register_form_data.png](/005_app_register_form_data.png) |
| **2. Submit the commitment hash from step 1 to the controller.** |
| ![006_app_register_submit_metrimask.png](/006_app_register_submit_metrimask.png) |
| **3. Wait for at least 90 seconds, but no longer than 7 days.** |
| ![009_app_register_processing.png](/009_app_register_processing.png) |
| **3. Submit a registration request for the name, along with the secret value from step 1 and a value of the rent price.** |
| ![016_app_register_final.png](/016_app_register_final.png) | 
> It is recommended to include 5% extra MRX to the .mrx registration price to accomodate any price changes.
{.is-info}


This process ensures that registrations cannot be frontrun unless the attacker is able to censor the user's transactions for at least 90 seconds.
## .addr.reverse
``.addr.reverse`` names can be registered for free through the ReverseRegistrar if the address calling the contract is the address belonging to the lookup.
| |
| :---: |
| **1. Give an Address Resolver and an owner to claim the address** |
| ![register-reverse.png](/register-reverse.png) |

## .test
``.test`` can be registered for free to the first person to claim them, but expire registrations 4 weeks after they're initially claimed.
> The test registrar only exists on the TestNet
{.is-warning}


# Renewals

## .mrx 
Renewals can be made by anyone, as long as sufficient funds are provided. Because the rent price may vary over time, callers are recommended to send slightly more than the value returned by rentPrice - a premium of 5% will likely be sufficient. Any excess funds are returned to the caller.

Renewals can also be done from the MNS App at the name details page.
![renew-selected.png](/renew-selected.png)

A price in MRX will be presented depending on the length of time selected.
![renew-modal.png](/renew-modal.png)
