---
solution: Campaign Classic
product: campaign
title: Monitoring jobs execution
description: Learn how to monitor import and export jobs execution.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
---

# Monitoring jobs execution {#monitoring-job-execution}

You can view the tracking of the execution in the upper section of this editor. You can close the export wizard and view the execution of the job via the list of import/export jobs.

![](assets/s_ncs_user_export_list_and_details.png)

* The **[!UICONTROL Log]** tab lets you look at log messages concerning execution.
* The **[!UICONTROL Rejects]** tab contains the rejected records. See [Behavior in the event of an error](../../platform/using/launching-import-jobs.md#behavior-in-the-event-of-an-error).

>[!NOTE]
>
>Import/export job statuses are presented in [Job statuses](../../platform/using/monitoring-jobs-execution.md).

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
