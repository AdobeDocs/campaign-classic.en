---
solution: Campaign Classic
product: campaign
title: Creating import and export templates
description: Learn how to create import and export templates in Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
---

# Creating import and export templates {#creating-import-export-templates}

Adobe Campaign offers a data export module that makes it easy to extract a list of customers or prospects (for example, following a targeting operation) who will then become part of a target population.

Adobe Campaign also offers an import module that lets you supply your database with data from external files.

>[!NOTE]
>
>Exports and imports are configured in dedicated templates executed through workflows via the **[!UICONTROL Import]** and **[!UICONTROL Export]** activities. They can be repeated automatically according to a schedule, for example to automate data exchange between several information systems. If necessary, you can create an occasional import or export via the **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]** node of the Adobe Campaign tree.

You can:

* Create an import or export template and configure it (see below).
* Create an import or export: refer to [Exporting data](../../platform/using/launching-export-jobs.md) or [Importing data](../../platform/using/launching-import-jobs.md).
* Launch the import or export and monitor its execution. refer to [Execution tracking](#execution-tracking).

![](assets/do-not-localize/how-to-video.png) [Discover this feature in video](../../platform/using/exporting-and-importing-profiles.md#import-profiles-video)

Import and export templates are stored in the **[!UICONTROL Resources > Templates > Job templates]** directory of the Adobe Campaign tree.

By default, three import templates and one export template are present in this directory. They must not be modified. You can duplicate them to create your own templates or create a new template via the **[!UICONTROL New > Import template]** / **[!UICONTROL Export template]** menu.

![](assets/s_ncs_user_export_wizard_template_create.png)

The procedure for creating a process template is presented in [this page](../../platform/using/creating-import-export-templates.md).

>[!NOTE]
>
>The native template **[!UICONTROL Import denylist]** is already configured to import a list of email addresses which were added to the denylist.
> 
>The **[!UICONTROL New text import]** and **[!UICONTROL New text export]** templates let you configure an import or export from scratch.

Once the template has been configured, import and export operations can be launched in several contexts in Adobe Campaign.

All of these open the [import](../../platform/using/launching-import-jobs.md) or [export](../../platform/using/launching-export-jobs.md) wizard.

* In the **[!UICONTROL Profiles and targets]** section of Adobe Campaign workspace, click the **[!UICONTROL Jobs]** link: this takes you to the list of existing imports and exports.

  Click the **[!UICONTROL Create]** button and select the type of job you want to perform.

  ![](assets/s_ncs_user_import_from_home.png)

* You can also launch imports and exports from the Supervision section of the workspace: two dedicated links enable you to start the import or export directly.

  ![](assets/s_ncs_user_import_from_production.png)

* Imports and exports can also be launched from the Adobe Campaign explorer.

  To export/import data, click the **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]** node, then the **[!UICONTROL New]** icon, and select **[!UICONTROL Export]** or **[!UICONTROL Import]**. This opens the appropriate wizard.

  ![](assets/s_ncs_user_export_wizard_launch_from_menu.png)
