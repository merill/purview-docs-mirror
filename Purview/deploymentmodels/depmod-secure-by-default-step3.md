---
layout: Conceptual
title: 'Step 3: Expand protection to your entire Microsoft 365 data estate - Secure by default with Microsoft Purview | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-secure-by-default-step3
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Securing by default - Step 3 - Expand to your entire Microsoft 365 data estate.
ms.author: kreagle
author: k-reagle
manager: laurawi
ms.reviewer: maximeb
ms.date: 2026-09-11T00:00:00.0000000Z
audience: ITPro
ms.topic: best-practice
ms.service: purview
ms.collection:
- purview-deployment-models
ai-usage: ai-assisted
ms.custom: msecd-doc-authoring-1028
locale: en-us
document_id: 439d54b2-803f-1b33-791d-1751d9a2293c
document_version_independent_id: 439d54b2-803f-1b33-791d-1751d9a2293c
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-secure-by-default-step3.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-secure-by-default-step3
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-secure-by-default-step3.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1dd701e0-441f-4b0a-9806-aa47decc4e35
- https://authoring-docs-microsoft.poolparty.biz/devrel/9d7be3ef-f27c-4c7f-9eba-67c3cd429995
- https://authoring-docs-microsoft.poolparty.biz/devrel/7428317a-e6c2-4461-ad3e-8a8ad3608734
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/0a2fc935-5977-4aa6-9f55-0be03bd2acb8
- https://authoring-docs-microsoft.poolparty.biz/devrel/feeb50f3-b677-44f9-b3a6-5f2f58182b0d
- https://authoring-docs-microsoft.poolparty.biz/devrel/e4f59707-f107-48f2-8d75-0afd91868cd7
platformId: 3c3bb0a6-d4e3-4566-d4b6-5eddb52d6816
---

# Step 3: Expand protection to your entire Microsoft 365 data estate - Secure by default with Microsoft Purview | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-secure-by-default-intro)
- [Step 1: Start with default labeling](depmod-secure-by-default-step1)
- [Step 2: Address files with the highest sensitivity](depmod-secure-by-default-step2)
- Step 3: Expand protection to your entire Microsoft 365 data estate (this article)
- [Step 4: Operate, expand, and retroactive actions](depmod-secure-by-default-step4)

![Secure by default with Microsoft Purview - Blueprint](../media/depmod-securebydefault-blueprintimage1.png)

