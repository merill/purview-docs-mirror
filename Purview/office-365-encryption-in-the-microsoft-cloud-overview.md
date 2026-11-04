---
layout: Conceptual
title: Encryption in the Microsoft cloud | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/office-365-encryption-in-the-microsoft-cloud-overview
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
f1.keywords:
- NOCSH
ms.author: kreagle
author: k-reagle
manager: laurawi
ms.date: 2024-03-18T00:00:00.0000000Z
audience: ITPro
ms.topic: article
ms.service: purview
ms.subservice: purview-encryption
search.appverid:
- MET150
ms.collection:
- purview-compliance
- Strat_O365_Enterprise
description: Read an overview of the various forms of encryption used to keep customer data safe in the Microsoft cloud.
ms.custom: seo-marvel-apr2020
locale: en-us
document_id: 2725db86-7bce-7ec1-dc3c-27adeb19f5b8
document_version_independent_id: 2725db86-7bce-7ec1-dc3c-27adeb19f5b8
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/office-365-encryption-in-the-microsoft-cloud-overview.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: office-365-encryption-in-the-microsoft-cloud-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/office-365-encryption-in-the-microsoft-cloud-overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/486161dc-fa28-4625-9b1c-1a21d690bc8d
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
- https://authoring-docs-microsoft.poolparty.biz/devrel/6ab06385-661e-4214-8870-bbe4071c960d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5dd28c86-729c-4723-ab5a-57e26fcec2a8
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
- https://authoring-docs-microsoft.poolparty.biz/devrel/131ba09e-4280-4ae7-8622-1f9f1c0daad1
platformId: c68450fd-81a9-8b54-6550-53b64fa092d4
---

# Encryption in the Microsoft cloud | Microsoft Learn

> 
> *[Microsoft Purview service description](/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description)*

Customer data within Microsoft's enterprise cloud services is protected by several technologies and processes, including various forms of encryption. (Customer data in this document includes Exchange Online mailbox content, e-mail body, calendar entries, and the content of e-mail attachments, and if applicable, Skype for Business content, SharePoint site content, and the files stored within sites, and files uploaded to OneDrive or Skype for Business.) Microsoft uses multiple encryption methods, protocols, and ciphers across its products and services. Encryption helps provide a secure path for customer data to travel through our cloud services, and helps protect the confidentiality of customer data stored within our cloud services. Microsoft uses some of the strongest, most secure encryption protocols available to provide barriers against unauthorized access to customer data. Proper key management is also an essential element of encryption best practices, and Microsoft works to ensure that all Microsoft-managed encryption keys are properly secured.

Customer data stored within Microsoft's enterprise cloud services is protected using one or more forms of encryption. (Multiple non-Microsoft auditors independently validate our crypto policy and its enforcement. Reports of those audits are available on the [Service Trust Portal](https://aka.ms/stp).)

Microsoft provides service-side technologies that encrypt customer data at rest and in transit. For example, for customer data at rest, Microsoft Azure uses [BitLocker](/en-us/windows/device-security/bitlocker/bitlocker-overview) and [DM-Crypt](https://en.wikipedia.org/wiki/Dm-crypt), and Microsoft 365 uses BitLocker, [Azure Storage Service Encryption](/en-us/azure/), [Distributed Key Manager](exchange-online-secures-email-secrets) (DKM), and Microsoft 365 service encryption. For customer data in transit, Azure, Office 365, Microsoft Commercial Support, Microsoft Dynamics 365, Microsoft Power BI, and Visual Studio Team Services use industry-standard secure transport protocols, such as Internet Protocol Security (IPsec) and Transport Layer Security (TLS), between Microsoft datacenters and between user devices and Microsoft datacenters.

In addition to the baseline level of cryptographic security provided by Microsoft, our cloud services also include cryptography options that you can manage. For example, you can enable encryption for traffic between their Azure virtual machines (VMs) and their users. With [Azure Virtual Networks](https://azure.microsoft.com/services/virtual-network/), you can use the industry-standard IPsec protocol to encrypt traffic between your corporate VPN gateway and Azure. You can also encrypt traffic between the VMs on your virtual network. In addition, [Microsoft Purview Message Encryption](set-up-new-message-encryption-capabilities) allows you to send encrypted mail to anyone.

Following the Public Key Infrastructure Operational Security Standard, which is a component of the Microsoft Security Policy, Microsoft uses the cryptographic capabilities included in the Windows operating system for certificates and authentication mechanisms. These mechanisms include the use of cryptographic modules that meet the U.S. government's [Federal Information Processing Standards](https://csrc.nist.gov/publications/PubsFIPS.html) (FIPS) 140-2 standard. You can search for the relevant National Institute of Standards and Technology (NIST) certificate numbers for Microsoft using the [Cryptographic Module Validation Program (CMVP)](https://csrc.nist.gov/projects/cryptographic-module-validation-program/validated-modules/search).

> 
> [NOTE] The Microsoft Security Policy is not made available as a public download. For information about the policy, contact Microsoft.

FIPS 140-2 is a standard designed specifically for validating product modules that implement cryptography rather than the products that use them. Cryptographic modules that are implemented within a service can be certified as meeting the requirements for hash strength, key management, and the like. The cryptographic modules and ciphers used to protect the confidentiality, integrity, or availability of data in Microsoft's cloud services meet the FIPS 140-2 standard.

Microsoft certifies the underlying cryptographic modules used in our cloud services with each new release of the Windows operating system:

- Azure and Azure U.S. Government
- Dynamics 365 and Dynamics 365 U.S. Government
- Office 365, Office 365 U.S. Government, and Office 365 U.S. Government Defense

Encryption of customer data at rest is provided by multiple service-side technologies, including BitLocker, DKM, Azure Storage Service Encryption, and service encryption in Exchange, OneDrive, and SharePoint. Microsoft 365 service encryption includes an option to use customer-managed encryption keys that are stored in Azure Key Vault. This customer-managed key option is called [Customer Key](customer-key-overview), and is available for Exchange, SharePoint, OneDrive, Teams files, and Windows 365 Cloud PCs (in public preview).

For customer data in transit, all Office 365 servers negotiate secure sessions using TLS by default with client machines to secure customer data. For example, Office 365 negotiates secure sessions to Skype for Business, Outlook, Outlook on the web, mobile clients, and web browsers.

(All customer-facing servers negotiate to TLS 1.2 by default.)

## Related Links

- [Encryption in Azure](office-365-azure-encryption)
- [BitLocker and Distributed Key Manager (DKM) for Encryption](office-365-bitlocker-and-distributed-key-manager-for-encryption)
- [Service encryption and key management](microsoft-365-service-encryption)
- [Microsoft 365 encryption for Skype for Business, OneDrive, SharePoint, and Exchange](/en-us/compliance/assurance/assurance-encryption-for-microsoft-365-services)
- [Encryption for data in transit](/en-us/compliance/assurance/assurance-encryption-in-transit)
- [Customer-managed encryption features](office-365-customer-managed-encryption-features)
- [Encryption risks and protections](office-365-encryption-risks-and-protections)
- [Encryption in Microsoft Dynamics 365](office-365-encryption-in-microsoft-dynamics-365)