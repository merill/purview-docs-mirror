---
layout: Conceptual
title: Deploy and use Data Security Posture Management | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-dspm-intro
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Learn how to deploy and use Microsoft Purview Data Security Posture Management (DSPM) with step-by-step guidance.
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
document_id: 572a878f-36f8-7bc2-e26c-0e1246357d30
document_version_independent_id: 572a878f-36f8-7bc2-e26c-0e1246357d30
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-dspm-intro.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-dspm-intro
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-dspm-intro.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
platformId: 1bb0c181-348a-064f-3dea-ed7519f43a54
---

# Deploy and use Data Security Posture Management | Microsoft Learn

Microsoft Purview Data Security Posture Management (DSPM) provides a centralized view of your organization's data security posture. DSPM helps you understand your data landscape, identify risks, and take action by providing analytics reports, trends, and actionable recommendations for creating Data Loss Prevention (DLP) and Insider Risk Management policies.

DSPM brings together insights from multiple Microsoft Purview solutions to provide:

- **Trends and analytics reports** to track and understand activities around sensitive data and users
- **Recommendations** that transform raw data discovery into actionable security measures
- **Microsoft Security Copilot-based investigation** for deeper insights through suggested prompts, open prompt investigation, and Promptbooks

In this deployment model, you receive step-by-step guidance to deploy and use DSPM, from establishing foundational elements through taking action on recommendations.

## About this guide

This guide includes the following articles:

- Introduction (this article)
- [Step 1: Establish foundational elements](depmod-dspm-step1)
- [Step 2: Configure access and analytics](depmod-dspm-step2)
- [Step 3: Understand data landscape and risks](depmod-dspm-step3)
- [Step 4: Take action and investigate with Security Copilot](depmod-dspm-step4)

These articles cover:

- Recommended foundational elements to have in place before using DSPM.
- Initial access and configuration for DSPM analytics.
- How to use DSPM reports, trends, and recommendations to understand your data landscape.
- How to create policies and investigate risks using DSPM recommendations and Security Copilot.

## Before you begin

This guide is for administrators with knowledge of Microsoft Purview Data Loss Prevention (DLP), Insider Risk Management, and Information Protection. If you're new to these solutions, refer to these articles to learn more:

- [Learn about data loss prevention](../dlp-learn-about-dlp)
- [Learn about insider risk management](../insider-risk-management)
- [Learn about sensitivity labels](../sensitivity-labels)
- [Learn about Data Security Posture Management](../data-security-posture-management)

## Licensing and subscriptions

See the Microsoft 365 guidance for security & compliance for details on the subscriptions that support the features you're deploying from this guide:

- Microsoft Purview Data Loss Prevention
- Microsoft Purview Insider Risk Management
- Microsoft Purview Information Protection
- Microsoft Security Copilot (optional, for investigation capabilities)

For information on licensing, see [Microsoft 365, Office 365, Enterprise Mobility + Security, and Windows 11 Subscriptions for Enterprises](https://aka.ms/M365EnterprisePlans).

## Deployment overview

The deployment model breaks the approach into four steps:

| Step | Description | Outcome |
| --- | --- | --- |
| [Step 1: Establish foundational elements](depmod-dspm-step1) | Identify sensitive information types (SITs), configure labeling, define Insider Risk Management program, and enable Microsoft Security Copilot. | Full data estate is understood and accessible. |
| [Step 2: Configure access and analytics](depmod-dspm-step2) | Assign roles, enable DLP and Insider Risk Management analytics, and start the initial scan. | DSPM starts pulling insights. |
| [Step 3: Understand data landscape and risks](depmod-dspm-step3) | Review DSPM reports, trends, and recommendations. | Risks are assessed and data security posture is understood. |
| [Step 4: Take action and investigate with Security Copilot](depmod-dspm-step4) | Create policies from recommendations and investigate with Security Copilot. | Actions taken to secure the environment. |

Note

After completing Step 4, plan a monthly iteration cycle to review DSPM recommendations, update policies, and strengthen your overall data security posture.

## Microsoft Purview deployment blueprint

![The image shows the deployment model to deploy and use Microsoft Purview Data Security Posture Management (DSPM) in four steps.](media/dspmdiagram.png)