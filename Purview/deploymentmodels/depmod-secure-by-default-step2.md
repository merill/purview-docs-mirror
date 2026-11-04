---
layout: Conceptual
title: 'Step 2: Address files with the highest sensitivity - Secure by default with Microsoft Purview | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-secure-by-default-step2
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Securing by default - Step 2 - Address files with the highest sensitivity.
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
document_id: ca93471c-8ec2-b8b3-bbc7-bc0a8897e235
document_version_independent_id: ca93471c-8ec2-b8b3-bbc7-bc0a8897e235
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-secure-by-default-step2.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-secure-by-default-step2
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-secure-by-default-step2.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/9d7be3ef-f27c-4c7f-9eba-67c3cd429995
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/feeb50f3-b677-44f9-b3a6-5f2f58182b0d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: e02dab2a-3c57-c7f9-2948-e73a43c27ecc
---

# Step 2: Address files with the highest sensitivity - Secure by default with Microsoft Purview | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-secure-by-default-intro)
- [Step 1: Start with default labeling](depmod-secure-by-default-step1)
- Step 2: Address files with the highest sensitivity (this article)
- [Step 3: Expand protection to your entire Microsoft 365 data estate](depmod-secure-by-default-step3)
- [Step 4: Operate, expand, and retroactive actions](depmod-secure-by-default-step4)

![Secure by default with Microsoft Purview - Blueprint](../media/depmod-securebydefault-blueprintimage1.png)

In the first step, you learned how to secure new and updated content. In this step, you explore how to secure your existing data, starting with the most sensitive data.

Identify your priority sites from:

- Well known sites, including sites from leadership teams
- Content Explorer with high number of sensitive documents
- Reporting
- Graph API for sites with high quantity of sensitive information

Note

If you opt to default files to **Confidential\All employees**, focus on sites with a higher priority label.

## Manually configure priority sites default library labeling

Currently, configuration requires two separate steps:

1. Add a sensitivity label to the SharePoint site.
2. Define a sensitivity label as the default for files in SharePoint libraries.

Site owners can configure sensitivity labels on SharePoint sites and the default library label in libraries. SharePoint administrators can configure the site sensitivity label in the SharePoint administrator portal. Later in this article, you learn how to configure sensitivity labeling on sites and libraries by using PowerShell.

## Auto-labeling for credentials and contextual conditions

Microsoft Purview provides both client-side and service-side auto-labeling.

Client-side auto-labeling provides user awareness and decision-making flexibility. When securing by default, client-side labeling is most useful for recommending higher sensitivity labeling for recipients with lower thresholds of sensitive information. Users can then decide to accept or not accept the recommendation, and report it if the label suggestion isn't appropriate.

Service-side labels apply to existing files in OneDrive and SharePoint, and in transport for emails. They provide more conditions, such as contextual conditions for:

- File type
- File size
- Document properties

In the context of the secure by default guide, secure first by site context, instead of only by sensitive information type. Therefore, you can use contextual conditions such as **Set label to Confidential\All Employees** on all Office/.pdf file extensions for these sites and quickly address existing priority sites. Step 3 covers more options at scale.

Important

Configure auto-labeling policies on **All credentials** to sensitive information because adversaries most value this information. For client-side auto-labeling, set the label to **Highly Confidential\Specific People**. For service-side auto-labeling, set the label to **Highly Confidential\All employees**.

## Turn on Data Loss Prevention for content that isn't labeled

At this stage, the foundation is well in place, defaults are secure, and you started addressing existing data. Enabling Data Loss Prevention (DLP) rules for unlabeled content (use the **Content is not labeled** condition) on Endpoint and Exchange accelerates the labeling of content by users and prevents the sharing of unlabeled content.

Turn on this DLP rule condition for Endpoint DLP with Office/PDF file types, and for relevant restrictive actions such as upload to cloud. Users must open and label their files before uploading files on websites.

## Turn on Adaptive protection and data leak behavioral rules

Insider Risk Management provides a layer of analytics and control, based on user behaviors. In the secure by default context using sensitivity labels, Insider Risk Management can identify and alert when users are downgrading labels or downloading, obfuscating, and exfiltrating that content.

Administrators are in control of the triggers and thresholds. In addition, you can now use Adaptive Protection to strengthen your DLP rules based on the user’s risk. For example, a DLP rule can audit by default when sharing files with the label **General**. A user identified as high risk can be prevented from sharing the same file.

Tip

Turn on and test a default policy with Adaptive Protection and iterate where applicable in your existing DLP rules.

Insider Risk Management provides many more capabilities, configurations, and controls. Review the following references and future Microsoft Purview deployment models that cover Insider Risk Management in more detail.

## Summary

- [Use sensitivity labels with Microsoft Teams, Groups, and SharePoint sites](../sensitivity-labels-teams-groups-sites)
- [Add a sensitivity label to SharePoint document library](https://support.microsoft.com/en-us/office/add-a-sensitivity-label-to-sharepoint-document-library-54b1602b-db0a-4bcb-b9ac-5e20cbc28089)
- [Configure a default sensitivity label for a SharePoint document library](../sensitivity-labels-sharepoint-default-label)
- [Automatically apply a sensitivity label in Microsoft 365](../apply-sensitivity-label-automatically)