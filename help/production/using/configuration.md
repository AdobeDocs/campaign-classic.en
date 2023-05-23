---
product: campaign
title: Additional configuration
description: Configuration
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
---
# Configuration{#configuration}



## Changing the syslogd listening port {#changing-the-syslogd-listening-port}

By default, the **syslogd** listening port is 666 (udp). You can alter it using an environment variable if necessary.

Once it is configured, this variable is taken into account by all Adobe Campaign modules.

### In Linux {#in-linux}

Edit the **customer.sh** file and add the following line:

```
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
