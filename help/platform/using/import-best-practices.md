---
solution: Campaign Standard
product: campaign
title: Import best practices
description: Learn more about the best practices to follow when importing data into the database.
audience: automating
content-type: reference
topic-tags: workflow-general-operation

---

# Import best practices {#import-best-practices}

>[!CAUTION]
>
>Please keep in mind the SFTP storage, DB Storage and active profile limits as per your Adobe Campaign contract while using this functionality.

Being cautious and following the few simple rules detailed below will help a lot in ensuring data consistency within the database and in avoiding common errors during database update or data exports.

## Using import templates {#using-import-templates}

Most import workflows should contain the following activities: **[!UICONTROL Load file]**, **[!UICONTROL Reconciliation]**, **[!UICONTROL Segmentation]**, **[!UICONTROL Deduplication]**, **[!UICONTROL Update data]**.

Using import templates makes it very convenient to prepare similar imports and ensure data consistency within the database.

In many projects, imports are built without **[!UICONTROL Deduplication]** activity because the files used in the project do not have duplicates. Duplicates sometimes appear from importing different files. De-duplication is then difficult. Therefore a deduplication step is a good precaution in all import workflows.

Do not rest on assumption that the incoming data is consistent and correct, or that the IT department or Adobe Campaign supervisor will take care of it. During the project, keep the data cleansing in mind. Deduplicate, reconcile, and maintain consistency when you import data.

An example of a generic workflow template designed for importing data is available in the [Example: Import workflow template](../../automating/using/creating-import-workflow-templates.md) section.

>[!NOTE]
>
>You can also use [import templates](../../automating/using/importing-data-with-import-templates.md). They are workflow templates defined by an administrator that, once activated, only offer the possibility to specify the file containing the data to import.

**Related topics:**

* [Load file activity](../../automating/using/load-file.md)
* [Reconciliation activity](../../automating/using/reconciliation.md)
* [Segmentation activity](../../automating/using/segmentation.md)
* [Deduplication activity](../../automating/using/deduplication.md)
* [Update data activity](../../automating/using/update-data.md)

## Using flat file formats {#using-flat-file-formats}

The most efficient format for imports is flat files. Flat files can be imported in bulk mode at the database level.

For example:

* Separator: tab or semicolon
* First line with headers
* No string delimiter
* Date format: YYYY/MM/DD HH:mm:SS

Example of file to import:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

## Using compression {#using-compression}

Use zipped files for imports and exports when possible. GZIP is supported by default. You can add pre-processing when importing files or post-processing when extracting data, respectively in the **[!UICONTROL Load file]** and **[!UICONTROL Extract file]** workflow activities.

**Related topics:**

* [Load file activity](../../automating/using/load-file.md)
* [Extract file activity](../../automating/using/extract-file.md)

## Importing in Delta mode {#importing-in-delta-mode}

Regular imports must be done in delta mode. It means that only modified or new data is sent to Adobe Campaign, instead of the whole table every time.

Full imports should be used for initial load only.

## Maintaining consistency {#maintaining-consistency}

To maintain data consistency in the Adobe Campaign database, follow the principles below:

* If the imported data matches a reference table in Adobe Campaign, then it should be reconciled with that table in the workflow. Records that do not match should be rejected.
* Ensure that the imported data is always **"normalized"** (email, phone number, direct mail address) and that this normalization is reliable and will not change over the years. If this is not the case, some duplicates are likely to appear in the database, and as Adobe Campaign does not provide tools to do "fuzzy" matching, it will be very difficult to manage and remove them.
* Transactional data should have a reconciliation key and be reconciled with the existing data in order to avoid creating duplicates.
* **Import related files in order**. If the import is composed of multiple files that depend on each other, the workflow should make sure that the files are imported in the correct order. When a file fails, the other files are not imported.
* **Deduplicate**, reconcile, and maintain consistency when you import data.
