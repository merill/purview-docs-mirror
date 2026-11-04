---
layout: Conceptual
title: 'Step 3: Understand data landscape and risks - Deploy and use Data Security Posture Management | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-dspm-step3
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Review Data Security Posture Management reports, trends, and recommendations to understand your data landscape and identify risks.
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
document_id: 63ca54d0-6eaa-df9c-11ff-0178cbb5c251
document_version_independent_id: 63ca54d0-6eaa-df9c-11ff-0178cbb5c251
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-dspm-step3.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-dspm-step3
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-dspm-step3.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: b6705b46-a585-2c17-698f-aa23bd9dea5a
---

# Step 3: Understand data landscape and risks - Deploy and use Data Security Posture Management | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-dspm-intro)
- [Step 1: Establish foundational elements](depmod-dspm-step1)
- [Step 2: Configure access and analytics](depmod-dspm-step2)
- Step 3: Understand data landscape and risks (this article)
- [Step 4: Take action and investigate with Security Copilot](depmod-dspm-step4)

![Deploy and use Microsoft Purview Data Security Posture Management (DSPM) deployment blueprint.](media/dspmdiagram.png)

After the initial Data Security Posture Management (DSPM) scan finishes, you can start reviewing insights to understand your data landscape and identify risks. This step covers the three main areas of DSPM: reports, trends, and recommendations.

## Review DSPM analytics reports

Use [DSPM analytics reports](../data-security-posture-management) to understand where sensitive data exists and how users interact with it. Each report provides options for filtering, reviewing, evaluating, and exporting insights.

DSPM analytics reports focus on two main areas:

- **Unprotected sensitive assets across data sources**: This report is similar to content explorer but covers the entire data estate. It provides insights on what isn't protected by Data Loss Prevention (DLP) and/or what isn't labeled with access control. The report shows the location of the files and their associated classifiers.
- **Users performing top risk-related activities on unprotected sensitive assets**: This report is associated with Insider Risk Management and flags based on Insider Risk Management identifiers such as departing users and high-risk users. It also includes activities based on classifiers not included in DLP.

1. Select [**Reports**](../data-security-posture-management) to view the analytics reports.
2. Review the **Unprotected sensitive assets** report to identify gaps in data protection.
3. Review the **Users performing top risk-related activities** report to identify high-risk user behaviors.

## Monitor DSPM trends

Use DSPM trends on the Overview page to track and understand historical activity around sensitive data and users. Trends highlight changes over time and help you measure the effectiveness of your data security posture.

DSPM tracks the following trends:

- **Sensitive assets labeled (automatically and manually)**: The percentage of assets per week that had sensitivity labels applied.
- **Sensitive assets protected by at least one DLP policy**: The percentage of sensitive assets in your organization protected by one or more DLP policies.
- **Potentially risky users**: The number of users per week who were assigned insider risk severity levels (low, medium, high).

To learn more, see [Learn about Data Security Posture Management](../data-security-posture-management).

## Review DSPM recommendations

Use DSPM recommendations to understand your current risk posture and determine next steps. Recommendations are generated from the processed data, current state of unprotected sensitive assets, and user activities that put these assets at risk.

DSPM recommendations:

- Enable organizations to act quickly by creating DLP and Insider Risk Management policies that mitigate data security risks.
- Identify gaps in existing DLP and Insider Risk Management policies.
- Automatically update, including removing recommendations older than 30 days.

Tip

Review DSPM recommendations at least every 30 days to understand current risk and determine next steps. Recommendations are refreshed regularly and reflect the latest state of your data estate.

To learn more, see [Learn about Data Security Posture Management](../data-security-posture-management).

## Summary

At the end of this step, your organization has:

- Reviewed analytics reports to understand unprotected sensitive assets and risky user activities.
- Monitored trends to track changes in data security posture over time.
- Reviewed DSPM recommendations to understand current risk and identify next steps.