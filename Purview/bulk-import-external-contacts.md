---
layout: Conceptual
title: Bulk import external contacts to Exchange Online | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/purview/bulk-import-external-contacts
breadcrumb_path: /purview/breadcrumb/toc.json
feedback_system: Standard
uhfHeaderId: MSDocsHeader-Purview
description: Learn how admins can use Exchange Online PowerShell and a CSV file to bulk import external contacts to the global address list.
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
ms.date: 2026-06-19T00:00:00.0000000Z
audience: End User
ms.topic: how-to
ms.service: purview
ms.subservice: purview-exchange-legacy
search.appverid:
- MET150
- MOP150
ms.assetid: bed936bc-0969-4a6d-a7a5-66305c14e958
ms.custom: msecd-doc-authoring-1014, admindeeplinkEXCHANGE, sfi-ga-nochange
ms.collection:
- purview-compliance
- import
ai-usage: ai-assisted
locale: en-us
document_id: 3a3e3864-a635-ad83-7065-6e6ec3384b99
document_version_independent_id: 3a3e3864-a635-ad83-7065-6e6ec3384b99
original_content_git_url: https://github.com/MicrosoftDocs/Purview-pr/blob/live/Purview/bulk-import-external-contacts.md
site_name: Docs
depot_name: MSDN.Purview
page_type: conceptual
toc_rel: toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: bulk-import-external-contacts
moniker_range_name: 
monikers: []
item_type: Content
source_path: Purview/bulk-import-external-contacts.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cf9b82c5-b6dc-45f3-b005-b1bc5fc03bea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/0c85d34e-bfd2-4466-957c-f0b61e9692df
platformId: f8f924af-6dda-cf04-fe7c-4ee2f7473f5a
---

# Bulk import external contacts to Exchange Online | Microsoft Learn

