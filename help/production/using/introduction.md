---
solution: Campaign Classic
product: campaign
title: Introduction
description: Introduction
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
---

# Introduction{#introduction}

This section presents the procedure to be applied to upgrade Adobe Campaign, client side and server side, and describes the switching to Unicode of an existing instance.

>[!NOTE]
>
>For hosted instances, you must coordinate with your Adobe Administrator.  
>For on-premise instances, you can get assistance from Adobe Consultants.

The upgrade must be applied to all servers where Adobe Campaign is installed. 

1. Migrate the redirection and tracking servers (Apache/IIS).
1. Migrate the Power Booster/Cluster servers.
1. Migrate the marketing server.

Adobe Campaign is based on several processes executed on the server side which you will need to manipulate during updates, in particular:

* Application server (nlserver web)
* Delivery server (nlserver mta)
* Redirection server (webmdl)

>[!CAUTION]
>
>The client console should be on the same build as the server instance.

>[!NOTE]
>
>For more on the various Adobe Campaign processes, refer to [this section](../../installation/using/general-architecture.md#logical-application-layer).  
>When using the Power Booster or Power Cluster type architecture, you must apply this process to all Power Booster/Cluster servers.

If the new version involves an alteration of the database structure, we recommend restarting the servers in the following order:

1. Application server (nlserver web),
1. Redirection server (webmdl),
1. Delivery server (nlserver mta).

