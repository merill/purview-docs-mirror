---
layout: Conceptual
title: 'Step 1: Establish foundational data security - Lightweight guide to mitigate data leakage | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-lightweight-dlp-step1
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Create sensitivity labels, set default labels, deploy basic DLP policies, and enable auditing with minimal configuration.
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
document_id: 88da23a5-bedc-3758-2b50-d4f4ff88a6df
document_version_independent_id: 88da23a5-bedc-3758-2b50-d4f4ff88a6df
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-lightweight-dlp-step1.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-lightweight-dlp-step1
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-lightweight-dlp-step1.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/9d7be3ef-f27c-4c7f-9eba-67c3cd429995
- https://authoring-docs-microsoft.poolparty.biz/devrel/7428317a-e6c2-4461-ad3e-8a8ad3608734
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/feeb50f3-b677-44f9-b3a6-5f2f58182b0d
- https://authoring-docs-microsoft.poolparty.biz/devrel/e4f59707-f107-48f2-8d75-0afd91868cd7
platformId: c1ba1c1d-6b74-d3fd-a08f-5a7db4e57862
---

# Step 1: Establish foundational data security - Lightweight guide to mitigate data leakage | Microsoft Learn

This guide is divided into three steps:

- [Introduction](depmod-lightweight-dlp-intro)
- Step 1: Establish foundational data security (this article)
- [Step 2: Expand protection to endpoints](depmod-lightweight-dlp-step2)
- [Step 3: Continuous improvement](depmod-lightweight-dlp-step3)

This step establishes foundational data security with minimal configuration. You create sensitivity labels, set default labels for new content, deploy basic Data Loss Prevention (DLP) policies, and enable audit logging. All features in this step are available with Microsoft 365 Business Premium or above.

## Create sensitivity labels

[Create sensitivity labels](../create-sensitivity-labels) in Microsoft Purview to classify and protect content across Microsoft 365.

1. Define parent labels (for example, **Confidential** and **General**) scoped to **Files and other data assets**.
2. Configure protection settings such as content marking.
3. Repeat to create additional parent labels as needed.

## Create sensitivity sub-labels

[Create sub-labels](../create-sensitivity-labels) under parent labels to apply more granular protection within a broader classification.

1. Create an **AllEmployees** sub-label under the **Confidential** parent label.
2. Scope the sub-label to **Files and SharePoint sites**.
3. Configure protection settings such as content marking.

## Order labels by priority

[Label priority](../create-sensitivity-labels) determines which sensitivity label is applied when multiple labels match the same content. The highest priority label is typically the one with the most restrictive protections.

1. Move less sensitive or default labels down (closer to 0).
2. Move highly sensitive labels up numerically.
3. Verify the most restrictive protections have the highest priority.

## Publish sensitivity labels and set a default

[Publish your labels](../create-sensitivity-labels) to ensure users can see and use them, then set a default label so new documents are automatically classified.

1. Publish all sensitivity labels to **All users and groups**.
2. Set the default label for documents to **Confidential/AllEmployees**.
3. Name your policy and save.

## Enable sensitivity labels for SharePoint and OneDrive

[Enable sensitivity labels for SharePoint and OneDrive](../sensitivity-labels-sharepoint-onedrive-files) so Microsoft Purview can recognize and enforce labels on files stored in these locations. This feature allows documents to inherit labels from libraries.

Note

If the enablement banner isn't displayed in Information Protection, the feature is likely already enabled for your organization.

## Create and deploy basic DLP policies

[Create DLP policies](../dlp-create-deploy-policy) for Exchange, SharePoint, and OneDrive to prevent sharing of labeled content.

1. Create a custom DLP policy for **Exchange email** (best practice is to have a separate policy for email).
2. Create a custom DLP policy for **SharePoint sites** and **OneDrive accounts**.
3. For each policy, set conditions to detect content labeled **Confidential/AllEmployees**.
4. Set the action to **block sharing with people outside the organization**.
5. Turn on the policies immediately.

## Enable audit logging

[Enable audit logging](../audit-log-enable-disable) to track user and administrator activity across Microsoft 365, including Microsoft 365 Copilot interactions. Auditing is usually enabled by default - confirm it's active to ensure no gap in visibility.

Note

You must be assigned the Audit Logs role in Exchange Online to turn auditing on or off.

## Summary

At the end of this step, your organization has:

- Sensitivity labels and sub-labels created and published to all users.
- A default label (Confidential/AllEmployees) applied to new documents.
- Sensitivity labels enabled for SharePoint and OneDrive.
- Basic DLP policies preventing external sharing of labeled content.
- Audit logging enabled to track user and administrator activity.