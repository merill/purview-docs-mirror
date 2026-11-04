---
layout: Conceptual
title: Prevent data leak to shadow AI | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-data-leak-shadow-ai-intro
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Learn how to prevent data leakage to shadow AI apps by using Microsoft Purview, Microsoft Defender for Cloud Apps, Microsoft Entra, and Microsoft Intune.
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
document_id: 6b782b1a-3f3a-25a1-dde5-fa74b35f4870
document_version_independent_id: 6b782b1a-3f3a-25a1-dde5-fa74b35f4870
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-data-leak-shadow-ai-intro.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-data-leak-shadow-ai-intro
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-data-leak-shadow-ai-intro.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
platformId: 62c63304-19e3-9289-0a4d-ee0cf36b8cfb
---

# Prevent data leak to shadow AI | Microsoft Learn

Shadow AI refers to the use of artificial intelligence (AI) tools, especially generative AI, by users without the knowledge, approval, or governance of their organization's IT or security teams. Shadow AI presents a significant challenge for organizations because unregulated use of AI tools can undermine security protocols, even when these tools enhance productivity.

If you don't address shadow AI risks, they can lead to:

- Data leak of sensitive information
- Noncompliance with regulations
- Reputational harm

By addressing these risks, organizations can ensure they adopt AI securely. Organizations need to establish clear guidelines and governance frameworks to manage the adoption of AI technologies effectively. By doing so, you can harness the benefits of AI while mitigating the associated risks.

In this deployment model, we provide a recommended approach to prevent data leak to shadow AI by using Microsoft Purview, Microsoft Defender for Cloud Apps, Microsoft Entra, and Microsoft Intune.

## About this guide

This guide includes the following articles:

- Introduction (this article)
- [Step 1: Discover AI apps](depmod-data-leak-shadow-ai-step1)
- [Step 2: Block access to unsanctioned AI apps](depmod-data-leak-shadow-ai-step2)
- [Step 3: Block sensitive data going to sanctioned AI apps](depmod-data-leak-shadow-ai-step3)
- [Step 4: Govern data sent to AI apps](depmod-data-leak-shadow-ai-step4)

These articles cover:

- An overview of what shadow AI is and its risks.
- A recommended, staged approach to protect your organization from shadow AI.
- Detailed guidance for using Microsoft Defender for Cloud Apps, Microsoft Entra, Microsoft Intune, and Microsoft Purview to prevent data leakage to shadow AI.

## Before you begin

This guide is for administrators with knowledge of Microsoft Purview Data Loss Prevention (DLP), Microsoft Defender for Cloud Apps, Microsoft Entra, and Microsoft Intune. If you're new to these solutions, refer to these articles to learn more:

- [Learn about data loss prevention](../dlp-learn-about-dlp)
- [What is Microsoft Defender for Cloud Apps?](/en-us/defender-cloud-apps/what-is-defender-for-cloud-apps)
- [What is Microsoft Entra Internet Access?](/en-us/entra/global-secure-access/concept-internet-access)
- [Microsoft Intune overview](/en-us/intune/intune-service/fundamentals/what-is-intune)

## Licensing and subscriptions

See the Microsoft 365 guidance for security and compliance for details on the subscriptions that support the features you're deploying from this guide:

- Microsoft Purview Data Loss Prevention
- Microsoft Defender for Cloud Apps
- Microsoft Entra Internet Access
- Microsoft Intune

For information on licensing, see [Microsoft 365, Office 365, Enterprise Mobility + Security, and Windows 11 Subscriptions for Enterprises](https://aka.ms/M365EnterprisePlans).

## Deployment overview

The deployment model breaks the approach into four steps:

| Step | Description | Outcome |
| --- | --- | --- |
| [Step 1: Discover AI apps](depmod-data-leak-shadow-ai-step1) | Discover and monitor AI app usage across your organization. | Unknown AI app usage is discovered. |
| [Step 2: Block access to unsanctioned AI apps](depmod-data-leak-shadow-ai-step2) | Block organizational and user-level access to unsanctioned AI apps. | Unsanctioned AI apps are blocked. |
| [Step 3: Block sensitive data going to sanctioned AI apps](depmod-data-leak-shadow-ai-step3) | Prevent sensitive data from being shared with sanctioned AI apps. | Sensitive data isn't sent to sanctioned AI apps. |
| [Step 4: Govern data sent to AI apps](depmod-data-leak-shadow-ai-step4) | Govern, audit, retain, and investigate AI interactions. | Prompts sent to AI apps are retained for future investigations. |

## Microsoft Purview deployment blueprint

![Prevent data leak to shadow AI with Microsoft.](media/depmod-data-leak-shadow-ai-intro/prevent-shadow-ai-thumb.png)