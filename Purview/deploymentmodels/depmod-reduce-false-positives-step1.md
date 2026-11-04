---
layout: Conceptual
title: 'Step 1: Configure pattern-based sensitive data detection - Reduce false positives | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-reduce-false-positives-step1
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Choose, customize, and refine sensitive information types for accurate pattern-based detection with fewer false positives.
ms.author: kreagle
author: k-reagle
manager: laurawi
ms.reviewer: maximeb
ms.date: 2026-10-14T00:00:00.0000000Z
audience: ITPro
ms.topic: best-practice
ms.service: purview
ms.localizationpriority: medium
ms.collection:
- tier2
- purview-deployment-models
ai-usage: ai-assisted
ms.custom: msecd-doc-authoring-1030
locale: en-us
document_id: 1e4aade4-05f8-3792-83f6-30f7f524d947
document_version_independent_id: 1e4aade4-05f8-3792-83f6-30f7f524d947
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-reduce-false-positives-step1.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-reduce-false-positives-step1
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-reduce-false-positives-step1.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
- https://authoring-docs-microsoft.poolparty.biz/devrel/7e593268-8d01-46ef-aa78-9d1388e6a294
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
- https://authoring-docs-microsoft.poolparty.biz/devrel/264d03ab-bab8-454b-a56c-0fedead7f602
platformId: e04dae70-2ebb-247a-d5d6-5a58ef2b2aee
---

# Step 1: Configure pattern-based sensitive data detection - Reduce false positives | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-reduce-false-positives)
- Step 1: Configure pattern-based sensitive data detection (this article)
- [Step 2: Implement Exact Data Match for precise matching](depmod-reduce-false-positives-step2)
- [Step 3: Use trainable classifiers for complex content](depmod-reduce-false-positives-step3)
- [Step 4: Apply document fingerprinting for templates](depmod-reduce-false-positives-step4)

![Screenshot of Reduce false positives by using SITs and advanced classifiers - Blueprint.](../media/blueprint-false-positives.png)

To use sensitive information types (SITs) for data security across your digital enterprise, it's important to have a comprehensive view of your data estate. Map the sensitive data first to identify what types of sensitive data exist in your enterprise and where it resides.

## Choose from built-in SITs and customize if needed

Start with the built-in SITs provided by Microsoft. If they don't suit your needs as is, clone and edit them to make them precisely relevant to your business context.

- **Use built-in SITs**: Start with the SITs provided by Microsoft Purview. To learn more, see [Learn about sensitive information types](../sit-sensitive-information-type-learn-about).
- **Clone and edit**: If built-in SITs don't fully meet your needs, clone and customize them. To learn more, see [Customize a built-in sensitive information type](../sit-customize-a-built-in-sensitive-information-type).
- **Create custom SITs**: Create your own SITs from scratch to address your organization's unique data classification needs. Use multiple patterns in a single SIT definition to ensure comprehensive identification. For example, a SIT created to identify date-of-birth should account for different formats (DD/MM/YYYY, MM/DD/YYYY, and so on). To learn more, see [Create custom sensitive information types](../sit-create-a-custom-sensitive-information-type).
- **Test custom SITs, then refresh classification where needed**: Use [uploaded-file tests](../sit-test-a-sit) with representative matching and nonmatching examples. For historical SharePoint and OneDrive files that need updated classification, use [on-demand classification](../on-demand-classification) after reviewing scope, estimates, charges, and active policies. A scan can trigger actions from active matching policies; it isn't a non-mutating policy simulation. See [Auto-labeling classification and simulation concepts](../auto-label-classification-simulation).
- **Use multiple SITs in DLP policy rules**: Create a more comprehensive and precise detection strategy by using multiple SITs. For instance, when detecting PII, choose a combination of SITs that cover SSN, driving license number, passport number, and so on, with an *OR* condition instead of depending solely on a single SIT.

## Identify appropriate primary element type in SIT configuration

When you define the primary element, choose from four options: Regular expression (regex), Keyword list, Keyword dictionary, or Function. Follow these recommendations for each type:

| Primary element type | Key recommendations |
| --- | --- |
| Regular expression | Use lookaround assertions to ensure context and reduce irrelevant matches. Validate regex patterns against diverse datasets. If you need to detect isolated strings, use `\b` at the beginning and end, or select "word match" instead of "string match." You can enhance detection by using other built-in validators with logic that isn't possible by using regular expressions only. |
| Keyword list | Use casing capability based on whether exact casing is required. In space-delimited languages, use "word match" instead of "string match" for better accuracy. For non-space-delimited languages like Chinese, Japanese, Thai, and Korean, "string match" improves classification accuracy by detecting keywords embedded inside larger words. |
| Keyword dictionary | Use this type over keyword list when you need easier management of keywords at a larger scale. Be mindful of the limit of 1 MB of compressed text across all dictionaries in the tenant. Keyword dictionaries are always case insensitive. |
| Function | Identify the appropriate function from a list of predefined functions. These functions behave in a similar way to regular expressions but with more programmatic functionality. |

To learn more, see [Learn about sensitive information types](../sit-sensitive-information-type-learn-about).

## Refine using proximity elements, confidence level, and exclusions

- **Add supporting elements**: Provide supporting elements as corroborative evidence alongside the primary element. For example, simply matching a date format for date-of-birth can lead to massive false positives from email headers and timestamps. Adding supporting keywords (DOB, DateOfBirth) ensures only high-confidence matches.
- **Set proximity limits**: Set the proximity limit to 300 characters for any new custom SIT. Avoid configuring unlimited proximity ("anywhere in the document"), as it leads to too many false positives. For large tabular data, use the `RelaxProximity` option configurable by using PowerShell.
- **Configure confidence levels**: Specify a higher confidence level for patterns with more supporting elements or more restrictive regular expressions. Set the confidence level to low if the SIT has few or no supporting elements.
- **Use exclusions**: Include or exclude specific text and patterns, prefixes, or suffixes to further improve match accuracy.
- **Test your configuration**: Use the [test functionality](../sit-test-a-sit) to validate your SIT's accuracy, and use Content Explorer to review detected matches.

To learn more, see [Test a sensitive information type](../sit-test-a-sit).

## Provide match and not-a-match feedback for identified items

Regularly submit your feedback for all matched items to help Microsoft tune its SITs. For every item in SharePoint and OneDrive, Microsoft Purview allows you to provide feedback in terms of whether it's a match (true positive) or not a match (false positive). You can also choose to submit a redacted version of the item to Microsoft to help improve the accuracy of built-in SITs.

## Summary

At the end of this step, your organization has:

- Built-in and custom sensitive information types (SITs) configured for your organization's data classification needs.
- Primary elements defined with appropriate regex, keyword, dictionary, or function patterns.
- Proximity limits, confidence levels, and exclusions refined to reduce false positives.
- Feedback loop established to continuously improve SIT accuracy.