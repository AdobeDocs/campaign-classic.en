---
product: campaign
title: Additional configurations
description: Learn how to set up additional configurations for Transactional messaging in Adobe Campaign Classic
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 4d25d740-db57-4d18-8cae-2dd49c4a786e
TQID: 'https://experienceleague.adobe.com/TJ5R6T1pu5JQU5SaGoWRgZLG2m29TWWPVB8nniorRUg'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
---
# Additional configurations {#mc-additional-configurations}

This page covers additional configurations for transactional messaging on Campaign Classic v7.

As part of the transition from Campaign v7 to v8, the Campaign Classic documentation set has been streamlined and reorganized. Common features are now available exclusively in the Campaign v8 documentation set. To learn more about transactional messaging event purge and technical workflows, refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/settings/transactional-msg-settings){target=_blank}.

[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/settings/transactional-msg-settings){target=_blank}

## Monitor thresholds {#monitoring-thresholds}

You can configure the warning thresholds (orange) and alert thresholds (red) of the indicators that appear in the **Message Center service level** and **Message Center processing time** reports (refer to [Access transactional messaging reports](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"} (Campaign v8 documentation)).

To do this, follow the steps below:

1. Open the deployment wizard on the **execution instance**.

1. Go to the **[!UICONTROL Message Center]** page.

1. Use the arrows to change the thresholds.

    ![](assets/messagecenter_monitor_events_001.png)

>[!NOTE]
>
>The number of events pending in queue is displayed in the [System indicators](../../production/using/monitoring-processes.md#system-indicators) section of the Adobe Campaign process monitoring page. For more information on the deployment wizard, refer to [this section](../../installation/using/deploying-an-instance.md#deployment-assistant).

## Technical workflows {#technical-workflows}

You must ensure that the technical workflows on the control instance and the different execution instances have indeed been created and started before deploying any transactional message templates.

### Archiving workflow schedule

Avoid modifying the **archiving workflow** schedule that runs on the control instance. Otherwise some tracking data being pulled from the execution instance may be lost.

If you do modify the archiving workflow schedule, you must also change the **tracking workflow** schedule on the execution instance to match the archiving workflow schedule on the control instance.

## Configure multibranding {#configuring-multibranding}

This section describes one solution to configure tracking and mirror page URLs per brand, for transactional messages in Adobe Campaign.

### Compatibility note {#compatibility-note}

This legacy branding configuration is not compatible with the new [centralized branding](https://experienceleague.adobe.com/docs/campaign-web/v8/conf/branding/branding-gs.html){target="_blank"} model introduced in Campaign v8.  

If your existing environment uses this legacy configuration, it cannot be migrated directly to the new centralized branding model. A full reimplementation of branding settings is required to adopt the new system.

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

1. Create a delivery template per brand. Refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-templates.html){target="_blank"}.

1. In the delivery template's **[!UICONTROL Properties]**, set the routing to the external account of the brand.
