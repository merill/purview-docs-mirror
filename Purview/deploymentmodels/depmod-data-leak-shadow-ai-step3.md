---
layout: Conceptual
title: 'Step 3: Block sensitive data going to sanctioned AI apps - Prevent data leak to shadow AI | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-data-leak-shadow-ai-step3
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Prevent sensitive data from being shared with sanctioned AI apps by using Microsoft Purview sensitivity labels, DLP, and data security policies.
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
document_id: df5cc709-c6d0-e814-5650-e9886a5dc39f
document_version_independent_id: df5cc709-c6d0-e814-5650-e9886a5dc39f
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-data-leak-shadow-ai-step3.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-data-leak-shadow-ai-step3
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-data-leak-shadow-ai-step3.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
platformId: 52c9b73e-8bd1-0b21-3d38-7b3af2265b02
---

# Step 3: Block sensitive data going to sanctioned AI apps - Prevent data leak to shadow AI | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-data-leak-shadow-ai-intro)
- [Step 1: Discover AI apps](depmod-data-leak-shadow-ai-step1)
- [Step 2: Block access to unsanctioned AI apps](depmod-data-leak-shadow-ai-step2)
- Step 3: Block sensitive data going to sanctioned AI apps (this article)
- [Step 4: Govern data sent to AI apps](depmod-data-leak-shadow-ai-step4)

![Prevent data leak to shadow AI with Microsoft.](media/depmod-data-leak-shadow-ai-intro/prevent-shadow-ai-thumb.png)

Even when you sanction AI apps for use in your organization, you still need to prevent sensitive data from being shared with those apps. This step focuses on using Microsoft Purview capabilities to protect sensitive information from being pasted, uploaded, or sent to sanctioned AI applications.

## Label content with sensitivity labels

Use Microsoft Purview [sensitivity labels](../sensitivity-labels) to classify and protect content. Other AI apps can't decrypt content that's encrypted by Microsoft Purview, which provides a foundational layer of protection against data leakage through AI applications.

When you label content with encryption, even if a user attempts to paste or upload the content to an AI app, the AI app can't process the encrypted content. This protection makes sensitivity labeling with encryption one of the most effective protections against data leakage to shadow AI.

To learn more about deploying sensitivity labels, see the [Secure by default with Microsoft Purview](depmod-secure-by-default-intro) deployment model.

## Block pasting and uploading of sensitive info with Endpoint DLP

Use Microsoft Purview [Endpoint Data Loss Prevention (DLP)](../endpoint-dlp-learn-about) to block pasting and uploading of sensitive information to AI apps. Endpoint DLP monitors user activities on managed devices and can prevent sensitive data from being shared through copy/paste operations or file uploads to AI application websites.

1. [Create a DLP policy](../dlp-create-deploy-policy) with **Devices** as the location.
2. Set conditions to detect content containing sensitive information types or sensitivity labels.
3. Set actions to block paste to browser, upload to cloud services, or copy to clipboard for AI application websites.
4. Run in simulation mode first to understand the impact on users.

Tip

Review the DLP activity explorer to identify false positives and fine-tune your policy conditions.

## Block sensitive info in AI prompts in Microsoft Edge

Use Microsoft Purview DLP or collection policies for Microsoft Edge to block sensitive information in text prompts being sent to consumer AI applications, including ChatGPT (consumer), Microsoft Copilot (consumer version), DeepSeek, and Google Gemini.

Browser Data Security in Microsoft Edge enables DLP policies to inspect text that users type or paste into AI application prompts in real time, blocking the submission of sensitive content before it leaves the browser.

To learn more, see [Learn about Browser Data Security](../dlp-browser-dlp-learn).

## Detect sensitive data shared through non-Microsoft browsers and apps

Use Microsoft Purview Network Data Security policies to detect sensitive data shared with cloud apps through non-Microsoft browsers, apps, APIs, add-ins, and more. Network Data Security extends DLP protection beyond Microsoft Edge to cover all network-level traffic, helping you detect data leakage through alternative pathways.

To learn more, see [Learn about Network Data Security](../dlp-network-data-security-learn).

## Monitor and protect Microsoft 365 Copilot use with Microsoft Defender for Cloud Apps

Use Microsoft Defender for Cloud Apps to monitor and protect Microsoft 365 Copilot use by detecting and responding to suspicious interactions. Defender for Cloud Apps provides visibility into how Copilot is being used and can alert administrators to potentially risky interactions.

To learn more, see [Investigate and remediate threats in Microsoft Defender for Cloud Apps](/en-us/defender-cloud-apps/investigate).

## Summary

At the end of this step, your organization has:

- Sensitivity labels applied to protect content with encryption, preventing AI apps from processing labeled data.
- Endpoint DLP policies blocking paste and upload of sensitive information to AI app websites.
- Browser Data Security policies in Microsoft Edge blocking sensitive prompts to consumer AI apps.
- Network Data Security policies detecting sensitive data shared through non-Microsoft browsers and apps.
- Defender for Cloud Apps monitoring Microsoft 365 Copilot interactions for suspicious activity.