---
layout: Conceptual
title: Microsoft Purview support for double byte character set release notes | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/mip-dbcs-relnotes
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
ms.author: kreagle
author: k-reagle
manager: laurawi
ms.date: 2023-10-25T00:00:00.0000000Z
audience: Admin
ms.topic: release-notes
ms.service: purview
ms.collection:
- purview-compliance
search.appverid:
- MOE150
- MET150
description: Release notes for support for double byte character sets.
locale: en-us
document_id: 39018980-4b1a-284c-75a7-3c0b602fc7dc
document_version_independent_id: 39018980-4b1a-284c-75a7-3c0b602fc7dc
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/mip-dbcs-relnotes.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: mip-dbcs-relnotes
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/mip-dbcs-relnotes.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 57f777f4-b3ec-b2bb-3b45-cf6ba92a61ad
---

# Microsoft Purview support for double byte character set release notes | Microsoft Learn

Microsoft Purview Information Protection now supports double byte character set languages for:

- Chinese (simplified)
- Chinese (traditional)
- Korean
- Japanese

This support is available for sensitive information types and keyword dictionaries and will be reflected in Microsoft Purview Data Loss Prevention (for Exchange Online, SharePoint Online, OneDrive for Business, and Teams), Communications Compliance, Auto Labelling in office apps and Microsoft Defender for Cloud Apps.

## Known issues

- When a text file attached to an email is in UTF-8 format without byte order mark (BOM), the email isn't detected by the Communication Compliance policy.
- Communication Compliance policies can't detect values if a sentence is entered for the policy condition: “Message contains any of these words”. If the text specified in the policy is written as a word, it can be detected; however, if it's written in the middle of a sentence, it will not be detected.
- Communication Compliance policies that specify dictionaries as type information don't detect Teams private chats and channel chats.
- The following conditions aren't supported for Communication Compliance at this stage (we plan to fix these issues in the future):

    - “Message contains any of these words”
    - “Message contains none of these words”
    - “Attachment contains any of these words”
    - “Attachment contains any of these words”
- Data loss prevention policies are enforceable on macOS devices (preview) running three latest released versions, except for the below mentioned conditions for East Asian languages including Japanese.

    - Full-width numbers aren’t detected such as using built-in template such as Japan bank account number
    - Numbers without delimiters aren’t detected
    - Keywords separated by a half-width space aren’t detected for a sensitive information type. For example: Japanese word is set at sensitive information type and dictionary isn't detected if it is in a sentence
    - Words containing both English and Japanese (東京2020) aren’t detected

Instead we recommend creating a custom Sensitive Information Type (SIT) with keyword dictionary which will detect patterns across messages and attachments, and using this custom SIT as a Communication Compliance policy condition.