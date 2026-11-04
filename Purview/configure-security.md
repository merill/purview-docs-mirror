---
layout: Conceptual
title: Configure Microsoft Purview for increased security | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/configure-security
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Learn how to improve your data security posture with Microsoft Purview.
ms.service: purview
ms.topic: concept-article
ms.date: 2026-05-07T00:00:00.0000000Z
ai-usage: ai-assisted
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
locale: en-us
document_id: f355d0dd-472b-accc-46ce-0f875530f466
document_version_independent_id: f355d0dd-472b-accc-46ce-0f875530f466
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/configure-security.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configure-security
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/configure-security.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
platformId: cd7b4f40-768f-fc9f-c7dd-93f8900e2d26
---

# Configure Microsoft Purview for increased security | Microsoft Learn

In Microsoft Purview, we group our security recommendations into multiple themes based on the Secure Future Initiative (SFI). This structure allows organizations to logically break up projects into related consumable chunks.

Tip

Some organizations might take these recommendations exactly as written, while others might choose to make modifications based on their own business needs.

We recommend that all of the following controls be implemented where licenses are available. These patterns and practices help to provide a foundation for other resources built on top of this solution. More controls will be added to this document over time.

## Automated assessment

Manually checking this guidance against a tenant's configuration can be time-consuming and error-prone. The Zero Trust Assessment transforms this process with automation to test for these security configuration items and more. Learn more in [What is the Zero Trust Assessment?](/en-us/security/zero-trust/assessment/overview)

## Licensing and billing requirements

Several Microsoft 365 subscriptions support the capabilities covered by this assessment. To identify the licenses required, see the [Microsoft Purview service description](/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description).

Some Microsoft Purview capabilities also require [pay-as-you-go billing](purview-billing-models)—for example, when the configuration includes non–Microsoft 365 data sources, AI hub locations, or retention scopes that cover some Copilots or other AI apps.

## Protect data

Reduce risk by ensuring encryption and collaboration settings are correctly configured for your organization's data.

| Check |
| --- |
| [Azure Rights Management service is activated](zero-trust-purview-protect-data#azure-rights-management-service-is-activated) |
| [Super user membership is configured for Microsoft Purview Information Protection](zero-trust-purview-protect-data#super-user-membership-is-configured-for-microsoft-purview-information-protection) |
| [On-demand scans are configured for sensitive information discovery](zero-trust-purview-protect-data#on-demand-scans-are-configured-for-sensitive-information-discovery) |
| [OCR is enabled for sensitive information detection](zero-trust-purview-protect-data#ocr-is-enabled-for-sensitive-information-detection) |
| [Custom sensitive information types are configured](zero-trust-purview-protect-data#custom-sensitive-information-types-are-configured) |
| [Exact data match is configured for sensitive information detection](zero-trust-purview-protect-data#exact-data-match-is-configured-for-sensitive-information-detection) |
| [Named entity sensitive information types are used in auto-labeling and data loss prevention policies](zero-trust-purview-protect-data#named-entity-sensitive-information-types-are-used-in-auto-labeling-and-data-loss-prevention-policies) |
| [Trainable classifiers are used in data loss prevention and auto-labeling policies](zero-trust-purview-protect-data#trainable-classifiers-are-used-in-data-loss-prevention-and-auto-labeling-policies) |
| [Purview audit logging is enabled](zero-trust-purview-protect-data#purview-audit-logging-is-enabled) |
| [Sensitivity labels are configured](zero-trust-purview-protect-data#sensitivity-labels-are-configured) |
| [Globally published sensitivity labels don't exceed the recommended maximum](zero-trust-purview-protect-data#globally-published-sensitivity-labels-dont-exceed-the-recommended-maximum) |
| [Sensitivity labels with encryption are configured](zero-trust-purview-protect-data#sensitivity-labels-with-encryption-are-configured) |
| [Double Key Encryption labels are configured](zero-trust-purview-protect-data#double-key-encryption-labels-are-configured) |
| [Co-authoring is enabled for encrypted documents](zero-trust-purview-protect-data#co-authoring-is-enabled-for-encrypted-documents) |
| [Container labels are configured for collaborative workspaces](zero-trust-purview-protect-data#container-labels-are-configured-for-collaborative-workspaces) |
| [Sensitivity labels are enabled in SharePoint](zero-trust-purview-protect-data#sensitivity-labels-are-enabled-in-sharepoint) |
| [PDF labeling is enabled in SharePoint](zero-trust-purview-protect-data#pdf-labeling-is-enabled-in-sharepoint) |
| [Sensitivity label policies are published to users](zero-trust-purview-protect-data#sensitivity-label-policies-are-published-to-users) |
| [A default sensitivity label is configured in label policies](zero-trust-purview-protect-data#a-default-sensitivity-label-is-configured-in-label-policies) |
| [Mandatory labeling is enabled in sensitivity label policies](zero-trust-purview-protect-data#mandatory-labeling-is-enabled-in-sensitivity-label-policies) |
| [Users must provide justification to downgrade sensitivity labels](zero-trust-purview-protect-data#users-must-provide-justification-to-downgrade-sensitivity-labels) |
| [Email label policies inherit sensitivity from attachments](zero-trust-purview-protect-data#email-label-policies-inherit-sensitivity-from-attachments) |
| [Default sensitivity labels are configured for SharePoint document libraries](zero-trust-purview-protect-data#default-sensitivity-labels-are-configured-for-sharepoint-document-libraries) |
| [Auto-labeling policies are configured for all workloads](zero-trust-purview-protect-data#auto-labeling-policies-are-configured-for-all-workloads) |
| [Auto-labeling policies are in enforcement mode](zero-trust-purview-protect-data#auto-labeling-policies-are-in-enforcement-mode) |
| [Auto-labeling policies are enabled for SharePoint and OneDrive](zero-trust-purview-protect-data#auto-labeling-policies-are-enabled-for-sharepoint-and-onedrive) |
| [Microsoft Purview Message Encryption is configured with simplified client access](zero-trust-purview-protect-data#microsoft-purview-message-encryption-is-configured-with-simplified-client-access) |
| [Custom branding templates are configured for Microsoft Purview Message Encryption](zero-trust-purview-protect-data#custom-branding-templates-are-configured-for-microsoft-purview-message-encryption) |
| [Email retention policies are configured](zero-trust-purview-protect-data#email-retention-policies-are-configured) |
| [Data loss prevention policies are enabled](zero-trust-purview-protect-data#data-loss-prevention-policies-are-enabled) |
| [Endpoint data loss prevention policies are configured](zero-trust-purview-protect-data#endpoint-data-loss-prevention-policies-are-configured) |
| [Adaptive Protection is enabled in data loss prevention policies](zero-trust-purview-protect-data#adaptive-protection-is-enabled-in-data-loss-prevention-policies) |
| [Browser data loss prevention is enabled for AI apps via Edge for Business](zero-trust-purview-protect-data#browser-data-loss-prevention-is-enabled-for-ai-apps-via-edge-for-business) |
| [Insider Risk Management policies are enabled for risky AI usage](zero-trust-purview-protect-data#insider-risk-management-policies-are-enabled-for-risky-ai-usage) |
| [Communication compliance monitoring is configured for Microsoft Copilot](zero-trust-purview-protect-data#communication-compliance-monitoring-is-configured-for-microsoft-copilot) |
| [Communication compliance monitoring is configured for enterprise AI tools](zero-trust-purview-protect-data#communication-compliance-monitoring-is-configured-for-enterprise-ai-tools) |