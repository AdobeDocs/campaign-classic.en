---
product: campaign
title: Architecture
description: Workflows are handled by a specific module, which can be started on multiple servers in order to share the processing load
feature: Workflows
hide: true
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
TQID: https://experienceleague.adobe.com/lQLXeSTFhKRCNhA9SdShd9Nyd1mbNt-KPa-XJw-6wAs
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
---
# Architecture {#architecture}



Workflows are handled by a specific module. This module can be started on multiple servers in order to share the processing load.

![](assets/architecture.png)

* The 'Workflow Instance Runner' (runwf) process executes all the tasks of a given workflow instance. When there are no tasks to be executed for the time being, it becomes 'passive', that is to say it saves its status in the database, then stops.
* The 'Workflow Server' (wfserver) module monitors current workflow instances. When there is a task to perform, this module creates a process to activate (or reactivate) the corresponding instance.
