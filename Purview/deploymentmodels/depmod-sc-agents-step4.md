---
layout: Conceptual
title: 'Step 4: Govern interactions - Secure and govern Microsoft 365 Copilot agents | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-sc-agents-step4
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Govern Microsoft 365 Copilot agent interactions with retention policies, Communication Compliance, Microsoft Purview eDiscovery, and Compliance Manager.
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
document_id: 1b9b578b-b8b6-ef0b-9cb0-35e429ed2660
document_version_independent_id: 1b9b578b-b8b6-ef0b-9cb0-35e429ed2660
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-sc-agents-step4.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-sc-agents-step4
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-sc-agents-step4.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0fc65d4-7c73-4029-a261-7f99ff744363
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/b2daec57-5914-4967-8ed3-1d444897ba59
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
platformId: 1752640a-cca0-4f53-d49f-c084eff771e6
---

# Step 4: Govern interactions - Secure and govern Microsoft 365 Copilot agents | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-sc-agents-deployment)
- [Step 1: Discover risks and identify gaps](depmod-sc-agents-step1)
- [Step 2: Protect sensitive info in grounding data](depmod-sc-agents-step2)
- [Step 3: Protect interactions](depmod-sc-agents-step3)
- Step 4: Govern interactions (this article)

![Secure and govern Microsoft 365 Copilot agents deployment blueprint.](media/depmod-sc-agents-deployment/screenshot-2025-08-26-130022.png)

The final step focuses on governing interactions with Microsoft 365 Copilot agents. After you put discovery, protection, and interaction-level controls in place, your organization needs to retain, investigate, and govern agent interaction data to ensure ongoing compliance and respond to incidents.

## Retain and delete interactions with Microsoft Purview Data Lifecycle Management

Use Microsoft Purview [Data Lifecycle Management](../data-lifecycle-management) retention policies to retain interactions for future investigations and delete interactions based on retention requirements. [Create retention policies](../create-retention-policies) to ensure agent interaction data is preserved when needed and removed when no longer required.

1. Create a retention policy that includes Microsoft 365 Copilot interaction locations.
2. Set retention and deletion periods based on your organization's compliance requirements.

## Detect inappropriate behaviors with Microsoft Purview Communication Compliance

Use Microsoft Purview [Communication Compliance](../communication-compliance-copilot) policies with built-in classifiers to detect inappropriate behaviors in agent interactions, including jailbreak attempts, harassment, inappropriate images, and other policy-violating content.

## Investigate legal and internal cases with Microsoft Purview eDiscovery

Use Microsoft Purview [eDiscovery](../edisc-search-copilot-data) to preserve, collect, analyze, review, and export agent interactions for legal and internal investigations.

## Investigate interactions and grounding data with Microsoft Purview Data Security Investigations

Use Microsoft Purview [Data Security Investigations](../data-security-investigations) to investigate interactions and grounding data by leveraging the power of AI. DSI provides advanced investigation capabilities that help you understand the full context of security incidents involving agent interactions.

To learn more, see [Learn about data security investigations](../data-security-investigations).

## Identify and address gaps in meeting AI regulations with Microsoft Purview Compliance Manager

Use Microsoft Purview Compliance Manager to identify and address gaps in meeting AI regulations on an ongoing basis. As regulatory requirements evolve, Compliance Manager helps ensure your organization stays current with AI governance obligations.

To learn more, see [Microsoft Purview Compliance Manager](../compliance-manager).

## Summary

At the end of this step, your organization has:

- Retention policies governing the lifecycle of Microsoft 365 Copilot agent interaction data.
- Communication Compliance policies detecting inappropriate behaviors in agent interactions.
- eDiscovery capabilities to investigate agent interactions when needed.
- Data Security Investigations providing AI-powered investigation of interactions and grounding data.
- Ongoing compliance monitoring through Compliance Manager for AI regulations.