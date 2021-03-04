---
solution: Campaign Classic
product: campaign
title: Get started with build upgrades
description: Learn key steps to upgrade to a new build
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
---

# Performing a build upgrade{#performing-a-build-upgrade}

This section will provide you with an in-depth walkthrough on the upgrade process and the steps to identify and resolve conflicts.

The build upgrade must be carried out with caution, its impacts must be fully considered beforehand and the procedure must be completed with a high level of discipline. To ensure a successful upgrade, ensure that only expert users perform the steps outlined below. In addition, we strongly recommend getting in touch with [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) before starting any upgrade.

The following prerequisites are needed:

* Understanding of the Campaign Architecture
* Systems and server side knowledge
* Administrative rights and permissions

You can find more information in these sections: [Updating Adobe Campaign](../../production/using/upgrading.md), [Migrating to a new version](../../migration/using/about-migration.md).

For hosted and hybrid instances, you must request the build upgrade to Adobe Technical Operations team. For more on this, refer to the Frequently Asked Questions section at the bottom if this page. Also consult the [build upgrade FAQ](../../platform/using/faq-build-upgrade.md).

## Prepare the upgrade

![](assets/do-not-localize/icon_planification.png)

Before starting the build upgrade, you must perform a full preparation as described below.
Once the system is ready to be upgraded, a build upgrade takes **at least** 2 hours.

The build upgrade process requires the following resources:

* an Adobe architect - to understand the database structures (out-of-the-box schemas and any additional schemas that have been added, campaign designs, and any critical path functionality that must be started and tested in a specific order).
* a project manager - In the case where the build upgrade involves many different instances (production, staging, testing) and other third party servers and applications (databases, SFTP sites, messaging service providers), having a project manager to coordinate all of the testing is considered a best practice.
* an Adobe Campaign administrator - your administrator knows the server's configuration including but not limited to: security, folder layout, reporting, and import\export requirements. Please do not perform a build upgrade without your administrator.
* an Adobe Campaign operator (marketing user) - a successful upgrade relies upon the user's ability to perform their daily tasks successfully. For this reason, always include at least one of your daily operators in your testing of the upgraded servers.

### Planning

Here are the key points on how to plan a build upgrade:

1. Reserve at least 2 hours for the upgrade.
1. Distribute contact details for Adobe and customer staff.
1. For hosted instances: Adobe and customer staff will coordinate the time for the upgrade and who will execute.
1. For on-premise instances: customer staff manages the entire process - if assistance in testing of customized workflows and delivery logic is needed, consulting services should be brought in.
1. Determine and confirm which version of Adobe Campaign you want to upgrade to - consult the [Adobe Campaign Classic release notes](../../rn/using/rn-overview.md).
1. Confirm possession of upgrade executables.

### Key people

The build upgrade process requires the following people to be involved:

* Adobe architect: for hosted or hybrid architectures, the architect must coordinate with Adobe Campaign Client Care.

* Project manager: 
    * for On Premise installations: the customer's internal Project Leader leads the upgrade and manages lifecycle tests.

    * for Hosted installation: the hosting team will partner with the Adobe Campaign Client Care team and the customer to coordinate the upgrade timeline for all instances.

* Adobe Campaign Administrator:
    * for On Premise installations: the administrator performs the upgrade.

    * for Hosted installations: the hosting team performs the upgrade.

* Adobe Campaign operator\marketing user: the operator runs tests on development, test and production instances.

### Prepare the build upgrade

Before starting the build upgrade, on-premise customers need to perform the following preparation:

1. Ensure any development work can be exported before the upgrade, export as packages.

1. Perform a full backup of the databases for all instances of the source and target environments. 

1. Get the latest version of your [server configuration file](../../installation/using/the-server-configuration-file.md).

1. [Download the latest build](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html). [Learn more](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html).

You also need to know all the [useful command lines](../../installation/using/command-lines.md) before starting a build upgrade:

* **nlserver pdump**: lists running processes
* **nlserver pdump -who**: lists active client sessions
* **nlserver monitor -missing**: lists missing properties
* **nlserver start process@instanceName**: starts a process
* **nlserver stop process@instanceName**: stops a process
* **nlserver restart process@instanceName**: restarts a process
* **nlserver shutdown**: stops all Campaign processes
* **nlserver watchdog -svc**: starts the watchdog (UNIX only)

## Perform the upgrade

![](assets/do-not-localize/icon_process.png)

Procedures below are only performed by **on-premise** customers. For hosted customers, it is taken care by the hosting team. To update Adobe Campaign to a new build, the detailed procedure is described below.

### Duplicate the environment

Here is how you duplicate an Adobe Campaign environment, in order to restore a source environment to a target environment, resulting in two identical work environments. 

To do this, follow the steps below:

1. Create a copy of the databases on all instances in the source environment.

1. Restore these copies on all instances of the target environment.

