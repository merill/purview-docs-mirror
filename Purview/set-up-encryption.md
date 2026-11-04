---
layout: Conceptual
title: Set up encryption in Microsoft 365 Enterprise | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/set-up-encryption
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
f1.keywords:
- NOCSH
ms.author: kreagle
author: k-reagle
manager: laurawi
ms.date: 2025-01-10T00:00:00.0000000Z
audience: Admin
ms.topic: landing-page
ms.service: purview
ms.subservice: purview-encryption
search.appverid:
- MET150
- MOE150
ms.collection:
- purview-compliance
description: With Microsoft 365, some encryption capabilities are turned on by default; other capabilities can be configured to meet certain compliance or legal requirements.
locale: en-us
document_id: 370f581d-6772-fb62-c504-d05a6308eb31
document_version_independent_id: 370f581d-6772-fb62-c504-d05a6308eb31
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/set-up-encryption.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: set-up-encryption
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/set-up-encryption.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1dd701e0-441f-4b0a-9806-aa47decc4e35
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/0a2fc935-5977-4aa6-9f55-0be03bd2acb8
platformId: 5184d77a-5861-4d62-c0ba-464aa1649026
---

# Set up encryption in Microsoft 365 Enterprise | Microsoft Learn

> 
> *[Microsoft Purview service description](/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description)*

Encryption can protect your content from being read by unauthorized users. Because [encryption in Microsoft 365](encryption) can be done using various technologies and methods, there isn't one single place where you turn on or set up encryption. This article provides information about various ways you can set up or configure encryption as part of your information protection strategy.

Tip

If you are looking for more technical details about encryption, see [Technical reference details about encryption](technical-reference-details-about-encryption).

With Microsoft 365, several encryption capabilities are available by default. Additional encryption capabilities can be configured to meet certain compliance or legal requirements. The following table describes several encryption methods for different scenarios.

| Scenario | Encryption Methods |
| --- | --- |
| Files are saved on Windows computers | Encryption at the computer level can be done using BitLocker on Windows devices. As an enterprise administrator or IT Pro, you can set this up using the Microsoft Deployment Toolkit (MDT). See [Set up MDT for BitLocker](/en-us/windows/deployment/deploy-windows-mdt/set-up-mdt-for-bitlocker). |
| Files are saved on mobile devices | Some kinds of mobile devices encrypt files that are saved to those devices by default. With [Capabilities of built-in Mobile Device Management for Office 365](https://support.microsoft.com/office/capabilities-of-built-in-mobile-device-management-for-microsoft-365-a1da44e5-7475-4992-be91-9ccec25905b0), you can set policies that determine whether to allow mobile devices to access data in Microsoft 365. For example, you can set a policy that allows only devices that encrypt content to access Microsoft 365 data. See [Create and deploy device security policies](https://support.microsoft.com/office/create-and-deploy-device-security-policies-d310f556-8bfb-497b-9bd7-fe3c36ea2fd6). For additional control over how mobile devices interact with Microsoft 365, consider adding [Microsoft Intune](/en-us/mem/intune/fundamentals/setup-steps). |
| You need control over the encryption keys used to encrypt your data in Microsoft's data centers | As an administrator, you can control your organization's encryption keys and then configure Microsoft 365 to use them to encrypt your data at rest in Microsoft's data centers. For information, see [Overview of Customer Key](customer-key-overview). |
| People are communicating via email (Exchange Online) | As an Exchange Online administrator, you have several options for configuring email encryption. These include [message encryption](set-up-new-message-encryption-capabilities) to enable people to send encrypted messages inside or outside your organization, [S/MIME](/en-us/exchange/security-and-compliance/smime-exo/smime-exo) to encrypt and digitally sign email messages, and TLS to [set up connectors for secure mail flow with another organization](/en-us/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner). For overviews, see [Email encryption](email-encryption) and [Encryption](encryption). |
| Files are accessed from team sites or document libraries (OneDrive for Business or SharePoint Online) | When people are working with files saved to OneDrive for Business or SharePoint Online, TLS connections are used. This is built into Microsoft 365 automatically. See [Data Encryption in OneDrive for Business and SharePoint Online](data-encryption-in-odb-and-spo). |
| Files are shared in online meetings and IM conversations (Skype for Business Online) | When people are working with files using Skype for Business Online, TLS is used for the connection. This is built into Microsoft 365 automatically. See [Security and Archiving (Skype for Business Online)](/en-us/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features). |
| Files are shared in online meetings and IM conversations (Microsoft Teams) | When people are working with files using Microsoft Teams, TLS is used for the connection. This is built into Microsoft Teams automatically. Microsoft Teams does not currently support inline rendering of encrypted email. To prevent encrypted email from landing in Microsoft Teams as encrypted, see [Message Encryption FAQ](ome-faq#can-i-automatically-remove-encryption-on-incoming-and-outgoing-mail-). |
|  |  |