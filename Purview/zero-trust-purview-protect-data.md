---
layout: Conceptual
title: Security guidance - Protect data | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/zero-trust-purview-protect-data
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Improve your security posture with the Microsoft Purview Zero Trust assessment to protect your organization's data.
ms.service: purview
ms.topic: concept-article
ms.date: 2026-03-31T00:00:00.0000000Z
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
locale: en-us
document_id: 7226a485-7e28-e4d9-1acb-ee6b10248858
document_version_independent_id: 7226a485-7e28-e4d9-1acb-ee6b10248858
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/zero-trust-purview-protect-data.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: zero-trust-purview-protect-data
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/zero-trust-purview-protect-data.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
- https://authoring-docs-microsoft.poolparty.biz/devrel/9d7be3ef-f27c-4c7f-9eba-67c3cd429995
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
- https://authoring-docs-microsoft.poolparty.biz/devrel/feeb50f3-b677-44f9-b3a6-5f2f58182b0d
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
platformId: c24183a6-d5bb-7853-9227-399cb713268a
---

# Security guidance - Protect data | Microsoft Learn

Protecting your organization's data means ensuring that encrypted content can flow securely to and from authorized users, both inside and outside your organization. Misconfigured settings can silently block legitimate collaboration on protected content, leaving users unable to open encrypted files or emails from external partners.

## Zero Trust security recommendations

### Azure Rights Management service is activated

The Azure Rights Management service provides the foundational encryption and access control technology for Microsoft Purview Information Protection. It's used with sensitivity labels that apply encryption, protects emails with Microsoft Purview Message Encryption, and even used with the older protection technologies such as SharePoint IRM and mail flow rules that apply encryption. This service should be activated for the tenant before you configure any other information protection features.

**Remediation action**

- [Activate the Azure Rights Management service](/en-us/purview/activate-rights-management-service)

### Super user membership is configured for Microsoft Purview Information Protection

The super user feature of the Azure Rights Management service grants designated accounts the ability to decrypt content your organization has encrypted by using this service, regardless of the original permissions assigned. Super users might be necessary for eDiscovery, data recovery, compliance investigations, and content migration. The super user feature ensures that authorized people and services can always read and inspect the data that the Azure Rights Management service encrypts for your organization.

When you use a group to designate super user accounts, membership of that group must be carefully controlled and limited, for example, to service accounts used by compliance tools or eDiscovery platforms. Unless you have a feature or business need that requires the feature to be enabled all the time, Microsoft recommends keeping the feature disabled by default, and enabling it only when needed. When you use a group to designate super user accounts, use Microsoft Entra Privileged Identity Management (PIM) to reduce risk by enabling just‑in‑time access when required and minimizing permanent privilege.

**Remediation action**

