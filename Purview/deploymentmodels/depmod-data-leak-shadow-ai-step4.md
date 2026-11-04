---
layout: Conceptual
title: 'Step 4: Govern data sent to AI apps - Prevent data leak to shadow AI | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-data-leak-shadow-ai-step4
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Govern, audit, retain, and investigate AI interactions by using Microsoft Purview Audit, Communication Compliance, Data Lifecycle Management, and Microsoft Purview eDiscovery.
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
document_id: 9fbb53c8-9521-c3d0-a252-f7f21fc1c3c5
document_version_independent_id: 9fbb53c8-9521-c3d0-a252-f7f21fc1c3c5
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-data-leak-shadow-ai-step4.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-data-leak-shadow-ai-step4
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-data-leak-shadow-ai-step4.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
platformId: 60bddf47-abd6-4b6b-de02-cdcef004ccd0
---

# Step 4: Govern data sent to AI apps - Prevent data leak to shadow AI | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-data-leak-shadow-ai-intro)
- [Step 1: Discover AI apps](depmod-data-leak-shadow-ai-step1)
- [Step 2: Block access to unsanctioned AI apps](depmod-data-leak-shadow-ai-step2)
- [Step 3: Block sensitive data going to sanctioned AI apps](depmod-data-leak-shadow-ai-step3)
- Step 4: Govern data sent to AI apps (this article)

![Prevent data leak to shadow AI with Microsoft.](media/depmod-data-leak-shadow-ai-intro/prevent-shadow-ai-thumb.png)

The final step focuses on governing interactions with AI apps. Even with discovery, blocking, and DLP protections in place, your organization needs to audit, retain, and investigate AI interactions to ensure ongoing compliance and respond to incidents.

## Capture AI interactions with Microsoft Purview Audit

[Turn on Microsoft Purview Audit](../audit-log-enable-disable) to capture all AI interactions across your organization. Audit logs provide a comprehensive record of user and administrator activities involving AI apps, including prompts, responses, and related actions. To learn about auditing AI activities specifically, see [Audit Copilot activity](../audit-copilot).

Note

Audit logging is typically enabled by default. Confirming it's active ensures no gap in visibility into AI interactions.

## Detect inappropriate behaviors in prompts with Microsoft Purview Communication Compliance

Use Microsoft Purview [Communication Compliance](../communication-compliance-copilot#other-ai-applications) to detect inappropriate behaviors in AI prompts using built-in classifiers. Communication Compliance supports monitoring interactions with AI applications beyond Microsoft 365 Copilot, including third-party AI tools accessed through the browser.

## Retain and delete prompts with Microsoft Purview Data Lifecycle Management

Use Microsoft Purview [Data Lifecycle Management](../data-lifecycle-management) retention policies to retain and delete AI prompts based on your organization's retention requirements.

1. [Create a retention policy](../create-retention-policies) that includes AI interaction locations.
2. Set the retention and deletion periods based on your organization's requirements.

## Investigate AI interactions with Microsoft Purview eDiscovery

Use Microsoft Purview [eDiscovery](../edisc-search-copilot-data) to preserve, collect, analyze, review, and export AI prompts and responses for legal and compliance investigations. eDiscovery enables you to:

- Search for specific AI interactions across your organization.
- Place holds on relevant AI interaction data to prevent deletion.
- Review and export AI prompts and responses for legal proceedings or internal investigations.

For more information, see [Search for Copilot data in eDiscovery](../edisc-search-copilot-data).

## Block elevated-risk users from AI interactions in Microsoft Edge

As an ongoing governance measure, use Microsoft Purview Insider Risk Management with Adaptive Protection to block elevated-risk users from submitting prompts to AI apps in Microsoft Edge. This approach provides a dynamic, risk-based governance layer that adjusts protections based on user behavior.

For more information, see [Help dynamically mitigate risks with Adaptive Protection](../insider-risk-management-adaptive-protection).

## Summary

At the end of this step, your organization has:

- Audit logging that captures all AI interactions for compliance monitoring.
- Communication Compliance policies that detect inappropriate or policy-violating AI prompts.
- Retention policies that govern the lifecycle of AI interaction data.
- eDiscovery capabilities to investigate AI interactions when needed.
- Adaptive Protection that dynamically restricts elevated-risk users from AI interactions.