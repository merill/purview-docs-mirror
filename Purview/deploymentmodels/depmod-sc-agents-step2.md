---
layout: Conceptual
title: 'Step 2: Protect sensitive info in grounding data - Secure and govern Microsoft 365 Copilot agents | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-sc-agents-step2
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Apply sensitivity labels, reduce stale data, and restrict sensitive files from Microsoft 365 Copilot processing with DLP policies.
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
document_id: e86d165c-9155-a279-be09-b7bb58ba9852
document_version_independent_id: e86d165c-9155-a279-be09-b7bb58ba9852
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-sc-agents-step2.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-sc-agents-step2
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-sc-agents-step2.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0fc65d4-7c73-4029-a261-7f99ff744363
- https://authoring-docs-microsoft.poolparty.biz/devrel/9d7be3ef-f27c-4c7f-9eba-67c3cd429995
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/b2daec57-5914-4967-8ed3-1d444897ba59
- https://authoring-docs-microsoft.poolparty.biz/devrel/feeb50f3-b677-44f9-b3a6-5f2f58182b0d
platformId: 47e66828-4524-5538-a99d-40a4d6741638
---

# Step 2: Protect sensitive info in grounding data - Secure and govern Microsoft 365 Copilot agents | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-sc-agents-deployment)
- [Step 1: Discover risks and identify gaps](depmod-sc-agents-step1)
- Step 2: Protect sensitive info in grounding data (this article)
- [Step 3: Protect interactions](depmod-sc-agents-step3)
- [Step 4: Govern interactions](depmod-sc-agents-step4)

![Secure and govern Microsoft 365 Copilot agents deployment blueprint.](media/depmod-sc-agents-deployment/screenshot-2025-08-26-130022.png)

After discovering risks in Step 1, the next step focuses on protecting the grounding data that Microsoft 365 Copilot agents use as knowledge sources. This step includes applying sensitivity labels, managing stale data, and restricting sensitive files from being processed by agents.

## Apply sensitivity labels to SharePoint and Microsoft Dataverse

Apply [sensitivity labels](../sensitivity-labels) to content in SharePoint and Microsoft Dataverse to classify and protect grounding data. Sensitivity labels travel with the content and Microsoft 365 Copilot agents respect them, ensuring that agents don't surface sensitive information to unauthorized users.

When a user interacts with a Copilot agent, the conversation displays the most restrictive sensitivity label from the references used to formulate a response. Responses include only content from references where the user has appropriate permissions.

To learn more about deploying sensitivity labels, see:

- [Create and configure sensitivity labels](../create-sensitivity-labels)
- [Enable sensitivity labels for SharePoint and OneDrive](../sensitivity-labels-sharepoint-onedrive-files)
- [Secure by default with Microsoft Purview](depmod-secure-by-default-intro) deployment model

## Reduce stale data to improve agent response accuracy with Microsoft Purview Data Lifecycle Management

Use Microsoft Purview [Data Lifecycle Management](../data-lifecycle-management) to reduce stale data and improve agent response accuracy. [Retention policies](../create-retention-policies) help ensure that outdated or irrelevant content is removed from SharePoint and OneDrive, reducing the likelihood of agents surfacing inaccurate or outdated information in responses.

1. Create a retention policy targeting SharePoint sites and OneDrive accounts that serve as agent knowledge sources.
2. Set retention and deletion periods based on your organization's data freshness requirements.

## Restrict sensitive files from Microsoft 365 Copilot processing with Microsoft Purview DLP

Use Microsoft Purview Data Loss Prevention (DLP) for Microsoft 365 Copilot to restrict sensitive files from being processed by Copilot agents. For detailed steps on creating DLP policies, see [Create and deploy DLP policies](../dlp-create-deploy-policy). To learn about DLP for Copilot, see [Learn about DLP for Microsoft 365 Copilot](../dlp-microsoft365-copilot-location-learn-about).

1. Create a custom DLP policy with **Microsoft 365 Copilot** as the location.
2. Set conditions to detect content labeled with specific sensitivity labels (for example, Highly Confidential).
3. Set the action to restrict Copilot from processing the file.
4. Run in simulation mode first to understand the impact on agent responses.

Tip

Review the DLP activity explorer to identify which files are restricted before enforcing the policy.

## Implement Data policies for Microsoft Dataverse

Implement Data policies for Microsoft Dataverse to restrict sensitive data from being used as a knowledge source for agents. Data policies provide controls over which Dataverse content agents can access and include in their responses.

To learn more, see [Learn about DLP for Microsoft 365 Copilot](../dlp-microsoft365-copilot-location-learn-about).

## Implement oversharing DLP policy for SharePoint and OneDrive

Implement an oversharing DLP policy for SharePoint and OneDrive to detect "anyone" sharing links for labeled and unlabeled data. This policy helps ensure that broadly shared content isn't inadvertently surfaced through agent responses to users who shouldn't have access.

For more information, see [Data Loss Prevention policy reference](../dlp-policy-reference).

## Summary

At the end of this step, your organization has:

- Sensitivity labels applied to grounding data in SharePoint and Microsoft Dataverse.
- Retention policies reducing stale data to improve agent response accuracy.
- DLP policies restricting highly sensitive files from Microsoft 365 Copilot processing.
- Data policies for Microsoft Dataverse controlling agent access to sensitive data.
- Oversharing DLP policies detecting broadly shared content in SharePoint and OneDrive.