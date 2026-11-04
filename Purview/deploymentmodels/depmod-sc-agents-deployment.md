---
layout: Conceptual
title: Secure and govern Microsoft 365 Copilot agents | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-sc-agents-deployment
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Learn how to secure and govern Microsoft 365 Copilot agents by using Microsoft Purview to protect grounding data and interactions.
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
document_id: b783f7c0-8313-0a17-224d-ef7910175aa9
document_version_independent_id: b783f7c0-8313-0a17-224d-ef7910175aa9
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-sc-agents-deployment.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-sc-agents-deployment
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-sc-agents-deployment.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0fc65d4-7c73-4029-a261-7f99ff744363
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/b2daec57-5914-4967-8ed3-1d444897ba59
platformId: a1271408-6248-27a5-0c0f-55f043af58f8
---

# Secure and govern Microsoft 365 Copilot agents | Microsoft Learn

[Agents in Microsoft 365](https://adoption.microsoft.com/ai-agents/agents-in-microsoft-365/) bring specialized skills and knowledge into Microsoft 365 Copilot. These agents are embedded directly in Microsoft 365 Copilot Chat and the Microsoft 365 apps you use every day. These out-of-the-box agents take on unique roles to work alongside you and your team. This collaboration makes your work easier, keeps teams aligned, and helps accelerate decision-making to unlock faster business value.

Agents in Microsoft 365 Copilot leverage information in SharePoint and Microsoft Dataverse, which raises concerns for organizations about oversharing, data loss, and insider risks. If grounding data and agent interactions aren't secured, it could lead to:

- Access to information beyond what the user needs for their role
- Unauthorized disclosure of confidential information
- Out-of-date or irrelevant responses

By addressing these risks, organizations can ensure that agents are secured end to end.

In this deployment model, you find a recommended approach to secure agents in Microsoft 365 by using Microsoft Purview, from grounding data to interactions.

## About this guide

This guide includes the following articles:

- Introduction (this article)
- [Step 1: Discover risks and identify gaps](depmod-sc-agents-step1)
- [Step 2: Protect sensitive info in grounding data](depmod-sc-agents-step2)
- [Step 3: Protect interactions](depmod-sc-agents-step3)
- [Step 4: Govern interactions](depmod-sc-agents-step4)

These articles cover:

- A problem summary of why you need to secure agents in Microsoft 365.
- A recommended, staged approach to secure agents in Microsoft 365.
- Detailed guidance for using Microsoft Purview features to secure agents in Microsoft 365, from grounding data to interactions.

## Before you begin

This guide is for administrators with knowledge of Microsoft Purview Information Protection, Data Loss Prevention (DLP), Insider Risk Management, Data Lifecycle Management, and Compliance Manager. If you're new to these solutions, refer to these articles to learn more:

- [Learn about sensitivity labels](../sensitivity-labels)
- [Learn about data loss prevention](../dlp-learn-about-dlp)
- [Learn about insider risk management](../insider-risk-management)
- [Learn about data lifecycle management](../data-lifecycle-management)
- [Microsoft Purview Compliance Manager](../compliance-manager)
- [Data security and compliance protections for generative AI apps](../ai-microsoft-purview)

## Licensing and subscriptions

See the Microsoft 365 guidance for security and compliance for details on the subscriptions that support the features you're deploying from this guide:

- Microsoft Purview Information Protection
- Microsoft Purview Data Loss Prevention
- Microsoft Purview Insider Risk Management
- Microsoft Purview Data Lifecycle Management
- Microsoft Purview Communication Compliance
- Microsoft Purview eDiscovery
- Microsoft Purview Compliance Manager

For information on licensing, see [Microsoft 365, Office 365, Enterprise Mobility + Security, and Windows 11 Subscriptions for Enterprises](https://aka.ms/M365EnterprisePlans).

## Deployment overview

The deployment model breaks the approach into four steps:

| Step | Description | Outcome |
| --- | --- | --- |
| [Step 1: Discover risks and identify gaps](depmod-sc-agents-step1) | Turn on auditing, discover oversharing risks, and identify gaps in AI regulations. | Potential gaps in data security are discovered. |
| [Step 2: Protect sensitive info in grounding data](depmod-sc-agents-step2) | Apply sensitivity labels, reduce stale data, and restrict sensitive files from Copilot processing. | Sensitive info in grounding data isn't used as a knowledge source. |
| [Step 3: Protect interactions](depmod-sc-agents-step3) | Enforce label inheritance in conversations and detect risky AI interactions. | Interactions are protected from data loss and insider risk. |
| [Step 4: Govern interactions](depmod-sc-agents-step4) | Retain, investigate, and govern AI interaction data. | Interactions with agents are retained for future investigations. |

## Microsoft Purview deployment blueprint

![The image shows the deployment model to secure and govern Microsoft 365 Copilot agents with Microsoft Purview in four steps.](media/depmod-sc-agents-deployment/screenshot-2025-08-26-130022.png)