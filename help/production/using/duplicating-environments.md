---
solution: Campaign Classic
product: campaign
title: Duplicating environments
description: Duplicating environments
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 2c933fc5-1c0a-4c2f-9ff2-90d09a79c55a
---
# Duplicating environments{#duplicating-environments}

## Introduction {#introduction}

### Overview {#overview}

>[!IMPORTANT]
>
>If you do not have access to the server and the database (hosted environments), you will not be able to perform the procedures described below. Please contact Adobe.

Using Adobe Campaign requires installing and configuring one or more environments: development, test, pre-production, production, etc.

Each environment contains an Adobe Campaign instance and each Adobe Campaign instance is linked to one or more databases. The application server can execute one or more processes: almost all of these have direct access to the instance database.

This section details the processes to be applied to duplicate an Adobe Campaign environment, i.e. to restore a source environment to a target environment, resulting in two identical work environments.

To do this, apply the following steps:

1. Create a copy of the databases on all instances in the source environment,
1. Restore these copies on all instances of the target environment, 
1. Run the **nms:freezeInstance.js** cauterization script on the target environment before starting it up.

   This process does not impact the servers and their configuration.

   >[!NOTE]
   >
   >In the context of Adobe Campaign, a **cauterization** combines actions that let you stop all processes interacting with the outside: logs, tracking, deliveries, campaign workflows, etc.  
   >This step is necessary to avoid delivering messages several times (once from the nominal environment and one from the duplicated environment).

   >[!IMPORTANT]
   >
   >One environment can contain several instances. Each Adobe Campaign instance is subjected to a license contract. Check your license agreement to see how many environments you can have.   
   >The procedure below lets you transfer an environment without impacting the number of environments and instances you have installed.

### Before you start {#before-you-start}

>[!IMPORTANT]
>
>We strongly recommend running a full backup of the databases for all instances of the source and target environments before starting the transfer process. This way if a problem occurs, you will be able to restore the backups and return to your initial configuration.

In order for this process to work, the source and target environments must have the same number of instances, the same purpose (marketing instance, delivery instance) and similar configurations. The technical configuration must comply with software prerequisites. The same components must be installed on both environments.

## Implementation {#implementation}

### Transfer procedure {#transfer-procedure}

This section will help you understand the steps required for transferring a source environment to a target environment via a case study: our aim here is to restore a production environment (**prod** instance) to a development environment (**dev** instance) to work in a context that is as close as possible to the 'live' platform.

The following steps must be performed with great care: some processes may still be in progress when the source environment databases are copied. Cauterization (step 3 below) prevents messages from being sent twice and maintains data consistency.

>[!IMPORTANT]
>
>* The following procedure is valid in PostgreSQL language. If the SQL language is different (Oracle, for example), the SQL queries must be adapted.
>* The commands below apply within the context of a **prod** instance and a **dev** instance under PostgreSQL.
>

### Step 1 - Make a backup of the source environment (prod) data {#step-1---make-a-backup-of-the-source-environment--prod--data}

Copy the databases

Start by copying all of the source environment databases. The operation depends on the database engine and is the responsibility of the database administrator.

Under PostgreSQL, the command is:

```
pg_dump mydatabase > mydatabase.sql
```

### Step 2 - Export the target environment configuration (dev) {#step-2---export-the-target-environment-configuration--dev-}

Most configuration elements are different for each environment: external accounts (mid-sourcing, routing, etc.), technical options (platform name, DatabaseId, email addresses and default URLs, etc.).

Before saving the source database on the target database, you need to export the target environment (dev) configuration. To do this, export the content of these two tables: **xtkoption** and **nmsextaccount**.

This export lets you keep the dev configuration and only refresh dev data (workflows, templates, Web applications, recipients, etc.).

To do this, perform a package export for the following two elements:

* Export the **xtk:option** table into an 'options_dev.xml' file, without the records with the following internal names: 'WdbcTimeZone', 'NmsServer_LastPostUpgrade' and 'NmsBroadcast_RegexRules'.
* In an 'extaccount_dev.xml' file, export the **nms:extAccount** table for all records whose ID is not 0 (@id <> 0).

Check that the number of exported options/accounts is equal to the number of lines to export in each file.

