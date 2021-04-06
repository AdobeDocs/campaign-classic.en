---
solution: Campaign Classic
product: campaign
title: Regenerating schemas
description: Regenerating schemas
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
---
# Regenerating schemas{#regenerating-schemas}

When you modify a schema and save the modifications, extended schema is automatically generated. Nevertheless, you may need to regenerate schemas manually to apply modifications. To do this:

1. Select the schema(s) you need to regenerate.
1. Right click and choose **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Click **[!UICONTROL OK]** to confirm and launch the process.

You can then check the structure of the generated schema in the Previw and Documentation tabs. For more on this, refer to the [Principles](../../configuration/using/data-schemas.md#principles) section.

>[!NOTE]
>
>If you need to force regeneration of all schema, for example to solve certain dependency problems in the reverse links, you can launch the following command from the Adobe Campaign application server:
>
>**nlserver config -postupgrade -instance:`<instance_name>' -force**
>
>You must then restart the Adobe Campaign application server and disconnect/reconnect to the client console.
