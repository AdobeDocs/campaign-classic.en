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

For more on how to monitor you workflows, refer to [this section](../../workflow/using/monitoring-workflow-execution.md).

## Start in progress {#start-in-progress}

If workflows aren't executing and their status is **Start in progress**, this might mean that the workflow module isn't launched.

To check this and to start the module if necessary, apply the following steps:

1. Check that your **wfserver@`<instance>`** modules are launched on your main application server.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
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

1. Check the workflow journal. For more on this, refer to the [Monitoring workflow execution](../../workflow/using/monitoring-workflow-execution.md) and [Display logs](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) sections.
1. Monitor technical workflows. For more on this refer to the [this section](../../workflow/using/monitoring-technical-workflows.md).p
1. Look for failures on the individual workflow activities.

