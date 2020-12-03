---
solution: Campaign Classic
product: campaign
title: SQL code and JavaScript code
description: Learn more about SQL and JavaScript codes workflow activities
audience: workflow
content-type: reference
topic-tags: action-activities
---

# SQL code and JavaScript code{#sql-code-and-javascript-code}

## SQL code {#sql-code}

An **[!UICONTROL SQL code]** activity executes an SQL script. The script is a JST template.

   ![](assets/sql_code.png)

* **[!UICONTROL Script]**

  The central area of the editor contains the script to be executed. This script is a JST template and can therefore be configured according to the workflow context.

* **[!UICONTROL Processing errors]**

  Refer to [Processing errors](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## JavaScript code and Advanced JavaScript code {#javascript-code}

**[!UICONTROL JavaScript code]** and **[!UICONTROL Advanced JavaScript code]** activities execute a JavaScript script in the context of a workflow. For more on scripting, refer to the [JavaScript scripts and templates](../../workflow/using/javascript-scripts-and-templates.md) section.

>[!NOTE]
>
>By default, the execution phase of **[!UICONTROL JavaScript code]** and **[!UICONTROL Advanced JavaScript code]** activities cannot exceed 1 hour. After this delay, the process will be aborted with an error message and the activity execution will fail.
>
>You can change this delay in the **[!UICONTROL Stop execution after]** field available in the activities' properties.

* **[!UICONTROL JavaScript code]**

    ![](assets/javascript_code.png)

    * **[!UICONTROL Script]**: The central area of the editor contains the script to be executed.
    * **[!UICONTROL Processing errors]**: Refer to [Processing errors](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

* **[!UICONTROL Advanced JavaScript code]**

   ![](assets/advanced_javascript_code.png)

    * **[!UICONTROL First call]**: The first zone of the editor contains the script to execute during the first call.
    * **[!UICONTROL Next calls]**: The second zone of the editor contains the script to execute during the next calls.
    * **[!UICONTROL Transitions]**: You can define several activity output transitions.
    * **[!UICONTROL Schedule]**: The **[!UICONTROL Schedule]** tab lets you schedule when to trigger the activity.
