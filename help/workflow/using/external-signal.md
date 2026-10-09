---
product: campaign
title: External signal
description: Learn more about the External signal workflow activity
feature: Workflows
hide: true
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
TQID: 'https://experienceleague.adobe.com/2fWd7-VtAc2x-MQm-o5rpGmDsrn6rszSfZxjVDzleTw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
---
# External signal{#external-signal}



The **External signal** activity lets you trigger execution of a set of tasks in a workflow to a schedule.

When an 'External signal' task is activated, it is paused indefinitely or until the end of the specified time period. Its transition is activated by the SOAP call **PostEvent(sessionToken, workflowId, activity, transition, parameters, complete).** The **[!UICONTROL complete]** parameter allows the task to be finished, so it will not react to subsequent calls.

Refer to the online documentation concerning SOAP calls for further information on the PostEvent function.

You can configure this activity in order to define events if no signal is received. To do this, edit the activity and click the **[!UICONTROL Expiration]** tab. Click the **[!UICONTROL Insert]** button to create and configure an event.

![](assets/edit_signal.png)

The configuration of expirations is detailed in [Expirations](defining-approvals.md).

The **Delay** field lets you specify an expiration delay in the units of your choice. See [Wait](wait.md).

Each line represents a type of expiration and coincides with a transition.

![](assets/external_sign_diag.png)