>[!NOTE]
>
>The number of lines to export in a package export is 1000 lines. If the number of options or external accounts is more than 1000, you must carry out several exports.
> 
>For more information, refer to [this section](../../platform/using/working-with-data-packages.md#exporting-packages).

>[!NOTE]
>
>When the nmsextaccount table is exported, passwords related to the external accounts (for example passwords for Mid-sourcing, Message Center Execution, SMPP, IMS and other external accounts) are not exported. Please make sure you have access to the correct passwords in advance, as they may need to be re-entered after the external accounts are imported back into the environment.

### Step 3 - Stop the target environment (dev) {#step-3---stop-the-target-environment--dev-}

You need to stop Adobe Campaign processes on all target environment servers. This operation depends on your operating system.

You can stop all processes, or only those that write to the database.

To stop all processes, use the following commands:

* In Windows:

  ```
  net stop nlserver6
  ```

* In Linux:

  ```
  /etc/init.d/nlserver6 stop
  ```

Use the following command to check that all processes have been stopped:

```
nlserver pdump
```

>[!NOTE]
>
>In Windows, the **webmdl** process can still be active without impacting other operations.

You can also check that no system processes are still running.

To do this, use the following process:

* In Windows: open the **Task manager** and check that there are no **nlserver.exe** processes.
* In Linux: run the **ps aux | grep nlserver** command and check that there are no **nlserver** processes.

### Step 4 - Restore the databases in the target environment (dev) {#step-4---restore-the-databases-in-the-target-environment--dev-}

To restore the source databases in the target environment, use the following command:

```
psql mydatabase < mydatabase.sql
```

### Step 5 - Cauterize the target environment (dev) {#step-5---cauterize-the-target-environment--dev-}

To avoid malfunctions, the processes linked to delivery sending and workflow execution must not be automatically executed when the target environment is activated.

To do this, run the following command:

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### Step 6 - Check cauterization {#step-6---check-cauterization}

1. Check that the only deliverypart is the one whose ID is set to 0:

   ```
   SELECT * FROM neolane.nmsdeliverypart;
   ```

1. Check that the delivery status update is correct:

   ```
   SELECT iState, count(*) FROM neolane.nmsdelivery GROUP BY iState;
   ```

1. Check that the workflow status update is correct:

   ```
   SELECT iState, count(*) FROM neolane.xtkworkflow GROUP BY iState;
   SELECT iStatus, count(*) FROM neolane.xtkworkflow GROUP BY iStatus;
   ```

### Step 7 - Restart the target environment Web process (dev) {#step-7---restart-the-target-environment-web-process--dev-}

On the target environment, re-start the Adobe Campaign processes for all servers.

>[!NOTE]
>
>Before re-starting Adobe Campaign on the **dev** environment, you can apply an additional safety procedure: start the **web** module only.
>  
>To do this, edit your instance's configuration file (**config-dev.xml**), then add the "_" character before the autoStart="true" options for each module (mta, stat, etc.).

Run the following command to start the Web process:

```
nlserver start web
```

Use the following command to check that only the web process has started:

```
nlserver pdump
```

Check that access to the client console functions.

### Step 8 - Import options and external accounts into the target environment (dev) {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!IMPORTANT]
>
>Only the web process should be started at this step. If this is not the case, stop other running processes before continuing

Above all, check the values of several lines of the files before importing (for example: 'NmsTracking_Pointer' for the options table and the delivery or mid-sourcing accounts for the external account table)

To import the configuration from the target environment database (dev):

1. Open the admin console of the database and purge the external accounts (table nms:extAccount) whose ID is not 0 (@id <> 0).
1. In the Adobe Campaign console, import the options_dev.xml package previously created via the import package functionality.

   Check that the options have indeed been updated in the **[!UICONTROL Administration > Platform > Options]** node.

1. In the Adobe Campaign console, import the extaccount_dev.xml previously created via the import package functionality

   Check that external databases have indeed been imported in the **[!UICONTROL Administration > Platform > External accounts]** .

### Step 9 - Restart all processes and change users (dev) {#step-9---restart-all-processes-and-change-users--dev-}

To start the Adobe Campaign processes, use the following commands:

* In Windows:

  ```
  net start nlserver6
  ```

* In Linux:

  ```
  /etc/init.d/nlserver6 start
  ```

Use the following command to check that the processes are started:

```
nlserver pdump
```

Change users to find the users that already existed on the dev platform.
