---
layout: Conceptual
title: Microsoft Security Copilot agents in Microsoft Purview (preview) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/copilot-in-purview-agents
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Learn about Security Copilot agents in Microsoft Purview
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 2026-02-24T00:00:00.0000000Z
ms.update-cycle: 180-days
ms.topic: overview
ms.service: security-copilot
ms.collection:
- security-copilot
- magic-ai-copilot
- essentials-get-started
search.appverid: MET150
f1.keywords: NOCSH
audience: ITPro
locale: en-us
document_id: 27318cd4-9a92-a4d7-92c0-24e85c95a1ab
document_version_independent_id: 27318cd4-9a92-a4d7-92c0-24e85c95a1ab
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/copilot-in-purview-agents.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: copilot-in-purview-agents
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/copilot-in-purview-agents.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/03921bea-3752-4ddc-98c2-5aa70db91565
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/09911d3e-3eb9-4c8d-ab86-ce80d8d36bbd
platformId: 9c202164-394c-bec0-2068-3cbb8a69a44d
---

# Microsoft Security Copilot agents in Microsoft Purview (preview) | Microsoft Learn

In preview, [Microsoft Security Copilot agents](copilot-in-purview-agents-overview) are available in Microsoft Purview to help triage [Microsoft Purview Data Loss Prevention (DLP)](/en-us/purview/dlp-learn-about-dlp) and [Microsoft Purview Insider Risk Management](insider-risk-management) alerts. These Microsoft Purview agents are AI-powered assistants that can help you triage alerts by working seamlessly with Microsoft security products.

## Available agents

### Triage Agent in Insider Risk Management

The Triage Agent in Insider Risk Management helps security teams by evaluating alerts based on user risk, file risk, and activity risk. The agent then sorts the triaged alerts into [four categories](copilot-in-purview-agents-overview#triaged-alerts). These categories are presented in the insider risk management solution on the **Alerts** tab.

| Attribute | Description |
| --- | --- |
| Identity | Runs as the administrator who turned on the agent. Agent authentication expires after 90 days and must be renewed. |
| License | Both the standard per seat licensing model and the pay-as-you-go billing model[Microsoft Purview Insider Risk Management with Microsoft 365 E3/E5/A5/F5/G5](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/modern-work-plan-comparison-enterprise.pdf). For information on Security Copilot licensing in E5 see, [Learn about Security Copilot in Microsoft 365 E5](/en-us/copilot/security/security-copilot-inclusion). |
| Permissions | Access policy configurations and settings in Insider Risk ManagementRead activities and events in Microsoft PurviewRead file content and metadata involved in Insider Risk Management alertsStore user feedback and apply feedback when evaluating Insider Risk Management alerts |
| Plugins | [Microsoft Purview](copilot-in-purview-agents-overview) |
| Products | [Security Copilot](/en-us/copilot/security/get-started-security-copilot)[Insider Risk Management](insider-risk-management-solution-overview) |
| Role-based access | **View activity**: Insider Risk Management Analysts, Insider Risk Management Investigators, or Insider Risk Management role group**Manage**: All roles needed to view activity, plus the Purview Content Analyst role in the Purview Agent Management role group |
| Trigger | Runs on a selected schedule or on one alert at a time |

### Alert Triage Agent in Data Loss Prevention (preview)

The Alert Triage Agent in Data Loss Prevention (DLP) helps security teams by evaluating alerts based on the sensitivity risk, exfiltration risk, and policy risk. The agent then sorts the triaged alerts into [four categories](copilot-in-purview-agents-overview#triaged-alerts). These categories are presented in the DLP solution on the **Alerts** page.

For devices, you must [set up evidence collection for file activities on devices](dlp-copy-matched-items-learn#learn-about-evidence-collection-for-file-activities-on-devices) and enable evidence collection in the DLP policy rule configuration.

| Attribute | Description |
| --- | --- |
| Identity | Runs as the administrator who turned on the agent. Agent authentication expires after 90 days and must be renewed. |
| License | Both the standard per seat licensing model and the pay-as-you-go billing model[Microsoft Purview Data Loss Prevention with Microsoft 365 E3/E5/A5/F5/G5](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/modern-work-plan-comparison-enterprise.pdf) |
| Permissions | Access policy configurations and settings in DLPRead activities and events in Microsoft PurviewRead file content and metadata involved in DLP alertsStore user feedback and apply feedback when evaluating DLP alertsRead file content and metadata involved in DLP alertsStore user feedback and apply feedback when evaluating DLP alerts |
| Plugins | [Microsoft Purview](copilot-in-purview-agents-overview) |
| Products | [Security Copilot](/en-us/copilot/security/get-started-security-copilot)[Data Loss Prevention](dlp-learn-about-dlp) |
| Role-based access | **View activity**: Insider Risk Management Analysts, Insider Risk Management Investigators, or Insider Risk Management role group**Manage**: All roles needed to view activity, plus must be assigned the Purview Content Analyst role in the Purview Agent Management role group |
| Trigger | Runs on a selected schedule or on one alert at a time |