---
layout: Conceptual
title: 'Step 1: Discover AI apps - Prevent data leak to shadow AI | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-data-leak-shadow-ai-step1
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Discover and monitor AI app usage across your organization by using Microsoft Defender for Cloud Apps and Microsoft Purview DSPM for AI.
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
document_id: 4f8d3355-e0cd-862d-6519-8bfd858108e8
document_version_independent_id: 4f8d3355-e0cd-862d-6519-8bfd858108e8
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-data-leak-shadow-ai-step1.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-data-leak-shadow-ai-step1
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-data-leak-shadow-ai-step1.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
platformId: b6d4e03d-681d-a69b-e438-65c5c42b200a
---

# Step 1: Discover AI apps - Prevent data leak to shadow AI | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-data-leak-shadow-ai-intro)
- Step 1: Discover AI apps (this article)
- [Step 2: Block access to unsanctioned AI apps](depmod-data-leak-shadow-ai-step2)
- [Step 3: Block sensitive data going to sanctioned AI apps](depmod-data-leak-shadow-ai-step3)
- [Step 4: Govern data sent to AI apps](depmod-data-leak-shadow-ai-step4)

![Prevent data leak to shadow AI with Microsoft.](media/depmod-data-leak-shadow-ai-intro/prevent-shadow-ai-thumb.png)

The first step in preventing data leakage to shadow AI is understanding which AI apps are used across your organization, who uses them, and whether sensitive data is shared. This step focuses on discovery and monitoring before taking any blocking actions.

## Discover and monitor AI app usage with Microsoft Defender for Cloud Apps

Use [Microsoft Defender for Cloud Apps](/en-us/defender-cloud-apps/discovered-apps) to discover and monitor AI app usage across your organization. Defender for Cloud Apps provides a risk assessment for each discovered app to help you determine whether to sanction or unsanction an app.

1. [Filter the **Cloud app catalog**](/en-us/defender-cloud-apps/risk-score#the-cloud-app-catalog) by **App category** &gt; **Generative AI** to identify AI apps in use.
2. [Review the risk score](/en-us/defender-cloud-apps/risk-score) and usage details for each discovered AI app.
3. [Tag apps as **Sanctioned** or **Unsanctioned**](/en-us/defender-cloud-apps/governance-discovery) based on your organization's policy.

Tip

Use the cloud discovery dashboard to identify AI app usage trends before making sanctioning decisions. Understanding the scope of AI app usage helps you prioritize which apps to address first.

## Discover user interactions with Microsoft Purview DSPM for AI

Use Microsoft Purview Data Security Posture Management (DSPM) for AI reports and activity explorer to discover user interactions and understand if sensitive data is being sent to AI apps. Create the following policies to extend your insights for data discovery:

- **Detect when users visit AI sites**: Configure Insider Risk Management to detect when users visit AI application websites.
- **Detect sensitive info shared in AI prompts in Microsoft Edge**: Configure Microsoft Purview [Browser Data Security](../dlp-browser-dlp-learn) to detect sensitive information shared in AI prompts within Microsoft Edge.
- **Detect sensitive info pasted or uploaded to AI sites**: Configure Microsoft Purview [Endpoint Data Loss Prevention (DLP)](../endpoint-dlp-learn-about) to detect sensitive information pasted or uploaded to AI application websites.

To learn more, see [Data security posture management for AI](../ai-other-apps#dspm-and-dspm-for-ai-classic).

## Gain visibility into risky AI interactions with Microsoft Purview Insider Risk Management

Use Microsoft Purview [Insider Risk Management](../insider-risk-management) to gain visibility into risky AI interactions in the browser or over the network. Insider Risk Management helps identify users who may be engaging in high-risk activities involving AI tools, such as uploading sensitive content or interacting with unsanctioned AI services. To get started configuring policies, see [Get started with insider risk management](../insider-risk-management-configure).

## Summary

At the end of this step, your organization has:

- Visibility into which AI apps are being used across the organization.
- User interaction data flowing into DSPM for AI.
- Baseline understanding of AI-related risk through Insider Risk Management.