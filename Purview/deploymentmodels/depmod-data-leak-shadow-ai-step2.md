---
layout: Conceptual
title: 'Step 2: Block access to unsanctioned AI apps - Prevent data leak to shadow AI | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-data-leak-shadow-ai-step2
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Block organizational and user-level access to unsanctioned AI apps by using Microsoft Defender for Cloud Apps, Microsoft Entra, and Microsoft Intune.
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
document_id: 68e20c1e-76d1-9876-d3b0-4501159e9dfd
document_version_independent_id: 68e20c1e-76d1-9876-d3b0-4501159e9dfd
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-data-leak-shadow-ai-step2.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-data-leak-shadow-ai-step2
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-data-leak-shadow-ai-step2.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 0b1889d9-43b7-18a0-497e-1c52e4cf40a1
---

# Step 2: Block access to unsanctioned AI apps - Prevent data leak to shadow AI | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-data-leak-shadow-ai-intro)
- [Step 1: Discover AI apps](depmod-data-leak-shadow-ai-step1)
- Step 2: Block access to unsanctioned AI apps (this article)
- [Step 3: Block sensitive data going to sanctioned AI apps](depmod-data-leak-shadow-ai-step3)
- [Step 4: Govern data sent to AI apps](depmod-data-leak-shadow-ai-step4)

![Prevent data leak to shadow AI with Microsoft.](media/depmod-data-leak-shadow-ai-intro/prevent-shadow-ai-thumb.png)

After discovering AI app usage in your organization, the next step is to block access to apps that your organization didn't sanction. This step uses Microsoft Defender for Cloud Apps, Microsoft Entra, and Microsoft Intune to enforce access restrictions at the organizational, user, and device levels.

## Block access for the organization with Microsoft Defender for Cloud Apps

Use [Microsoft Defender for Cloud Apps](/en-us/defender-cloud-apps/governance-discovery) to block access to unsanctioned AI apps for the entire organization. After you identify and tag AI apps as unsanctioned in Step 1, you can enforce blocking policies.

1. [Select the AI apps](/en-us/defender-cloud-apps/governance-discovery) you identified as unsanctioned in the **Cloud app catalog**.
2. Select **Unsanction** to [mark the apps as blocked](/en-us/defender-cloud-apps/governance-discovery).
3. Verify that the block action is propagated to your network controls.

Important

Blocking unsanctioned apps at the organizational level prevents all users from accessing these apps through managed network connections. Users can still access these apps through unmanaged devices or personal networks, which is addressed later in this step.

## Restrict specific users and groups with Microsoft Entra

While Defender for Cloud Apps provides organization-wide blocking, you might need more granular control over AI app access. Use Microsoft Entra Internet Access to allow limited access to certain AI apps while restricting specific users and groups from accessing unsanctioned AI apps.

You can also combine Microsoft Entra with Microsoft Purview Insider Risk Management to block elevated-risk users from accessing AI apps. By using Adaptive Protection with Conditional Access policies, users identified as high risk by Insider Risk Management are automatically restricted from accessing AI applications.

To learn more, see:

- [What is Microsoft Entra Internet Access?](/en-us/entra/global-secure-access/concept-internet-access)
- [Help dynamically mitigate risks with Adaptive Protection](../insider-risk-management-adaptive-protection)

## Block installation of unsanctioned AI apps on devices with Microsoft Intune

Use Microsoft Intune to block the installation of unsanctioned AI apps on managed devices. This approach addresses the scenario where users attempt to install AI applications directly on their devices rather than accessing them through a browser.

To learn more, see [Blocking and removing apps on Intune managed devices](https://techcommunity.microsoft.com/blog/intunecustomersuccess/blocking-and-removing-apps-on-intune-managed-devices-windows-iosipados-android-a/4383156).

## Summary

At the end of this step, your organization has:

- Organization-wide blocking of unsanctioned AI apps through Microsoft Defender for Cloud Apps.
- Granular user and group-level access restrictions through Microsoft Entra Internet Access.
- Elevated-risk users automatically blocked from AI app access through Adaptive Protection and Conditional Access.
- Device-level controls preventing installation of unsanctioned AI apps through Microsoft Intune.