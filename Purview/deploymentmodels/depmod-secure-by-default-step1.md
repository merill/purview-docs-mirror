---
layout: Conceptual
title: 'Step 1: Start with default labeling - Secure by default with Microsoft Purview | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-secure-by-default-step1
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Securing by default - Step 1 - Start with default labeling.
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
document_id: dda6b17a-eedc-b6ba-fdcf-d57ab12bbd10
document_version_independent_id: dda6b17a-eedc-b6ba-fdcf-d57ab12bbd10
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/deploymentmodels/depmod-secure-by-default-step1.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: deploymentmodels/depmod-secure-by-default-step1
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/deploymentmodels/depmod-secure-by-default-step1.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/9d7be3ef-f27c-4c7f-9eba-67c3cd429995
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/feeb50f3-b677-44f9-b3a6-5f2f58182b0d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
platformId: 31f4a09e-7172-95a1-aa22-a9444bc417d6
---

# Step 1: Start with default labeling - Secure by default with Microsoft Purview | Microsoft Learn

This guide is divided into four steps:

- [Introduction](depmod-secure-by-default-intro)
- Step 1: Start with default labeling (this article)
- [Step 2: Address files with the highest sensitivity](depmod-secure-by-default-step2)
- [Step 3: Expand protection to your entire Microsoft 365 data estate](depmod-secure-by-default-step3)
- [Step 4: Operate, expand, and retroactive actions](depmod-secure-by-default-step4)

![Secure by default with Microsoft Purview - Blueprint](../media/depmod-securebydefault-blueprintimage1.png)

## Sensitivity labels in Microsoft Purview

Sensitivity labels are organizational tags that are meaningful and intuitive to users. They're integrated and consistent across Microsoft solutions and non-Microsoft solutions such as Adobe Acrobat Reader.

Protection policies on labels vary based on the data asset. For example:

- Encryption and Dynamic Watermarking on supported file types
- Conditional Access controls and privacy for SharePoint sites and Teams
- Permission control on Azure SQL Databases, Azure Storage, and Amazon Web Services (AWS) S3

The strategy for applying labels often starts with manual labeling, then client-side auto-labeling with Sensitive Information Types (SIT), followed by service-side auto-labeling (at rest) with SIT and contextual conditions. SharePoint also offers a contextual default label per library, which this guide covers in more detail.

## Start with default labels and protection at file and site level

Most customers should start with the following definition. You can adapt these recommended labels if you have an existing deployment, and iterate later with more scenarios.

At the top level, start with the following labels:

- **Public**: Public data is unrestricted data meant for public consumption, like publicly released source code and announced financials. Share it freely.
- **General**: Business data that isn't meant for public consumption, such as daily work product. Data that you can share internally and with trusted partners.
- **Confidential**: Sensitive business data crucial to achieving your organizational goals. Limited distribution.
- **Highly confidential**: Your most critical data. Share it only with named recipients.

Note

For organizations that accept personal content on managed devices, define a **Non-business** or **Personal** label at the lowest priority and without protection.

For **Confidential** and **Highly confidential**, add the following sublabels:

- **\All Employees**: Data can be accessed by anyone within your organization.
- **\Specific People**: Data can only be accessed by the specified people.
- **\Internal exception**: Data can be accessed by anyone internally but prevented from being shared externally. Use this label in situations where encryption is impacting daily operations.

For a complete list of parent and child labels with recommended configurations, see the following table:

