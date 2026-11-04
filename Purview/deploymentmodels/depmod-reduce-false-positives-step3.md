---
layout: Conceptual
title: 'Step 3: Use trainable classifiers for complex content - Reduce false positives | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-reduce-false-positives-step3
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Use trainable classifiers to identify complex content that doesn't follow standard patterns, reducing false positives with AI-driven classification.
ms.author: kreagle
author: k-reagle
manager: laurawi
ms.reviewer: maximeb
ms.date: 2026-03-31T00:00:00.0000000Z
audience: ITPro
ms.topic: best-practice
ms.service: purview
ms.localizationpriority: medium
ms.collection:
- tier2
- purview-deployment-models
ai-usage: ai-assisted
locale: en-us
document_id: 8b3a590b-19c3-202e-8d0f-7a560954fe18
document_version_independent_id: 8b3a590b-19c3-202e-8d0f-7a560954fe18
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-reduce-false-positives-step3.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-reduce-false-positives-step3
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-reduce-false-positives-step3.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/d6f38669-3d05-40f2-afd8-e49f7dd20884
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/55265cca-de9b-48dc-a77a-9047cc39a575
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
platformId: f5f798f6-34c8-65d0-4f1d-9893f5d96633
---

# Step 3: Use trainable classifiers for complex content - Reduce false positives | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-reduce-false-positives)
- [Step 1: Configure pattern-based sensitive data detection](depmod-reduce-false-positives-step1)
- [Step 2: Implement Exact Data Match for precise matching](depmod-reduce-false-positives-step2)
- Step 3: Use trainable classifiers for complex content (this article)
- [Step 4: Apply document fingerprinting for templates](depmod-reduce-false-positives-step4)

![Screenshot of Reduce false positives by using SITs and advanced classifiers - Blueprint.](../media/blueprint-false-positives.png)

Use trainable classifiers when you need to identify organization-specific or proprietary content that built-in sensitive information types (SITs) or Microsoft-pretrained classifiers can't reliably detect. Trainable classifiers use machine learning to identify document patterns, providing a customizable and intelligent approach to complex data types.

## Choose from built-in pretrained classifiers

Use the pretrained ready-to-use trainable classifiers provided by Microsoft. Identify which trainable classifier suits your use case, test it with your sample data to validate that it meets your requirement, and start using it in your policies with no extra effort of manual setup and fine-tuning.

If the built-in trainable classifiers don't meet your needs, create your own custom classifiers based on relevant documents from your organization.

To learn more, see [Learn about trainable classifiers](../trainable-classifiers-learn-about).

## Seed custom classifiers with a large, diverse set of samples

Train your custom classifier with an adequate number of positive and negative samples of the type of content you want it to detect. If some of the trainable classifiers that Microsoft provides in Microsoft Purview are relevant to your needs but don't provide the necessary accuracy in your environment, use them to detect a large set of documents that are correct matches. Collect them in one location (removing the false positives and adding manually identified relevant documents). Use unrelated documents and documents that were incorrectly matched by the original classifier as negative examples.

This approach ensures that the training set accounts for your specific jargon, names, and other relevant aspects of your information.

To learn more, see [Get started with trainable classifiers](../trainable-classifiers-get-started-with).

## Provide match and nonmatch feedback for identified items

Like the case of SITs, provide regular feedback for each item matched to a trainable classifier to improve the classifier accuracy. If the classifier detects many false positives, remove the custom classifier and create it afresh with a larger and more precise sample data set.

## Combine trainable classifiers with SITs for more accuracy

Use the hybrid approach of blending machine learning (with trainable classifier) and rule-based pattern matching (with [SIT](../sit-sensitive-information-type-learn-about)) to attain higher accuracy. For example, to identify sensitive business contracts exceeding $100K value, pair the pretrained `Business Context` trainable classifier with a custom SIT that detects contract sums over $100K. You can use these classifiers in [DLP policies](../dlp-create-deploy-policy) for comprehensive data protection.

## Summary

At the end of this step, your organization has:

- Built-in pretrained classifiers evaluated and deployed where applicable.
- Custom trainable classifiers created with a diverse set of positive and negative samples.
- Feedback loop established to continuously improve classifier accuracy.
- Hybrid approach combining trainable classifiers with SITs for higher accuracy.