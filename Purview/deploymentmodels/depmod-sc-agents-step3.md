---
layout: Conceptual
title: 'Step 3: Protect interactions - Secure and govern Microsoft 365 Copilot agents | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-sc-agents-step3
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Enforce sensitivity label inheritance in Microsoft 365 Copilot conversations and detect risky AI interactions with Microsoft Purview.
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
document_id: cadf61d6-3f61-d4eb-0252-ae5073852bfa
document_version_independent_id: cadf61d6-3f61-d4eb-0252-ae5073852bfa
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-sc-agents-step3.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-sc-agents-step3
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-sc-agents-step3.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0fc65d4-7c73-4029-a261-7f99ff744363
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/b2daec57-5914-4967-8ed3-1d444897ba59
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
platformId: e7c4afbe-85e5-b177-c52e-9ac7e332777c
---

# Step 3: Protect interactions - Secure and govern Microsoft 365 Copilot agents | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-sc-agents-deployment)
- [Step 1: Discover risks and identify gaps](depmod-sc-agents-step1)
- [Step 2: Protect sensitive info in grounding data](depmod-sc-agents-step2)
- Step 3: Protect interactions (this article)
- [Step 4: Govern interactions](depmod-sc-agents-step4)

![Secure and govern Microsoft 365 Copilot agents deployment blueprint.](media/depmod-sc-agents-deployment/screenshot-2025-08-26-130022.png)

After protecting grounding data in Step 2, focus on protecting the interactions themselves. Microsoft Purview provides capabilities to enforce sensitivity label inheritance in agent conversations, restrict processing of sensitive files referenced in interactions, and detect risky AI interactions.

## Use automatic sensitivity label inheritance from SharePoint and Microsoft Dataverse

Microsoft 365 Copilot conversations automatically display and respect [sensitivity labels](../ai-m365-copilot#sensitivity-labels-and-ai-interactions) applied to data in SharePoint and Microsoft Dataverse. When a user interacts with a Copilot agent, the conversation inherits the most restrictive sensitivity label from the referenced content.

Verify that automatic label inheritance is working correctly:

1. Verify that [sensitivity labels are applied](../create-sensitivity-labels) to content in SharePoint sites and Microsoft Dataverse that serve as agent knowledge sources.
2. Open a Microsoft 365 Copilot conversation that references labeled content.
3. Confirm that the conversation displays the [most restrictive sensitivity label](../ai-m365-copilot#sensitivity-labels-and-ai-interactions) from the referenced sources.

This automatic label inheritance ensures that:

- A sensitivity label is displayed for the entire conversation.
- Users are aware of the sensitivity level of the information they're working with.
- Protection policies associated with the label are enforced on the conversation.

## Restrict Microsoft 365 Copilot from processing sensitive files referenced in interactions

Use Microsoft Purview Data Loss Prevention (DLP) for Microsoft 365 Copilot to restrict Copilot from processing sensitive files referenced in interactions. This restriction ensures that sensitive prompts aren't used for web queries and that highly sensitive content isn't included in agent responses, even when a user has access to the file.

Important

DLP for Microsoft 365 Copilot provides a critical layer of protection by ensuring that even if sensitive files are accessible, the system doesn't process them or include them in agent responses when they match your DLP policy conditions.

For more information, see [Learn about DLP for Microsoft 365 Copilot](../dlp-microsoft365-copilot-location-learn-about).

## Detect risky AI interactions with Microsoft Purview Insider Risk Management

Use Microsoft Purview [Insider Risk Management's](../insider-risk-management) Risky AI usage [policy template](../insider-risk-management-policy-templates) to detect risky AI interactions across your organization. This policy identifies users who engage in potentially suspicious interactions with AI agents, such as attempts to access sensitive content or exfiltrate data through prompts.

1. [Create an Insider Risk Management policy](../insider-risk-management-configure) using the **Risky AI usage** template.
2. Configure the policy scope, triggers, and thresholds based on your organization's risk tolerance.
3. Turn on the policy.

## Summary

At the end of this step, your organization has:

- Automatic sensitivity label inheritance in Microsoft 365 Copilot conversations.
- DLP policies restricting Copilot from processing sensitive files referenced in interactions.
- Insider Risk Management policies detecting risky AI interactions.