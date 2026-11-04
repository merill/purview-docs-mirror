---
layout: Conceptual
title: Deprecating OME Viewer app | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/deprecating-ome-viewer
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
ms.topic: article
ms.service: purview
ms.subservice: purview-encryption
search.appverid:
- MET150
- MOE150
ms.collection:
- purview-compliance
ms.custom:
- seo-marvel-apr2020
description: The Office 365 Message Encryption (OME) Viewer app was removed from Android and Apple stores in 2018.
locale: en-us
document_id: d7f0a0ad-9749-720d-e764-b2be0d61fbda
document_version_independent_id: d7f0a0ad-9749-720d-e764-b2be0d61fbda
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deprecating-ome-viewer.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deprecating-ome-viewer
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deprecating-ome-viewer.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6ab06385-661e-4214-8870-bbe4071c960d
- https://authoring-docs-microsoft.poolparty.biz/devrel/7ebba99b-05c3-4387-8883-f7bbf6632cb8
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/131ba09e-4280-4ae7-8622-1f9f1c0daad1
- https://authoring-docs-microsoft.poolparty.biz/devrel/006ab567-b18c-4cf1-9a25-c24daa46ede1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
platformId: b7d25e8b-8e86-4525-670f-f1374aa465e9
---

# Deprecating OME Viewer app | Microsoft Learn

> 
> *[Microsoft Purview service description](/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description)*

On August 15, 2018, we removed the Office 365 Message Encryption (OME) Viewer mobile app from Android and Apple stores. The Office 365 Message Encryption Viewer mobile app was required to read email messages and attachments that were encrypted with the previous version of OME on Apple and Android phones. Apart from removing the OME Viewer app, we aren't making any other changes to the previous version of OME.

## Changes from August 2018

As announced September 2017, we released a new version of [Office 365 Message Encryption](https://aka.ms/ome2017). Users can send encrypted and protected messages to anyone inside or outside the organization without the requirement of the mobile app. Since then, we added more capabilities:

- [Encrypt-only template](https://aka.ms/encryptonly)
- [Control to decrypt attachments](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Admin-control-for-attachments-now-available-in-Office-365/ba-p/204007)

With this change, users will no longer be able to download the Office 365 Message Encryption Viewer mobile app beginning August 1, 2018. As a result, mail recipients might not be able to read messages encrypted with the previous version of OME on some Android and Apple mobile devices. However, they can still read these messages on personal computers (by using desktop browsers). Users who already downloaded the app can still use it.

## Why this change was made

The new version of OME no longer requires a mobile app to read protected email messages and attachments. Customers using Microsoft Purview Message Encryption can view the protected message in Outlook mobile and noncustomers can view protected messages in a browser.

Requiring users to download a mobile app is another hurdle for customers to view protected messages. Microsoft Purview Message Encryption provides a better mobile experience.

## Can I still use the previous version of Office 365 Message Encryption

The previous version of Office 365 Message Encryption isn't deprecated at this time. However, we made significant enhancements to Microsoft Purview Message Encryption. These changes make it easier to encrypt and rights protect sensitive data you send to anyone on any device - including the ability for users to read protected messages directly in Outlook (desktop, mobile, and web).

## What do I need to do to prepare for this change

If your organization currently sends encrypted attachments to recipients that require the OME Viewer app, you should update your documentation and training resources.

We recommend updating existing Exchange mail flow rules to use Microsoft Purview Message Encryption so that your organization can take advantage of the new and improved capabilities. Once you set up Microsoft Purview Message Encryption, recipients don't need the OME Viewer app to read encrypted messages on mobile devices.

Microsoft recommends that you make a plan to move to Microsoft Purview Message Encryption as soon as it's reasonable for your organization. For instructions, see [Set up Microsoft Purview Message Encryption](set-up-new-message-encryption-capabilities). If you want to find out more about how message encryption works first, see [Message Encryption](ome).