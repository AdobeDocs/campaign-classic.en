---
product: campaign
title: AND-join
description: AND-join
feature: Workflows
hide: true
exl-id: 8b6d5c03-e104-4cf0-82ab-a08467e3e478
TQID: https://experienceleague.adobe.com/L6SmrK6xHkRqZI69OepbB4drLPfrX-cmvi6h6su3LYk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: Workflow HeatMap (Campaign)
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities (Campaign)
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities (Campaign)
---
# AND-join{#and-join}



A join triggers its outbound transition only when all inbound transitions are activated, i.e. when all prior activities are finished. This allows you to make sure that certain activities have finished before continuing to execute the workflow.

For example, you can use an AND-join activity in the context of content creation and delivery sending automation, to make sure that a delivery is started only once target querying and content updates steps are complete. A dedicated use case is available in [this section](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)

![](assets/and-join-usage.png)

>[!NOTE]
>
>Note that inbound transitions that are configured with different targeting dimensions cannot be joined together using an **[!UICONTROL AND-join]** activity.

The outbound sent population of the activity is determined by choosing a main set among the inbound transitions in the activity.

The outbound transition can only contain one of the inbound transition populations. If the activity is not configured, the outbound transition will randomly select one of the inbound populations.

>[!CAUTION]
>
>In the case of **AND-join** type activities, the event variables are merged but if a same variable is defined twice, there is a conflict and the value remains undetermined. For more on this, refer to [this section](javascript-scripts-and-templates.md#event-variables).
