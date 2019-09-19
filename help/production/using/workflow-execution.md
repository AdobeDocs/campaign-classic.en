---
title: Workflow execution
seo-title: Workflow execution
description: Workflow execution
seo-description: 
page-status-flag: never-activated
uuid: 115256f6-bdf2-4594-885c-e90d02a25b80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 7d8828c5-5776-49ca-b4f7-a4a6aaaa9db1
index: y
internal: n
snippet: y
---

# Workflow execution{#workflow-execution}

Workflow execution cycle is presented in [this section](../../workflow/using/executing-a-workflow.md).
For more on best practices when using workflows, refer to [this section](../../workflow/using/workflow-best-practices.md)

## Start as soon as possible in campaigns {#start-as-soon-as-possible-in-campaigns}

In some cases, workflows executed from a campaign do not start when clicking the **[!UICONTROL Start]** button. Instead of starting, it goes to a "Start as soon as Possible" state.

There can be several causes for this issue, follow the steps below to solve it:

1. Check the [**[!UICONTROL operationMgt]**](../../workflow/using/campaign.md) technical workflow status. This workflow manages jobs or workflows inside a campaign. If it fails, this will result in workflows to not start / stop.

    You can retrieve its status in the **[!UICONTROL Administration]** / **[!UICONTROL Production]** / **[!UICONTROL Technical workflows]** / **[!UICONTROL Campaign process]** node. If the workflow has failed, restart it to resume the running of campaign workflows.

    >[NOTE]
    >
    >Once the workflow restarted, make sure you execute the pending tasks (right-click the **[!UICONTROL Scheduler]** activity / **[!UICONTROL Execute pending task(s) now]**) in order to check if it fails again on any of the activities.

    If the workflow still fails, check the audit log for specific error, troubleshoot accordingly, then restart the workflow again.
    For example, you may get a failure like:

    ```
    Campaign jobs workflow (operationmgt) was failed with error:
    25/08/2016 17:34:25 scheduler JavaScript: error while evaluating script 'operationMgt/scheduler'.
    25/08/2016 17:34:25 scheduler No access token found to perform user update.
    25/08/2016 17:34:25 scheduler Starting targeting workflow 'xyz_wkf_engage_4' for campaign '01 - Engage campaign (xyz_engage_campaign)'
    ```

    This means **[!UICONTROL operationMgt]** is trying to start the workflow "xyz_wkf_engage_4" but is not able to. In most cases, the workflow it is pointing to is in a finished state and cannot be started. In this case, perform an unconditional stop for the workflow "xyz_wkf_engage_4", then restart **[!UICONTROL operationMgt]**.

1. Check the **[!UICONTROL wfserver]** module state in the **[!UICONTROL Monitoring]** tab,accessible from Campaign Classic homepage (see [Monitoring processes](../../production/using/monitoring-campaign-classic/production-procedures/monitoring-processes.html)). This process is responsible for running all workflows. If it is not running, contact Adobe Customer Care. If you have an on-premise installation, restart the service (detailed procedure is described [here](../../production/using/workflow-execution.md#start-in-progress)).

1. Check if the **number of campaign processes running** on the instance is more than the threshold. There is a limit defined by the [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md##campaign-e-workflow-management) option on how many campaign processes can run on the instance in parallel. When this limit is reached, the workflow stays in the "Start as soon as possible" state as long as the number of workflows running is above the limit.

    To solve this issue, stop unwanted workflows and delete failed deliveries. If the threshold was reached, this will allow the running of new processes.

    >[CAUTION]
    >
    >Increasing the **[!UICONTROL NmsOperation_LimitConcurrency]** option threshold may lead to performance issues on your instance. In any case, do not perform this on your own and reach out to your Adobe Campaign consultant.

## Start in progress {#start-in-progress}

If workflows aren't executing and their status is **Start in progress**, this might mean that the workflow module isn't launched.

To check this and to start the module if necessary, apply the following steps:

1. Check that your **wfserver@`<instance>`** modules are launched on your main application server.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

1. If the workflow server is not listed, start it using the following command:

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Replace **`<instancename>`** with the name of your instance (production, development, etc.). The instance name is identified via the configuration files:   
   >`[path of application]nl6/conf/config-<instancename>.xml`

## Failed workflow {#failed-workflow}

If a workflow fails, take the following steps:

1. Check the workflow journal. For more on this, refer to the [Monitoring workflow execution](../../workflow/using/executing-a-workflow.md#monitoring-workflow-execution) and [Display logs](../../workflow/using/executing-a-workflow.md#displaying-logs) sections.
1. Monitor technical workflows. For more on this refer to the [this section](../../workflow/using/executing-a-workflow.md#monitoring-technical-workflows). 
1. Look for failures on the individual workflow activities.

