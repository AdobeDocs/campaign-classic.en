---
title: Configuring multibranding
seo-title: Configuring multibranding
description: Configuring multibranding
seo-description: 
page-status-flag: never-activated
uuid: 7a68aec8-75e2-4f23-9ebe-14d078aba8ba
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: adc14f53-e60e-4c08-a6f7-f192d3ae11d8
index: y
internal: n
snippet: y
---

# Configuring multibranding{#configuring-multibranding}

This section describes one solution to configure tracking and mirror page URLs per brand, for transactional messages in Adobe Campaign.

## Prerequisites {#prerequisites}

* All of the hosts must be added to the configuration file of the instance (config- `<instance>  .xml). </instance>`
* Each brand must be assigned a sub-domain.
* You must have an HTTPS certificate for all brands if the web tracking is done on HTTPS pages.

## Typical process {#typical-process}

To configure multibranding, you need to configure both execution instances and control instance. In the execution instances, follow the steps below:

1. Create one external account per brand.

   >[!NOTE]
   >
   >Creating an execution instance type external account is presented in the [Control instance](../../message-center/using/configuring-multibranding.md#control-instance) section.

1. Extend the nms:extAccount schema to add the tracking URL:

   ```
   
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   
   ```

   >[!NOTE]
   >
   >Extending an existing schema is presented in the [Extending a schema](../../configuration/using/extending-a-schema.md) section.

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

   >[!CAUTION]
   >
   >These changes could lead to conflicts when upgrading. You may need to manually merge these formulas with their new version.

On the control instance, you need to link delivery templates and external accounts. To do this, you need to:

1. Create one external account per brand with the same internal name as defined in step 1.
1. Create one default delivery template per brand.
1. In the delivery template's **Properties**, set the routing to the external account of the brand.

