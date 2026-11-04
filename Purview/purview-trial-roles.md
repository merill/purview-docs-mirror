---
layout: Conceptual
title: User roles for starting Microsoft 365 trials | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/purview-trial-roles
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
ms.date: 2026-04-28T00:00:00.0000000Z
audience: Admin
ms.topic: get-started
ms.service: purview
ms.subservice: purview-compliance-trials
ms.collection:
- purview-compliance
search.appverid:
- MOE150
- MET150
description: Learn which user roles are required in order to sign up for a trial of Microsoft 365 Purview and security products.
ms.custom: sfi-ga-nochange
locale: en-us
document_id: 61a337a6-81fa-d801-70b0-cd6bcb5135e8
document_version_independent_id: 61a337a6-81fa-d801-70b0-cd6bcb5135e8
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/purview-trial-roles.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: purview-trial-roles
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/purview-trial-roles.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
- https://authoring-docs-microsoft.poolparty.biz/devrel/1dd701e0-441f-4b0a-9806-aa47decc4e35
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
- https://authoring-docs-microsoft.poolparty.biz/devrel/0a2fc935-5977-4aa6-9f55-0be03bd2acb8
platformId: ddef7b97-4329-81c4-1a34-6c5188a1cc3a
---

# User roles for starting Microsoft 365 trials | Microsoft Learn

This article outlines the user roles required in order to enroll your organization in a Microsoft 365 trial.

## Who can start all trials

A user with one of the roles listed below can start any Microsoft 365 trial.

| Role | Role Group | Where to assign |
| --- | --- | --- |
| Global Administrator | Global Administrator | Microsoft Purview portal &gt; Settings &gt; Roles and scopes |
| Billing Administrator | Billing Administrator | Microsoft Purview portal &gt; Settings &gt; Roles and scopes |

Get detailed instructions on [adding users to a Microsoft Purview role group](purview-permissions#add-users-or-groups-to-a-microsoft-purview-built-in-role-group).

Important

Microsoft recommends that you use roles with the fewest permissions. Minimizing the number of users with the Global Administrator role helps improve security for your organization. Learn more about Microsoft Purview [roles and permissions](purview-permissions).

## Roles for starting specific trials

The Microsoft Purview and Defender trials allow users with specific roles aside from Global Administrator and Billing Administrator to start their trials. Refer to the tables below for details.

#### Microsoft Purview trials

Microsoft Purview trials include the **Microsoft Purview Suite** trial and the **Compliance Manager premium assessments** trial.

| Role | Role Group | Where to assign |
| --- | --- | --- |
| Compliance Administrator | Compliance Administrator | Microsoft Purview portal &gt; Settings &gt; Roles and scopes |
| DLP Compliance Management, Information Protection Admin, RecordManagement, Retention Management, and Sensitivity Label Administrator | Compliance Data Administrator | Microsoft Purview portal &gt; Settings &gt; Roles and scopes |

#### Security trials

Security trials include the **Defender Vulnerability Management** trial and the **Defender Vulnerability Management add-on** trial. Users will need a role with one of the permissions listed below in order to start a trial.

| Permission | Where to assign |
| --- | --- |
| Security operations | Microsoft Defender portal &gt; Permissions &gt; Endpoints roles & groups &gt; Roles |
| Threat and vulnerability management | Microsoft Defender portal &gt; Permissions &gt; Endpoints roles & groups &gt; Roles |

## How to assign roles

For more information about how to assign user roles and permissions, see the following articles:

- **Microsoft Purview**: [Permissions in the Microsoft Purview portal](purview-permissions)
- **Microsoft Defender XDR**: [Create and manage roles for role-based access control](/en-us/microsoft-365/security/defender-endpoint/user-roles)