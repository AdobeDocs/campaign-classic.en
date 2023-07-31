---
product: campaign
title: Adapt your configuration
description: Learn how to adapt your configuration before and after a migration to Campaign v7
feature: Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: yes
hidefromtoc: yes
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
---
# Adapt your configuration{#configuring-your-platform}



Certain major changes in Adobe Campaign v7 require specific configuration. These configurations may be necessary before or after migrating. 

During the migration, the **NmsRecipient** table is rebuilt from the schemas definition. Any change made to the SQL structure of this table outside of Adobe Campaign will be lost.

Example of elements to check:

* If you have added a column (or an index) into the **NmsRecipient** table but you have not detailed it in the schema, this will not be saved.
* The **tablespace** attribute takes back its values by default, in other words those defined in the deployment wizard.
* If you have added a reference view to the **NmsRecipient** table, you must delete it before migrating.


## Before the migration {#before-the-migration}

When migrating to Adobe Campaign v7, the following elements must be configured. These elements must be addressed before starting the **postupgrade**.

<!--

  * Timezones

  During a migration from a v5.11 platform, you must specify the timezone to use during the postupgrade.

  If you wish to use the "multi timezone" mode, refer to [this section](../../migration/using/general-configurations.md#time-zones).

  If you use Oracle as a database, check that the Oracle timezone files have properly been synched between the application server and the database server. [Learn more](../../migration/using/general-configurations.md#oracle)

* Security zones

  For security reasons, the Adobe Campaign platform is no longer accessible by default: you must configure the security zones, which requires collecting the user IP addresses before the migration. [Learn more](../../migration/using/general-configurations.md#security)

* Syntax

  Some Javascript code may no longer accepted in the v7 version, due to the use of a new interpreter. [Learn more](../../migration/using/general-configurations.md#javascript).

  Similarly, a new syntax is introduced in Adobe Campaign v7 to replace the SQLData based syntax. If you use code elements with this syntax, you must adapt them. [Learn more](../../migration/using/general-configurations.md#sqldata)

  -->

* Passwords

  You must configure the **Admin** and **Internal** passwords. [Learn more](../../migration/using/before-starting-migration.md#user-passwords)

<!--
* Tree structure

  If migrating from a v5.11 platform, you must reorganize the tree structure folders according to Adobe Campaign v6 norms. [Learn more](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11).

-->

<!--

* Interaction

  If you are migrating from Campaign v6.02 and using the  **Interaction** module, you must delete all 6.02 schema references that no longer exist in v7. [Learn more](../../migration/using/general-configurations.md#interaction)

-->

## After the migration {#after-the-migration}

After running **postupgrade**, check and configure the following elements:

* Mirror pages

  Mirror page personalization block has changed with v6.x. This new version improves security when accessing these pages.

  If you used the v5 personalization block in your messages, the mirror page display will fail. Adobe highly recommends to use the new personalization block when inserting mirror page in your messages.

  However, as a temporary workaround (and as the mirror pages are still live), you can turn back to the old personalization block to avoid this problem by changing the option **[!UICONTROL XtkAcceptOldPasswords]** and set it to **[!UICONTROL 1]**. This will not affect the usage of the new v6.x personalization block.

* Syntax

  If you encounter any errors related to the syntax, during the postupgrade, you must temporarily activate the **allowSQLInjection** option in the **serverConf.xml** file, as this gives you time to rewrite the code. Once the code is adapted, make sure to reactivate the security.

* Conflicts

  The migration is performed through a postupgrade and conflicts may appear in reports, forms or web applications. These conflicts can be resolved from the console.

* Tomcat

  If you customized the installation folder, make sure to check it is correctly updated after the migration. 

* Reports

  All out-of-the-box reports currently use the v6.x rendering engine. If you had added JavaScript code into the reports, some elements may be impacted. 

* Web Applications

  After the postupgrade, if you have any problems connecting to your identified Web applications, you must activate the **allowUserPassword** and **sessionTokenOnly** options in the **serverConf.xml** file. To avoid any security issue, these two options must be reactivated after the problem is solved.

  Depending on the type of Web applications and their configuration, you must perform additional manipulations to ensure they work correctly. 

<!--
  If migrating from a v5.11 platform, additional configurations must be carried out. [Learn more](../../migration/using/general-configurations.md#specific-configurations-in-v5-11.md)

* Security zones

  Before starting the server, you must configure the security zones. [Learn more](../../installation/using/security-zones.md) and [see here](../../migration/using/general-configurations.md#security)

-->

<!--

* Workflows

  If migrating from a v5.11 platform, you must check the workflows folder. [Learn more](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

-->

<!--

* Tracking

  If migrating from a v5.11 platform, you must configure the tracking mode. [Learn more](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

-->

* Interaction

  If you use **Interaction**, you must adjust any parameters after the migration.

<!--

* Dashboards

  If a client error appears, you have to either update your dashboards with the new Adobe Campaign v7 code, or manually copy the following files from the v6.02 instance to the v7 instance:

  ```
  v6.02 files and spaces:
  /usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
  /usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
  v6.1 files and spaces:
  /usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
  /usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
  ```

-->

<!--

## Specific configurations from a v5.11 to v7{#specific-configurations-in-v5-11}



This section details the additional configuration required when migrating from v5.11. You should also configure the settings detailed in the [General configurations](../../migration/using/general-configurations.md) section.

### Web applications {#web-applications-v5}

The following warning will be displayed automatically during migration:

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side JavaScript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Some components of web applications, for instance the various formula fields, have @id attributes. These are used in the XML code of web applications and are no longer generated in the same way. They are not visible in the interface and you must not normally use them. However, in some cases, @id attributes may have been used to personalize the rendering of web applications, for instance via a stylesheet or using JavaScript code.

During migration, you **must** check the log file path specified in the warning:

* **The file is not empty**: it contains warnings which concern inconsistencies recorded before migration and which still exist. This can be JavaScript code in a web application which references a non-existent ID. Each error must be checked and corrected.
* **The file is empty**: this means that Adobe Campaign has not detected any issues.

Whether the file is empty or not, you must check that these IDs are not used for configuration elsewhere (and adapt configuration if this is the case).

### Workflows {#workflows}

Since the name of the Adobe Campaign installation directory has changed, some workflows may not work after the migration. If a workflow references the nl5 directory in one of its activities, this will raise an error. Replace this reference with **build**. You can run an SQL query to identify these workflows (PostgreSQL example):

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

### MySQL {#mysql}

>[!CAUTION]
>
>MySQL is only supported in v7 as the main database engine when migrating from version 6.02 or 5.11 using this engine.

MySQL does not manage timezones by default. To enable timezone management, run the following command:

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>For more information, refer to the [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) page.

If modifications have been made to the database structure, during configuration for example (creating specific indexes, creating SQL views, etc.), certain precautions should be taken when migrating. Indeed, certain modifications can be generated from incompatibilities with the migration procedure. For example, creating SQL views containing **Timestamp** fields are not compatible with the **usetimestamptz** option. We therefore advise you to follow the recommendations below:

1. Before starting the migration, back up the database.
1. Delete SQL changes.
1. Perform the postupgrade
    >[!NOTE]
    >
    >You must follow the migration steps presented in [this section](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md).
1. Reintegrate SQL changes.

In this example, a **NmcTrackingLogMessages** view had been created and this has a **Timestamp** field named **tslog**. In this case, the migration procedure fails and the following error message appears:

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

To make sure the postupgrade works, you must delete the view before the migration and re-create it after the migration while adapting it to the TIMESTAMP WITH TIMEZONE mode.

### Tracking {#tracking}

The tracking formula has been modified. When migrating, the old formula (v5) is replaced by the new one (v7). If you use a personalized formula in Adobe Campaign v5, this configuration has to be adapted in Adobe Campaign v7 (**NmsTracking_ClickFormula** and **NmsTracking_OpenFormula** options).

Web tracking management has also been modified. Once migration to v7 has been carried out, you must start the deployment wizard to finish configuring the web tracking.

  ![](assets/migration_web_tracking.png)

Three modes are available:

* **Session web tracking**: If the **[!UICONTROL Leads]** package has not been installed, this option is selected by default. This option is the most ideal in terms of performance and it allows you to limit the size of the tracking logs.
* **Permanent Web tracking**
* **Anonymous Web Tracking**: If the **[!UICONTROL Leads]** package is installed, this option is selected by default. It is the most resource-consuming option. As above, the **sSourceId** column must be indexed (in the tracking table and the **CrmIncomingLead** table).

>[!NOTE]
>
>For more information on these three modes, refer to [this section](../../configuration/using/about-web-tracking.md).

### Adobe Campaign v7 tree structure {#campaign-vseven-tree-structure}

During migration, the tree structure is automatically reorganized based on the v7 standards. The new folders are added, the obsolete folders are deleted, and their content is placed in the "To move" folder. All items in this folder must be checked after the migration, and the consultant has to decide to either keep it or delete each one. Items to be kept then have to be moved to the right place.

An option has been added for disabling the automatic migration of the navigation tree. This operation is now manual. Obsolete folders are not deleted and new folders are not added. This option should only be used if the out-of-the-box v5 navigation tree has undergone too many changes. Add the option to the console, before migrating, in the **[!UICONTROL Administration > Options]** node:

* Internal name: NlMigration_KeepFolderStructure
* Data type: Integer
* Value (text): 1

If you use this option, after migration you will have to delete obsolete folders, add the new folders and run all necessary checks.

**List of new folders**:

The following folders need to be added after the migration:

| Internal name | Label | Condition |
|---|---|---|
| nmsAutoObjects | Objects created automatically | - |
| nmsCampaignAdmin | Campaign management | - |
| nmsCampaignMgt | Campaign management | - |
| nmsCampaignRes | Campaign management | - |
| nmsModels | Templates | - |
| nmsOnlineRes | Online | - |
| nmsProduction | Production | - |
| nmsProfilProcess | Processes | - |
| xtkDashboard | Dashboards | - |
| xtkPlatformAdmin | Platform | - |
| nmsLocalOrgUnit | Organizational units | - |
| nmsMRM | MRM | MRM installed |
| nmsOperations | Campaigns | Campaign installed |

**List of obsolete folders**:

The obsolete folders to be deleted after the migration are as follows:

>[!NOTE]
>
>The entire content of the obsolete folders must be checked, and for each item the consultant decides whether to keep or delete it. The items to be kept must be moved to the appropriate place.

| Internal name | Label | Condition |
|---|---|---|
| nmsAdministration | Administration | - |
| nmsDeliveryMgt | Campaign execution | - |
| ncmContent | Content management | Content Manager installed |
| ncmForm | Input form | Content Manager installed |
| ncmImage | Images | Content Manager installed |
| ncmJavascript | JavaScript codes | Content Manager installed |
| ncmJst | JavaScript templates | Content Manager installed |
| ncmParameters | Configuration | Content Manager installed |
| ncmSrcSchema | Data schemas | Content Manager installed |
| ncmStylesheet | XSL style files | Content Manager installed |
| nmsAdminPlan | Administration | Campaign installed |
| nmsResourcePlan | Resources | Campaign installed |
| nmsResourcesModels | Templates | Campaign installed |
| nmsRootPlan | Campaign management | Campaign installed |
| nmsOperator | Marketing operators | MRM installed |


## Specific configurations from v6.02 to v7{#specific-configurations-in-v6-02}



The following section details the additional configuration required when migrating from v6.02. You should also configure the settings detailed in [this page](../../migration/using/general-configurations.md).

### Web applications {#web-applications-v6}

If you are migrating from v6.02, error logs regarding overview-type web applications may appear. Error message examples:

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

These web applications used SQLData and are not compatible with v7, due to heightened security. These errors will lead to a migration failure.

If you didn't use these web applications, run the following cleanup script and rerun the postupgrade:

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

If you have modified these web applications and would like to continue using them in v7, you must activate the **allowSQLInjection** option in your different security zones and re-start the postupgrade. Refer to the [SQLData](../../migration/using/general-configurations.md#sqldata) section for more on this.

### Message Center {#message-center}

After a Message Center control instance migration, you must republish the transactional message templates for them to work.

In v7, the names of transactional message templates on execution instances have changed. They are currently prefixed by the operator name that corresponds to the control instance on which they are created, for example **control1_template1_rt** (where **control1** is the name of the operator). If you have a significant volume of templates, we recommend deleting old templates on control instances.

-->