- [Configure Azure Rights Management super users for discovery services or data recovery](/en-us/purview/encryption-super-users#security-best-practices-for-the-super-user-feature)

### On-demand scans are configured for sensitive information discovery

Items in SharePoint, OneDrive and on Devices are evaluated and classified when they're edited or touched. If they aren't edited and they are in scope of a Microsoft Purview policy, they remain unclassified and invisible to Microsoft Purview policies. On-demand scans let you manually trigger evaluation of items across specified SharePoint, OneDrive, or Devices locations to discover and classify historical content. This can provide you with a more complete view of your information protection posture.

**Remediation action**

- [On-demand classification in Microsoft Purview](/en-us/purview/on-demand-classification)

### OCR is enabled for sensitive information detection

OCR (optical character recognition) extends sensitive information type and trainable classifier detection to images across Exchange, SharePoint, OneDrive, Teams, and endpoint devices. Without OCR, DLP policies, and auto-labeling policies can't scan image-based content, scanned documents, screenshots, and invoices, leaving sensitive data in images unprotected. OCR requires Azure pay-as-you-go billing for Microsoft Syntex, and is configured at the tenant level.

**Remediation action**

- [Learn about and configure optical character recognition in Microsoft Purview](/en-us/purview/ocr-learn-about)

### Custom sensitive information types are configured

Custom sensitive information types (SITs) extend Microsoft Purview's ability to detect sensitive information beyond the built-in SITs to cover organization-specific data patterns, proprietary identifiers, internal classification schemes, specialized industry codes, or other formats that built-in SITs don't look for. Use them to create tailored detection rules that align with your organization's unique data protection needs, ensuring that more sensitive information is accurately identified and protected.

**Remediation action**

- [Create custom sensitive information types](/en-us/purview/create-a-custom-sensitive-information-type)

### Exact data match is configured for sensitive information detection

Exact data match (EDM) is an advanced sensitive information type that detects organization-specific data by matching exact values against an uploaded reference database. Unlike pattern-based sensitive information types (SITs) that detect common formats, EDM identifies things like customer lists, employee IDs, or proprietary codes unique to your organization. By configuring EDM-based SITs, you can significantly enhance the accuracy of sensitive information detection in Microsoft Purview, ensuring that critical data is properly identified and protected.

**Remediation action**

- [Learn about exact data match based sensitive information types](/en-us/purview/sit-learn-about-exact-data-match-based-sits)
- [Get started with exact data match based sensitive information types](/en-us/purview/sit-get-started-exact-data-match-based-sits-overview)

### Named entity sensitive information types are used in auto-labeling and data loss prevention policies

Named entity sensitive information types (SITs) are prebuilt Microsoft classifiers that detect common sensitive entities like people's names, physical addresses, and medical terminology. They extend data protection beyond pattern matching into context aware classification, and can be used in auto-labeling policies and DLP rules without any custom development.

**Remediation action**

- [Learn about named entities](/en-us/purview/sit-named-entities-learn)
- [Use named entities in your data loss prevention policies](/en-us/purview/sit-named-entities-use)

### Trainable classifiers are used in data loss prevention and auto-labeling policies

Trainable classifiers are machine learning-based classifiers that recognize content by meaning and context rather than fixed patterns. Unlike sensitive information types that match predefined formats, trainable classifiers can identify unstructured content like strategic plans, financial reports, or HR documents. Using trainable classifiers in auto-labeling policies, and data loss prevention (DLP) rules, extends protection to sensitive business content that pattern-based rules can't reliably capture.

**Remediation action**

- [Learn about trainable classifiers](/en-us/purview/classifier-learn-about)
- [Get started with trainable classifiers](/en-us/purview/trainable-classifiers-get-started-with)

### Purview audit logging is enabled

Audit logging in Microsoft 365 records which users and admins accessed sensitive data, when policy violations occurred, and what administrative actions they took across Microsoft 365. When audit logs are available, security teams can investigate incidents, perform electronic discovery for investigations and legal cases, detect insider threats, and demonstrate controls to auditors and regulators by using Microsoft Purview auditing solutions.

Audit logging is on by default for Microsoft 365 organizations, but you can turn it off. If you turn off audit logging, threat actors can often operate undetected, and incident response becomes impossible due to lack of evidence. Organizations that don't enable audit logging also risk noncompliance with regulatory requirements that mandate activity logging for sensitive operations.

**Remediation action**

- [Turn auditing on or off](/en-us/purview/audit-log-enable-disable)

### Sensitivity labels are configured

Sensitivity labels are the foundation of Microsoft Purview Information Protection. They enable organizations to classify and protect sensitive data across Microsoft 365, on-premises locations, and non-Microsoft applications.

Without sensitivity labels, organizations lack a standardized way to protect their data, leaving it vulnerable to unauthorized access and sharing. A well-designed label taxonomy typically includes 3-7 top-level labels—too many labels overwhelm users and reduce effectiveness.

**Remediation action**

- [Get started with sensitivity labels](/en-us/purview/get-started-with-sensitivity-labels)
- [Create and configure sensitivity labels and their policies](/en-us/purview/create-sensitivity-labels)

### Globally published sensitivity labels don't exceed the recommended maximum

Publishing too many labels globally creates confusion and decision paralysis for users, reducing adoption and increasing misclassification. When users face more than 25 labels, they struggle to identify the appropriate classification, leading to incorrect labels or avoiding the feature entirely.

Microsoft recommends no more than 25 labels in global policies, ideally organized as five main labels with up to five sublabels each. Use scoped policies to publish specialized labels only to specific users, groups, or departments, keeping the global label set focused on common scenarios.

**Remediation action**

- [Sensitivity label limitations per tenant](/en-us/purview/sensitivity-labels#sensitivity-label-limitations-per-tenant)
- [Create and publish sensitivity labels](/en-us/microsoft-365/compliance/create-sensitivity-labels)

### Sensitivity labels with encryption are configured

Without encryption, sensitivity labels denote an item's sensitivity level without preventing unauthorized access, unless supplemented by another protection mechanism. Sensitivity labels that are configured to apply encryption from the Azure Rights Management service enforce access control and usage rights. This protection persists regardless of where the content is stored or shared. For example, users can still share a document labeled as "Confidential", but if that label applies encryption, unauthorized people won't be able to open it.

Organizations using labels without encryption gain visibility of the sensitivity level but the labels themselves lack technical enforcement. Labels that apply encryption ensure only authorized users can decrypt content and use it with any restrictions that are specified for that user. For example, read-only, or prevent copying. This protection helps prevent data exfiltration even if files are leaked or improperly shared. At least one sensitivity label should be configured to apply encryption for high-value data that requires protection beyond identifying the sensitivity level.

**Remediation action**

- [Restrict access to content by using encryption in sensitivity labels](/en-us/purview/encryption-sensitivity-labels)

### Double Key Encryption labels are configured

Double Key Encryption (DKE) provides an extra layer of protection for highly sensitive data by requiring two keys to decrypt content: one managed by Microsoft and one by the customer. This "hold your own key" approach ensures Microsoft can't decrypt content even with legal compulsion, meeting stringent regulatory requirements for data sovereignty.

However, DKE introduces significant operational complexity including dedicated key service infrastructure, reduced feature compatibility, and increased support burden. Organizations should maintain 1-3 labels reserved for truly mission-critical or heavily regulated data, with documented business justification for each DKE label. Use standard encryption for general business content. Excessive DKE labels (4 or more) create management overhead, user confusion, and reduce collaboration. DKE should never be broadly deployed, as key service unavailability prevents access to business-critical documents.

**Remediation action**

- [Double Key Encryption](/en-us/purview/double-key-encryption)
- [Set up Double Key Encryption](/en-us/purview/double-key-encryption-setup)

### Co-authoring is enabled for encrypted documents

When co-authoring isn't enabled for documents protected by sensitivity labels that apply encryption, only one person can edit the file at a time when they use Office desktop apps. As a result, this can slow down teams, which makes collaboration difficult and can delay project completion. This limitation is especially challenging for groups working on sensitive projects that require encryption for privacy but also need to work together efficiently.

Turning on co-authoring for files encrypted with sensitivity labels lets several authorized users edit the file at the same time in Office desktop apps. Unless you can ensure that all users edit these files by using Office for the web, this change removes the slowdown of requiring checkout and allows teams to efficiently collaborate without sacrificing security. The co-authoring setting might also be a requirement for other labeling features.

**Remediation action**

- [Enable co-authoring for files encrypted with sensitivity labels](/en-us/purview/sensitivity-labels-coauthoring)

### Container labels are configured for collaborative workspaces

Container labels extend sensitivity labels beyond individual items to entire collaboration workspaces like Microsoft Teams, Microsoft 365 Groups, SharePoint sites, Viva Engage communities, and Loop workspaces. These labels can control workspace-level settings such as external sharing, guest access, device restrictions, and privacy.

Without container labels, users might be able to create Teams with external guest access even when handling confidential information. This action creates data exfiltration risks where properly labeled documents exist in improperly secured workspaces. Container labels can help to ensure that workspace security matches the sensitivity of stored content, for example, prevent documents labeled as "Highly Confidential" from residing in Teams sites that permit external sharing.

**Remediation action**

- [Use sensitivity labels to protect collaborative workspaces (groups and sites)](/en-us/purview/sensitivity-labels-teams-groups-sites)

### Sensitivity labels are enabled in SharePoint

When sensitivity label integration is disabled (the default) in SharePoint, files in SharePoint and OneDrive can't be labeled or display existing labels, and can't benefit from the additional protection of sensitivity labels that apply encryption. This protection gap leaves sensitive files unclassified and vulnerable to unauthorized access and external sharing.

Enabling sensitivity labels in SharePoint allows users to apply labels by using Office for the web and SharePoint. It's also a requirement for default labeling for these locations, and for auto-labeling policies that can classify files automatically. Sensitivity labels for these files can also strengthen security for Microsoft 365 Copilot, and be used with data loss prevention policies and other Microsoft Purview solutions.

**Remediation action**

- [Enable sensitivity labels for files in SharePoint and OneDrive](/en-us/purview/sensitivity-labels-sharepoint-onedrive-files)

### PDF labeling is enabled in SharePoint

When PDF labeling is disabled (the default) in SharePoint, PDF files can't be labeled or display existing labels, which creates a protection gap. Unlike Office files, PDFs can circulate externally without visible classification markers, making it impossible for recipients to determine the handling requirements or for data loss prevention (DLP) policies to detect sensitive content.

Enabling PDF labeling for SharePoint and OneDrive extends sensitivity label support to PDFs, allowing users to apply labels by using Office for the web and SharePoint, and supports other labeling methods such as auto-labeling policies to classify PDF content automatically.

**Remediation action**

- [Enable sensitivity labels for PDF files in SharePoint and OneDrive](/en-us/purview/sensitivity-labels-sharepoint-onedrive-files#adding-support-for-pdf)

### Sensitivity label policies are published to users

Labels must be published by using label policies before users can apply them to items, such as files, emails, and meetings. Label policies define which users receive which labels, set default labeling behavior, and other labeling requirements. Without published policies, sensitivity labels remain unavailable to users.

**Remediation action**

- [Create and configure sensitivity labels and their policies](/en-us/purview/create-sensitivity-labels?tabs=classic-label-scheme#publish-sensitivity-labels-by-creating-a-label-policy)

### A default sensitivity label is configured in label policies

Setting a default label ensures a base level of protection settings for all new and edited items that support sensitivity labels, and for new containers such as Teams. Users can manually override the label if necessary, and other labeling methods such as auto-labeling can replace the default label with a label that has a higher sensitivity level. Setting a default sensitivity label extends your labeling reach and reduces decision fatigue for users, ensuring content has at least a minimum level of protection.

Unlabeled content might bypass data loss prevention (DLP) policies, and other protection solutions that rely on label detection. If appropriate, set a different default sensitivity label for unlabeled documents and Loop components and pages, emails and meeting invites, new containers, and also a default label for Power BI content.

**Remediation action**

- [Publish sensitivity labels by creating a label policy](/en-us/purview/create-sensitivity-labels#publish-sensitivity-labels-by-creating-a-label-policy)
- [Default label policy for Fabric and Power BI](/en-us/fabric/governance/sensitivity-label-default-label-policy)

### Mandatory labeling is enabled in sensitivity label policies

The policy setting **Require users to apply a label** ensures a sensitivity label must be applied before users can save files and send emails or meeting invites, create new groups or sites, and use Power BI content. This setting also prevents users from completely removing a sensitivity label. Unlabeled items create security and compliance risks. For example, threat actors can exfiltrate sensitive data that could be prevented by protection solutions that trigger based on label detection.

**Remediation action**

- [Publish sensitivity labels by creating a label policy](/en-us/purview/create-sensitivity-labels?tabs=modern-label-scheme#publish-sensitivity-labels-by-creating-a-label-policy)
- [Require users to apply a label to their email and documents](/en-us/purview/sensitivity-labels-office-apps#require-users-to-apply-a-label-to-their-email-and-documents)

### Users must provide justification to downgrade sensitivity labels

When users aren't required to provide a justification for changing a label, they can silently replace a label with one that has a lower sensitivity. For example, replace the "Confidential" label that applies additional protection settings, with "General". This action creates security and compliance risk. Requiring a justification reason makes this risk more obvious to users, and forces them to provide a reason as a visible audit trail.

Compromised accounts or departing employees could downgrade labels to enable data exfiltration. Requiring justification is a lightweight control that increases accountability with low impact on user workflows.

**Remediation action**

- [Publish sensitivity labels by creating a label policy](/en-us/purview/create-sensitivity-labels#publish-sensitivity-labels-by-creating-a-label-policy)
- [What label policies can do](/en-us/purview/sensitivity-labels#what-label-policies-can-do)
- [Review labeling activities in activity explorer](/en-us/purview/data-classification-activity-explorer-available-events#protection-removed)

### Email label policies inherit sensitivity from attachments

When users attach sensitive documents to emails, the email should inherit the highest sensitivity label from attachments to maintain consistent protection. Without this setting enabled, users might send unlabeled emails that contain sensitive attachments, creating a mismatch between the email's sensitivity and its actual content.

Email label inheritance automatically applies the attachment's highest priority label to the email message, ensuring protection levels match and prevent accidental data exposure.

**Remediation action**

- [Publish sensitivity labels](/en-us/purview/create-sensitivity-labels?tabs=modern-label-scheme#publish-sensitivity-labels-by-creating-a-label-policy) to [Configure label inheritance from email attachments](/en-us/purview/sensitivity-labels-office-apps#configure-label-inheritance-from-email-attachments).

### Default sensitivity labels are configured for SharePoint document libraries

When you configure SharePoint with a default label for document libraries, any new files uploaded to that library, or existing files edited in the library will have that label applied if they don't already have a sensitivity label, or they have a sensitivity label but with lower priority. This location-based labeling offers a baseline level of protection and a form of automatic labeling without content inspection. When files aren't labeled, important files can bypass protection and remain vulnerable.

This configuration is most suitable for document libraries that contain files with the same level of sensitivity. It can be supplemented with auto-labeling policies that uses content inspection, and manual labeling with a higher priority sensitivity label if needed.

**Remediation action**

- [Configure a default sensitivity label for a SharePoint document library](/en-us/purview/sensitivity-labels-sharepoint-default-label)

### Auto-labeling policies are configured for all workloads

Auto-labeling greatly extends your labeling reach, by automatically labeling items based on content inspection. When you rely on just manual labeling, users might not always recognize what counts as sensitive data or might forget to label information during their daily tasks. Default labels offer a baseline of protection but don't take into consideration content that requires a higher level of protection. This leads to gaps in classification, allowing sensitive content to move through Microsoft 365 applications without proper labels or protection.

You can configure auto-labeling settings for labels that trigger when users open files in their Office apps, and auto-labeling policies that require no user interactions. Setting up at least one auto-labeling policy to detect sensitive content automatically labels this content, no matter what actions people take. In turn, this labeled content can be used with other Microsoft Purview solutions to increase your security, such as data loss prevention (DLP) rules and access restrictions.

**Remediation action**

- [Automatically apply a sensitivity label to Microsoft 365 data](/en-us/purview/apply-sensitivity-label-automatically)

### Auto-labeling policies are in enforcement mode

When auto-labeling policies are left in simulation mode, you're not realizing the protection from labeling that data. As a result, users and services can't take additional protective measures to safeguard the identified sensitive data. For example, users won't see in their Office apps that a file is labeled Highly Confidential. Data loss prevention rules might use sensitivity labels to prevent sharing with external users, and other risky actions. Labeled data also provides an additional layer of protection when you use Microsoft 365 Copilot.

To ensure sensitive information is automatically labeled, turn on at least one auto-labeling policy. Turning on auto-labeling policies after simulation testing puts protective measures into effect and starts reducing risk.

**Remediation action**

- [How to configure auto-labeling policies for SharePoint, OneDrive, and Exchange](/en-us/purview/apply-sensitivity-label-automatically#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)

### Auto-labeling policies are enabled for SharePoint and OneDrive

When auto-labeling for SharePoint and OneDrive isn't set up, files uploaded without sensitivity labels might not be visible to Data Loss Protection (DLP) policies that rely on labels. As a result, those files can move through the environment with fewer safeguards, which can raise the risk of inappropriate sharing or access.

For example, enabling at least one auto-labeling policy in enforcement mode for SharePoint and OneDrive helps classify sensitive files when users create or edit them. Auto-labeling classification supports downstream protections, such as DLP policies, so they can respond based on the file’s sensitivity and help reduce data exposure risk.

**Remediation action**

- [Apply sensitivity labels automatically for SharePoint and OneDrive](/en-us/purview/apply-sensitivity-label-automatically)

### Microsoft Purview Message Encryption is configured with simplified client access

The SimplifiedClientAccessEnabled setting controls whether the Protect button appears in Outlook on the web. This button lets users quickly add encryption to their emails. If the setting is not turned on, users cannot use the Protect button and must find other ways to encrypt their messages.

To enable this setting, AzureRMSLicensingEnabled must also be active. Azure Rights Management encryption service provides the encryption technology needed for the Protect button to work.

**Remediation action**

- [Manage the display of the Encrypt button in Outlook on the web](/en-us/purview/manage-office-365-message-encryption#manage-the-display-of-the-encrypt-button-in-outlook-on-the-web)

### Custom branding templates are configured for Microsoft Purview Message Encryption

When an organization doesn’t use custom branding templates, people outside the company who receive encrypted messages could see a generic Microsoft‑branded portal. Because the portal doesn’t reflect the organization’s identity, recipients can be less confident about where the message came from.

Custom branding templates let organizations add their logo, colors, disclaimers, and contact details to the portal. These elements help the portal look familiar to recipients and can support trust when they view and interact with encrypted messages.

**Remediation action**

- [Add your organization's brand to your encrypted messages](/en-us/purview/add-your-organization-brand-to-encrypted-messages)

### Email retention policies are configured

Without retention policies, emails persist indefinitely in user mailboxes, creating liability for regulatory violations (GDPR, HIPAA, SOX), increased eDiscovery costs, and uncontrolled storage expenses.

Retention policies automatically manage email lifecycle by deleting or preserving messages based on compliance requirements, reducing legal risk, and ensuring regulatory record-keeping obligations are met.

**Remediation action**

- [Create and manage retention policies](/en-us/purview/create-retention-policies)

### Data loss prevention policies are enabled

A DLP policy can help you identify, monitor, and automatically protect sensitive information in Enterprise applications & devices and Inline web traffic data. DLP policies act on a variety of locations, methods of data transmission, and types of user activities. By protecting sensitive information, DLP policies can help you prevent data leaks, ensure compliance with regulations, and maintain the confidentiality of your organization's data.

**Remediation action**

- [Create and configure DLP policies](/en-us/purview/dlp-create-deploy-policy)

### Endpoint data loss prevention policies are configured

Endpoint data loss prevention policies help protect against egress of sensitive information from user devices to various locations, such as:

- USB drives
- Printers
- External applications
- Removable media
- Bluetooth app
- Windows Recall
- Copy to cli
- Paste to unallowed doamins

It integrates with Microsoft Defender for Endpoint to:

- Monitor data handling activities
- Prevent unauthorized data exfiltration in real time

**Remediation action**

- [Get started with endpoint data loss prevention](/en-us/purview/endpoint-dlp-getting-started)
- [Configure endpoint data loss prevention settings](/en-us/purview/dlp-create-deploy-policy)

### Adaptive Protection is enabled in data loss prevention policies

With Adaptive Protection, organizations can apply the right controls to the right users based on the risk of their behavior.

Adaptive Protection in Microsoft Purview integrates Microsoft Purview Insider Risk Management machine learning with Microsoft Purview Data Loss Prevention (DLP). When insider risk identifies a user who is engaging in risky behavior, they're dynamically assigned to an inside risk level. Then Adaptive Protection can automatically create a DLP policy to help protect the organization against the risky behavior that's associated with that inside risk level. As users insider risk levels change in insider risk management, the DLP policies applied to users can adjust.

**Remediation action**

- [Help dynamically mitigate risks with Adaptive Protection](/en-us/purview/insider-risk-management-adaptive-protection)

### Browser data loss prevention is enabled for AI apps via Edge for Business

Microsoft Purview Data Loss Prevention (DLP) monitoring and protection are built right into the Microsoft Edge for Business browser. You don’t need to onboard the device into Microsoft Purview. This integration helps you stop users from sharing sensitive information to and from cloud apps using Edge for Business. With the rise of AI applications, this capability is crucial to help prevent users from sharing sensitive information with unmanaged AI apps through Edge for Business, which could lead to data leaks and compliance risks. By enabling browser DLP for AI apps via Edge for Business, you can extend your data protection policies to cover web-based interactions, ensuring that sensitive data is safeguarded even when accessed through the browser.

**Remediation action**

- [Help prevent sharing via Microsoft Edge for Business to unmanaged AI apps from managed devices](/en-us/purview/dlp-create-policy-block-to-ai-via-edge)

### Insider Risk Management policies are enabled for risky AI usage

Until organizations use Insider Risk Management with Adaptive Protection, they could fail to detect insider threats, risky behaviors such as misuse of legitimate access to exfiltrate data, or unsafe AI scenarios where users expose sensitive data to large language models or unauthorized cloud AI services.

Insider Risk Management works with Data Loss Prevention (DLP) to combine user behavior signals with content-based rules, helping teams detect risks early and respond before sensitive data is exposed or compromised.

**Remediation action**

- [Create and configure Insider Risk Management policies](/en-us/purview/insider-risk-management-policies)
- [Help dynamically mitigate risks with Adaptive Protection](/en-us/purview/insider-risk-management-adaptive-protection)

### Communication compliance monitoring is configured for Microsoft Copilot

Until organizations configure Communication Compliance policies to capture Copilot interactions, they can’t see when users expose sensitive data to AI services. They also can’t tell how people use Copilot with confidential information or spot possible policy violations. As a result, users may unknowingly share customer records, financial data, source code, or trade secrets with AI services.

Communication Compliance policies that focus on Copilot interactions give organizations clear oversight of AI use while respecting privacy controls. These policies show how users work with sensitive data in AI features and help ensure teams follow data governance and compliance requirements.

**Remediation action**

- [Create and manage Communication Compliance policies](/en-us/purview/communication-compliance-policies)

### Communication compliance monitoring is configured for enterprise AI tools

Collection Policies provide the data ingestion layer that supports monitoring of enterprise AI app activity. When these policies are in place, Communication Compliance can collect signals from AI app interactions and help organizations understand where data protection risks may exist across AI‑enabled workflows. This visibility helps teams apply data protection controls more consistently as AI use expands beyond Microsoft 365 Copilot.

In practice, users may accidentally share sensitive data with custom AI applications, Power Automate flows, AI Builder automations, or non‑Microsoft AI services that aren’t approved to handle confidential information. However, Communication Compliance policies that cover enterprise AI app interactions can help surface potential data exposure to these services and extend data protection practices to custom and third‑party AI solutions.

**Remediation action**

- [Create and Deploy collection policies](/en-us/purview/collection-policies-create-deploy-policy)
- [Create and manage Communication Compliance policies](/en-us/purview/communication-compliance-policies)