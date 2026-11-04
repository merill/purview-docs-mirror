---
layout: Conceptual
title: Lightweight guide to mitigate data leakage | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-lightweight-dlp-intro
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Learn how to mitigate data leakage with minimal configuration by using Microsoft Purview Information Protection and Data Loss Prevention.
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
document_id: 13747dea-f80f-a9db-8b63-e4ce84e8aae9
document_version_independent_id: 13747dea-f80f-a9db-8b63-e4ce84e8aae9
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-lightweight-dlp-intro.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-lightweight-dlp-intro
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-lightweight-dlp-intro.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
- https://authoring-docs-microsoft.poolparty.biz/devrel/1dd701e0-441f-4b0a-9806-aa47decc4e35
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
- https://authoring-docs-microsoft.poolparty.biz/devrel/0a2fc935-5977-4aa6-9f55-0be03bd2acb8
platformId: 0fabf175-1b9a-a7f5-6c0c-7a154eb863a1
---

# Lightweight guide to mitigate data leakage | Microsoft Learn

This deployment model enables core data security capabilities with minimal configuration, focusing on essential steps to get started quickly. It's designed for organizations that want to protect confidential data across their Microsoft 365 estate using a progressive Good/Better/Best approach.

The model uses Microsoft Purview Information Protection and Data Loss Prevention (DLP) to establish foundational data security, then progressively expands protection to endpoints, automates classification, and enables continuous improvement through Microsoft Purview Insider Risk Management and Adaptive Protection.

## About this guide

This guide includes the following articles:

- Introduction (this article)
- [Step 1: Establish foundational data security](depmod-lightweight-dlp-step1)
- [Step 2: Expand protection to endpoints](depmod-lightweight-dlp-step2)
- [Step 3: Continuous improvement](depmod-lightweight-dlp-step3)

These articles cover:

- How to create and deploy sensitivity labels and DLP policies with minimal configuration.
- How to expand protection to endpoints, Microsoft Teams, and email with custom sensitive information types (SITs) and auto-labeling.
- How to encrypt files, extend service-side auto-labeling, and enable Adaptive Protection for dynamic risk-based policies.

## Before you begin

This guide is for administrators with knowledge of Microsoft Purview Information Protection and Data Loss Prevention (DLP). If you're new to these solutions, refer to these articles to learn more:

- [Learn about sensitivity labels](../sensitivity-labels)
- [Learn about data loss prevention](../dlp-learn-about-dlp)
- [Learn about insider risk management](../insider-risk-management)

## Licensing and subscriptions

Features in this guide start at **Microsoft 365 Business Premium** and expand to **E5 Compliance** for advanced capabilities. See the licensing notes in each step for details.

For information on licensing, see [Microsoft 365, Office 365, Enterprise Mobility + Security, and Windows 11 Subscriptions for Enterprises](https://aka.ms/M365EnterprisePlans).

## Deployment overview

The deployment model uses a progressive Good/Better/Best approach:

| Step | Level | Description | Outcome |
| --- | --- | --- | --- |
| [Step 1: Establish foundational data security](depmod-lightweight-dlp-step1) | Good | Create sensitivity labels, set defaults, deploy basic DLP policies, and enable auditing. | Foundational data security with minimal configuration. |
| [Step 2: Expand protection to endpoints](depmod-lightweight-dlp-step2) | Better | Create custom SITs, configure client-side auto-labeling, and deploy DLP for Teams, endpoints, and email. | Expanded protection with automated classification. |
| [Step 3: Continuous improvement](depmod-lightweight-dlp-step3) | Best | Encrypt files, extend service-side auto-labeling, and enable Adaptive Protection. | Continuous improvement of data security practices. |

Note

Review the suggested efforts and adjust the timelines based on your tenant size and organizational complexity.

## Microsoft Purview deployment blueprint