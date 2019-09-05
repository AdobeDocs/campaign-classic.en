---
title: Interaction - Data buffer
seo-title: Interaction - Data buffer
description: Interaction - Data buffer
seo-description: 
page-status-flag: never-activated
uuid: 4cb742b5-6bde-43e8-b26b-16f27dd65f72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: cbfdeb2f-4f20-45b8-8cc0-89362f9ea9c1
index: y
internal: n
snippet: y
---

# Interaction - Data buffer{#interaction-data-buffer}

>[!NOTE]
>
>Some configurations can only be performed by Adobe for deployments hosted by Adobe. For example, to access the server and instance configuration files. To learn more about the different deployments, refer to the [Hosting models](../../installation/using/hosting-models.md) section or to [this article](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

In Adobe Campaign, a **data buffer zone** has been introduced in the Interaction module. This allows you to **increase performance** of inbound Interaction by desynchronizing stock and offer calculations.

It only concerns inbound Interaction, whether by a call (with or without call data), or by a status update (updateStatus).

To avoid a queue when writing proposals related to a recipient, a ne w process generates a **data buffer zone** that allows proposals to be **written asynchronously**. This data buffer zone is periodically read and emptied. The default period is in the space of about one second.Proposal writing is therefore grouped.

Data buffer zone **configuration** can be done in the instance's configuration file (config-Instance.xml).

>[!NOTE]
>
>Any changes made to the configuration requires a restart of the web server (Apache:IIS) and the Adobe Campaign processes.  
>After configuring the data buffer zone, please ensure that an adapted hardware configuration is available. (amount of memory present).

After configuring the data buffer zone, please ensure that an adapted hardware configuration is available. (amount of memory present).

The definition for a writing daemon (process named: interaction) is as follows:

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>

```

If you use Inbound Interaction, the @autostart attribute must be "true" to automatically launch the process when the Adobe Campaign server launches.

Argument details:

```

 args: Start-up parameters 
 autoStart: Automatic start Default: false 
 callDataSize: Max. number of characters stored in the shared memory for call data
 Default: 0 
 initScript: ID of JavaScript to execute when starting the process 
 maxProcessMemoryAlertMb: Alert concerning the amount of RAM consumed (in Mb) by a given process Default: 1800 
 maxProcessMemoryWarningMb: Warning concerning the amount of RAM consumed (in Mb) by a given process Default: 1600 
 maxSharedEntries: Max. number of events stored in the shared memory. Default: 25000 
 nextOffersSize: Maximum number of eligible offers sorted right after propositions, to be stored for statistics Default: 0 
 processRestartTime: Time of the day when the process is automatically restartedDefault: '06:00:00' 
 runLevel: Priority at start Default: 10 
 targetKeySize: Max. number of characters stored in the shared memory for identifying individuals Default: 16 

```

