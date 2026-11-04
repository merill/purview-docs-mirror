---
layout: Conceptual
title: Apply IRM to a list or library | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/apply-irm-to-a-list-or-library
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
f1.keywords:
- NOCSH
ms.author: kreagle
author: k-reagle
manager: laurawi
ms.date: 2026-06-22T00:00:00.0000000Z
audience: Admin
ms.topic: how-to
ms.service: purview
ms.subservice: purview-encryption
search.appverid:
- SPO160
- OSU150
- OSU160
- MET150
ms.collection:
- purview-compliance
- SPO_Content
description: Configure Information Rights Management (IRM) for SharePoint lists and libraries to restrict and protect downloaded files. Supported only in the Microsoft global cloud.
ms.custom: seo-marvel-apr2020, msecd-doc-authoring-1014
ai-usage: ai-assisted
locale: en-us
document_id: f127ccee-700c-5889-47ab-cf624afdd47f
document_version_independent_id: f127ccee-700c-5889-47ab-cf624afdd47f
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/apply-irm-to-a-list-or-library.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: apply-irm-to-a-list-or-library
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/apply-irm-to-a-list-or-library.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/9d7be3ef-f27c-4c7f-9eba-67c3cd429995
- https://authoring-docs-microsoft.poolparty.biz/devrel/dc29fde7-b949-4135-9273-ad8e4a53d516
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/feeb50f3-b677-44f9-b3a6-5f2f58182b0d
- https://authoring-docs-microsoft.poolparty.biz/devrel/25d6050c-71f5-4b48-8bc7-575debd6530a
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
platformId: 84604485-4fbe-4332-aad0-bb257e7e6191
---

# Apply IRM to a list or library | Microsoft Learn

> 
> *[Microsoft Purview service description](/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description)*

You can use Information Rights Management (IRM) to help control and protect files that are downloaded from lists or libraries. IRM for SharePoint lists and libraries is only supported in the Microsoft global cloud. IRM isn't supported for SharePoint lists and libraries in national cloud deployments.

## Administrator preparations before applying IRM

The Azure Rights Management service from Microsoft Purview Information Protection, and the on-premises equivalent, Active Directory Rights Management Services (AD RMS), support Information Rights Management for sites. No other installations are required.

- Before you apply IRM to a list or library, you need to enable IRM for your site. You need administrator permissions for the site to enable IRM. In addition, to apply IRM to a list or library, you must have administrator permissions for that list or library.
- If you're using SharePoint, your users might experience timeouts when downloading larger IRM-protected files. To avoid timeouts, use your Office apps to apply IRM protection, and store larger files in a SharePoint library that doesn't use IRM.

Note

If you're using SharePoint Server 2013, a server administrator must install protectors on all front-end Web servers for every file type that the users in your organization want to protect by using IRM.

## Apply IRM to a list or library

Perform the following steps to configure IRM settings for a list or library:

![Screenshot of the Information Rights Management Settings page for a SharePoint library.](media/1b708102-9c90-42b0-b255-ef0e72d0be88.png)

