---
layout: Conceptual
title: Introduction to secure by default with Microsoft Purview | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-secure-by-default-intro
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Secure by default by deriving labels from SharePoint sites, your organization can quickly reduce the risk associated with unintentional and intentional oversharing. Training users on how to manage exceptions instead of when to protect helps the adoption velocity.
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
document_id: 5cf1e467-cfe4-97fd-cb19-2f8325b13a25
document_version_independent_id: 5cf1e467-cfe4-97fd-cb19-2f8325b13a25
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-secure-by-default-intro.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-secure-by-default-intro
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-secure-by-default-intro.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/9d7be3ef-f27c-4c7f-9eba-67c3cd429995
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/feeb50f3-b677-44f9-b3a6-5f2f58182b0d
platformId: 27e79878-e82f-3c19-df3e-c715a7853577
---

# Introduction to secure by default with Microsoft Purview | Microsoft Learn

Microsoft Purview sensitivity labeling provides an efficient and robust capability to protect data. This protection is centered around encrypting your data and preventing oversharing. Use labels as conditions in other solutions such as Microsoft Purview Data Loss Prevention (DLP) and Microsoft Purview Insider Risk Management.

The traditional 'crawl-walk-run' approach is often challenging or slow to adopt due to:

- Defining the label taxonomy
- Concerns about encryption affecting users and line of business applications
- Limited adoption through manual labeling and/or only using auto-labeling to label

This guide provides an alternative deployment model focused on labeling at scale based on your protection strategy. You learn how to:

- Configure secure by default sensitivity labeling.
- Use label publishing defaults and auto-labeling in the Office client.
- Use contextual defaults in SharePoint sites to rapidly achieve deployment velocity.

When you derive Microsoft Teams and SharePoint site labeling to file labels, you can reach high labeling volumes with limited user interactions. This approach achieves a measured approach that helps overcome traditional challenges.

Tip

By securing by default by deriving labels from SharePoint sites, your organization can quickly reduce the risk associated with unintentional and intentional oversharing. Training users on how to manage exceptions, instead of when to protect, helps accelerate adoption velocity.

## About this guide

This guide includes the following articles:

- Introduction (this article)
- [Step 1: Start with default labeling](depmod-secure-by-default-step1)
- [Step 2: Address files with the highest sensitivity](depmod-secure-by-default-step2)
- [Step 3: Expand protection to your entire Microsoft 365 data estate](depmod-secure-by-default-step3)
- [Step 4: Operate, expand, and retroactive actions](depmod-secure-by-default-step4)

These articles cover:

- A focus on the required solutions to only meet the goal of a model’s scenario.
- The starting point for your deployment, recommended by the engineering team.
- High level activities and deployment tips to help you plan an implementation.
- A solid foundation to grow on and augment with more scenarios.

These articles don't cover:

- A complete project plan
- A deep dive technical reference (however, this guide contains links to several articles on Microsoft Learn for additional information)
- Comprehensive guides for all solutions in Microsoft Purview

## Before you begin

This guide is for administrators with knowledge of Microsoft Purview Information Protection, DLP, and Insider Risk Management. If you're new to Microsoft Purview, refer to these articles to learn more:

- [Learn about sensitivity labels](../sensitivity-labels)
- [Learn about data loss prevention](../dlp-learn-about-dlp)
- [Learn about insider risk management](../insider-risk-management)

## Licensing and subscriptions

See the Microsoft 365 guidance for security and compliance for details on the subscriptions that support the features you're deploying from this guide:

- Sensitivity Labels (auto-labeling and default library labeling in SharePoint)
- Data Loss Prevention
- Insider Risk Management (adaptive protection)

For information on licensing, see [Microsoft 365, Office 365, Enterprise Mobility + Security, and Windows 11 Subscriptions for Enterprises](https://aka.ms/M365EnterprisePlans).

## Simplify your deployment strategy with the following actions

As the strategy name implies, its purpose is to secure your information by default and start training users on when to remove protection.

1. Secure by default and protect information to **All employees** (and users within your identity ecosystem).
2. Derive file labels from site (container) labels to quickly reach scale.
3. Train users to update labels for sharing exceptions (instead of when to protect).
4. Use auto-labeling for higher sensitivity recommendations and more restriction.
5. Accelerate Data Loss Prevention deployment to restrict sharing of labeled content.
6. Use Insider Risk Management to identify suspicious user labeling and sharing behaviors (intentional and unintentional).

You're in control of the protections you apply by default. For example:

- DLP policy on content with default label
- Encryption of content with default label
- Select which workload has what default label

With these options, you're empowered to start smaller, train users, and iterate through deployment milestones. An example of a measured list of deployment milestones:

1. SharePoint default label set to **Confidential\All employees** without encryption but prevented from sharing externally by DLP. Other workloads set to General by default.
2. Elevate default label to all files (client default), set email to inherit from document labels.
3. Add encryption to **Confidential\All employees**.

## Why labeling matters in protecting your content

- **Protection travels with your document**: Easy-to-use encryption for all users
- **Simple, integrated, and consistent**: Built-in Office, Acrobat Reader, Teams, Power BI, Defender for Cloud Apps, and more
- **Copilot**: End-to-end protection of sensitive information with Copilot interactions
- **Protection beyond Microsoft 365**: Protect data assets in Azure, Amazon Web Services (AWS), and more

## Microsoft Purview deployment blueprint

The blueprint provides:

- a recommended label taxonomy to get your organization started
- options for users to manage exceptions, if encryption prevents them from working effectively
- help to enable your organization to augment its data security rapidly

Review and adapt this blueprint based on your existing deployment, data security objectives, and experience. To help you deploy in stages, the blueprint offers more options. You're in complete control of your deployment experience.

Note

This blueprint closely aligns with Microsoft's internal strategy. To learn more about Microsoft labeling deployment, see [How we’re using sensitivity labels to make Microsoft more secure](https://www.microsoft.com/insidetrack/blog/empowering-employee-self-service-with-guardrails-how-were-using-sensitivity-labels-to-make-microsoft-more-secure/).

![Secure by default with Microsoft Purview - Blueprint](../media/depmod-securebydefault-blueprintimage1.png)