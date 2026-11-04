---
layout: Conceptual
title: 'Step 1: Establish foundational elements - Deploy and use Data Security Posture Management | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-dspm-step1
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Identify sensitive information types, configure labeling, define an Insider Risk Management program, and enable Microsoft Security Copilot for DSPM.
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
document_id: d4effffb-20b1-7023-6472-8f47e07ddf20
document_version_independent_id: d4effffb-20b1-7023-6472-8f47e07ddf20
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-dspm-step1.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-dspm-step1
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-dspm-step1.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/03921bea-3752-4ddc-98c2-5aa70db91565
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/09911d3e-3eb9-4c8d-ab86-ce80d8d36bbd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
platformId: f8dabd17-13be-225e-ed65-bbc8acb15161
---

# Step 1: Establish foundational elements - Deploy and use Data Security Posture Management | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-dspm-intro)
- Step 1: Establish foundational elements (this article)
- [Step 2: Configure access and analytics](depmod-dspm-step2)
- [Step 3: Understand data landscape and risks](depmod-dspm-step3)
- [Step 4: Take action and investigate with Security Copilot](depmod-dspm-step4)

![Deploy and use Microsoft Purview Data Security Posture Management (DSPM) deployment blueprint.](media/dspmdiagram.png)

Before configuring Microsoft Purview Data Security Posture Management (DSPM), you need foundational elements in place. These elements ensure that when you review recommendations and perform analysis, DSPM has the context it needs to provide actionable insights.

## Identify built-in and custom sensitive information types

Identify the built-in and custom sensitive information types (SITs) that are relevant to your organization. This step ensures that when you review DSPM recommendations and perform analysis, you're aware of what needs to be prioritized.

Built-in SITs are a good starting point for organizational requirements and can be improved after investigation. If the built-in SITs don't fully address your organization's needs, [create custom SITs](../sit-create-a-custom-sensitive-information-type) to detect data unique to your business, such as internal project codes, employee IDs, or proprietary information.

To learn more, see [Learn about sensitive information types](../sit-sensitive-information-type-learn-about).

## Configure a labeling schema

Configure a [sensitivity labeling](../sensitivity-labels) schema for your organization. While labeling isn't required for DSPM, it's extremely helpful for identifying how files should be handled and for setting up Data Loss Prevention (DLP) policies later. A configured labeling schema also helps improve DSPM recommendations and provides better insights in DSPM reports.

Tip

If you haven't deployed sensitivity labels yet, see the [Secure by default with Microsoft Purview](depmod-secure-by-default-intro) deployment model for a recommended approach to labeling at scale.

To learn more, see [Learn about sensitivity labels](../sensitivity-labels).

## Define an Insider Risk Management program

Define your organization's Insider Risk Management program. Insider Risk Management enables organizations to proactively address insider threats and ensures compliance with regulations. When combined with DLP and Adaptive Protection, DSPM provides a stronger data security landscape.

With an Insider Risk Management program defined, DSPM can surface insights about potentially risky users and their activities, providing recommendations for Insider Risk Management policies alongside DLP recommendations.

To learn more, see [Learn about insider risk management](../insider-risk-management) and [Get started with insider risk management](../insider-risk-management-configure).

## Enable Microsoft Security Copilot (optional)

Enable Microsoft Security Copilot to unlock advanced investigation capabilities within DSPM. Security Copilot is optional but enables:

- Custom investigations using natural language prompts
- DSPM Promptbooks for guided investigation workflows
- AI-powered analysis to understand the role of AI in making investigations more efficient

Note

If you enable Security Copilot, you need the Data Security Viewer role to use Security Copilot within DSPM.

To learn more, see [Data Security Posture Management with Security Copilot](../data-security-posture-management-copilot).

## Summary

At the end of this step, your organization has:

- Identified built-in and custom SITs for your organization's data classification needs.
- Configured a labeling schema to improve DSPM recommendations and insights.
- Defined an Insider Risk Management program to enable risk-based insights.
- Enabled Security Copilot (optional) for advanced investigation capabilities.