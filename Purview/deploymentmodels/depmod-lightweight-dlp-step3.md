---
layout: Conceptual
title: 'Step 3: Continuous improvement - Lightweight guide to mitigate data leakage | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-lightweight-dlp-step3
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Apply encryption to labeled content, extend service-side auto-labeling, and enable Adaptive Protection for dynamic DLP policies.
ms.author: kreagle
author: k-reagle
manager: laurawi
ms.reviewer: maximeb
ms.date: 2026-10-14T00:00:00.0000000Z
audience: ITPro
ms.topic: best-practice
ms.service: purview
ms.collection:
- purview-deployment-models
ai-usage: ai-assisted
ms.custom: msecd-doc-authoring-1030
locale: en-us
document_id: 8b06988f-4dd4-d282-a88c-778f256a44d5
document_version_independent_id: 8b06988f-4dd4-d282-a88c-778f256a44d5
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-lightweight-dlp-step3.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-lightweight-dlp-step3
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-lightweight-dlp-step3.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/9d7be3ef-f27c-4c7f-9eba-67c3cd429995
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/feeb50f3-b677-44f9-b3a6-5f2f58182b0d
platformId: af9f5590-f717-db7b-e35d-061e3311683d
---

# Step 3: Continuous improvement - Lightweight guide to mitigate data leakage | Microsoft Learn

This guide is divided into three steps:

- [Introduction](depmod-lightweight-dlp-intro)
- [Step 1: Establish foundational data security](depmod-lightweight-dlp-step1)
- [Step 2: Expand protection to endpoints](depmod-lightweight-dlp-step2)
- Step 3: Continuous improvement (this article)

With foundational security and expanded endpoint protection in place, this step focuses on continuous improvement. You apply encryption to labeled content, extend auto-labeling to files at rest, and enable risk-based Adaptive Protection. Features in this step require Microsoft 365 E5 Compliance or above.

## Apply encryption to labeled content

Configure sensitivity labels to automatically [apply encryption](../encryption-sensitivity-labels) to files labeled with high-sensitivity sub-labels or containing critical sensitive information types (SITs). Encryption ensures only authorized users can access the content, even if it's shared externally.

1. Edit the high-sensitivity sub-labels and select **Control access** under **Items**.
2. Choose **Assign permissions now**.
3. Set expiration and offline access settings.
4. Assign permissions to users or groups.

## Extend service-side auto-labeling to Microsoft 365 services

Configure [service-side auto-labeling](../apply-sensitivity-label-automatically) to label eligible existing files in SharePoint and OneDrive, as well as emails in transit through Exchange. For existing files, policy evaluation uses available classification results. Changing a custom SIT or restarting simulation doesn't by itself refresh those results. See [Auto-labeling classification and simulation concepts](../auto-label-classification-simulation) to decide whether historical files need updated classification and to review the active-policy effects before running on-demand classification.

1. Create an auto-labeling policy and choose the label to auto-apply.
2. Choose locations: **Exchange**, **SharePoint**, and **OneDrive**.
3. Define conditions using your custom SITs.
4. Run the policy in simulation mode and optionally set it to automatically apply after 7 days.

## Run Microsoft Purview Insider Risk Management analytics

Use [Insider Risk Management analytics](../insider-risk-management-configure) to detect risky user activities such as data leaks, exfiltration, or policy violations. Analytics provides recommendations using [built-in policy templates](../insider-risk-management-policy-templates) to help you address the top risks in your organization.

1. Turn on analytics in the Insider Risk Management overview.
2. Review results and select **View details** to get recommended policies based on your top risks.
3. Create a policy defining users or groups to monitor and customizing triggers as needed (for example, DLP alerts, label changes, file downloads).

## Enable Adaptive Protection in Data Loss Prevention policies

Enable [Adaptive Protection](../dlp-adaptive-protection-learn) to dynamically adjust Data Loss Prevention (DLP) policies based on a user's risk level. Adaptive Protection allows low-risk users to take certain actions while blocking high-risk users, balancing data security with productivity.

1. Enable Adaptive Protection in **Insider Risk Management** &gt; **Adaptive Protection settings**.
2. Configure the thresholds for **Minor**, **Moderate**, and **Elevated** risk levels to align with your risk tolerance.
3. Edit a DLP policy and add a condition for **Insider risk level for Adaptive Protection is** &gt; **Elevated risk level**.
4. Set actions to block file activities for elevated-risk users.

## Enable Adaptive Protection for dynamic Conditional Access policies

Configure [Adaptive Protection with Conditional Access](../insider-risk-management-adaptive-protection) policies that dynamically restrict access when a user is flagged as high risk. Conditional Access policies can automatically restrict access to sensitive SharePoint sites and OneDrive content for elevated-risk users.

1. In Insider Risk Management, select **Adaptive Protection** &gt; **Conditional Access** &gt; **Create Policy**.
2. In the Microsoft Entra admin center, select the **Insider risk** condition and toggle it **On**.
3. Select **Target resources** &gt; **SharePoint and OneDrive**.
4. Under **Access controls**, select **Block access**.
5. Enable the policy in **Report-only** mode or **On**.

## Summary

At the end of this step, your organization has:

- Encryption applied to content labeled with high-sensitivity sub-labels.
- Service-side auto-labeling configured for eligible existing files in SharePoint and OneDrive, and emails in transit.
- Insider Risk Management analytics identifying top risks with recommended policies.
- Adaptive Protection dynamically adjusting DLP policies based on user risk levels.
- Conditional Access policies restricting elevated-risk users from accessing sensitive SharePoint and OneDrive content.