In the previous steps, we laid the security foundation and discussed the priority sites. Both client-side and service-side auto-labeling functionalities were covered. For a comparison table, see [Automatically apply a sensitivity label in Microsoft 365](../apply-sensitivity-label-automatically#compare-auto-labeling-for-office-apps-with-auto-labeling-policies).

In this step, we explain options to help iteratively address all your Microsoft 365 data estate.

Previously, we recommended initial policies to familiarize users. In this step, you're ready to use them progressively in scenarios. Auto-labeling is best for scenarios where you need higher sensitivity than your default label.

We also discuss how to retroactively label existing sites and set default library labels.

## Auto-label sensitive files on clients (low thresholds)

Client-side auto-labeling gives users the chance to decide whether to apply a recommended label or report a false positive. You can implement this process by using the [300+ Sensitive Information Types (SITs)](../sit-sensitive-information-type-entity-definitions) and [Trainable classifiers](../trainable-classifiers-definitions#trainable-classifiers-definitions).

At a high level, follow this approach. The thresholds are examples only.

- Identify the relevant SIT for your industry.
- Recommend a label with lower SIT thresholds (1-9).
- Automatically apply a label with higher thresholds (10+) and/or Trainable classifiers.

Your client default label affects your auto-labeling strategy. While this guide recommends setting this label to **Confidential\All employees**, it also provides alternatives when the Office client defaults to General, and then to **Confidential\All employees** when saved in SharePoint.

Tip

If you set your default to **Confidential\All employees**, your auto-labeling strategy is less complex and focused for **Highly Confidential** labels.

You can progressively deploy this strategy with more SITs and trainable classifiers over time as you identify more business scenarios. By using defaults and client-side auto-labeling, you address all new and updated content.

## Simulate auto-labeling sensitive files at rest

Service-side auto-labeling labels files at rest in SharePoint and OneDrive, and provides more conditions. The **absolute maximum throughput** is 500,000 automatically labeled SharePoint and OneDrive files per tenant per day, in aggregate across all auto-labeling policies. This ceiling isn't a guaranteed or consistently expected daily processing rate; actual throughput can be lower. Simulation supports up to 20,000,000 matched files per policy simulation.

While client-side auto-labeling is limited to sensitive content, service-side auto-labeling adds support for contextual conditions such as:

- Content is shared
- File extension is
- Document name contains words or phrases
- Document property is
- Document size equals or is greater than
- Document created by

These conditions, combined with selecting specific sites and user’s OneDrive, allow your organization to prioritize which content to label first.

For example, if your organization uses templates with document properties or document name prefixes, you can run a policy across all SharePoint sites and OneDrive. You can also prioritize based on file size or documents created by your leadership teams.

You can finalize labeling all documents by using **Office/PDF file extensions** in batches of SharePoint sites, and set to match their respective site’s label, starting with higher sensitivity sites, progressively catching **General** sites.

Finally, you can implement more service-side auto-labeling for **Highly Confidential** content, often with higher thresholds than used in client-side auto-labeling to reduce potential false positives.

## Reduce false positives with advanced classifiers

This section explains the basics of advanced classifiers and when to use them.

In the context of this secure by default blueprint, focus on the use of classifiers with auto-labeling for highly confidential content. Advanced classifiers are limited to trainable classifiers. In most cases, Sensitive Information Types (SITs) are a mix of patterns and keywords. Templates such as Protected Health Information (PHI) and Personally Identifiable Information (PII) can return many false positives as they can't determine context or can be false positives for your organization.

Microsoft Purview administrators can reduce false positives by:

- Increasing required confidence and threshold counts.
- Looking for multiple SITs with the AND operator instead of the OR operator.
- Cloning a SIT into a custom SIT and fine tuning the requirements.
- Using multiple regex expressions instead of a single but wide-ranging one.
- Forcing word matching.
- Using [trainable classifiers](../trainable-classifiers-learn-about), [exact data match (EDM)](../sit-learn-about-exact-data-match-based-sits), and [document fingerprinting](../sit-document-fingerprinting).

Trainable classifiers use machine learning to identify document patterns. Microsoft Purview provides several pretrained classifiers such as legal documents, strategic business documents, and financial information. You can also create and train custom classifiers from a SharePoint document library.

By using both SITs and trainable classifiers, you can narrow down your scope – for example, **contains credit cards** SITs and Financial information trainable classifier.

Exact data match and document fingerprinting aren't currently available to auto-labeling but should be considered in your overall Microsoft Purview Data Loss Prevention (DLP) strategy. Similar to trainable classifiers, they can both help reduce false positives. By using EDM, you can, for example, find **contains SSN** out of the box SIT, and then verify against your EDM SIT to verify it's an SSN from one of your customers or employees. EDM allows you to securely store a hash of information to look for.

Document Fingerprinting operates differently than Trainable Classifiers by identifying document templates and using them in DLP policies. This method is most useful if your organization has standardized templates. You can use these templates to create precise fingerprinting.

## Automate and improve Microsoft 365 protection for historical and in-use data

In the final part of this step, review options to retroactively apply labels on your existing SharePoint sites and apply default library labels accordingly.

At this point, you configured defaults throughout the environment and stopped the proliferation of unlabeled sites and documents. You started addressing labeling sites and libraries manually on priority sites and you're looking at scaling this process throughout your complete Microsoft 365 content estate.

Consider a few strategies:

- Use site owners – Communicate to site owners that they must configure a label on their site and default library. If you intend to use the second option, include mentions that it automatically receives a new default at a target date.
- Run automation scripts on remaining unlabeled sites – Use the Graph API to identify unlabeled sites and configure the container label and default library label to "Confidential\All employees."
- Optionally, prevent sharing of unlabeled files only – By using previous measures such as DLP on unlabeled content and file auto-labeling, you can choose to let sites expire naturally over scripting retroactive actions for all sites.
- Capture a timeline of unlabeled sites – If you're planning to use service-side auto-labeling for all your historical data based on container labels, capture when container labels are added and progressively add newly labeled sites in your auto-labeling policies.

Your *risk posture* defines how to best approach all strategies, or possibly use them progressively. While securing your data estate is important, it can be a complex task depending on its size. Start small and iterate often.

You can script sensitivity labels to SharePoint sites by using `Set-PnPTenantSite` and the `SensitivityLabel` parameter.

For the default library label, set the `DefaultSensitivityLabelForLibrary` parameter by using REST API on a library. [A sample is provided in this article](https://www.linkedin.com/pulse/default-label-document-library-sanjoyan-mustafi/?trackingId=posQqQ7LSfiBvvJYBjaWig%3D%3D).

## Summary

- [Automatically apply a sensitivity label in Microsoft 365](../apply-sensitivity-label-automatically)
- [Minimum versions for sensitivity labels in Microsoft 365 Apps](../sensitivity-labels-versions)
- [Manage sensitivity labels in Office apps](../sensitivity-labels-office-apps)
- [Automatically apply a sensitivity label in Microsoft 365](../apply-sensitivity-label-automatically)