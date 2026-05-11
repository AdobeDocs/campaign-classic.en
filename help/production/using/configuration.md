---
product: campaign
title: Additional configuration
description: Configuration
feature: Monitoring, Configuration
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
TQID: https://experienceleague.adobe.com/gzcQquM9q71NIOt8mScgRpLtwffxvopslrrpLxxIang
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
---
# Configuration{#configuration}



## Changing the syslogd listening port {#changing-the-syslogd-listening-port}

By default, the **syslogd** listening port is 666 (udp). You can alter it using an environment variable if necessary.

Once it is configured, this variable is taken into account by all Adobe Campaign modules.

### In Linux {#in-linux}

Edit the **customer.sh** file and add the following line:

```sql
export TRACE_ADDR=localhost:<listening port>
```

### In Windows {#in-windows}

You need to create the **TRACE_ADDR** environment variable with the **localhost** value: **`<listening port="" />`**.

>[!IMPORTANT]
>
>We recommend running some tests to make sure your platform is working after you create this environment variable.

## Configuring security zones {#configuring-security-zones}

Each operator needs to be linked to a zone to log on to an instance and the operator IP must be included in the addresses or address sets defined in the security zone. Technical zone configuration is carried out in the configuration file of the Adobe Campaign server. The linking of an operator to a security zone has to be defined in the console ( **[!UICONTROL Administration > Access management > Operators]** node).

>[!NOTE]
>
>For more on configuring security zones, refer to [this section](../../installation/using/security-zones.md).
