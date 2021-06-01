---
product: campaign
title: Manage workflow permissions
description: Learn how to manage workflow permissions
audience: workflow
content-type: reference
topic-tags: advanced-management
exl-id: 88995fb3-d336-4355-acd4-33118dd0e2b0
---
# Manage workflow permissions{#managing-rights}

If they are not Administrators, Adobe Campaign operators need access rights for creating, executing or modifying workflows.

Generally speaking, operators acting on workflows need to access the files containing the data used during the various activities (recipients, recipient list, subscriptions, deliveries, etc.), and possibly their sub-files.

They must also be mapped to the named rights that coincide with the actions performed by workflows which they will affect (recipient import, file access, fusion, SQL script execution, etc.).

For more on managing operators and permissions, refer to this [section](../../platform/using/access-management.md).

## Operator groups {#operator-groups-wf}

The following operator groups are associated to the workflow:

* The **[!UICONTROL Workflow execution]** group lets you control the execution and approval of targeting workflows: the WORKFLOW named right is mapped to this group's operators. It is required for all actions on workflows, in addition to access rights to the data files. By default, the **[!UICONTROL Workflow execution]** group has read-only access to standard targeting workflow files and workflow templates. Operators in this group also have read and write access to the pending approvals file.
* The **[!UICONTROL Workflow supervisors]** group lets operators manage workflow approvals.
* The **[!UICONTROL Operation Managers]** group to access campaign workflows.

## Named rights {#named-rights}

Only the WORKFLOW named right is specific to workflows: it lets you create, start and stop workflows. Reading rights on the workflow file are required for the named right to be applicable. For targeting workflows, the reading right on the **[!UICONTROL Profiles and Targets]** file is necessary.

## Workflow execution account {#workflow-execution-account}

You can configure the execution account to be used at the workflow template level. The execution account lets you map authorizations to the workflow directly, irrespective of the Adobe Campaign operator starting the execution. By default, every workflow is executed with the rights of the operator who started it.

To map an execution account to a workflow, go to the list of workflow templates and right-click on the template linked to the workflow. Choose **[!UICONTROL Action > Change execution account...]** then select the account to be used.
