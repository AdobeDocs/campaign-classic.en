---
solution: Campaign Classic
product: campaign
title: Testing the migration
description: Testing the migration
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
---
# Testing the migration{#testing-the-migration}

## General procedure {#general-procedure}

Depending on your configuration, there are several ways of carrying out migration tests.

You should have a test/development environment to carry out migration tests. Development environments are subject to license: check your license contract or contact Adobe Campaign's sales service.

1. Stop all developments in progress and carry them over to the production environment.
1. Make a backup of the development environment database.
1. Stop all Adobe Campaign processes on the development instance.
1. Make a backup of the production environment database and restore it as a development environment.
1. Before starting the Adobe Campaign services, run the **freezeInstance.js** cauterization script which lets you clear the database of any objects that were running when the backup was started.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >The command launches by default in **dry** mode, and lists all the requests that were executed by that command, without launching them. To execute cauterization requests, use **run** in the command.

1. Make sure your backups are correct by trying to restore them. Make sure you can access your database, your tables, your data, etc.
1. Test the migration procedure in the development environment.

   The full procedures are detailed in the [Prerequisites for migration to Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) section.

1. If the migration of the development environment is successful, you can migrate the production environment.

>[!IMPORTANT]
>
>Due to changes made to the data structure, importing and exporting data packages is not possible between a v5 platform and a v7 platform.

>[!NOTE]
>
>The Adobe Campaign update command (**postupgrade**) lets you synchronize resources and update schemas and the database. This operation can only be carried out once and only on the application server. After synchronizing resources, the **postupgrade** command lets you detect whether the synchronization generates any errors or warnings.

## Migration tools {#migration-tools}

Various options let you measure the impact from a migration and identify the potential problems. These options are to be executed:

* in the **config** command:

  ```
  nlserver.exe config <option> -instance:<instanceName>
  ```

* or at the postupgrade:

  ```
  nlserver.exe config -postupgrade <option> -instance:<instanceName>
  ```

>[!NOTE]
>
>You must use the **-instance:`<instanceame>`** option. We do not recommend using the **-allinstances** option.

### -showCustomEntities and -showDeletedEntities options {#showcustomentities-and--showdeletedentities-options}

* The **-showCustomEntities** option displays the list of all non-standard objects:

  ```
  nlserver.exe config -showCustomEntities -instance:<instanceName>
  ```

  Example of a sent message:

  ```
  xtk_migration:opsecurity2 xtk:entity
  ```

* The **-showDeletedEntities** option displays the list of all the standard objects that are missing in the database or the file system. For each missing object, the path is specified.

  ```
  nlserver.exe config -showDeletedEntities -instance:<instanceName>
  ```

  Example of a sent message:

  ```
  Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
  ```

### Verification process {#verification-process}

Integrated as standard in the postupgrade command, this process lets you display warnings and errors that could make the migration fail. **If errors are displayed, the migration has not been executed.** If this happens, correct all the errors then re-start the postupgrade.

You can start the verification process on its own (without migration) using the command:

```
nlserver.exe config -postupgrade -check -instance:<instanceName>
```

>[!NOTE]
>
>Please ignore all warnings and errors which have the JST-310040 code.

The following expressions are searched for (case sensitive):

<table> 
 <thead> 
  <tr> 
   <th> Expression<br /> </th> 
   <th> Error code<br /> </th> 
   <th> Log type<br /> </th> 
   <th> Comments<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> Warning<br /> </td> 
   <td> This type of syntax is no longer supported in delivery personalization. Refer to <a href="../../migration/using/general-configurations.md#javascript" target="_blank">JavaScript</a>. Otherwise, check that the value type is correct.<br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> Warning<br /> </td> 
   <td> This library must not be used.<br /> </td> 
  </tr> 
  <tr> 
   <td> logon(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> Warning<br /> </td> 
   <td> This connection method must be no longer be used. Refer to <a href="../../migration/using/general-configurations.md#identified-web-applications" target="_blank">Identified web applications</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> Warning<br /> </td> 
   <td> This function is only supported when it is used in JavaScript code executed from a security zone that is in <strong>sessionTokenOnly</strong> mode.<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> Error<br /> </td> 
   <td> This type of error leads to a migration failure. Refer to <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> SQLDATA<br /> </td> 
   <td> PU-0006<br /> </td> 
   <td> Error<br /> </td> 
   <td> This type of error leads to a migration failure. Refer to <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>. If you get overview-type web application error logs (migration from v6.02), refer to <a href="../../migration/using/specific-configurations-in-v6-02.md#web-applications" target="_blank">Web applications</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

A database and schema coherence check is also carried out.

### Restoration option {#restoration-option}

This option lets you restore out-of-the-box objects if they had been modified. For each restored object, a backup of your changes is stored in the selected folder:

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instanceName>
```

>[!NOTE]
>
>We strongly recommend using absolute folder paths and keeping the folder tree structure. For example: backupFolder\nms\srcSchema\billing.xml.

### Resuming migration {#resuming-migration}

If you restart the postupgrade after a migration failure, it resumes from the same place it was stopped.