1. Run the **nms:freezeInstance.js** cauterization script on the target environment before starting it up. This will stop all processes interacting with the outside: logs, tracking, deliveries, campaign workflows, etc.

    ```
    nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
    ```

1. Check cauterization, as follows:

    * Check that the only delivery part is the one which ID is set to **0**:

      ```
      SELECT * FROM neolane.nmsdeliverypart;
      ```

    * Check that the delivery status update is correct:

      ```
      SELECT iSate, count(*) FROM neolane.nmsdeliveryGroup By iProd;
      ```
    
    * Check that the workflow status update is correct:

      ```
      SELECT iState, count (*) FROM neolane.xtkworkflowGROUP BY iState;
      SELECT iStatus, count (*) FROM neolane.xtkworkflowGROUP BY iStatus;
      ```
    
### Shut down services

In order to replace all files with the new version, it is required that all instances of the nlserverservice are shut down.

1. Shut down the following services:

    * Web services (IIS): **iisreset /stop**
    * Adobe Campaign service: **net stop nlserver6**

    >[!NOTE]
    >
    >Make sure that the redirection server (webmdl) is stopped, so that the nlsrvmod.dll file used by IIS can be replaced with the new version.
    >

1. Validate that no tasks are active by running the **nlserver pdump** command. If there are no tasks, then the output should resemble the following:

    ```
    C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
    ```

1. Check the Windows Task Manager to confirm that all processes have stopped.

### Upgrade the Adobe Campaign Server Application

1. Run the **Setup.exe** file. If you need to download this file, access [the Download center](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html).

1. Select the installation mode: **Update** or **Repair**.

1. Click **Next**.

1. Click **Finish**: the installation program copies the new files.

1. Once the operation is complete, click **Finish**.

### Synchronize resources

1. Open up the command line.

1. Run **nlserver config -postupgrade -allinstances** to perform the following:

    * Synchronize resources
    * Update schemas
    * Update the database

    >[!NOTE]
    >
    >This operation should only be performed once and only on an nlserverweb application server.
    >

    To synchronize only one database, run the following command:

    ```
    nlserver config -postupgrade -instance: <instance_name>
    ```

1. Check if the synchronization has generated any errors or warnings.

### Restart services

The following services need to be restarted:

* Web services (IIS): **issreset /start**
* Adobe Campaign service: **net start nlserver6**

### Client consoles update

The client console must be on the same build as the server instance.

On the machine where the Adobe Campaign application server is installed (nlserverweb), download and copy the file:

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

The next time client consoles are connected, a window will inform users about the availability of a new update and offer them the possibility of downloading and installing it.

### Specific additional tasks

Some configurations require specific additional tasks to update to a new build.

#### Transactional messaging

When Transactional Messaging (Message Center) is enabled on your Campaign instance, you need to perform these additional steps to upgrade:

1. Update the Message Center production server to the chosen version.
1. Run the postupgrade scripts.
1. Run tests and ensure that the emails are successfully received through the Message Center production instance.
1. Upgrade clients and clear cache.
1. Export packages:
    * Export packages using the client package export tool
    * Import schema package
    * Disconnect and reconnect client
    * Update database
    * Disconnect and reconnect
    * Import Admin package
    * Import Content package
    * Import Content Management package
    * Disconnect and reconnect
    * Perform a quick sanity check of workflows

1. Publish Message Center templates to ensure that the interface between servers and Message Center instance is working.
1. Run tests to ensure that emails are successfully received through the Message Center production instance.
1. Run workflow tests in production to ensure that deliveries are received.

#### Mid-sourcing

In the context of a mid-sourcing environment, you need to perform these additional steps to upgrade:

1. Contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) to coordinate the upgrade of the Mid-Sourcing server. 
1. Validate that the version has been updated by running a test link. For example: 

    ```
    http://[InsertServerURL]/r/test
    ```

>[!NOTE]
>
>The Mid-Sourcing server must always run the same version (or more recent) as for the marketing servers.
>

## In case of conflicts

### Identify conflicts

You need to check the synchronization result. This procedure is only performed by on-premise customers. For hosted customers, it is taken care by the hosting team. There are two ways to view the synchronization result:

In the command-line interface, errors are materialized by a triple chevron '>>>' and synchronization is stopped automatically. Warnings are materialized by a double chevron '>>' and must be resolved once synchronization is complete. At the end of the postupgrade, a summary is displayed in the command prompt. It can look like this:

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

If the warning concerns a conflict of resources, user attention is required to resolve it.

The **postupgrade_ServerVersionNumber_TimeOfPostupgrade.log** file contains the synchronization result. It is available by default in the following directory: **installationDirectory/var/instanceName/postupgrade**. Errors and warnings are indicated by the error and warning attributes.

### Analyze conflicts

**How is a conflict found?**

