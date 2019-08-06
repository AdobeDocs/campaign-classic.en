---
title: Workflow execution
seo-title: Workflow execution
description: Workflow execution
seo-description: 
page-status-flag: never-activated
uuid: 21ec9ede-1250-437f-9de7-8cfb7d856dee
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 22082f7b-2b17-42d3-9b44-cc17f2c4ede8
index: y
internal: n
snippet: y
---

# Workflow execution{#workflow-execution}

Workflow execution cycle and best practices are presented in [this section](../../workflow/using/executing-a-workflow.md).

## Start in progress {#start-in-progress}

If workflows aren't executing and their status is **Start in progress**, this might mean that the workflow module isn't launched.

To check this and to start the module if necessary, apply the following steps:

1. Check that your **wfserver@ `<instance>`** modules are launched on your main application server.

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
   >Replace ** `<instancename>`** with the name of your instance (production, development, etc.). The instance name is identified via the configuration files:   
   >[path of application]nl6/conf/config- `<instancename>  .xml </instancename>`

## Failed workflow {#failed-workflow}

If a workflow fails, take the following steps:

1. Check the workflow journal. For more on this, refer to the [Monitoring workflow execution](../../workflow/using/executing-a-workflow.md#monitoring-workflow-execution) and [Display logs](../../workflow/using/executing-a-workflow.md#displaying-logs) sections.
1. Monitor technical workflows. For more on this refer to the [this section](../../workflow/using/executing-a-workflow.md#monitoring-technical-workflows). 
1. Look for failures on the individual workflow activities.

