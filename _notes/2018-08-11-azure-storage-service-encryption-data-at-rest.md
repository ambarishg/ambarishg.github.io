---
layout: post
title: Azure Storage Service Encryption
categories: Cloud
date: 2018-08-12 01:30:00
tags:
- azure
- azure security
description: Azure Storage Service Encryption 
---

**Azure Storage Service Encryption** for data at rest helps you protect your data to meet your organizational security and compliance commitments. With this feature, the Azure storage platform automatically `encrypts your data` before persisting it to Azure Managed Disks, Azure Blob storage, Azure Files, or Azure Queue storage, and decrypts the data before retrieval. The handling of encryption, encryption at rest, decryption, and key management in Storage Service Encryption is transparent to users. All data written to the Azure storage platform is encrypted through **256-bit AES encryption**, one of the strongest block ciphers available.                   

Storage Service Encryption is enabled for all new and existing storage accounts and cannot be disabled. Because your data is secured by default, you don't need to modify your code or applications to take advantage of Storage Service Encryption.                

The feature automatically encrypts data in:

* Azure `storage services`:
    - Azure Managed Disks
    - Azure Blob storage
    - Azure Files
    - Azure Queue storage
    - Azure Table storage.
* Both performance tiers (Standard and Premium).
* Both deployment models (Azure Resource Manager and classic).
* Storage Service Encryption does not affect the performance of Azure storage services.                     

You can use Microsoft-managed encryption keys with Storage Service Encryption, or you can use your own encryption keys.                    

