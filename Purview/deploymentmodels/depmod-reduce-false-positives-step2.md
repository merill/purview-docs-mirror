---
layout: Conceptual
title: 'Step 2: Implement Exact Data Match for precise matching - Reduce false positives | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-reduce-false-positives-step2
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Use Exact Data Match to precisely identify known sensitive data by matching against hashed reference data tables.
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
document_id: 61a758d3-671b-1336-a777-9c695bf81836
document_version_independent_id: 61a758d3-671b-1336-a777-9c695bf81836
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-reduce-false-positives-step2.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-reduce-false-positives-step2
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-reduce-false-positives-step2.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
platformId: 27e20afa-5de3-9f31-3182-045af63d5f2d
---

# Step 2: Implement Exact Data Match for precise matching - Reduce false positives | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-reduce-false-positives)
- [Step 1: Configure pattern-based sensitive data detection](depmod-reduce-false-positives-step1)
- Step 2: Implement Exact Data Match for precise matching (this article)
- [Step 3: Use trainable classifiers for complex content](depmod-reduce-false-positives-step3)
- [Step 4: Apply document fingerprinting for templates](depmod-reduce-false-positives-step4)

![Screenshot of Reduce false positives by using SITs and advanced classifiers - Blueprint.](../media/blueprint-false-positives.png)

Microsoft Purview helps you identify specific known sensitive data in your data estate by using Exact Data Match (EDM). EDM minimizes false positives by only flagging data that matches exactly to entries in an uploaded reference data table.

To learn more about EDM and how it works, see [Learn about exact data match based sensitive information types](../sit-learn-about-exact-data-match-based-sits).

## Use well-known information to define the EDM schema

Upload a sample file and use the automation provided by Microsoft Purview to define the schema. The schema defines the structure of your reference data table, including the columns that contain sensitive data and the columns that provide corroborative evidence.

To learn more, see [Get started with exact data match based sensitive information types](../sit-get-started-exact-data-match-based-sits-overview).

## Map primary element to a strongly defined SIT

Select as primary elements columns that contain strongly patterned data, such as SSNs or credit card numbers, and use a strongly defined [sensitive information type (SIT)](../sit-sensitive-information-type-learn-about) as the base SIT for primary elements. When you map the primary field to a loosely defined SIT that covers a broad range of values, the performance of the EDM classifier suffers, resulting in throttling or timeout scenarios that cause missed detections.

Avoid the following examples of "loose" SITs:

- Plain numbers with fewer than five digits (too common).
- Email address SIT that doesn't exclude the company's domain (matches on every email).
- Date of Birth SIT that doesn't exclude recent or future dates.
- All Full Names SIT (produces too many matches and captures superstrings).
- A regex to detect GUIDs (matches on headers of every email).
- A regex that doesn't isolate a single word or sequence - for example, the regex `\d{6}` matches on a six-digit number but also numbers with greater than six digits. A better regex would be `\b\d{6}\b`.
- Street address SIT (detects too many variations in the writing).

## Ignore delimiters and punctuation to improve match accuracy

Select the option to ignore delimiters and punctuation in the data wherever applicable while defining the schema columns. For instance, a U.S. phone number can be written as +11234567890, or (+1) 123 456 7890, or +1 123-456-7890. By choosing to ignore delimiters and punctuation, you can ensure that each format is identified as a valid match.

To learn more, see [Create an EDM SIT schema and rule package](../sit-create-edm-sit-unified-ux-schema-rule-package).

## Use additional columns as correlated evidence for higher confidence matches

Select the appropriate match mode for each column out of the three available options: single-token, multi-token, or a SIT. If you can accurately map any of the supporting evidence fields to a built-in or custom SIT, do so to ensure higher accuracy and improved latency. Avoid using multi-token matching for a field that consistently contains single-token data only.

- For high confidence matches, include a greater number of supporting elements in the defined character proximity range.
- Optionally, create a low confidence pattern with only a lower number of supporting elements, or none if the primary element is accurate enough on its own.
- Select *wide* mode or *narrow* mode as the proximity detection mode based on how you want the supporting elements to be checked.

To learn more, see [Create an EDM SIT schema and rule package](../sit-create-edm-sit-unified-ux-schema-rule-package).

## Summary

At the end of this step, your organization has:

- An EDM schema defined based on well-known reference data.
- Primary elements mapped to strongly defined SITs to avoid performance issues.
- Delimiters and punctuation configured to improve match accuracy across data formats.
- Additional columns configured as correlated evidence for higher confidence matches.