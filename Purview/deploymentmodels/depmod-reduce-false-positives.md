---
layout: Conceptual
title: Reduce false positives by using SITs and advanced classifiers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-reduce-false-positives
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Learn how to reduce false positives by using Microsoft Purview sensitive information types, EDM, trainable classifiers, and document fingerprinting.
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
document_id: 82ac320b-d0a8-4505-8d4a-0e8399cc3786
document_version_independent_id: 82ac320b-d0a8-4505-8d4a-0e8399cc3786
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-reduce-false-positives.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-reduce-false-positives
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-reduce-false-positives.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: 67829f94-288f-4128-9df9-aa612ed34896
---

# Reduce false positives by using SITs and advanced classifiers | Microsoft Learn

Accurate data identification and classification is the foundation of robust data security. It enables enterprises to confidently deploy data protection policies across their digital estate. Microsoft Purview supports this critical step with [sensitive information types (SITs)](../sit-sensitive-information-type-learn-about) and advanced classification technologies such as [Exact Data Match (EDM)](../sit-get-started-exact-data-match-based-sits-overview), [trainable classifiers](../trainable-classifiers-learn-about), and [document fingerprinting](../sit-document-fingerprinting).

However, to control the volume of false positives, you need to configure and apply these tools in the right contexts and scenarios. A false positive means that the system incorrectly flags something as a match even though it isn't. False positives:

- **Increase alert fatigue**: Overwhelms security and compliance teams, increasing the probability of genuine risks slipping through.
- **Drain time and resources**: Verification of false positives leads to escalation of operational costs, especially for enterprises handling high data volumes.
- **Create unnecessary obstructions**: Access restrictions incorrectly applied on content that isn't sensitive leads to friction in workflows and productivity.
- **Reduce user trust**: Lowers overall product adoption.

Therefore, it's important to have a clear understanding of the utility and relevance of SITs and advanced classifiers for the diversity of business scenarios in an enterprise.

## About this guide

This guide includes the following articles:

- Introduction (this article)
- [Step 1: Configure pattern-based sensitive data detection](depmod-reduce-false-positives-step1)
- [Step 2: Implement Exact Data Match for precise matching](depmod-reduce-false-positives-step2)
- [Step 3: Use trainable classifiers for complex content](depmod-reduce-false-positives-step3)
- [Step 4: Apply document fingerprinting for templates](depmod-reduce-false-positives-step4)

## Before you begin

This guide is for administrators with knowledge of Microsoft Purview Data Loss Prevention (DLP) and classification technologies. If you're new to these solutions, see the following articles to learn more:

- [Learn about sensitive information types](../sit-sensitive-information-type-learn-about)
- [Learn about exact data match based sensitive information types](../sit-learn-about-exact-data-match-based-sits)
- [Learn about trainable classifiers](../trainable-classifiers-learn-about)
- [About document fingerprinting](../sit-document-fingerprinting)

## Classification technologies overview

| Classification technology | Typical use case | Why? |
| --- | --- | --- |
| **SITs** | Identification of common sensitive data types that are widely recognized and follow standardized patterns. For example, credit card numbers, SSNs. | Quickly deployable with minimal configuration, along with built-in support. |
| **Exact Data Match** | Scenarios requiring precise data matching from a known data source. For example, detecting specific customer account numbers, employee IDs, or patient IDs. | Minimizes false positives by only flagging data that matches exactly to entries in the uploaded reference data table. |
| **Trainable classifier** | Identifying complex and contextual data, documents with varied structure and unpredictable format where traditional patterns don't apply. For example, legal documents with varying clauses and formats. | Provides a customizable and intelligent approach to complex data types. |
| **Document fingerprinting** | Use cases where document template and formatting are consistent across the organization. For example, business contracts, invoices, RFPs, or standard forms containing sensitive data. | Provides targeted protection for critical, structured documents. |

## Deployment overview

The deployment model breaks the approach into four steps, each focusing on a different classification technology:

| Step | Classification technology | Description |
| --- | --- | --- |
| [Step 1: Configure pattern-based sensitive data detection](depmod-reduce-false-positives-step1) | Sensitive information types (SITs) | Choose, customize, and refine SITs for accurate pattern-based detection. |
| [Step 2: Implement Exact Data Match for precise matching](depmod-reduce-false-positives-step2) | Exact Data Match (EDM) | Use hashed reference data for precise identification of known sensitive data. |
| [Step 3: Use trainable classifiers for complex content](depmod-reduce-false-positives-step3) | Trainable classifiers | Use AI-driven classifiers for complex content that doesn't follow standard patterns. |
| [Step 4: Apply document fingerprinting for templates](depmod-reduce-false-positives-step4) | Document fingerprinting | Detect specific document templates and fixed-format documents. |

## Microsoft Purview deployment blueprint

![Screenshot of Reduce false positives by using SITs and advanced classifiers - Blueprint.](../media/blueprint-false-positives.png)

## Scenario-based data classification strategies

The following table provides deployment guidance with examples of the recommended data classification techniques for different scenarios.

| Scenario | Preferred method | Alternative methods | Techniques to reduce false positives |
| --- | --- | --- | --- |
| Detect PII/PHI for known individuals (customers or patients) | EDM for data from LoB app extract | Custom SITs including employee ID + common PII SITs (for example, SSN) | If you use regular SITs, consider requiring the presence of All Full Names, and limit rules to documents with more than a certain minimum match count. |
| Detect PII/PHI for employees or contractors | EDM for data from HR system extract | Custom SITs including employee ID + Named Entities (for example, all full names) + common PII SITs | If you use regular SITs, consider requiring the presence of All Full Names, and limit rules to documents with more than a certain minimum match count. |
| Detect forms with personal data | Form fingerprinting + standard SITs or fingerprinting + custom SITs | Custom SITs + OCR (for scanned forms) | Use EDM instead of custom SITs if not using fingerprinting. |
| Contracts, legal documents, or other business forms | Custom trainable classifiers (+ OCR) | Built-in trainable classifiers + OCR | Identify documents in your organization that the built-in TC correctly identifies, copy them to a repository, and use them to train a custom TC. |
| Important contracts or other documents | Trainable classifier + sensitivity label | Trainable classifier + custom SIT (for example, regex to detect monetary amounts over $100K) | Combine multiple TCs in a single rule, for example, "Contracts" and "Documents about Project X." |
| General PII or PHI of unknown individuals | Built-in SITs if available or custom SITs | Manual labeling | Copy and edit an existing SIT to fine-tune its keyword requirements. Add requirements for named entities such as All Full Names. |
| Scanned identity cards (or similar) | Built-in or custom SITs + OCR | Custom SIT with keyword lists + OCR | Add requirements for Named Entities (names or addresses) if expected to be written in one line. |
| Project data | Location-based labeling (for example, default label for library) | Manual labeling or custom trainable classifiers | Once location-based labeling identifies enough relevant documents, use them to train a custom TC. |

## Optimize DLP policy configuration

When you use classifiers in your Data Loss Prevention (DLP) policies, adjust the instance count to reduce false positives. Keep the minimum threshold for instance count at a higher value when small or trivial occurrences of sensitive data don't require action. However, when your business context demands tightened data security, use a lower instance count to block even a single occurrence. Tailor the instance count to the sensitivity level of the data.

Content Explorer is your central hub for discovering sensitive content across your data estate. It provides exhaustive visibility into the types and locations of sensitive data. By tuning instance thresholds and setting the appropriate confidence levels for detection, you can ensure alerts are triggered only when the context aligns with your organizational risk posture.