1. Go to the list or library for which you want to configure IRM.
2. On the ribbon, select the **Library** tab, and then select **Library Settings**. (If you're working in a list, select the **List** tab, and then select **List Settings**).

    ![Screenshot of the SharePoint ribbon showing the Library tab and Library Settings option.](media/cdf718fa-d792-40fc-8026-00c3b80b9e05.png)
3. Under **Permissions and Management**, select **Information Rights Management**. If the Information Rights Management link doesn't appear, IRM might not be enabled for your site. Contact your server administrator to see if you can enable IRM for your site. The **Information Rights Management** link doesn't appear for picture libraries.
4. On the **Information Rights Management Settings** page, select the **Restrict permission to documents in this library on download** check box to apply restricted permissions to documents that users download from this list or library.
5. In the **Create a permission policy title** box, enter a descriptive name for the policy. Use a name that helps you identify this policy from other policies. For example, use **Company Confidential** to apply restricted permissions to a list or library that contains confidential company documents.
6. In the **Add a permission policy description** box, type a description that appears to users who use this list or library that explains how they should handle the documents in this list or library. For example, you can type **Discuss the contents of this document only with other employees** if you want to restrict access to the information in these documents to internal users.
7. To apply another restriction to the documents in this list or library, select **Show Options**, and do any of the following:

| **To do this:** | **Do this:** |
| --- | --- |
| Allow users to print documents from this list or library | Select the **Allow viewers to print** check box. |
| Allow users with at least the View Items permission to run embedded code or macros on a document. | Select the **Allow viewers to run script and screen reader to function on downloaded documents** check box. If you select this option, users could run code to extract the contents of a document. |
| Select this option if you want to restrict access to content to a specified period of time. If you select this option, user issuance licenses to access the content will expire after the specified number of days Users need to return to the server to verify their credentials and download a new copy. | Select the **After download, document access rights will expire after these number of days (1-365)** check box, and then specify the number of days for which you want the document to be viewable. |
| Prevent users from uploading documents that don't support IRM to this list or library. If you select this option, users can't upload these file types: File types that don't have corresponding IRM protectors installed on all of the front-end web servers. File types that SharePoint Server 2010 can't decrypt. File types that are IRM protected in another program. | Select the **Do not allow users to upload documents that do not support IRM** check box. |
| Remove restricted permissions from this list or library on a specific date. | Select the **Stop restricting access to the library at** check box, and then select the date that you want. |
| Control the interval that the Azure Rights Management service credentials are cached for the program that is licensed to open the document. | Select the **Users must verify their credentials using this interval (days)** check box, then enter the interval for caching credentials in number of days. |
| Allow group protection so that users can share with members of the same group. | Select **Allow group protection**, and enter the group's name for sharing. |
| Prevent opening documents in the browser for this Document Library. | Select this option if you want to restrict users from opening Office files in the browser. Note that this setting applies only to Office files and will not affect other file types, such as Loop or PDF. |

1. After you finish selecting the options you want, select **OK**.

## What is Information Rights Management?

Information Rights Management (IRM) enables you to limit the actions that users can take on files that downloaded from lists or libraries. IRM encrypts the downloaded files and limits the set of users and programs that are allowed to decrypt these files. IRM can also limit the rights of the users who are allowed to read files, so that they can't take actions such as print copies of the files or copy text from them.

You can use IRM on lists or libraries to limit the dissemination of sensitive content. For example, create a document library to share information about upcoming products with selected marketing representatives. Then use IRM to prevent these individuals from sharing this content with other users in the company.

On a site, you apply IRM to an entire list or library, rather than to individual files. Protecting content at the list or library level makes it easier to ensure a consistent level of protection for an entire set of documents or files. IRM can thus help your organization to enforce corporate policies that govern the use and dissemination of confidential or proprietary information.

Note

The information in this article regarding Information Rights Management supersedes any terms that reference 'Information Rights Management' in any Microsoft SharePoint Server 2013 and SharePoint Server 2016 license term agreements.

### How IRM can help protect content

IRM helps to protect restricted content in the following ways:

- Helps to prevent an authorized viewer from copying, modifying, printing, faxing, or copying and pasting the content for unauthorized use
- Helps to prevent an authorized viewer from copying the content by using the Print Screen feature in Microsoft Windows
- Helps to prevent an unauthorized viewer from viewing the content if it was sent in e-mail after it was downloaded from the server
- Restricts access to content to a specified period of time, after which users must confirm their credentials and download the content again
- Helps to enforce corporate policies that govern the use and dissemination of content within your organization

### How IRM can't help protect content

IRM can't protect restricted content from:

- Erasure, theft, capture, or transmission by malicious programs such as Trojan horses, keystroke loggers, and certain types of spyware
- Loss or corruption because of the actions of computer viruses
- Manual copying or retyping of content from the display on a screen
- Digital or film photography of content that is displayed on a screen
- Copying by non-Microsoft screen-capture programs
- Copying of content metadata (column values) by non-Microsoft screen-capture programs or copy-and-paste action

## How IRM works for lists and libraries

IRM protection is applied to files at the list or library level. When IRM is enabled for a library, rights management applies to all of the files in that library. When IRM is enabled for a list, rights management applies only to files that are attached to list items, not the actual list items.

When users download files in an IRM-enabled list or library, the files are encrypted so that only authorized users can view them. Each rights-managed file also contains an issuance license that imposes restrictions on the users who view the file. Typical restrictions include:

- Making a file read-only
- Disabling the copying of text
- Preventing users from saving a local copy
- Preventing users from printing the file

Client programs that can read IRM-supported file types use the issuance license within the rights-managed file to enforce these restrictions. Because the issuance license is embedded in the file, a rights-managed file retains its protection even after being downloaded from the server.

The types of restrictions applied to a file that is downloaded from a list or library are based on the user's site permissions. The following table explains how the permissions on sites correspond to IRM permissions.

| **Permissions** | **IRM Permissions** |
| --- | --- |
| Manage Permissions, Manage Web Site | **Full control** (as defined by the client program): This permission generally allows a user to read, edit, copy, save, and modify permissions of rights-managed content. |
| Edit Items, Manage Lists, Add, and Customize Pages | **Edit**, **Copy**, and **Save**: A user can print a file only if the **Allow users to print documents** check box is selected on the Information Rights Management Settings page for the list or library. |
| View Items | **Read**: A user can read the document, but can't copy or modify its content. A user can print only if the **Allow users to print documents** check box is selected on the Information Rights Management Settings page for the list or library. |
| Other | No other permissions correspond directly to IRM permissions. |

When you enable IRM for a list or library in SharePoint Server 2013, you can only protect file types in that list or library for which a protector is installed on all front-end web servers. A protector is a program that controls the encryption and decryption of rights-managed files of a specific file format. SharePoint includes protectors for the following file types:

- Microsoft Office InfoPath forms
- The 97-2003 file formats for the following Microsoft Office programs: Word, Excel, and PowerPoint
- The Office Open XML Formats for the following Microsoft Office programs: Word, Excel, and PowerPoint
- The XML Paper Specification (XPS) format

If your organization plans to use IRM to protect any other file types in addition to the formats listed in this article, your server administrator must install protectors for these other file formats.