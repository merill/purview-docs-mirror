---
layout: Conceptual
title: Customer-managed encryption features | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/office-365-customer-managed-encryption-features
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
description: In this article, you'll learn about encryption technologies that you can manage and configure in Microsoft 365.
locale: en-us
document_id: 603cd9f9-39dd-1b05-606c-e7e4dc09f18e
document_version_independent_id: 603cd9f9-39dd-1b05-606c-e7e4dc09f18e
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/office-365-customer-managed-encryption-features.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: office-365-customer-managed-encryption-features
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/office-365-customer-managed-encryption-features.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
- https://authoring-docs-microsoft.poolparty.biz/devrel/1dd701e0-441f-4b0a-9806-aa47decc4e35
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
- https://authoring-docs-microsoft.poolparty.biz/devrel/0a2fc935-5977-4aa6-9f55-0be03bd2acb8
platformId: 6d0d62df-7779-bcbf-97e9-007cafd2b874
---

# Customer-managed encryption features | Microsoft Learn

> 
> *[Microsoft Purview service description](/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description)*

- [Learn about the Azure Rights Management encryption service](azure-rights-management-learn-about)
- [Microsoft Purview Message Encryption](https://products.office.com/en-us/exchange/office-365-message-encryption)
- [Secure mail flow with a partner organization](/en-us/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)

For more information about these technologies, see the [Microsoft 365 service descriptions](/en-us/office365/servicedescriptions/office-365-service-descriptions-technet-library).

## The Azure Rights Management service

[The Azure Rights Management service](azure-rights-management-learn-about) is the encryption technology used by Microsoft Purview Information Protection. It uses encryption, identity, and authorization policies to help secure your files and email across multiple platforms and devices—phones, tablets, and PCs. Information can be protected both within and outside your organization because protection remains with the data.

For more information about the Azure Rights Management encryption service, including how it works, the cryptographic controls it uses, and the key management options available, see [Learn about the Azure Rights Management encryption service](azure-rights-management-learn-about).

## Secure Multipurpose Internet Mail Extension

Secure/Multipurpose Internet Mail Extensions (S/MIME) is a standard for public key encryption and digital signing of MIME data. S/MIME is defined in RFCs 3369, 3370, 3850, 3851, and others. It allows a user to encrypt an email and digitally sign an email. An email that is encrypted using S/MIME can only be decrypted by the recipient of the email using their private key, which is only available to that recipient. As such the emails can’t be decrypted by anybody other than the recipient of the email.

[Microsoft supports S/MIME](https://blogs.technet.com/b/exchange/archive/2014/12/15/how-to-configure-s-mime-in-office-365.aspx). Public certificates are distributed to the customer's on-premises Active Directory and stored in attributes that can be replicated to a Microsoft 365 tenant. The private keys that correspond to the public keys remain on-premises and are never transmitted to Office 365. Users can compose, encrypt, decrypt, read, and digitally sign emails between two users in an organization using Outlook, Outlook on the web, and Exchange ActiveSync clients.

## Microsoft Purview Message Encryption

[Microsoft Purview Message Encryption](https://products.office.com/exchange/office-365-message-encryption) built on top of the [Azure Rights Management encryption service](azure-rights-management-learn-about) enables you to send encrypted and rights-protected mail to anyone. Message encryption mitigates threats such as wire-tapping and man-in-the-middle attacks, and other threats, such as unwarranted access of data by an unauthorized user who doesn't have appropriate permissions. We have made investments that provide you with a simpler, more intuitive, secure email experience built on top of the Azure Rights Management encryption service. You can protect messages sent from Microsoft 365 to anyone inside or outside your organization. These messages can be viewed across a diverse set of mail clients using any identity, including Microsoft Entra ID, Microsoft Account, and Google IDs. For more information on how your organization can use encrypted messages, see [Message encryption(./ome.md).

## Transport Layer Security

If you want to ensure secure communication with a partner, you can use inbound and outbound connectors to provide security and message integrity. You can configure forced inbound and outbound TLS on each connector, using a certificate. Using an encrypted SMTP channel can prevent data from being stolen via a man-in-the-middle attack. For more information, see [How Exchange Online uses TLS to secure email connections](exchange-online-uses-tls-to-secure-email-connections).

## Domain Keys Identified Mail

Exchange Online supports inbound validation of Domain Keys Identified Mail (DKIM) messages. DKIM is a method for validating that a message was sent from the domain it says it originated from and that it wasn't spoofed by someone else. It ties an email message to the organization responsible for sending it, and is part of a larger paradigm of email encryption. For more information about the three parts of this paradigm, see:

- [Set up SPF to help prevent spoofing](/en-us/defender-office-365/email-authentication-spf-configure)
- [Use DKIM to validate outbound email sent from your custom domain](/en-us/defender-office-365/email-authentication-dkim-configure)
- [Use DMARC to validate email](/en-us/defender-office-365/email-authentication-dmarc-configure)