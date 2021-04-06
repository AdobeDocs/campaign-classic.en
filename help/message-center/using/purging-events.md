---
solution: Campaign Classic
product: campaign
title: Purging events
description: Purging events
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 275a333b-70cc-4549-ac52-ac8ce54c2805
---
# Purging events{#purging-events}

You can use the [deployment wizard](../../production/using/database-cleanup-workflow.md#deployment-wizard) to configure how long the data is to be stored in the database.

Event purging is carried out automatically by the [Database cleanup workflow](../../production/using/database-cleanup-workflow.md). This workflow purges the events received and stored on the execution instances and events archived on a control instance.

Use the arrows as appropriate to change the purge settings.

Event purge settings on a control instance:

![](assets/messagecenter_delete_events_001.png)

Event purge settings on an execution instance:

![](assets/messagecenter_delete_events_002.png)

For more on the database cleanup workflow, refer to [this section](../../production/using/database-cleanup-workflow.md).
