---
product: campaign
title: Additional configurations
description: Learn how to set up additional configurations for Transactional messaging in Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 4d25d740-db57-4d18-8cae-2dd49c4a786e
---
# Additional configurations {#mc-additional-configurations}

## Monitor thresholds {#monitoring-thresholds}

You can configure the warning thresholds (orange) and alert thresholds (red) of the indicators that appear in the **Message Center service level** and **Message Center processing time** reports (refer to [Access transactional messaging reports](../../message-center/using/about-transactional-messaging-reports.md)).

To do this, follow the steps below:

1. Open the deployment wizard on the **execution instance**.

1. Go to the **[!UICONTROL Message Center]** page.

1. Use the arrows to change the thresholds.

    ![](assets/messagecenter_monitor_events_001.png)

>[!NOTE]
>
>The number of events pending in queue is displayed in the [System indicators](../../production/using/monitoring-processes.md#system-indicators) section of the Adobe Campaign process monitoring page. For more information on the deployment wizard, refer to [this section](../../installation/using/deploying-an-instance.md#deployment-wizard).

## Purge events {#purging-events}

You can use the [deployment wizard](../../production/using/database-cleanup-workflow.md#deployment-wizard) to configure how long the data is to be stored in the database.

Event purging is carried out automatically by the [Database cleanup workflow](../../production/using/database-cleanup-workflow.md). This workflow purges the events received and stored on the execution instances and events archived on a control instance.

Use the arrows as appropriate to change the purge settings.

Event purge settings on a control instance:

![](assets/messagecenter_delete_events_001.png)

Event purge settings on an execution instance:

![](assets/messagecenter_delete_events_002.png)

For more on the database cleanup workflow, see [this section](../../production/using/database-cleanup-workflow.md).


## Technical workflows {#technical-workflows}

You must ensure that the technical workflows on the control instance and the different execution instances have indeed been created and started before deploying any transactional message templates.

The various technical workflows related to transactional messaging (Message Center) are broken down between the control instance and the execution instance(s).

### Control instance workflows {#control-instance-workflows}

On the control instance, whether you have one or several execution instances registered, you must create one archiving workflow for each **[!UICONTROL Message Center execution instance]** external account. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_002.png)

These workflows can then be accessed from the **Administration > Production > Message Center** folder. Once created, the archiving workflows are automatically started.

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

### Execution instance workflows {#execution-instance-workflows}

On the execution instance(s), the technical workflows for transactional messaging can be accessed from the **Administration > Production > Message Center** folder. You just have to start them. The workflows in the list are:

* **[!UICONTROL Processing batch events]** (internal name: **[!UICONTROL batchEventsProcessing]** ): this workflow lets you break down batch events in a queue before they are linked to a message template.
* **[!UICONTROL Processing real time events]** (internal name: **[!UICONTROL rtEventsProcessing]** ): this workflow lets you break down real time events in a queue before they are linked to a message template.
* **[!UICONTROL Update event status]** (internal name: **[!UICONTROL updateEventStatus]** ): this workflow lets you attribute a status to the event.

  The following event statuses are available:

    * **[!UICONTROL Pending]** : the event is in the queue. No message template has been assigned to it yet.
    * **[!UICONTROL Pending delivery]** : the event is in the queue, a message template has been assigned to it and it is being processed by the delivery.
    * **[!UICONTROL Sent]** : this status is copied from the delivery logs. It means that the delivery has been sent.
    * **[!UICONTROL Ignored by the delivery]** : this status is copied from the delivery logs. It means that the delivery was ignored.
    * **[!UICONTROL Delivery failed]** : this status is copied from the delivery logs. It means that the delivery failed.
    * **[!UICONTROL Event not taken into account]** : the event could not be linked to a message template. The event will not be processed.

## Configure multibranding {#configuring-multibranding}

This section describes one solution to configure tracking and mirror page URLs per brand, for transactional messages in Adobe Campaign.

### Prerequisites {#prerequisites}

* All of the hosts must be added to the configuration file of the instance (`config-<instance>.xml`).
* Each brand must be assigned a sub-domain.
* You must have an HTTPS certificate for all brands if the web tracking is done on HTTPS pages.

To configure multibranding, you need to configure both execution instances and control instance.

### Execution instance {#execution-instance}

On the execution instance(s), follow the steps below:

1. Create one external account per brand.

   >[!NOTE]
   >
   >Learn how to create an execution instance type external account in [this section](../../message-center/using/configuring-instances.md#control-instance).

1. Extend the nms:extAccount schema to add the tracking URL:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >Learn how to extend an existing schema in the [Extending a schema](../../configuration/using/extending-a-schema.md) section.

1. Modify the nms:extAccount form:

   ```
   <container label="Message domain branding" type="frame">
        <static type="help"> These parameters are used to override the DNS alias and addresses used during message delivery. When not populated, the values of the 'NmsServer_MirrorPageUrl' and 'NmsEmail_DefaultErrorAddr' options are used.</static>
        <input xpath="@mirrorURL"/>
        <input xpath="@trackingURL"/>
        <input img="nms:sendemail.png" menuId="deliveryMenuBuilder" type="scriptEdit">
               xpath="errorAddress"/>
      </container>
   ```

1. Modify the NmsTracking_OpenFormula and NmsTracking_ClickFormula options to use the external account instead of a global option.

   To do this, replace:

   ```
   <%@ include option='NmsTracking_ServerUrl' %>
   ```

   with:

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!IMPORTANT]
   >
   >These changes could lead to conflicts when upgrading. You may need to manually merge these formulas with their new version.

### Control instance {#control-instance}

On the control instance, you need to link delivery templates and external accounts.

To do this, follow the steps below:

1. Create one external account per brand with the same internal name as defined on the [execution instance](#execution-instance) (step 1).

1. Create one default delivery template per brand.

    >[!NOTE]
    >
    >    Learn how to create a delivery template in [this section](../../delivery/using/creating-a-delivery-template.md#creating-a-new-template).

1. In the delivery template's **[!UICONTROL Properties]**, set the routing to the external account of the brand.
