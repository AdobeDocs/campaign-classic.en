---
product: campaign
title: Monitor your deliveries in Campaign UI
description: Learn how to access the list of deliveries and use the delivery dashboard to monitor your deliveries
feature: Monitoring
role: User, Developer
exl-id: 44ecc8c6-6584-43eb-96b4-7d8463053123
---
# Monitor your deliveries in Campaign UI {#delivery-dashboard}

>[!NOTE]
>
>Comprehensive guidance on accessing the delivery list and using the delivery dashboard is documented in the [Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard). This content applies to both Campaign Classic v7 and Campaign v8 users.
>
>This page documents **Campaign Classic v7-specific customizations** for hybrid and on-premise deployments.

Monitoring your deliveries is essential to ensure your campaigns are efficient and reach your customers. 

For comprehensive information on accessing the delivery list, using the delivery dashboard tabs, and monitoring your deliveries, refer to the [Campaign v8 Monitor deliveries in Campaign UI documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}.

## Customize delivery logs {#use-case}

For **Campaign Classic v7 hybrid/on-premise deployments**, you can customize delivery logs by extending schemas. This section shows how to add senders' IP addresses to the delivery logs.

>[!NOTE]
>
>This customization requires schema extension capabilities available in on-premise deployments. Campaign v8 Managed Cloud Services users should contact Adobe Customer Care for custom delivery log fields.
>
>This modification is different if you are using a single instance or mid-sourcing instance. Before doing the modification, ensure you're connected to email sending instance.

### Step 1: Extend the schema

To add **publicID** in your delivery logs you need to extend the schema first. You can proceed as follow.

1. Create a schema extension, under **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data Schemas]** > **[!UICONTROL New]**.

    For more information about schema extensions, refer to [this page](../../configuration/using/extending-a-schema.md).

1. Select **[!UICONTROL broadLogRcp]** to extend the Recipient delivery logs (nms) and define a custom Namespace. In this case it will be "cus":

    ![](assets/schema-parameters.png)

    >[!NOTE]
    >
    >If your instance is in Mid-sourcing, you need to work with broadLogMid schema.

1. Add the new field in your extension. In this sample, you need to replace:

    ```
    <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp"/>
    ```

    by:

    ```
    <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp">
    <attribute desc="Outbound IP identifier" label="IP identifier"
    name="publicId" type="long"/>
    </element>
    ```

    ![](assets/edit-schema.png)

### Step 2: Update database structure

Once modifications are done, you need to update database structure so that it is aligned with its logical description.

To do this, follow the steps below:

1. Click the **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Update database structure...]** menu.

    ![](assets/update-database-structure.png)

1. In the **[!UICONTROL Edit tables]** window, the **[!UICONTROL NmsBroadLogRcp]** table is checked (or the **[!UICONTROL broadLogMid]** table if your are in a Mid-sourcing environment), as below:

    ![](assets/edit-tables.png)

    >[!IMPORTANT]
    >
    >Always ensure there is no other modification, except the **[!UICONTROL NmsBroadLoGRcp]** table (or the **[!UICONTROL broadLogMid]** table if your are in a Mid-sourcing environment). If so, uncheck other tables.

1. Click **[!UICONTROL Next]** to validate. The following screen displays:

    ![](assets/update-script.png)

1. Click **[!UICONTROL Next]**, then **[!UICONTROL Start]** to start updating database structure. Index building is starting. This step can be long, depending on the number of rows in the **[!UICONTROL NmsBroadLogRcp]** table.

    ![](assets/start-database-update.png)

  >[!NOTE]
  >
  >Once the update of the physical structure of the database is successfully completed, you need to disconnect and reconnect so that your modifications are taken into account.

### Step 3: Validate the modification

To confirm everything worked correctly, you need to update delivery logs screen.

To do this, access the delivery logs and add the "IP identifier" column.

![](assets/list-config.png)

>[!NOTE]
>
>To learn how to configure lists in Campaign Classic interface, refer to [this page](../../platform/using/adobe-campaign-workspace.md).

Below is what you should see in the **[!UICONTROL Delivery]** tab after modifications:

![](assets/logs-with-ip.png)

## Related topics

* [Monitor deliveries in Campaign UI](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (Campaign v8 documentation)
* [Delivery statuses](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (Campaign v8 documentation)
* [Understanding delivery failures](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (Campaign v8 documentation - comprehensive guide for both v7 and v8)
* [Quarantine management](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (Campaign v8 documentation - comprehensive guide for both v7 and v8)
* [Bounce mail configuration](understanding-delivery-failures.md) (v7 hybrid/on-premise)
* [Quarantine configuration](understanding-quarantine-management.md) (v7 hybrid/on-premise)
