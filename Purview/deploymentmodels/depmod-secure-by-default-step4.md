---
layout: Conceptual
title: 'Step 4: Operate, expand, and retroactive actions - Secure by default with Microsoft Purview | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-secure-by-default-step4
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Securing by default - Step 4 - Operate, expand, and retroactive actions.
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
document_id: 3f6c4939-952e-0478-a80c-48ac9f174bf0
document_version_independent_id: 3f6c4939-952e-0478-a80c-48ac9f174bf0
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-secure-by-default-step4.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-secure-by-default-step4
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-secure-by-default-step4.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/1dd701e0-441f-4b0a-9806-aa47decc4e35
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/0a2fc935-5977-4aa6-9f55-0be03bd2acb8
platformId: 5783cc15-bff1-b538-e8ef-118602e54350
---

# Step 4: Operate, expand, and retroactive actions - Secure by default with Microsoft Purview | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-secure-by-default-intro)
- [Step 1: Start with default labeling](depmod-secure-by-default-step1)
- [Step 2: Address files with the highest sensitivity](depmod-secure-by-default-step2)
- [Step 3: Expand protection to your entire Microsoft 365 data estate](depmod-secure-by-default-step3)
- Step 4: Operate, expand, and retroactive actions (this article)

![Secure by default with Microsoft Purview - Blueprint](../media/depmod-securebydefault-blueprintimage1.png)

In this final step, you implement operational procedures and expand protection beyond Microsoft 365.

## Operational review of user labeling behaviors

File labeling is an integral part of this blueprint. Administrators should review risky behaviors and configurations that deviate from the standards.

Review these core operational scenarios:

- **Unlabeled Sites/Teams**: Use Graph API to identify sites and contact site owners or apply corrective measures.
- **Mismatch between site label and default library label**: Use Graph API to identify discrepancy and contact site owners or apply corrective measures.
- **Leverage Data Loss Prevention (DLP) on SIT and unrestricted labels**: Catch exceptions by using DLP when content is labeled without protection and sharing is attempted.
- **Look for risky users with Insider Risk Management audit**: Review risky users and behaviors, fine tune Insider Risk Management policies, and implement stricter Adaptive Protection.

## Iterate with new labeling scenarios

This deployment model focuses on labeling scenarios that fit most organizations. You can quickly deploy it and secure your data estate rapidly without the need for identifying all edge cases.

In this section, consider potential iterations your organization should consider after a core deployment.

### Secure collaboration with trusted partners or multitenanted organizations

In situations where your organization has multiple tenants or works openly with a trusted partner, consider using labels with encryption that support multiple domains such as `@contoso.com + @adventureworks.com`.

These labels are either or both Confidential and Highly confidential.

### Tented projects

Tented projects are highly confidential. For example, merger and acquisition projects, where access to the content must be restricted to a specific group of users.

You can create a label with encryption for a security group and publish it only to the same individuals. When this project isn't required, you can unpublish the label. The information remains protected, but no new labeling is done with this label.

### Full-time employees, vendors, offshore, or country/region teams

Some organizations need to identify and protect a segment of users such as:

- Full-time employees (FTE)
- Vendors
- Offshore
- Country/region

In this guide, the labeling simplifies to "All Employees" but there might be a need to secure labeling differently in some cases between FTE and vendors or partners, and sometimes for specific a country/region.

As with the previous scenario, limit the number of labels visible to users to no more than five group labels, each with no more than five labels (5x5) whenever possible. In the context of country/region labeling, target publishing to the appropriate users and use containers to file labeling to simplify defaulting to the most appropriate label.

### Labeling on-premises file shares and SharePoint server

You can use sensitivity labels with your on-premises file shares and SharePoint server by using the Information Protection scanner. As this guide focuses on securing by default, configure the right defaults in SharePoint, migrate your content to SharePoint, and automatically label the content as it's uploaded.

Note

For remaining on-premises scenarios, see [Learn about the Microsoft Purview Information Protection scanner](../deploy-scanner).

### Bring Your Own Key (BYOK) and Double Key Encryption (DKE)

Both BYOK and DKE are options to meet regulatory requirements, and they're outside of the scope of this guide. BYOK is about ownership and how the rolling of encryption keys function, while DKE is intended for a small fraction of highly sensitive content that requires more security. DKE affects several collaborative capabilities.

To learn more about BYOK, see [Service encryption and key management - Microsoft Purview](../microsoft-365-service-encryption).

To learn more about DKE, see [Double Key Encryption (DKE)](../double-key-encryption).

### Set up accountability chain and lifecycle management

Empowering collaboration with SharePoint comes with responsibilities for site owners. Implement a chain of accountability and lifecycle management by following these recommendations:

- **Two or more site owners on all sites**: Use site ownership policies to identify sites without at least two owners and contact current owners or members to resolve.
- **Inactive site**: Use inactive site policies to remove unused sites.
- **Site attestation**: Require site owners to attest sites regularly.
- **Review content shared with "everyone except external users"**: Use SharePoint Advanced Management reporting to identify content shared with everyone except guests, and contact site owners.
- **Site access reviews**: Use SharePoint Advanced Management, review site data governance, and initiate site access review, particularly for sites with high volume of sharing or access.

## Extend protection to Azure SQL and non-Microsoft 365 storage

Sensitivity Labels can now extend protection to non-Microsoft 365 data sources. Microsoft currently supports the following data sources in public preview:

- Azure SQL Database
- Azure Blob Storage
- Azure Data Lake Storage Gen2
- Amazon S3 buckets

Microsoft Purview is a combination of what was formerly known as Azure Purview and Microsoft Purview. This experience is now all under the new Microsoft Purview portal, generally available as of July 2024. It allows data security administrators to set up labeling, auto labeling, and protection policies across both Microsoft 365 and non-Microsoft 365.

For protection policies for non-Microsoft 365 data assets, you can set up oversharing protection with "deny all except" permissions at the data level. For example, if storage accounts are inadvertently used for more sensitive content than intended, protection policies can ensure that permissions are restricted to data security admins.

Similarly, for Azure SQL Database, protection policies restrict access to a column if sensitive content is found and the column labeled. Granular configurations are available to set up who can retain access for each data asset.

## Summary

- [Initiate site access reviews for data access governance reports - SharePoint in Microsoft 365](/en-us/sharepoint/site-access-review)
- [Review activities with the insider risk management audit log](../insider-risk-management-audit-log)
- [Best practices for managing your alert volume in insider risk management](../insider-risk-management-best-practices-alert-tuning)
- [Manage site lifecycle policies - SharePoint in Microsoft 365](/en-us/sharepoint/site-lifecycle-management)
- [Initiate site access reviews for data access governance reports - SharePoint in Microsoft 365](/en-us/sharepoint/site-access-review)