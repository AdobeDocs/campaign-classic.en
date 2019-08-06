---
title: Regenerating schemas
seo-title: Regenerating schemas
description: Regenerating schemas
seo-description: 
page-status-flag: never-activated
uuid: 6bfc0f5e-70a9-41fb-a991-c0e1a3e66d46
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 9f80c268-d538-4693-a9b9-3ef02b0d8347
index: y
internal: n
snippet: y
---

# Regenerating schemas{#regenerating-schemas}

When you modify a schema and save the modifications, extended schema is automatically generated. Nevertheless, you may need to regenerate schemas manually to apply modifications. To do this:

1. Select the schema(s) you need to regenerate.
1. Right click and choose **Actions > Regenerate selected schemas...**.
1. Click **OK** to confirm and launch the process.

You can then check the structure of the generated schema in the Previw and Documentation tabs. For more on this, refer to the [Principles](../../configuration/using/regenerating-schemas.md#principles) section.

>[!NOTE]
>
>If you need to force regeneration of all schema, for example to solve certain dependency problems in the reverse links, you can launch the following command from the Adobe Campaign application server:   
>**nlserver config -postupgrade -instance:`<instance_name>  -force</instance_name>`** 
>You must then restart the Adobe Campaign application server and disconnect/reconnect to the client console.

