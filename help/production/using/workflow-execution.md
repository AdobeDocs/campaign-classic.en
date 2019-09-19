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

Workflow execution cycle and best practices are presented in [this section](../../workflow/using/executing-a-workflow.md).

## Start as soon as possible in campaigns {#start-as-soon-as-possible-in-campaigns}

In some cases, workflows executed from a campaign do not start when clicking the **[!UICONTROL Start]** button. Instead of starting, it goes to a "Start as soon as Possible" state.

This issue is caused when the background process responsible for running them are not working. Manual intervention is usually required to put them back in service.

There can be several causes for this issue:

* The **[!UICONTROL operationMgt]** technical workflow is in a failure state. This workflow manages jobs or workflows inside a campaign. If it fails, this will result in workflows to not start / stop.

* The server module wfserver is not runnning. This process is responsible for running all workflows and if it is not running, none of the workflows run.

* The number of campaign processes running on the instance are more than the threshold. There is a limit defined by the NmsOperation_LimitConcurrency option on how many campaign processes can run on the instance in parallel. When this limit is reached, the workflow stays in the "start as soon as possible" state as long as the number of workflows running is above the concurrency limit. This limit is defined by option .

1. Check the operationMgt technical workflow status. It can found in the Campaign Process folder under  Administration>Production>Technical workflows node. You can restart this workflow if it is failed to resume running of the campaign workflows.

    note: once restarted, we make sure we "execute the pending tasks" on the scheduler to check if it fails again on any of the activities.

    If the workflow fails again, check the audit log for specific error, troubleshoot accordingly, then restart the workflow again.
    Example: You may get a failure like:

    ```
    Campaign jobs workflow (operationmgt) was failed with error:
    25/08/2016 17:34:25 scheduler JavaScript: error while evaluating script 'operationMgt/scheduler'.
    25/08/2016 17:34:25 scheduler No access token found to perform user update.
    25/08/2016 17:34:25 scheduler Starting targeting workflow 'xyz_wkf_engage_4' for campaign '01 - Engage campaign (xyz_engage_campaign)'
    ```

    This means it's trying to start the workflow xyz_wkf_engage_4 but is not able to. In most cases, this workflow is pointing to would be in a finished state and cannot be started. For this, we can do an unconditional stop for the workflow xyz_wkf_engage_4 and then Restart Campaign jobs (operation mgt).

1. Check wether the sever module wfserver is running. This process is responsible for running all workflows and if it is not running, none of the workflows run. If the process is not running contact customer care. In on-premise installation, restart the service.

1. Check if the concurrency limit is reached. TThis can be confirmed by checking the number of workflows running inside a campaign and check the value of NmsOperation_LimitConcurrency under Platform>Options.

    If the threshold is reached, stop unwanted workflows and delete failed deliveries to bring within threshold.

    Increase the concurrency limit if it's a business need or we can explain that the workflow starts as soon as the concurrency threshold is restored.
    + warning: increase not recommended, may lead to performance issues, reach out to your Adobe consultant before proceeding

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