| Label name | Label description for users | Settings |
| --- | --- | --- |
| Public | Business data that is prepared and approved for public consumption. | **Scope**: Files and other data assets (File, Email) **Content marking**: No**Auto-labeling**: No**Data Loss Prevention**: None |
| General | Business data that isn't intended for public consumption. However, you can share this data with external partners, as required. | This label is selected as the default label for emails. This label is also selected for sites allowing external partners.**Scope**: Files and other data assets (File, Email, Meetings, Sites) **Content marking**: No**Auto-labeling**: No**Site privacy**: Private or Public**Data Loss Prevention**: Block anyone with the link |
| Confidential  \ All Employees | Confidential data that requires protection, which allows all employees full permissions. Data owners can track and revoke content. | This label is selected as the default label for documents and sites.**Scope**: Files and other data assets (File, Email, Meetings, Sites) **Encryption**: All users and groups in the org: Co-Author (note: encryption of labels can be implemented later)**Content marking**: Footer: Classified as Confidential**Auto-labeling**: No**Site privacy**: Private or Public**Data Loss Prevention**: Block anyone with the link, Block external |
| Confidential  \ Specific People | Confidential data that you can share with trusted people inside and outside your organization. These people can also reshare the data as needed. | **Scope**: Files and other data assets (File, Email, Meetings, Sites) **Encryption**: Let users assign permissions:  - Encrypt-Only for Outlook - Prompt users in Word, PowerPoint, and Excel**Content marking**: Footer: Classified as Confidential**Auto-labeling**: No**Site privacy**: Private or Public**Data Loss Prevention**: Block anyone with the link |
| Confidential  \ Internal exception | Confidential data that doesn’t need to be encrypted. Use this option with care and appropriate business justification. | This label is selected for confidential information that doesn't need to be encrypted. This label can be used as an internal exception when encryption isn't supported with a process or application using this information. Leverage [Data Loss Prevention](../dlp-learn-about-dlp) and [Insider Risk Management](../insider-risk-management-solution-overview) to manage risk and user deviations.**Scope**: Files and other data assets (File, Email, Meetings, Sites) **Content marking**: Footer: Classified as Confidential**Auto-labeling**:No**Site privacy**: Private or Public**Data Loss Prevention**: Block anyone with the link, Block external |
| Highly Confidential  \ All Employees | Highly confidential data that allows all employees view, edit, and reply permissions to this content. Data owners can track and revoke content. | This label is selected for [client-side auto-labeling](../mip-easy-trials#client-side-auto-labeling) and [service-side auto-labeling](../mip-easy-trials#service-side-auto-labeling).**Scope**: Files and other data assets (File, Email, Meetings, Sites) **Encryption**: All users and groups in the org: Co-Author**Content marking**: Footer: Classified as Highly Confidential**Auto-labeling**: Automatically apply the label. Consider automatically applying for the highly sensitive [All credentials sensitive information types](../sit-defn-all-creds).**Site privacy**: Private or Public**Data Loss Prevention**: Block anyone with the link, Block external |
| Highly Confidential  \ Specific People | Highly confidential data that requires protection and can be viewed only by people you specify and with the permission level you choose. | **Scope**: Files and other data assets (File, Email, Meetings, Sites) **Encryption**: Let users assign permissions: - Do Not Forward for Outlook - Prompt users in Word, PowerPoint, and Excel**Content marking**: Footer: Classified as Highly Confidential**Auto-labeling**: No**Site privacy**: Private or Public**Data Loss Prevention**: Block anyone with the link, Block external |
| Highly Confidential  \ Internal exception | Highly confidential data that doesn’t need to be encrypted. Use this option with care and appropriate business justification. | This label is selected for highly confidential information that doesn't need to be encrypted. This label can be used as an internal exception when encryption isn't supported with a process or application using this information. Leverage [Data Loss Prevention](../dlp-learn-about-dlp) and [Insider Risk Management](../insider-risk-management-solution-overview) to manage risk and user deviations.**Scope**: Files and other data assets (File, Email, Meetings, Sites) **Content marking**: Footer: Classified as Confidential**Auto-labeling**: No**Site privacy**: Private or Public**Data Loss Prevention**: Block anyone with the link, Block external |

## Secure by default

The recommended labels in this deployment model differ slightly from the traditional crawl, walk, run approach or the [Default labels and policies to protect your data](../mip-easy-trials) article:

- Set the default label to **Confidential\All Employees** for files. For existing files, use service-side auto-labeling with the contextual condition **file extension is** for all PPTX, DOCX, XLSX, and PDF files in all relevant SharePoint sites.
- Set the default label to **General** for emails. This label reduces deployment friction by enabling users to function normally, with the exception that confidential files attached to an email inherit the label of the file.
- Set controls for default sharing and DLP limits.
- Use auto-labeling use cases centered around **Highly Confidential**.
- Use the **Specific People** label, intuitively named and self-explanatory.
- Use **Internal Exception** to address edge cases where encryption prevents users from their daily work.

## Highlights and recommendations

- Use intuitive names for labels.
    - Avoid mixing terms such as **Confidential**, **Restricted**, or **Internal** together – users can find it challenging to understand the different meanings of these terms.
    - Keep the list of labels to 5x5 whenever possible, that is: up to five parent labels and up to five child labels under a parent.
- Where applicable, use labels for both files and SharePoint sites.
- Use **Highly Confidential** most often with auto-labeling and contextual defaults. It provides more controls and restrictions.
- Use labels to set your SharePoint sites and Teams privacy to **Private**by default.
    - For organizations that use public privacy settings extensively in SharePoint and Teams, update to **Private** and use company-shareable links instead.
    - Private SharePoint sites with company-shareable links provide the same collaboration flexibility but reduce the risks of unintended discovery in search and Copilot.
    - For more protection, set default sharing to **Specific people**.
- Create a chain of accountability with site owners. Use reporting and Graph API to identify deviations of use and behaviors.
- Turn on DLP on labeled content, blocking **anyone with link** and **external** where applicable. If existing shared content matches those condition blocks, DLP raises alerts and policy tips visible to users.
- Turn on email label inheritance. For more information, see [Configure label inheritance from email attachments](../sensitivity-labels-office-apps#configure-label-inheritance-from-email-attachments).

## Turn on data security prerequisites and advanced analytics

Microsoft Purview has many capabilities. To reduce impacts to users, some capabilities aren't activated by default. Review the following settings:

1. Turn on ability to process content in Office Online: [Enable sensitivity labels for files in SharePoint and OneDrive](../sensitivity-labels-sharepoint-onedrive-files)
2. Turn on labeling for Microsoft Teams and SharePoint Sites: [Use sensitivity labels to protect collaborative workspaces (groups and sites)](../sensitivity-labels-teams-groups-sites#how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels)
    - Keep the [**label mismatch email** label](../sensitivity-labels-teams-groups-sites#auditing-sensitivity-label-activities). This feature sends an email to the document owner and site owner about a document that has a higher sensitivity than the site’s sensitivity label. You can confirm it's not disabled by verifying `-BlockSendLabelMismatchEmail` is set to `$False`.
    - Include a help link with `-LabelMismatchEmailHelpLink`.
3. Enable support for PDF files in OneDrive and SharePoint: [Enable sensitivity labels for files in SharePoint and OneDrive](../sensitivity-labels-sharepoint-onedrive-files)
4. Mark files as sensitive by default: [Prevent guest access to files while DLP rules are applied - SharePoint in Microsoft 365](/en-us/sharepoint/sensitive-by-default)
5. DLP analytics: [Get started with data loss prevention analytics](../dlp-analytics-get-started)
6. Turn on co-authoring for files with sensitivity labels: [Enable co-authoring for encrypted documents](../sensitivity-labels-coauthoring#how-to-enable-co-authoring-for-files-with-sensitivity-labels)
7. Insider Risk Management analytics: [Enable analytics in Insider Risk Management](../insider-risk-management-settings-analytics)
8. Turn on Insider Risk Management Indicators: [Configure policy indicators in insider risk management](../insider-risk-management-settings-policy-indicators)
9. Turn on Microsoft Purview audits: [Get started with auditing solutions](../audit-get-started)
10. Enable integration with Microsoft Entra B2B: [SharePoint and OneDrive integration with Microsoft Entra B2B](/en-us/sharepoint/sharepoint-azureb2b-integration)

## Company-shareable links or links for specific people

OneDrive and SharePoint sharing is configured via shareable links. To learn more, see [How shareable links work in OneDrive and SharePoint in Microsoft 365](/en-us/sharepoint/shareable-links-anyone-specific-people-organization).

For organizations using SharePoint sites with privacy settings set to public, move to private with default shareable links set to **People in your organization**. Open collaboration is available to users, but it reduces automatic content discoverability in enterprise search and Copilot.

Tip

To further reduce risks, configure **Specific people** as your default.

Microsoft Purview Sensitivity Labels allow you to configure the shareable links based on the SharePoint site sensitivity label. For example, this setting greatly facilitates the granular configurations between **General** and **Confidential** sites. To learn more, see [Use sensitivity labels to configure the default sharing link type](../sensitivity-labels-default-sharing-link).

## Train users on managing exceptions

When you use the secure by default approach, focus your training on the following topics:

- Making your organization aware of how important it is to secure information by default.
- The importance of labeling at SharePoint sites and how labels affect protection to files and sharing.
- How users can change labels when working with trusted external partners.
- How users can change labels when a line of business application or an add-in doesn't work correctly with encryption.
- Whether to share from OneDrive or SharePoint with trusted external partners, and how to select the appropriate site label.
- Justification required when downgrading labels.

Deriving file labeling from SharePoint site labeling reduces the number of times users must change their label. For example:

- John is sharing a file externally via OneDrive. He then reviews the content and determines that it isn't confidential and changes the label to General. John then shares externally.
- Jane is working with a partner and sharing multiple files. Jane uses SharePoint and labels the site to General. All files within the site can be shared. But if a Confidential file gets uploaded on the site, that file is protected, a notification is sent to Jane about the higher sensitivity file and she can move the file or change the label.
- Jack works in Excel with a partner using an add-in important to business operations. If this add-in is incompatible with encryption, Jack must change the label to Confidential\Internal exception.

Important

There's an important trade-off to consider between label priority, downgrade and justification, and defaults. For example, assuming **General** is lower priority than **Confidential\All employees**, and if your Office client defaults to **Confidential\All employees**, a SharePoint default library label set to **General** doesn't apply. Similarly, **Confidential\Internal exception** set at a higher priority doesn't require justification. Review label priorities and justification requirements.

## Turn on DLP for labeled content

Microsoft Purview Data Loss Prevention (DLP) integrates with sensitivity labels, so you can quickly address DLP requirements with limited configurations.

For example, if you use the recommended labels and set the default to **Confidential\All employees**, include a DLP rule that blocks sharing to external users and blocks **Anyone with the link**. For details about each label, see the recommended label table and the DLP limits column.

To learn more about this functionality, see:

- [Use sensitivity labels as conditions in DLP policies](../dlp-sensitivity-label-as-condition#use-sensitivity-labels-as-conditions-in-dlp-policies)
- [Data Loss Prevention policy reference](../dlp-policy-reference#policy-scoping)
- [Data loss prevention Exchange conditions and actions reference](../dlp-exchange-conditions-and-actions)

## Summary

At the end of this step, your organization has:

- Labels available for users to use manually.
- Default labeling for any new or updated documents and emails.
- User communications and training on how to manage exceptions, either when sharing or if encryption is causing challenges with their business files.
- DLP preventing the sharing of confidential files.