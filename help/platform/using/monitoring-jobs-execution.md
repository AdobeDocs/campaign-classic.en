---
solution: Campaign Classic
product: campaign
title: Generic imports and exports
description: Generic imports and exports
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
---

# Execution tracking {#execution-tracking}

You can view the tracking of the execution in the upper section of this editor. You can close the export wizard and view the execution of the job via the list of import/export jobs.

![](assets/s_ncs_user_export_list_and_details.png)

* The **[!UICONTROL Log]** tab lets you look at log messages concerning execution.
* The **[!UICONTROL Rejects]** tab contains the rejected records. See [Behavior in the event of an error](../../platform/using/importing-data.md#behavior-in-the-event-of-an-error).

>[!NOTE]
>
>Import/export job statuses are presented in [Job statuses](../../platform/using/importing-data.md#job-statuses).





## Job statuses {#job-statuses}

Job status indicates the current status of a job. Each status is represented by a special icon and label. This information is displayed in the list of jobs. The statuses and their icons are listed below:

![](assets/s_ncs_user_export_status.png)

* **Editing in progress**

  Job is being created.

* **Execution in progress**

  The job is being executed.

* **Cancel**

  Click the **[!UICONTROL Cancel]** button: the job in progress is cancelled.

* **Cancellation in progress**

  The cancellation command has been taken into account and the job is being cancelled.

* **Pause in progress**

  Click **[!UICONTROL Pause]**: the job is being suspended.

* **Paused**

  Click **[!UICONTROL Pause]**: the job is suspended. It can be restarted by clicking **[!UICONTROL Start]**.

* **Finished**

  Execution of the job is finished.

* **Finished with error**

  The job was not executed because of a technical error.

* **Server shutdown in progress**

  The job in progress is interrupted because the Adobe Campaign server has shut down.


## Importing data from a workflow {#importing-data-from-a-workflow}

Workflows can be a useful way to automate some of your import processes. Whether you import data from a local file or from a SFTP, you can use workflows to standardize your data management procedures.

To learn more about importing data from a workflow, refer to [this section](../../workflow/using/importing-data.md).




