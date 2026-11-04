---
layout: Conceptual
title: 'Step 4: Take action and investigate with Security Copilot - Deploy and use Data Security Posture Management | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-dspm-step4
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Create DLP and Insider Risk Management policies from DSPM recommendations and investigate risks with Microsoft Security Copilot.
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
document_id: 0b6915cb-e2a4-a761-4211-f9bbd24c5a74
document_version_independent_id: 0b6915cb-e2a4-a761-4211-f9bbd24c5a74
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-dspm-step4.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-dspm-step4
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-dspm-step4.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/03921bea-3752-4ddc-98c2-5aa70db91565
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/09911d3e-3eb9-4c8d-ab86-ce80d8d36bbd
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 12cdbd09-282f-358f-9276-63676b682ca1
---

# Step 4: Take action and investigate with Security Copilot - Deploy and use Data Security Posture Management | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-dspm-intro)
- [Step 1: Establish foundational elements](depmod-dspm-step1)
- [Step 2: Configure access and analytics](depmod-dspm-step2)
- [Step 3: Understand data landscape and risks](depmod-dspm-step3)
- Step 4: Take action and investigate with Security Copilot (this article)

![Deploy and use Microsoft Purview Data Security Posture Management (DSPM) deployment blueprint.](media/dspmdiagram.png)

With a clear understanding of your data landscape and risks from Step 3, this step focuses on taking action. Use Data Security Posture Management (DSPM) recommendations to create policies that mitigate identified risks, and use Microsoft Security Copilot to investigate specific users and activities.

## Create DLP and Insider Risk Management policies based on DSPM recommendations

Use [DSPM recommendations](../data-security-posture-management) to create Data Loss Prevention (DLP) and Insider Risk Management policies that address identified risks. DSPM provides step-by-step guidance to create policies without leaving the DSPM page.

1. Select **Recommendations** and [choose a recommendation](../data-security-posture-management) to review.
2. Select the option to create a [DLP](../dlp-create-deploy-policy) or [Insider Risk Management](../insider-risk-management-configure) policy based on the recommendation.
3. Follow the step-by-step guidance to configure and create the policy.
4. Review the policy settings and submit.

Note

It takes a few minutes to create each policy and about 24 hours for the triggering event to take effect. You can find created policies on each solution's page (DLP or Insider Risk Management). Creating policies can generate additional recommendations that help with policy updates and tuning.

Administrators can also use the guidance to update existing policies instead of creating new policies. Recommendations are updated accordingly following administrator actions.

## Investigate users with Microsoft Security Copilot in DSPM recommendations

Use Microsoft Security Copilot within DSPM to investigate users involved in recommendations. Security Copilot provides an AI-powered investigation experience that helps you understand user activities and risks in context.

1. In a DSPM recommendation, select **Show Users Involved** to start an interaction with Security Copilot.
2. Use follow-up prompts to deep dive into the activity surrounding the recommendation.
3. Alternatively, open Security Copilot from the top of the DSPM page to investigate any action or user.

Example prompts for investigation:

- "Provide a list of events where sensitive files were shared externally."
- "List all the sensitive files that were uploaded to cloud in the last week."
- "Show me the data activities for user [UPN] in the last 30 days."

To learn more, see [Data Security Posture Management with Security Copilot](../data-security-posture-management-copilot).

## Use Promptbooks and Copilot Prompt Gallery for guided investigations

Use DSPM Promptbooks and the Copilot Prompt Gallery to run guided investigations with curated prompt sequences. These resources help administrators get started with overall investigations or find deeper insights.

- **Risky user investigation Promptbook**: A six-prompt sequence designed to aid in identifying users handling sensitive data, show their data activities, anomalies, and related alerts. Input a user principal name (UPN) and a timeframe (maximum of 30 days).
- **Sensitive data protection Promptbook**: A six-prompt sequence to identify and protect sensitive data across the organization and suggest recommended policy changes and DLP rules. Input a SIT or label, and a duration (maximum of 30 days).
- **Copilot Prompt Gallery**: Includes sample prompts to aid in investigations across five categories: alerts and policies, data at risk, potentially risky users, potentially suspicious activity, and sensitive data.

To learn more, see [Data Security Posture Management with Security Copilot - Copilot Prompt Gallery](../data-security-posture-management-copilot#copilot-prompt-gallery).

## Plan a monthly iteration cycle

After completing all four steps, establish a monthly iteration cycle to continuously improve your data security posture:

1. Review DSPM reports and trends to identify changes in your data landscape.
2. Review DSPM recommendations to understand current risk and determine next steps.
3. Create or update DLP and Insider Risk Management policies based on new recommendations.
4. Investigate flagged users and activities with Security Copilot.
5. Assess overall risks and strengthen your data security posture.

To learn more, see [Learn about Data Security Posture Management](../data-security-posture-management).

## Summary

At the end of this step, your organization has:

- Created DLP and Insider Risk Management policies from DSPM recommendations to mitigate identified risks.
- Used Security Copilot to investigate users and activities associated with recommendations.
- Used promptbooks and Copilot Prompt Gallery for guided investigations.
- Established a monthly iteration cycle to continuously improve data security posture.