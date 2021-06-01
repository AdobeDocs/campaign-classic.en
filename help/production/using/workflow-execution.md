---
product: campaign
title: Workflow execution
description: Workflow execution
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
---
# Workflow execution{#workflow-execution}

The section below presents information on common issues related to workflows execution and how to troubleshoot them.

For more information on workflows, refer to these sections:

* [About workflows](../../workflow/using/about-workflows.md)
* [Starting a workflow](../../workflow/using/starting-a-workflow.md)
* [Workflow life cycle](../../workflow/using/workflow-life-cycle.md)
* [Best practices when using workflows](../../workflow/using/workflow-best-practices.md)

## Start as soon as possible in campaigns {#start-as-soon-as-possible-in-campaigns}

In some cases, workflows executed from a campaign do not start when clicking the **[!UICONTROL Start]** button. Instead of starting, it goes to a "Start as soon as Possible" state.

There can be several causes for this issue, follow the steps below to solve it:

1. Check the [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md) technical workflow status. This workflow manages jobs or workflows inside a campaign. If it fails, this will result in workflows to not start / stop. Restart it to resume the running of campaign workflows.

    For more on technical workflows monitoring, refer to [this page](../../workflow/using/monitoring-technical-workflows.md).

    >[!NOTE]
    >
    >Once the workflow restarted, make sure you execute the pending tasks (right-click the **[!UICONTROL Scheduler]** activity / **[!UICONTROL Execute pending task(s) now]**) in order to check if it fails again on any of the activities.

    If the workflow still fails, check the audit log for specific error, troubleshoot accordingly, then restart the workflow again.

1. Check the **[!UICONTROL wfserver]** module state in the **[!UICONTROL Monitoring]** tab, accessible from Campaign Classic homepage (see [Monitoring processes](../../production/using/monitoring-processes.md)). This process is responsible for running all workflows.

    An admin user can also check that the **wfserver@`<instance>`** module is launched on your main application server using the command below.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

    If the module is not running, contact Adobe Customer Care. If you have an on-premise installation, an admin user must restart the service using the command below.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Replace **`<instancename>`** with the name of your instance (production, development, etc.). The instance name is identified via the configuration files:
   >`[path of application]nl6/conf/config-<instancename>.xml`

    For more on how to restart modules, refer to [this section](../../production/using/usual-commands.md#module-launch-commands).

1. Check if the **number of campaign processes running** on the instance is more than the threshold. There is a limit defined by the [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) option on how many campaign processes can run on the instance in parallel. When this limit is reached, the workflow stays in the "Start as soon as possible" state as long as the number of workflows running is above the limit.

    To solve this issue, stop unwanted workflows and delete failed deliveries. If the threshold was reached, this will allow the running of new processes.

    To check the number of workflows running of your instance, we recommend using the predefined views, accessible by default in the **[!UICONTROL Administration]** / **[!UICONTROL Audit]** folder. For more information, refer to [this page](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

    >[!IMPORTANT]
    >
    >Increasing the **[!UICONTROL NmsOperation_LimitConcurrency]** option threshold may lead to performance issues on your instance. In any case, do not perform this on your own and reach out to your Adobe Campaign contact.

For more on how to monitor you workflows, refer to [this section](../../workflow/using/monitoring-workflow-execution.md).

## Start in progress {#start-in-progress}

If workflows aren't executing and their status is **Start in progress**, this might mean that the workflow module isn't launched.

To check this and to start the module if necessary, apply the following steps:

1. Check the **[!UICONTROL wfserver]** module state in the **[!UICONTROL Monitoring]** tab, accessible from Campaign Classic homepage (see [Monitoring processes](../../production/using/monitoring-processes.md)).
    
    An admin user can also check that the **wfserver@`<instance>`** module is launched on your main application server using the command below.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

    For more on how to monitor modules, refer to [this section](../../production/using/usual-commands.md#monitoring-commands-).

1. If the module is not running, contact Adobe Customer Care. If you have an on-premise installation, an admin must restart it using the command below.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Replace **`<instancename>`** with the name of your instance (production, development, etc.). The instance name is identified via the configuration files:
   >`[path of application]nl6/conf/config-<instancename>.xml`

    For more on how to restart modules, refer to [this section](../../production/using/usual-commands.md#module-launch-commands).

## Failed workflow {#failed-workflow}

If a workflow fails, take the following steps:

1. Check the workflow journal. For more on this, refer to the [Monitoring workflow execution](../../workflow/using/monitoring-workflow-execution.md) and [Display logs](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) sections.
1. Monitor technical workflows. For more on this refer to the [this section](../../workflow/using/monitoring-technical-workflows.md).
1. Look for failures on the individual workflow activities.
