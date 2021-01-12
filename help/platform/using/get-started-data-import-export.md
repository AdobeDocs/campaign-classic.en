---
solution: Campaign Classic
product: campaign
title: Get started with data import and export
description: Learn more on data import and export in Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
---

# Get started with data import and export {#get-started-data-import-export}

Adobe Campaign offers a data export module that makes it easy to extract a list of customers or prospects (for example, following a targeting operation) who will then become part of a target population.

Adobe Campaign also offers an import module that lets you supply your database with data from external files.

>[!NOTE]
>
>Exports and imports are configured in dedicated templates executed through workflows via the **[!UICONTROL Import]** and **[!UICONTROL Export]** activities. They can be repeated automatically according to a schedule, for example to automate data exchange between several information systems. If necessary, you can create an occasional import or export via the **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]** node of the Adobe Campaign tree.

>[!CAUTION]
>
>Data import in Campaign should be performed through workflows to secure data consistency and improve efficiency. For more on this, refer to the [Importing data](../../platform/using/collecting-data-workflows.md), [Import best practices](../../platform/using/import-best-practices.md) and [Import workflow template example](../../platform/using/collecting-data-workflows.md#setting-up-a-recurring-import) sections.

>[!CAUTION]
>
>Please keep in mind the SFTP storage, Database Storage and Active profile limits as per your Adobe Campaign contract while importing data.






Workflows can be a useful way to automate some of your import processes. Whether you import data from a local file or from a SFTP, you can use workflows to standardize your data management procedures.

To learn more about importing data from a workflow, refer to [this section](../../platform/using/collecting-data-workflows.md).