Conflicts can be found within the postupgrade.log on the server in question or within the Campaign client interface (Administration > Configuration > Package management > Edit conflicts).

The document with identifier ‘stockOverview’ and type ‘nms:webApp’ is in conflict with the new version. 

If a conflict is found, check if the following conditions match:

* Has the object been modified or customized by the customer?
* Has the object changed in the product?

If neither of these conditions apply, this is a false positive. If both these conditions apply, a real conflict has been found.

**Has the object been modified by the customer?**

1. Identify the conflicting object.
1. Ask the customer if they modified the object.
1. Is there anything unusual with the object?
1. Is the last modified date set in the object's code?
1. Examine the XML code from the conflict for “_conflict” attributes. Does it look like a customization?

**Has the object been changed in the new build?**

1. Any "usual suspects?" Built-in web applications or reports (ex: 'deliveryValidation', 'deliveryOverview', 'budget').
1. Examine the change logs for any updates.
1. Ask Adobe Campaign experts.
1. Perform a "diff" on the code.

### Resolve a conflict

To resolve conflicts, apply the following process:

1. In the Adobe Campaign explorer, go to **Administration > Configuration > Package management > Edit conflicts**.

1. Select the conflict you want to resolve in the list.
There are three options to resolve conflicts: **Accept the new version**, **Keep the current version**, **Merge the code (and declare as resolved)**, **Ignore the conflict (not recommended)**.

**When can I accept the new version?** 

* If you want the standard features.
* If you don’t have customizations (all customizations will be removed)

**When can I keep the current version?**

* If you have customizations
* If you don't want to merge
* If you don't need any fixes on the conflicting object from the upgrade

**When to perform a merge?**

* Only forms, reports and web applications can be merged.
* Some minor merges can be resolved without understanding the code.
* More complex merges should be performed by someone with the appropriate skills and ability.
* See [Perform a merge](#perform-a-merge).

**What if I ignore the conflicts?**

* The conflict will remain
* The object will not be upgraded
* Long term impacts: version incompatibilities, the customer will not benefit from bug fixes.

>[!IMPORTANT]
>It is highly recommended to resolve conflicts.
>

### Perform a merge{#perform-a-merge}

There are different types of merges:

1. Easy merge: custom and new elements are small and unrelated, and there is no coding required.
1. No changes: accept new version, only last update date changed, only comments, tabs, spaces or new lines. Example: accidental save.
1. Trivial changes: only one line changed. Example: xpathToLoad
1. Complex merge: when coding is required. Development skills are required. See [Complex merges](#complex-merges).

#### How to merge?

1. Get all three versions: the original version, the new version and the custom version.
1. Run a "diff" between the original and new versions.
1. Isolate the changes.
1. If no changes, resolve by keeping current version.

#### Where to find the code?

1. Built-in code is stored in XML files in the datakit folder. Find the XML file that matches the conflicting object. Example: installationDirectory\datakit\nms\fra\form\recipient.xml
1. Retrieve the original version: via the [Download center](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) or another non-upgraded installation of the product.
1. Retrieve the new version: via the [Download center](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) or the customer's installed files.
1. Retrieve the custom version: retrieve the object's source code from within the Campaign client.

### How to make a diff?

1. Install a text or merge editor, for example Notepad ++, AraxisMerge, WinMerge.
1. Open the original file and the new file in the editor.
1. Run the diff (compare the two files).
1. Identify any differences.

### How to merge?

1. Start from the custom version.
1. Apply the changes.
1. Resolve the conflict by declaring it as resolved.
1. Check for non-regressions.

If you choose to resolve the conflict manually, proceed as follows:

1. In the lower section of the window, search for the **_conflict_string_** to locate the entities with conflicts. The entity installed with the new version contains the new argument, the entity that matches the previous version contains the custom argument.
1. Delete the version you don't want to keep. Delete the **_conflict_argument_** string of the entity you are keeping.
1. Go to the conflict you have resolved. Click the **Actions** icon and select **Declare as resolved**.
1. Save your changes: the conflict is now resolved.

#### Complex merges{#complex-merges}

1. Understand what the change does: reverse-engineer the changes, examine the change logs, follow up with Adobe Campaign experts.
1. Decide what to do with the change.
1. Understand what the customizations do: reverse-engineer the changes

Here are the steps to perform a complex merge:

1. Copy bits of code from the change set
1. Paste to the customized version
1. Test for non-regressions of customization
1. Test for function of changes
1. Perform User Acceptance Testing
1. Perform in test environment


>[!IMPORTANT]
>Development skills are required to perform complex merges.
>

**Related topics**

* [Build upgrade FAQ](../../platform/using/faq-build-upgrade.md)
* [Campaign Classic Release Notes](../../rn/using/rn-overview.md)
* [Help and Support options for Campaign Classic](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support-req)
* [Gold Standard program](https://helpx.adobe.com/campaign/kb/gold-standard.html)