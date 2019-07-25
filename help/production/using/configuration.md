---
title: Configuration
seo-title: Configuration
description: Configuration
seo-description: 
page-status-flag: never-activated
uuid: 043947c8-8bff-4f7f-870a-52ec0c1c56e3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: b8fdf21f-475b-4c1a-aaa5-78bf66f380f9
index: y
internal: n
snippet: y
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

You need to create the **TRACE_ADDR** environment variable with the **localhost** value: ** `<listening port="" />`**.

>[!CAUTION]
>
>We recommend running some tests to make sure your platform is working after you create this environment variable.

## Configuring security zones {#configuring-security-zones}

Each operator needs to be linked to a zone to log on to an instance and the operator IP must be included in the addresses or address sets defined in the security zone. Technical zone configuration is carried out in the configuration file of the Adobe Campaign server. The linking of an operator to a security zone has to be defined in the console (**Administration > Access management > Operators** node).

>[!NOTE]
>
>For more on configuring security zones, refer to [this section](../../installation/using/configuring-campaign-server.md#defining-security-zones).

