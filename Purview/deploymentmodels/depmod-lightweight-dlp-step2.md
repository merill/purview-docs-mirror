---
layout: Conceptual
title: 'Step 2: Expand protection to endpoints - Lightweight guide to mitigate data leakage | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-lightweight-dlp-step2
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Create custom sensitive information types, configure client-side auto-labeling, and deploy DLP for Teams, endpoints, and email.
ms.author: kreagle
author: k-reagle
manager: laurawi
ms.reviewer: maximeb
ms.date: 2026-03-31T00:00:00.0000000Z
audience: ITPro
ms.topic: best-practice
ms.service: purview
ms.collection:
- purview-deployment-models
ai-usage: ai-assisted
locale: en-us
document_id: cca2968c-7948-c27f-4eaf-6fd5f9683930
document_version_independent_id: cca2968c-7948-c27f-4eaf-6fd5f9683930
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-lightweight-dlp-step2.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-lightweight-dlp-step2
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-lightweight-dlp-step2.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 2ab225d3-37d7-3f7b-e8c3-d57d34c37abc
---

# Step 2: Expand protection to endpoints - Lightweight guide to mitigate data leakage | Microsoft Learn

This guide is divided into three steps:

- [Introduction](depmod-lightweight-dlp-intro)
- [Step 1: Establish foundational data security](depmod-lightweight-dlp-step1)
- Step 2: Expand protection to endpoints (this article)
- [Step 3: Continuous improvement](depmod-lightweight-dlp-step3)

With foundational data security in place from Step 1, this step expands protection to endpoints and automates classification. You create custom sensitive information types (SITs), configure client-side auto-labeling, and deploy Data Loss Prevention (DLP) policies for Microsoft Teams, endpoints, and email. Features in this step require Microsoft 365 Information Protection Governance (IPG) or above.

## Create custom sensitive information types

[Create custom SITs](../sit-create-a-custom-sensitive-information-type) to detect and classify data unique to your organization. Custom SITs can be used in auto-labeling and DLP policies.

| Name | Pattern type | Example match |
| --- | --- | --- |
| Employee ID | Regex | EMP-123456 |
| Internal project code | Keyword list | Project Falcon, Orion, Phoenix |
| Proprietary source code | Regex + keyword | Code snippets containing 'internal\_use=true' near class or function |

1. Define the name, description, and confidence levels for each custom SIT.
2. Configure the primary element (keyword list, regex, or function), character proximity, and supporting elements.
3. Save and publish the custom SIT.

## Configure client-side auto-labeling

[Configure client-side auto-labeling](../apply-sensitivity-label-automatically) to classify and protect content as users create or edit it in Microsoft 365 apps like Word, Excel, and Outlook.

1. Edit the **Confidential/AllEmployees** label and enable **Auto-labeling for files and emails**.
2. Add conditions by using your custom SITs.
3. Set the action to **Recommend that users apply the label** rather than automatically applying it.

Tip

Start with recommending labels rather than auto-applying them. This approach gives users the opportunity to review and accept the recommendation, reducing friction during initial deployment.

## Create a DLP policy for endpoints

[Create an Endpoint DLP policy](../dlp-create-deploy-policy) to prevent sensitive data from being copied to USB drives, printed, or uploaded to unapproved apps. To learn more about Endpoint DLP, see [Learn about Endpoint data loss prevention](../endpoint-dlp-learn-about).

1. Create a custom DLP policy with **Devices** as the location.
2. Set conditions to detect content containing custom SITs or the **Confidential/AllEmployees** sensitivity label.
3. Set actions to block copy to USB, print, clipboard, or browser upload.
4. Run in simulation mode or turn on the policy immediately.

## Create a DLP policy for Microsoft Teams

[Create a DLP policy](../dlp-create-deploy-policy) to prevent sensitive data from being shared in chat or channel messages with external users or guests.

1. Create a custom DLP policy with **Teams chat and channel messages** as the location.
2. Set conditions to detect content containing custom SITs or the **Confidential/AllEmployees** sensitivity label.
3. Add a condition for **Content is shared from Microsoft 365** with **people outside my organization**.
4. Set the action to **Block only people outside your organization**.
5. Run in simulation mode or turn on the policy immediately.

## Apply DLP to email with custom SITs and label inheritance

[Create a DLP policy for email](../dlp-create-deploy-policy) that detects sensitive information in emails and attachments and enables [email label inheritance](../sensitivity-labels-office-apps#configure-label-inheritance-from-email-attachments) so the email automatically adopts the most restrictive sensitivity label from attached or linked files.

1. Create a custom DLP policy with **Exchange mail** as the location (best practice is to have email as its own DLP policy workload).
2. Set conditions for content shared with **people outside my organization** containing the **Confidential/AllEmployees** sensitivity label.
3. Set the action to **Restrict access or encrypt the content in Microsoft 365 locations**.
4. Run in simulation mode and optionally turn on automatically after 15 days.

## Summary

At the end of this step, your organization has:

- Custom SITs detecting organization-specific data in auto-labeling and DLP policies.
- Client-side auto-labeling recommending labels as users create or edit content.
- Endpoint DLP policies preventing sensitive data from being copied to USB drives, printed, or uploaded.
- Teams DLP policies blocking external sharing of sensitive content in chats and channels.
- Email DLP policies with label inheritance protecting sensitive email communications.