**This article is for administrators. Are you trying to import contacts to your own mailbox? See [Import contacts to Outlook](https://support.office.com/article/bb796340-b58a-46c1-90c7-b549b8f3c5f8).**

Does your company have lots of existing business contacts that you want to include in the shared address book (also called the global address list) in Exchange Online? Do you want to add external contacts as members of distribution groups, just like you can with users inside your company? If so, you can use Exchange Online PowerShell and a CSV (comma-separated value) file to bulk import external contacts into Exchange Online. It's a three-step process:

Step 1: Create a CSV file that contains information about the external contacts

Step 2: Create the external contacts with PowerShell

Step 3: Add information to the properties of the external contacts

After you complete these steps to import contacts, you can perform these additional tasks:

- Add more external contacts
- Hide external contacts from the shared address book

## Step 1: Create a CSV file that contains information about the external contacts

First, create a CSV file that contains information about each external contact you want to import to Exchange Online.

1. Copy the following text to a text file in Notepad, and save it on your desktop as a CSV file by using a filename suffix of .csv, such as ExternalContacts.csv.

    Tip

    If your language contains special characters (such as **å**, **ä**, and **ö** in Swedish), save the CSV file with UTF-8 or other Unicode encoding when you save the file in Notepad.

    ```text
    ExternalEmailAddress,Name,FirstName,LastName,StreetAddress,City,StateorProvince,PostalCode,Phone,MobilePhone,Pager,HomePhone,Company,Title,OtherTelephone,Department,CountryOrRegion,Fax,Initials,Notes,Office,Manager
    danp@fabrikam.com,Dan Park,Dan,Park,1234 23rd Ave,Golden,CO,80215,206-111-1234,303-900-1234,555-1212,123-456-7890,Fabrikam,Shipping clerk,555-5555,Shipping,US,123-4567,R.,Good worker,31/1663,Dan Park
    pilar@contoso.com,Pilar Pinilla,Pilar,Pinilla,1234 Main St.,Seattle,WA,98017,206-555-0100,206-555-0101,206-555-0102,206-555-1234,Contoso,HR Manager,206-555-0104,Executive,US,206-555-0105,P.,Technical decision maker,31/1000,Dan Park
    ```

    The first row, or header row, of the CSV file lists the properties of contacts that you can use when you import them to Exchange Online. Each property name is separated by a comma. Each row under the header row represents the property values for importing a single external contact.

    Note

    This text includes sample data, which you can delete. But don't delete or change the first (header) row. It contains all of the properties for the external contacts.
2. Open the CSV file in Microsoft Excel to edit the CSV file because it's much easier to use Excel to edit the CSV file.
3. Create a row for each contact that you want to import to Exchange Online. Populate as many of the cells as possible. This information appears in the shared address book for each contact.

    Important

    The following properties (which are the first four items in the header row) are required to create an external contact and must be populated in the CSV file: **ExternalEmailAddress**, **Name**, **FirstName**, **LastName**. The PowerShell command that you run in Step 2 uses the values for these properties to create the contacts.

## Step 2: Create the external contacts with PowerShell

In this step, use the CSV file that you created in Step 1 and PowerShell to bulk import the external contacts listed in the CSV file to Exchange Online.

1. Connect PowerShell to your Exchange Online organization. For step-by-step instructions, see [Connect to Exchange Online PowerShell](/en-us/powershell/exchange/connect-to-exchange-online-powershell). Be sure to use the user name and password for your global administrator account when you connect to Exchange Online PowerShell.

    Important

    Microsoft recommends that you use roles with the fewest permissions. Minimizing the number of users with the Global Administrator role helps improve security for your organization. Learn more about Microsoft Purview [roles and permissions](purview-permissions).
2. After you connect PowerShell to Exchange Online, go to the desktop folder where you saved the CSV file in Step 1; for example `C:\Users\Administrator\desktop`.
3. Run the following command to create the external contacts:

    ```powershell
    Import-Csv .\ExternalContacts.csv|%{New-MailContact -Name $_.Name -DisplayName $_.Name -ExternalEmailAddress $_.ExternalEmailAddress -FirstName $_.FirstName -LastName $_.LastName}
    ```

    It might take a while to create the new contacts, depending on how many you're importing. When the command finishes running, PowerShell displays a list of the new contacts that it created.
4. To view the new external contacts, go to the Exchange admin center (EAC), and then select **Recipients** &gt; [**Contacts**](https://go.microsoft.com/fwlink/?linkid=2182970).

    Tip

    For instructions for connecting to the EAC, see [Exchange admin center in Exchange Online](/en-us/exchange/exchange-admin-center).
5. If necessary, select **Refresh** to update the list and see the external contacts that you imported.

    The imported contacts appear in the shared address book in Outlook and Outlook on the web.

    Note

    You can also view the contacts in the Microsoft 365 admin center by going to **Users** &gt; **Contacts**.

## Step 3: Add information to the properties of the external contacts

When you run the command in Step 2, you create the external contacts but don't add any contact or organization information. Most of this information comes from the cells in the CSV file. The contact and organization information from the nonrequired CSV columns is missing because you only populate the required properties when you create new external contacts. Don't worry if you don't have all the information in the CSV file. If it's missing, the information isn't added.

1. Connect PowerShell to your Exchange Online organization. For step-by-step instructions, see [Connect to Exchange Online PowerShell](/en-us/powershell/exchange/connect-to-exchange-online-powershell).
2. Go to the desktop folder where you saved the CSV file in Step 1, such as `C:\Users\Administrator\desktop`.
3. Run the following command to add the other properties from the CSV file to the external contacts that you created in Step 2.

    ```powershell
     Import-Csv .\ExternalContacts.csv|%{Set-Contact -Identity $_.Name -StreetAddress $_.StreetAddress -City $_.City -StateorProvince $_.StateorProvince -PostalCode $_.PostalCode -Phone $_.Phone -MobilePhone $_.MobilePhone -Pager $_.Pager -HomePhone $_.HomePhone -Company $_.Company -Title $_.Title -OtherTelephone $_.OtherTelephone -Department $_.Department -Fax $_.Fax -Initials $_.Initials -Notes  $_.Notes -Office $_.Office -Manager $_.Manager}
    ```

    Note

    The *Manager* parameter might be problematic. If the cell is blank in the CSV file, you get an error and none of the property information is added to the contact. If you don't need to specify a manager, delete `-Manager $_.Manager` from the previous PowerShell command.

    It might take a while to update the contacts, depending on how many you imported in Step 1.
4. To verify that you added the properties to the contacts:
5. In the [Exchange admin center](https://go.microsoft.com/fwlink/p/?linkid=2059104), go to **Recipients** &gt; **Contacts**.
6. Select a contact, and then select **Edit**![Edit icon to open the contact properties pane.](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) to display the contact's properties.

That's it! Users can see the contacts and the additional information in the address book in Outlook and Outlook on the web.

## Add more external contacts

To add new external contacts in Exchange Online, repeat Steps 1 through 3. You or users in your company can add a new row in the CSV file for the new contact. Then, run the PowerShell commands from Step 2 and Step 3 to create and add information to the new contacts.

Note

When you run the command to create new contacts, you might get an error saying that the contacts you created earlier already exist. However, the new contact you added to the CSV file is created.

## Hide external contacts from the shared address book

Some companies use external contacts only so they can add them as members of distribution groups. In this scenario, companies might want to hide external contacts from the shared address book. Complete the following steps.:

1. Connect PowerShell to your Exchange Online organization. For step-by-step instructions, see [Connect to Exchange Online PowerShell](/en-us/powershell/exchange/connect-to-exchange-online-powershell).
2. To hide a single external contact, run the following command.

    ```powershell
    Set-MailContact <external contact> -HiddenFromAddressListsEnabled $true
    ```

    For example, to hide Pilar Pinilla from the shared address book, run this command:

    ```powershell
    Set-MailContact "Pilar Pinilla" -HiddenFromAddressListsEnabled $true
    ```
3. To hide all external contacts from the shared address book, run this command:

    ```powershell
    Get-Contact -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'MailContact')} | Set-MailContact -HiddenFromAddressListsEnabled $true
    ```

After you hide the external contacts, they don't display in the shared address book, but you can still add them as members of a distribution group.