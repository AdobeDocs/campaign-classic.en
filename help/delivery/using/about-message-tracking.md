---
title: About message tracking
seo-title: About message tracking
description: About message tracking
seo-description: 
page-status-flag: never-activated
uuid: 91127faf-b9c4-46af-b842-b9816c501ecf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: tracking-messages
discoiquuid: 5d8bbfe0-e202-4062-aa47-9ad87b975bb7
index: y
internal: n
snippet: y
---

# About message tracking{#about-message-tracking}

In the context of an email delivery, tracking lets you track the messages sent and the behavior of recipients: opening, clicks on links, unsubscription, etc. This information is retrieved in the **[!UICONTROL Tracking]** tab of the profile of each recipient of the delivery. This tab presents all the URL links tracked and clicked by the recipient selected from the list. This is the accumulation of all URLs tracked in the deliveries that are still present in the delivery screen. The list can be configured and typically will contain: the URL clicked, the date and time of the click, and the document in which the URL was found. For more on this, refer to [this section](../../platform/using/editing-a-profile.md#tracking-tab).

Tracking metrics can be consulted in the **[!UICONTROL URLs and click streams]**, **[!UICONTROL Tracking statistics]**, and **[!UICONTROL Hot clicks]** reports, and in the **[!UICONTROL Tracking]** tab of the delivery.

The delivery dashboard is also key to monitor your deliveries and eventual issues encountered during the sending of messages. For more on this refer to this [section](../../delivery/using/monitoring-a-delivery.md).

**Related topics**:

* [Campaign Classic tracking guide](https://helpx.adobe.com/campaign/kb/acc-tracking.html)
* [How to configure tracked links](../../delivery/using/how-to-configure-tracked-links.md)
* [Tracking a web application](../../web/using/tracking-a-web-application.md)
* [Web application tracking opt-out](../../web/using/web-application-tracking-opt-out.md)

## Tracking Troubleshooting{#tracking-troubleshooting}

The following troubleshooting tips will help you solve the most common problems happening when using tracking. For a more advanced troubleshooting, refer to the following [page](https://helpx.adobe.com/campaign/kb/classic-tracking-troubleshooting.html).

If tracking is not working and you are not able to see the opens/clicks in the Tracking tab, you should check the following procedures:

First, check the **trackinglogd** process. This process reads from the IIS/Web Server shared memory and writes the redirection logs (**0x0000xxx.log** in **/redir/log folder**).
You can check if the **trackinglogd** is running from the Homepage in the Monitoring tab of your console, or execute the following command on the instance.

``` javascript
<user>@<instance>:~$ nlserver pdump
16:08:55 >   Application server for Adobe Campaign Classic (7.0 19.2 build 9069@4a05ee3d089) of 06/27/2019
watchdog (3358) - 3.4 Mo
syslogd@default (20321) - 10.0 Mo
trackinglogd@default (20394) - 39.4 Mo
web@default (20395) - 62.3 Mo
mta@<instance> (20396) - 16.9 Mo
stat@<instance> (20397) - 13.6 Mo
wfserver@<instance> (20398) - 13.4 Mo
```

If **trackinglogd** process doesn’t appear in the list, launch it with the following command in the instance:

``` javascript
<user>@<instance>:~$ nlserver start trackinglogd
16:13:04 >   Application server for Adobe Campaign Classic (7.0 19.2 build 9069@4a05ee3d089) of 06/27/2019
16:13:04 >   Launching task 'trackinglogd@default' ('nlserver trackinglogd -tracefile:trackinglogd@default -instance:default -detach') in a new process
```

Then, check that the **tracking** technical workflow has been running recently.
The **tracking** workflow reads from the redirection logs, then populates the **Tracking table (nms:trackinglogrcp)**.
