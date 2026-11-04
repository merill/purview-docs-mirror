---
layout: Conceptual
title: Data encryption in OneDrive and SharePoint | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/data-encryption-in-odb-and-spo
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
f1.keywords:
- NOCSH
ms.author: kreagle
author: k-reagle
manager: laurawi
ms.date: 2025-01-10T00:00:00.0000000Z
audience: ITPro
ms.topic: overview
ms.service: purview
ms.subservice: purview-encryption
search.appverid:
- SPO160
- MET150
ms.collection:
- purview-compliance
- SPO_Content
description: Understand the basic elements of encryption for data security in OneDrive and SharePoint.
ms.custom: seo-marvel-apr2020
locale: en-us
document_id: 0a0a496f-286d-6cbc-01e6-898b7c435e32
document_version_independent_id: 0a0a496f-286d-6cbc-01e6-898b7c435e32
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/data-encryption-in-odb-and-spo.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: data-encryption-in-odb-and-spo
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/data-encryption-in-odb-and-spo.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7428317a-e6c2-4461-ad3e-8a8ad3608734
- https://authoring-docs-microsoft.poolparty.biz/devrel/9d7be3ef-f27c-4c7f-9eba-67c3cd429995
- https://authoring-docs-microsoft.poolparty.biz/devrel/1dd701e0-441f-4b0a-9806-aa47decc4e35
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e4f59707-f107-48f2-8d75-0afd91868cd7
- https://authoring-docs-microsoft.poolparty.biz/devrel/feeb50f3-b677-44f9-b3a6-5f2f58182b0d
- https://authoring-docs-microsoft.poolparty.biz/devrel/0a2fc935-5977-4aa6-9f55-0be03bd2acb8
platformId: c3995c48-4e55-68d6-db1a-a9d90c3802ef
---

# Data encryption in OneDrive and SharePoint | Microsoft Learn

> 
> *[Microsoft Purview service description](/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description)*

Understand the basic elements of encryption for data security in OneDrive and SharePoint.

## Security and data encryption in Microsoft 365

Microsoft 365 is a highly secure environment that offers extensive protection in multiple layers: physical data center security, network security, access security, application security, and data security. This article specifically focuses on the in-transit and at-rest encryption side of data security for OneDrive and SharePoint.

Watch how data encryption works in the following video.

## Encryption of data in transit

In OneDrive and SharePoint, there are two scenarios in which data enters and exits the data centers.

- **Client communication with the server** Communication to OneDrive across the Internet uses SSL/TLS connections. All TLS connections are established using 2048-bit keys.
- **Data movement between data centers** The primary reason to move data between data centers is for geo-replication to enable disaster recovery. For instance, SQL Server transaction logs and blob storage deltas travel along this pipe. While this data is already transmitted by using a private network, it's further protected with best-in-class encryption.

## Encryption of data at rest

Encryption at rest includes two components: BitLocker disk-level encryption and per-file encryption of customer content.

BitLocker is deployed for OneDrive and SharePoint across the service. Per-file encryption is also in OneDrive and SharePoint in Microsoft 365 multitenant and new dedicated environments that are built on multitenant technology.

While BitLocker encrypts all data on a disk, per-file encryption goes even further by including a unique encryption key for each file. Further, every update to every file is encrypted using its own encryption key. The keys to the encrypted content are stored in a physically separate location from the content. Every step of this encryption uses Advanced Encryption Standard (AES) with 256-bit keys and is Federal Information Processing Standard (FIPS) 140-2 compliant. The encrypted content is distributed across many containers throughout the data center, and each container has unique credentials. These credentials are stored in a separate physical location from either the content or the content keys.

For more information about FIPS 140-2 compliance, see [FIPS 140-2 Compliance](/en-us/previous-versions/sql/sql-server-2008-r2/bb326611%28v=sql.105%29).

File-level encryption at rest takes advantage of blob storage to provide for storage growth and to enable unprecedented protection. All customer content in OneDrive and SharePoint is migrated to blob storage. Here's how that data is secured:

1. All content is encrypted, potentially with multiple keys, and distributed across the data center. Each file to be stored is broken into one or more chunks, depending on its size. Then, each chunk is encrypted using its own unique key. Updates are handled similarly: the set of changes, or deltas, submitted by a user is broken into chunks, and each is encrypted with its own key.
2. All of these chunks—files, pieces of files, and update deltas—are stored as blobs in our blob store. They also are randomly distributed across multiple blob containers.
3. The "map" used to reassemble the file from its components is stored in the Content Database.
4. Each blob container has its own unique credentials per access type (read, write, enumerate, and delete). Each set of credentials is held in the secure Key Store and is regularly refreshed.

In other words, there are three different types of stores involved in per-file encryption at rest, each with a distinct function:

- Content is stored as encrypted blobs in the blob store. The key to each chunk of content is encrypted and stored separately in the content database. The content itself holds no clue as to how it can be decrypted.
- The Content Database is a SQL Server database. It holds the map required to locate and reassemble all of the content blobs held in the blob store and the keys needed to decrypt those blobs.

Each of these three storage components—the blob store, the Content Database, and the Key Store—is physically separate. The information held in any one of the components is unusable on its own. This strategy provides an unprecedented level of security. Without access to all three it's impossible to retrieve the keys to the chunks, decrypt the keys to make them usable, associate the keys with their corresponding chunks, decrypt any chunk, or reconstruct a document from its constituent chunks.