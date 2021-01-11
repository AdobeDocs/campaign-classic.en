---
solution: Campaign Classic
product: campaign
title: Generic imports and exports
description: Generic imports and exports
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
---

# Generic imports and exports{#generic-imports-and-exports}

Adobe Campaign offers a data export module that makes it easy to extract a list of customers or prospects (for example, following a targeting operation) who will then become part of a target population.

Adobe Campaign also offers an import module that lets you supply your database with data from external files.

>[!NOTE]
>
>Exports and imports are configured in dedicated templates executed through workflows via the **[!UICONTROL Import]** and **[!UICONTROL Export]** activities. They can be repeated automatically according to a schedule, for example to automate data exchange between several information systems. If necessary, you can create an occasional import or export via the **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]** node of the Adobe Campaign tree.

>[!CAUTION]
>
>Data import in Campaign should be performed through workflows to secure data consistency and improve efficiency. For more on this, refer to the [Importing data](../../workflow/using/importing-data.md), [Import best practices](../../workflow/using/importing-data.md#best-practices-when-importing-data) and [Import template example](../../workflow/using/importing-data.md#setting-up-a-recurring-import) sections.

>[!CAUTION]
>
>Please keep in mind the SFTP storage, Database Storage and Active profile limits as per your Adobe Campaign contract while importing data.


