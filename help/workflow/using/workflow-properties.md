---
title: Workflow properties
seo-title: Workflow properties
description: Workflow properties
seo-description: 
page-status-flag: never-activated
uuid: c0a48b5f-72ee-4c60-8ad8-401294c9c3cc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 39179c98-cef5-47e0-8fa8-07588ff26c96
index: y
internal: n
snippet: y
---

# Workflow properties{#workflow-properties}

## Execution tab {#execution-tab}

The **Execution** tab of the **Properties** window in a workflow is broken down into 3 sections:

![](assets/wf_execution_tab.png)

### Scheduler {#scheduler}

This section is only displayed in campaign workflows.

* **Priority**

  The workflow engine processes the workflows to be executed based on the priority criterion defined in this field. For instance, all workflows with an **Average** priority will be executed before those with a **Low** priority.

* **Schedule execution for a time of low activity**

  This option postpones workflow start to a less busy period. Some workflows can be costly in terms of resources for the database engine. We recommend scheduling execution for a time of low activity (at night for instance). Low activity periods are defined in the **Processes on campaigns** technical workflow.

### Execution {#execution}

* **Default affinity**

  If your installation includes several workflow servers, use this field to choose the machine which the workflow will be executed on. If the value defined in this field doesn't exist on any server, the workflow will remain pending.

  Refer to this [section](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

* **History in days**

  The work tables of the database keep a history of executions (tasks, events, log). Here you can define the number of days to be archived for this workflow: the cleanup process will delete the oldest archives once a day. If the value in this field is zero, the archive will never be deleted.

* **Log SQL queries in the journal**

  This functionality is reserved for advanced users. It concerns workflows that contain targeting activities (query, union, intersection, etc.). When this option is checked, the SQL queries sent to the database during workflow execution are displayed in Adobe Campaign: this means you can analyze them to optimize queries or diagnose issues.

  Queries are displayed in an **SQL logs** tab which is added to the workflow (except campaign workflows) and to the **Properties** activity when the option is enabled. The **Audit** tab also includes SQL queries. 

  ![](assets/wf_tab_log_sql.png)

* **Execute in the engine**

  This option may only be used for de-bugging and never in production. When it is enabled, the workflow takes priority and all other workflows are stopped until this one is finished.

### Error management {#error-management}

* **Troubleshooting**

  This field lets you define the actions to be taken if a workflow task has errors. There are two possible options:

    * **Stop the process**: the workflow is automatically paused. the workflow status changes to **Failed**. Once the issue is solved, restart the workflow using the **Start** or **Restart** buttons.
    * **Ignore**: the status of the task that triggered the error changes to **Failed**, but the workflow keeps the **Started** status. This configuration is relevant for recurring tasks: if the branch includes a scheduler, it will start normally next time the workflow is executed.

* **Consecutive errors**

  This field becomes available when the **Ignore** value is selected in the **In case of errors** field. You can specify the number of errors that can be ignored before the process is stopped. Once this number is reached, the workflow status changes to **Failed**. If the value of this field is 0, the workflow will never be stopped regardless of the number of errors.

* **Template**

  This field lets you select the notification template to be sent to the workflow supervisors when its status changes to **Failed**.

  The concerned operators will be notified by email, if there is an email address in their profile. To define workflow supervisors, go to the **Supervisor(s)** field of the properties (**General** tab).

  ![](assets/wf-properties_select-supervisors.png)

  The **Notification to a workflow supervisor** default template includes a link for accessing the Adobe Campaign console via the Web so that the recipient can work on the issue once they are logged on.

  To create a personalized template, go to **Administration>Campaign management>Technical deliveries and templates**.

