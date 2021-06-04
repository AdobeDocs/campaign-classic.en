---
product: campaign
title: Get started with data import and export
description: Learn more on data import and export in Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d6055d97-75fc-4ed7-89bd-8336157454eb
---
# Get started with data import and export {#get-started-data-import-export}

Adobe Campaign Classic provides data management capabilities that allow you to import and export data. These operations can be performed using either workflows or generic imports and exports.

>[!IMPORTANT]
>
>Please keep in mind the SFTP storage, database storage and active profile limits as per your Adobe Campaign contract while using this functionality.

## Workflows {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Workflows** are a useful way to automate your import processes. Whether you import data from a local file or from a SFTP, they allow you to standardize your data management procedures.

With workflows, import and export operations can be repeated automatically according to a schedule, for example to automate data exchange between several information systems.

For more on this, refer to [this section](../../platform/using/import-export-workflows.md).

## Generic imports and exports {#generic-import-export}

<img src="assets/do-not-localize/icon_templates.svg" width="60px">

Additionally, Campaign Classic provides **generic imports and exports** that allow you to create occasional import or export jobs.

Imports and exports are configured in dedicated templates, that you can configure and use to launch and monitor import and export jobs.

For more on generic imports and exports, refer to [this section](../../platform/using/about-generic-imports-exports.md).

>[!IMPORTANT]
>Generic imports and exports should be used for occasional operations only. To ensure data consistency and improve efficiency, it is recommended to perform your import and export operations using workflows.

## Data encryption and compression {#data-encryption-compression}

<img src="assets/do-not-localize/icon_encrypt.svg" width="60px">

Campaign Classic allows you to import zipped or encrypted files, and export zipped or encrypted file.

These operations are performed within workflows, by applying pre-processing stages to the data you want to leverage.

For more on this, refer to these sections:

* [Unzip or decrypt a file](../../platform/using/unzip-decrypt.md)
* [Zip or encrypt a file](../../platform/using/zip-encrypt.md)

## Best practices and troubleshooting {#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

Several [best practices](../../platform/using/import-export-best-practices.md) should be followed when performing import and export operations to ensure data consistency within the database and avoid commong error during update or export.

Additionally, recommendations and common issues related to SFTP servers usage are available in [this section](../../platform/using/sftp-server-usage.md).
