---
layout: Conceptual
title: Encryption in Azure | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/office-365-azure-encryption
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
f1.keywords:
- NOCSH
ms.author: kreagle
author: k-reagle
manager: laurawi
ms.date: 2025-04-22T00:00:00.0000000Z
audience: Admin
ms.topic: article
ms.service: purview
ms.subservice: purview-encryption
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- purview-compliance
description: Learn about encryption available in Azure, such as Azure Disk Encryption
ms.custom: seo-marvel-apr2020
locale: en-us
document_id: fa7d3202-5030-782b-0526-4ba59f4fde81
document_version_independent_id: fa7d3202-5030-782b-0526-4ba59f4fde81
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/office-365-azure-encryption.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: office-365-azure-encryption
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/office-365-azure-encryption.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://authoring-docs-microsoft.poolparty.biz/devrel/de8ce683-cbe1-461b-bae7-77db0888ec6d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://authoring-docs-microsoft.poolparty.biz/devrel/a06cf482-4ca9-4582-a142-bcf842258d42
platformId: f16546e4-5773-0587-84bd-6bb8aea97b9e
---

# Encryption in Azure | Microsoft Learn

> 
> *[Microsoft Purview service description](/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description)*

Technological safeguards in Azure, such as encrypted communications and operational processes, help keep your data secure. You also have the flexibility to implement additional encryption features and manage your own cryptographic keys. Regardless of customer configuration, Microsoft applies encryption to protect customer data in Azure. Microsoft also enables you to control your data hosted in Azure through a range of advanced technologies to encrypt, control, and manage cryptographic keys, and control and audit access to data. In addition, Azure Storage provides a comprehensive set of security capabilities which together enable developers to build secure applications.

Azure offers many mechanisms for protecting data as it moves from one location to another. Microsoft uses TLS to protect data when it's traveling between the cloud services and customers. Microsoft's data centers negotiate a TLS connection with client systems that connect to Azure services. Forward Secrecy (FS) protects connections between customers' client systems and Microsoft's cloud services by unique keys. Connections also use RSA-based 2,048-bit encryption key lengths. This combination makes it difficult for someone to intercept and access data that is in-transit.

Data can be secured in transit between an application and Azure by using [client-side encryption](/en-us/azure/storage/storage-client-side-encryption), HTTPS, or SMB 3.0. You can enable encryption for traffic between your own virtual machines (VMs) and your users. With [Azure Virtual Networks](https://azure.microsoft.com/services/virtual-network/), you can use the industry-standard IPsec protocol to encrypt traffic between your corporate VPN gateway and Azure as well as between the VMs located on your Virtual Network.

For data at rest, Azure offers many encryption options, such as support for AES-256, allowing you to choose the data storage scenario that best meets your needs. Data can be automatically encrypted when written to Azure Storage using [Storage Service Encryption](/en-us/azure/storage/storage-service-encryption) (SSE), and operating system and data disks used by VMs can be encrypted. For more information, see [Security recommendations for Windows virtual machines in Azure](/en-us/azure/virtual-machines/security-recommendations). In addition, delegated access to data objects in Azure Storage can be granted using [Shared Access Signatures](/en-us/azure/storage/storage-dotnet-shared-access-signature-part-1). Azure also provides encryption for data at rest using [Transparent Data Encryption for Azure SQL Database and Data Warehouse](/en-us/sql/relational-databases/security/encryption/transparent-data-encryption-azure-sql).

For more information about encryption in Azure, see [Azure encryption overview](/en-us/azure/security/security-azure-encryption-overview) and [Azure Data Encryption-at-Rest](/en-us/azure/security/azure-security-encryption-atrest).

## Azure Disk Encryption

Azure Disk Encryption enables you to encrypt your Windows and Linux Infrastructure as a Service (IaaS) VM disks. Azure Disk Encryption uses the BitLocker feature of Windows and the DM-Crypt feature of Linux to provide volume-level encryption for the operating system and the data disks. It also ensures that all data on the VM disks are encrypted at rest in your Azure storage. Azure Disk Encryption is integrated with Azure Key Vault to help you control, manage, and audit the use of the encryption keys and secrets.

For more information, see [Security recommendations for Windows virtual machines in Azure](/en-us/azure/virtual-machines/windows/security-recommendations).

## Azure Storage Service Encryption

With [Azure Storage Service Encryption](/en-us/azure/storage/storage-service-encryption), Azure Storage automatically encrypts data prior to persisting it to storage and decrypts data prior to retrieval. The encryption, decryption, and key management processes are totally transparent to users. Azure Storage Service Encryption can be used for [Azure Blob Storage](https://azure.microsoft.com/services/storage/blobs/) and [Azure Files](https://azure.microsoft.com/services/storage/files/). You can also use Microsoft-managed encryption keys with Azure Storage Service Encryption, or you can use your own encryption keys. (For information on using your own keys, see [Storage Service Encryption using customer managed keys in Azure Key Vault](/en-us/azure/storage/common/storage-service-encryption-customer-managed-keys). For information about using Microsoft-managed keys, see [Storage Service Encryption for Data at Rest](/en-us/azure/storage/storage-service-encryption).) In addition, you can automate the use of encryption. For example, you can programmatically enable or disable Storage Service Encryption on a storage account using the [Azure Storage Resource Provider REST API](/en-us/rest/api/storagerp/), the [Storage Resource Provider Client Library for .NET](/en-us/dotnet/api/overview/azure/storage), [Azure PowerShell](/en-us/powershell/azureps-cmdlets-docs), or the [Azure CLI](/en-us/azure/storage/storage-azure-cli).

Some Microsoft 365 services use Azure for storing data. For example, SharePoint Online and OneDrive for Business store data in Azure Blob storage, and Microsoft Teams stores data for its chat service in tables, blobs, and queues. In addition, the Compliance Manager feature in the Microsoft Purview portal stores customer-entered data in encrypted form in [Azure Cosmos DB](/en-us/azure/cosmos-db/database-encryption-at-rest), a Platform as a Service (PaaS), globally-distributed, multi-model database. Azure Storage Service Encryption encrypts data stored in Azure Blob storage and in tables, and Azure Disk Encryption encrypts data in queues, as well as Windows and IaaS virtual machine disks to provide volume encryption for the operating system and the data disk. The solution ensures that all data on the virtual machine disks are encrypted at rest in your Azure storage. [Encryption at rest in Azure Cosmos DB](/en-us/azure/cosmos-db/database-encryption-at-rest) is implemented by using several security technologies, including secure key storage systems, encrypted networks, and cryptographic APIs.

## Azure Key Vault

Secure key management is not just core to encryption best practices; it's also essential for protecting data in the cloud. [Azure Key Vault](/en-us/azure/key-vault/key-vault-whatis) enables you to encrypt keys and small secrets like passwords that use keys stored in hardware security modules (HSMs). Azure Key Vault is Microsoft's recommended solution for managing and controlling access to encryption keys used by cloud services. Permissions to access keys can be assigned to services or to users with Microsoft Entra accounts. Azure Key Vault relieves organizations of the need to configure, patch, and maintain HSMs and key management software. With Azure Key Vault, Microsoft never sees your keys and applications don't have direct access to them; you maintain control. You can also import or generate keys in HSMs. Organizations that have a subscription that includes Microsoft Purview Information Protection can configure the root key for their Azure Rights Management service to use a customer-managed key [Bring Your Own Key](rights-management-byok) (BYOK)) and [log its usage](rights-management-usage-logging).