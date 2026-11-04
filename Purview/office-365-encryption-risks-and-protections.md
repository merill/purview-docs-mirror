---
layout: Conceptual
title: Encryption risks and protections | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/office-365-encryption-risks-and-protections
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
f1.keywords:
- NOCSH
ms.author: kreagle
author: k-reagle
manager: laurawi
ms.date: 2024-03-19T00:00:00.0000000Z
audience: Admin
ms.topic: article
ms.service: purview
ms.subservice: purview-encryption
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- purview-compliance
ms.custom:
- seo-marvel-mar2020
description: Learn about risks to Microsoft 365 and the encryption technologies available for protection.
locale: en-us
document_id: b8da2ef0-7e2a-fc6c-b137-1b7a55b615dd
document_version_independent_id: b8da2ef0-7e2a-fc6c-b137-1b7a55b615dd
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/office-365-encryption-risks-and-protections.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: office-365-encryption-risks-and-protections
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/office-365-encryption-risks-and-protections.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/9d7be3ef-f27c-4c7f-9eba-67c3cd429995
- https://authoring-docs-microsoft.poolparty.biz/devrel/1dd701e0-441f-4b0a-9806-aa47decc4e35
- https://authoring-docs-microsoft.poolparty.biz/devrel/7428317a-e6c2-4461-ad3e-8a8ad3608734
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/feeb50f3-b677-44f9-b3a6-5f2f58182b0d
- https://authoring-docs-microsoft.poolparty.biz/devrel/0a2fc935-5977-4aa6-9f55-0be03bd2acb8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e4f59707-f107-48f2-8d75-0afd91868cd7
platformId: 04b95ea5-55c9-8c03-a537-0864f7493027
---

# Encryption risks and protections | Microsoft Learn

> 
> *[Microsoft Purview service description](/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description)*

Microsoft 365 follows a control and compliance framework that focuses on risks to the service and to customer data. The service implements a large set of technology and process-based methods, referred to as controls, to mitigate these risks. Identification, evaluation, and mitigation of risks through controls is a continuous process.

The implementation of controls within layers of our cloud services such as facilities, network, servers, applications, users (such as Microsoft administrators), and data form a defense-in-depth strategy. The key to this strategy is that many different controls are implemented at different layers to protect against the same or similar risk scenarios. This multi-layered approach provides fail-safe protection in case a control fails.

Some risk scenarios and the currently available encryption technologies that mitigate them are listed in this table. In many cases, these scenarios are also mitigated by other controls implemented in Microsoft 365.

| Encryption technology | Services | Key management | Risk scenario | Value |
| --- | --- | --- | --- | --- |
| BitLocker | Exchange and SharePoint | Microsoft | Disks or servers are stolen or improperly recycled. | BitLocker provides a fail-safe approach to protect against loss of data due to stolen or improperly recycled hardware (server/disk). |
| Service encryption | SharePoint and OneDrive; Exchange | Microsoft | Internal or external hacker tries to access individual files/data as a blob. | The encrypted data can't be decrypted without access to keys. Helps to mitigate risk of a hacker accessing data. |
| Customer Key | SharePoint, OneDrive, and Exchange | Customer | N/A (This feature is designed as a compliance feature; not as a mitigation for any risk.) | Helps customers meet internal regulation and compliance obligations, and the ability to leave the service and revoke Microsoft's access to data |
| Transport Layer Security (TLS) between Microsoft 365 and clients | Exchange, SharePoint, OneDrive, Teams, and Viva Engage | Microsoft, Customer | Man-in-the-middle or other attack to tap the data flow between Microsoft 365 and client computers over Internet. | This implementation provides value to both Microsoft and customers and assures data integrity as it flows between Microsoft 365 and the client. |
| TLS between Microsoft datacenters | Exchange, SharePoint, and OneDrive | Microsoft | Man-in-the-middle or other attack to tap the customer data flow between Microsoft 365 servers located in different Microsoft datacenters. | This implementation is another method to protect data against attacks between Microsoft datacenters. |
| The Azure Rights Management service (included in Microsoft 365 or Microsoft Purview Information Protection) | Exchange, SharePoint, and OneDrive | Customer | Data falls into the hands of a person who shouldn't have access to the data. | Microsoft Purview Information Protection uses the Azure Rights Management service, which provides value to customers by using encryption, identity, and authorization policies to help secure files and email across multiple devices. The Azure Rights Management service provides configuration options where all emails originating from Microsoft 365 that match certain criteria (for example, all emails to a certain address) can be automatically encrypted before they get sent to another recipient. |
| S/MIME | Exchange | Customer | A person who isn't the intended recipient obtained an email. | S/MIME helps ensure that only the intended recipient can decrypt an encrypted email. |
| Microsoft Purview Message Encryption | Exchange, SharePoint | Customer | A person who isn't the intended recipient obtained an email and its protected attachments. | Message encryption lets you configure your tenant so that emails originating from Microsoft 365 that match certain criteria (for example, all emails to a certain address) are automatically encrypted before they're sent. |
| Simple Mail Transfer Protocol (SMTP) TLS with partner organization | Exchange | Customer | Email is intercepted via a man-in-the-middle or other attack while in transit from a Microsoft 365 tenant to a partner organization. | Allows you to send and receive all emails between your Microsoft 365 tenant and your partner's email organization inside an encrypted SMTP channel. |

