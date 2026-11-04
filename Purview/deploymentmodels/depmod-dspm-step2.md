---
layout: Conceptual
title: 'Step 2: Configure access and analytics - Deploy and use Data Security Posture Management | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-dspm-step2
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Assign roles with least privilege, enable DLP and Insider Risk Management analytics, and start the initial Data Security Posture Management scan.
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
document_id: d1f45b4f-b97a-0a4c-eb0f-441f766c4a1e
document_version_independent_id: d1f45b4f-b97a-0a4c-eb0f-441f766c4a1e
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-dspm-step2.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-dspm-step2
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-dspm-step2.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
platformId: 3772a83c-f599-6a5e-f210-ebfe4e666524
---

# Step 2: Configure access and analytics - Deploy and use Data Security Posture Management | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-dspm-intro)
- [Step 1: Establish foundational elements](depmod-dspm-step1)
- Step 2: Configure access and analytics (this article)
- [Step 3: Understand data landscape and risks](depmod-dspm-step3)
- [Step 4: Take action and investigate with Security Copilot](depmod-dspm-step4)

![Deploy and use Microsoft Purview Data Security Posture Management (DSPM) deployment blueprint.](media/dspmdiagram.png)

With the foundational elements in place from Step 1, this step focuses on configuring access to Data Security Posture Management (DSPM) and enabling the analytics that power its insights.

## Assign a role with least privilege

Assign users to one of the following roles or role groups to provide access to DSPM. Use roles with the fewest permissions to enhance your organization's security posture.

| Role or role group | Description |
| --- | --- |
| Data Security Management role group | Provides full access to DSPM management capabilities. |
| Data Security Viewer role | Required to use Microsoft Security Copilot in DSPM. |
| Insider Risk Management Admins role | Provides access to Insider Risk Management-related DSPM capabilities. |
| Microsoft Entra ID Global Administrator role | Provides full access (use sparingly). |
| Microsoft Entra Compliance Administrator role | Provides compliance-focused access to DSPM. |

Important

Use roles with the fewest permissions. Reducing the number of users with the Global Administrator role enhances security for your organization.

To learn more, see [Permissions in Microsoft Purview](../microsoft-365-compliance-center-permissions).

## Enable Data Loss Prevention and Insider Risk Management analytics

Enable Data Loss Prevention (DLP) and Insider Risk Management analytics to power DSPM insights. DSPM processes and correlates data states, signals, and user activities based on the configuration of other data security and compliance solutions in Microsoft Purview.

There are two ways to enable analytics:

- **Opt in to DSPM**: Enables both DLP and Insider Risk Management analytics together.
- **Enable individually**: Enable [DLP analytics](../dlp-analytics-get-started) and [Insider Risk Management analytics](../insider-risk-management-settings-analytics) separately.

1. Opt in to DSPM analytics, or enable DLP and Insider Risk Management analytics individually.
2. Verify the analytics are enabled in each solution's settings page.

## Verify the initial scan starts

After you enable analytics, the initial scan starts automatically. DSPM scans your organization's data and activities, offering baseline insights and recommendations. To learn more, see [Learn about Data Security Posture Management](../data-security-posture-management).

Note

The initial scan can take up to three days to complete.

## Summary

At the end of this step, your organization has:

- Assigned appropriate roles with least privilege for DSPM access.
- Enabled DLP and Insider Risk Management analytics to power DSPM insights.
- Started the initial DSPM scan and is processing organizational data.