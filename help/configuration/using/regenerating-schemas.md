---
product: campaign
title: Regenerate schemas
description: Learn how to regenerate Campaign schemas
feature: Custom Resources
role: Developer
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
TQID: https://experienceleague.adobe.com/gkWtbp4Vw-wY5yHsd4xJbDx04u3aPhdg-8kB5OXZu94
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
---
# Regenerate schemas{#regenerating-schemas}

When you modify a schema and save the modifications, extended schema is automatically generated. Nevertheless, you may need to regenerate schemas manually to apply modifications. To do this:

1. Select the schema(s) you need to regenerate.
1. Right click and choose **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Click **[!UICONTROL OK]** to confirm and launch the process.

You can then check the structure of the generated schema in the Preview and Documentation tabs. For more on this, refer to the [Principles](../../configuration/using/data-schemas.md#principles) section.

>[!NOTE]
>
>If you need to force regeneration of all schema, for example to solve certain dependency problems in the reverse links, you can launch the following command from the Adobe Campaign application server:
>
> `nlserver config -postupgrade -instance:`<instance_name>` -force`
>
>You must then restart the Adobe Campaign application server and disconnect/reconnect to the client console.
