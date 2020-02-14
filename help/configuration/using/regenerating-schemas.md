---
title: Regenerating schemas
seo-title: Regenerating schemas
description: Regenerating schemas
seo-description: 
page-status-flag: never-activated
uuid: 455c37f1-cbaf-4503-b2e9-5eec7fad6e97
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 0f7c835e-b429-422b-87ae-1234c7dd8fe6
index: y
internal: n
snippet: y
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