## Encryption technologies available in multitenant environments

| Encryption technology | Implemented by | Key exchange algorithm and strength | Key management\* | Federal Information Processing Standards (FIPS) 140-2 validated |
| --- | --- | --- | --- | --- |
| BitLocker | Exchange | Advanced Encryption Standard (AES) 256-bit | AES external key is stored in a secret safe and in the registry of the Exchange server. The secret safe is a secured repository that requires high-level elevation and approvals to access. Access can be requested and approved only by using an internal tool called Lockbox. The AES external key is also stored in the Trusted Platform Module in the server. A 48-digit numerical password is stored in Active Directory and protected by Lockbox. | Yes |
|  | SharePoint | AES 256-bit | AES external key is stored in a secret safe. The secret safe is a secured repository that requires high-level elevation and approvals to access. Access can be requested and approved only by using an internal tool called Lockbox. The AES external key is also stored in the Trusted Platform Module in the server. A 48-digit numerical password is stored in Active Directory and protected by Lockbox. | Yes |
|  | Skype for Business | AES 256-bit | AES external key is stored in a secret safe. The secret safe is a secured repository that requires high-level elevation and approvals to access. Access can be requested and approved only by using an internal tool called Lockbox. The AES external key is also stored in the Trusted Platform Module in the server. A 48-digit numerical password is stored in Active Directory and protected by Lockbox. | Yes |
| Service encryption | SharePoint | AES 256-bit | The keys used to encrypt the blobs are stored in the SharePoint Content Database. The SharePoint Content Database is protected by database access controls and encryption at rest. Encryption is performed using transparent data encryption (TDE) in Azure SQL Database. These secrets are at the service level for SharePoint, not at the tenant level. These secrets (sometimes referred to as the master keys) are stored in a separate secure repository called the Key Store. TDE provides security at rest for both the active database and the database backups and transaction logs. When customers provide the optional key, the key is stored in Azure Key Vault, and the service uses the key to encrypt a tenant key, which is used to encrypt a site key, which is then used to encrypt the file level keys. Essentially, a new key hierarchy is introduced when the customer provides a key. | Yes |
|  | Skype for Business | AES 256-bit | Each piece of data is encrypted using a different randomly generated 256-bit key. The encryption key is stored in a corresponding metadata XML file, which is encrypted by a per-conference master key. The master key is also randomly generated once per conference. | Yes |
|  | Exchange | AES 256-bit | Each mailbox is encrypted using a data encryption policy that uses encryption keys controlled by Microsoft or by the customer (when Customer Key is used). | Yes |
| TLS between Microsoft 365 and clients/partners | Exchange | [Opportunistic TLS supporting multiple cipher suites](exchange-online-uses-tls-to-secure-email-connections) | The TLS certificate for Exchange (outlook.office.com) is a 2048-bit SHA256RSA certificate issued by Baltimore CyberTrust Root.  The TLS root certificate for Exchange is a 2048-bit SHA1RSA certificate issued by Baltimore CyberTrust Root. | Yes, when TLS 1.2 with 256-bit cipher strength is used |
|  | SharePoint | TLS 1.2 with AES 256 [Data Encryption in OneDrive and SharePoint](data-encryption-in-odb-and-spo) | The TLS certificate for SharePoint (\*.sharepoint.com) is a 2048-bit SHA256RSA certificate issued by Baltimore CyberTrust Root.  The TLS root certificate for SharePoint is a 2048-bit SHA1RSA certificate issued by Baltimore CyberTrust Root. | Yes |
|  | Microsoft Teams | TLS 1.2 with AES 256 [Frequently asked questions about Microsoft Teams – Admin Help](/en-us/MicrosoftTeams/teams-overview) | The TLS certificate for Microsoft Teams (teams.microsoft.com, edge.skype.com) is a 2048-bit SHA256RSA certificate issued by Baltimore CyberTrust Root.  The TLS root certificate for Microsoft Teams is a 2048-bit SHA256RSA certificate issued by Baltimore CyberTrust Root. | Yes |
| TLS between Microsoft datacenters | All Microsoft 365 services | TLS 1.2 with AES 256  Secure Real-time Transport Protocol (SRTP) | Microsoft uses an internally managed and deployed certification authority for server-to-server communications between Microsoft datacenters. | Yes |
| Azure Rights Management service (included in Microsoft 365 or Microsoft Purview Information Protection) | Exchange | Supports [Cryptographic Mode 2](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439%28v=ws.10%29), an updated and enhanced RMS cryptographic implementation. It supports RSA 2048 for signature and encryption, and SHA-256 for hash in the signature. | [Managed by Microsoft](/en-us/azure/information-protection/plan-implement-tenant-key). | Yes |
|  | SharePoint | Supports [Cryptographic Mode 2](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439%28v=ws.10%29), an updated and enhanced RMS cryptographic implementation. It supports RSA 2048 for signature and encryption, and SHA-256 for signature. | [Managed by Microsoft](/en-us/azure/information-protection/plan-implement-tenant-key), which is the default setting; or  Customer-managed, which is an alternative to Microsoft-managed keys. Organizations that have an IT-managed Azure subscription can use bring your own key (BYOK) and log its usage at no extra charge. For more information, see [Implementing bring your own key](/en-us/azure/information-protection/plan-implement-tenant-key). In this configuration, nCipher Hardware Security Modules (HSMs) are used to protect your keys. | Yes |
| S/MIME | Exchange | Cryptographic Message Syntax Standard 1.5 (Public Key Cryptography Standard (PKCS) #7) | Depends on the customer-managed public key infrastructure deployed. The customer manages the keys, and Microsoft never has access to the private keys used for signing and decryption. | Yes, when configured to encrypt outgoing messages with 3DES or AES256 |
| Microsoft Purview Message Encryption | Exchange | Same as the Azure Rights Management service ([Cryptographic Mode 2](technical-reference-details-about-encryption) - RSA 2048 for signature and encryption, and SHA-256 for signature) | Uses the Azure Rights Management service as its encryption infrastructure. The encryption method used depends on where you obtain the RMS keys used to encrypt and decrypt messages. | Yes |
| SMTP TLS with partner organization | Exchange | TLS 1.2 with AES 256 | The TLS certificate for Exchange (outlook.office.com) is a 2048-bit SHA-256 with RSA encryption certificate issued by DigiCert Cloud Services CA-1.  The TLS root certificate for Exchange is a 2048-bit SHA-1 with RSA encryption certificate issued by [GlobalSign Root CA – R1](exchange-online-uses-tls-to-secure-email-connections).  For security reasons, our certificates do change from time to time. | Yes, when TLS 1.2 with 256-bit cipher strength is used |

*\*TLS certificates referenced in this table are for US datacenters; non-US datacenters also use 2048-bit SHA256RSA certificates.*

## Encryption technologies available in Government cloud community environments

| Encryption Technology | Implemented by | Key Exchange Algorithm and Strength | Key Management\* | FIPS 140-2 Validated |
| --- | --- | --- | --- | --- |
| BitLocker | Exchange | AES 256-bit | AES external key is stored in a secret safe and in the registry of the Exchange server. The secret safe is a secured repository that requires high-level elevation and approvals to access. Access can be requested and approved only by using an internal tool called Lockbox. The AES external key is also stored in the Trusted Platform Module in the server. A 48-digit numerical password is stored in Active Directory and protected by Lockbox. | Yes |
|  | SharePoint | AES 256-bit | AES external key is stored in a secret safe. The secret safe is a secured repository that requires high-level elevation and approvals to access. Access can be requested and approved only by using an internal tool called Lockbox. The AES external key is also stored in the Trusted Platform Module in the server. A 48-digit numerical password is stored in Active Directory and protected by Lockbox. | Yes |
|  | Skype for Business | AES 256-bit | AES external key is stored in a secret safe. The secret safe is a secured repository that requires high-level elevation and approvals to access. Access can be requested and approved only by using an internal tool called Lockbox. The AES external key is also stored in the Trusted Platform Module in the server. A 48-digit numerical password is stored in Active Directory and protected by Lockbox. | Yes |
| Service encryption | SharePoint | AES 256-bit | The keys used to encrypt the blobs are stored in the SharePoint Content Database. The SharePoint Content Databases is protected by database access controls and encryption at rest. Encryption is performed using TDE in Azure SQL Database. These secrets are at the service level for SharePoint, not at the tenant level. These secrets (sometimes referred to as the master keys) are stored in a separate secure repository called the Key Store. TDE provides security at rest for both the active database and the database backups and transaction logs. When customers provide the optional key, the Customer Key is stored in Azure Key Vault. The service uses the key to encrypt a tenant key, which is used to encrypt a site key, which is then used to encrypt the file level keys. Essentially, a new key hierarchy is introduced when the customer provides a key. | Yes |
|  | Skype for Business | AES 256-bit | Each piece of data is encrypted using a different randomly generated 256-bit key. The encryption key is stored in a corresponding metadata XML file. A per-conference master key encrypts this XML file. The master key is also randomly generated once per conference. | Yes |
|  | Exchange | AES 256-bit | Each mailbox is encrypted using a data encryption policy that uses encryption keys controlled by Microsoft or by the customer (when Customer Key is used). | Yes |
| TLS between Microsoft 365 and clients/partners | Exchange | [Opportunistic TLS supporting multiple cipher suites](exchange-online-uses-tls-to-secure-email-connections) | The TLS certificate for Exchange (outlook.office.com) is a 2048-bit SHA256RSA certificate issued by Baltimore CyberTrust Root.  The TLS root certificate for Exchange is a 2048-bit SHA1RSA certificate issued by Baltimore CyberTrust Root. | Yes, when TLS 1.2 with 256-bit cipher strength is used |
|  | SharePoint | TLS 1.2 with AES 256 | The TLS certificate for SharePoint (\*.sharepoint.com) is a 2048-bit SHA256RSA certificate issued by Baltimore CyberTrust Root.  The TLS root certificate for SharePoint is a 2048-bit SHA1RSA certificate issued by Baltimore CyberTrust Root. | Yes |
|  | Microsoft Teams | [Frequently asked questions about Microsoft Teams – Admin Help](/en-us/MicrosoftTeams/teams-overview) | The TLS certificate for Microsoft Teams (teams.microsoft.com; edge.skype.com) is a 2048-bit SHA256RSA certificate issued by Baltimore CyberTrust Root.  The TLS root certificate for Microsoft Teams is a 2048-bit SHA256RSA certificate issued by Baltimore CyberTrust Root. | Yes |
| TLS between Microsoft datacenters | Exchange, SharePoint, Skype for Business | TLS 1.2 with AES 256 | Microsoft uses an internally managed and deployed certification authority for server-to-server communications between Microsoft datacenters. | Yes |
|  |  | Secure Real-time Transport Protocol (SRTP) |  |  |
| The Azure Rights Management service | Exchange | Supports [Cryptographic Mode 2](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439%28v=ws.10%29), an updated and enhanced rights management solution cryptographic implementation. It supports RSA 2048 for signature and encryption, and SHA-256 for hash in the signature. | [Managed by Microsoft](/en-us/azure/information-protection/plan-implement-tenant-key). | Yes |
|  | SharePoint | Supports [Cryptographic Mode 2](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439%28v=ws.10%29), an updated and enhanced RMS cryptographic implementation. It supports RSA 2048 for signature and encryption, and SHA-256 for hash in the signature. | [Managed by Microsoft](/en-us/azure/information-protection/plan-implement-tenant-key), which is the default setting; or  Customer-managed (also known as BYOK), which is an alternative to Microsoft-managed keys. Organizations that have an IT-managed Azure subscription can use BYOK and log its usage at no extra charge. For more information, see [Implementing bring your own key](/en-us/azure/information-protection/plan-implement-tenant-key).  In the BYOK scenario, nCipher HSMs are used to protect your keys. | Yes |
| S/MIME | Exchange | Cryptographic Message Syntax Standard 1.5 (PKCS #7) | Depends on the public key infrastructure deployed. | Yes, when configured to encrypt outgoing messages with 3DES or AES-256. |
| Office 365 Message Encryption | Exchange | Same as the Azure Rights Management service ([Cryptographic Mode 2](technical-reference-details-about-encryption) - RSA 2048 for signature and encryption, and SHA-256 for hash in the signature) | Uses the Azure Rights Management service as its encryption infrastructure. The encryption method used depends on where you obtain the rights management solution keys used to encrypt and decrypt messages.  If you use the Azure Rights Management service to obtain the keys, Cryptographic Mode 2 is used. If you use Active Directory (AD) RMS to obtain the keys, either Cryptographic Mode 1 or Cryptographic Mode 2 is used. The method used depends on your on-premises AD RMS deployment. Cryptographic Mode 1 is the original AD RMS cryptographic implementation. It supports RSA 1024 for signature and encryption and supports SHA-1 for signature. All current versions of the rights management solutions support this mode, except for BYOK configurations that use HSMs. | Yes |
| SMTP TLS with partner organization | Exchange | TLS 1.2 with AES 256 | The TLS certificate for Exchange (outlook.office.com) is a 2048-bit SHA-256 with RSA Encryption certificate issued by DigiCert Cloud Services CA-1.  The TLS root certificate for Exchange is a 2048-bit SHA-1 with RSA Encryption certificate issued by [GlobalSign Root CA – R1](exchange-online-uses-tls-to-secure-email-connections).  For security reasons, our certificates do change from time to time. | Yes, when TLS 1.2 with 256-bit cipher strength is used. |

*\*TLS certificates referenced in this table are for US datacenters; non-US datacenters also use 2048-bit SHA256RSA certificates.*