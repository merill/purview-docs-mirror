---
layout: Conceptual
title: 'Step 1: Discover risks and identify gaps - Secure and govern Microsoft 365 Copilot agents | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-sc-agents-step1
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Discover oversharing risks, sensitive info in Dataverse, and risky AI activities by using Microsoft Purview Audit, DSPM, and Compliance Manager.
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
document_id: fe8ddbd2-4c96-7379-5a0a-d924320d00e6
document_version_independent_id: fe8ddbd2-4c96-7379-5a0a-d924320d00e6
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-sc-agents-step1.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-sc-agents-step1
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-sc-agents-step1.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/0ceb3227-2ff7-4d97-8e75-3d7b9ccc937a
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4d680e1a-c470-4772-a236-5c714bd09be0
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
platformId: c2064399-aae6-237e-f794-e0e67fbdc65d
---

# Step 1: Discover risks and identify gaps - Secure and govern Microsoft 365 Copilot agents | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-sc-agents-deployment)
- Step 1: Discover risks and identify gaps (this article)
- [Step 2: Protect sensitive info in grounding data](depmod-sc-agents-step2)
- [Step 3: Protect interactions](depmod-sc-agents-step3)
- [Step 4: Govern interactions](depmod-sc-agents-step4)

![Secure and govern Microsoft 365 Copilot agents deployment blueprint.](media/depmod-sc-agents-deployment/screenshot-2025-08-26-130022.png)

Before securing and governing Microsoft 365 Copilot agents, first understand your current risk posture. This step focuses on turning on auditing, discovering oversharing risks, identifying where sensitive information resides, and understanding gaps in regulatory compliance.

## Turn on Microsoft Purview Audit

[Turn on Microsoft Purview Audit](../audit-log-enable-disable) to log all activity related to grounding data and AI app and agent interactions. Audit logs provide the foundation for visibility into how agents access and use organizational data.

1. [Verify that auditing is enabled](../audit-log-enable-disable). If it's not, select **Start recording user and admin activity**.
2. Wait up to 60 minutes for auditing to activate.

Note

Audit logging is typically enabled by default. Confirming it's active ensures no gap in visibility into agent interactions.

To learn more, see [Get started with auditing solutions](../audit-get-started).

## Discover oversharing risks with Microsoft Purview data risk assessments

Discover potential oversharing in SharePoint and OneDrive with Microsoft Purview data risk assessments. Data risk assessments help you identify content that might be overshared and accessible to Microsoft 365 Copilot agents, so you can take corrective action before deploying agents broadly.

To learn more, see [Data Security Posture Management (DSPM) for AI](../dspm-for-ai).

## Discover sensitive info in Microsoft Dataverse with Unified Catalog

Use Microsoft Purview Data Governance's Unified Catalog to discover where sensitive information resides in Microsoft Dataverse. Since agents can use Dataverse as a knowledge source, understanding what sensitive data exists in Dataverse is critical to preventing unintended data exposure through agent responses.

To learn more, see [Connect to and manage Microsoft Dataverse in Microsoft Purview](../register-scan-dataverse).

## Discover risky AI activities with Microsoft Purview DSPM for AI

Use Microsoft Purview Data Security Posture Management (DSPM) for AI's Apps and Agents report to discover risky AI activities across your organization. This report provides visibility into how AI apps and agents are used, including potentially risky interactions.

To learn more, see [Data Security Posture Management (DSPM) for AI](../dspm-for-ai).

## Identify and address gaps in meeting AI regulations with Microsoft Purview Compliance Manager

Use Microsoft Purview Compliance Manager to identify and address gaps in meeting AI regulations. Compliance Manager provides assessments and recommended improvement actions to help your organization meet regulatory requirements related to AI governance.

To learn more, see [Microsoft Purview Compliance Manager](../compliance-manager).

## Summary

At the end of this step, your organization has:

- Enabled audit logging to capture all agent interactions with grounding data.
- Gained visibility into oversharing risks in SharePoint and OneDrive through data risk assessments.
- Developed an understanding of where sensitive information resides in Microsoft Dataverse.
- Obtained insight into risky AI activities through DSPM for AI reports.
- Identified gaps in AI regulatory compliance through Compliance Manager.