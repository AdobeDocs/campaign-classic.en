---
product: campaign
title: Monitoring jobs execution
description: Learn how to monitor import and export jobs execution
feature: Monitoring
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 415c5137-2eb0-4581-a46e-26e8e3d264fa
TQID: https://experienceleague.adobe.com/g25R2WVJ2ULkITvhyNbvq87lxMdUNaHDJdm9rZNg-PA
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
    internal-label: Profiles and audiences (Campaign)
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
    internal-label: Profiles (Campaign)
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
    internal-label: Audiences (Campaign)
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
    internal-label: Query Editor (Campaign)
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management (Campaign)
---
# Monitor jobs execution {#monitoring-job-execution}

 

You can track the execution of your import and export jobs directly from the list of import/export jobs.

![](assets/s_ncs_user_export_list_and_details.png)

* The **[!UICONTROL Journal]** tab lets you look at log messages concerning execution.
* The **[!UICONTROL Rejects]** tab contains the rejected records. See [this section](../../platform/using/executing-import-jobs.md#behavior-in-the-event-of-an-error).

In the **[!UICONTROL General]** tab, the **[!UICONTROL Status]** field indicates the current status of a job.

Each status is represented by a special icon and label. The statuses and their icons are listed below:

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
