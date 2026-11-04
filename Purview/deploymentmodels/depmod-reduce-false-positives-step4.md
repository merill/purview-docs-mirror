---
layout: Conceptual
title: 'Step 4: Apply document fingerprinting for templates - Reduce false positives | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-reduce-false-positives-step4
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Use document fingerprinting to detect specific document templates and fixed-format documents with consistent structure.
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
document_id: e483e69e-7c58-4edd-1731-4db8052f4cd3
document_version_independent_id: e483e69e-7c58-4edd-1731-4db8052f4cd3
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-reduce-false-positives-step4.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-reduce-false-positives-step4
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-reduce-false-positives-step4.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
platformId: 29ae9e8d-6739-df53-7faa-a3723fb4a7aa
---

# Step 4: Apply document fingerprinting for templates - Reduce false positives | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-reduce-false-positives)
- [Step 1: Configure pattern-based sensitive data detection](depmod-reduce-false-positives-step1)
- [Step 2: Implement Exact Data Match for precise matching](depmod-reduce-false-positives-step2)
- [Step 3: Use trainable classifiers for complex content](depmod-reduce-false-positives-step3)
- Step 4: Apply document fingerprinting for templates (this article)

![Screenshot of Reduce false positives by using SITs and advanced classifiers - Blueprint.](../media/blueprint-false-positives.png)

Use the document fingerprinting technique to detect specific document templates or fixed-format documents that have a consistent structure. Document fingerprinting is most useful when your organization has standardized templates for contracts, invoices, RFPs, or other business forms containing sensitive data.

To learn more, see [About document fingerprinting](../sit-document-fingerprinting).

## Choose a small number of high-value assets

To choose what to fingerprint, identify the high-value or highly sensitive documents that are well-known within your organization. Fingerprint these documents at either "full match" or "high match" rates so you can detect either identical copies of these documents or closely matching variations as they move within or outside the organization.

## Use partial matching to detect modified or partial versions

Tune your fingerprint sensitive information type (SIT) to detect content that has a partial match with the fingerprint. This tuning covers cases where there are slight modifications to the standard template on which the fingerprint is defined. For instance, if you want Microsoft Purview to flag items that are at least a 50% match to the fingerprint, define confidence levels as:

- **Low**: 50% match and above
- **Medium**: 70% match and above
- **High**: 90% match and above

## Adjust confidence level based on real-world results

If you see many false positives, increase the minimum match threshold and adjust the confidence levels. If you see many false negatives, lower the match threshold. Make this adjustment regularly by carefully analyzing the matched items. For more information about how confidence levels affect [DLP policy](../dlp-create-deploy-policy) rule matching, see [Data Loss Prevention policy reference](../dlp-policy-reference).

## Set high confidence level value to exact for exact matching

Choose an exact match in document fingerprinting when you're dealing with highly structured, critical documents that require precise identification without room for variation. Otherwise, define a high rate rather than use full rate, since some forms of document conversion (for example, transcription as PDF, addition of a header or footer, or upgrade to a newer file format) can introduce minor modifications that prevent matching at 100%.

## Summary

At the end of this step, your organization has:

- High-value document templates identified and fingerprinted.
- Partial matching configured to detect modified or partial versions of templates.
- Confidence levels tuned based on real-world results to balance false positives and false negatives.
- Exact matching configured for critical documents requiring precise identification.

By following this blueprint, you can strategically apply Microsoft Purview's classification technologies - sensitive information types (SITs), Exact Data Match (EDM), trainable classifiers, and document fingerprinting - across different scenarios to maximize detection accuracy while reducing friction.