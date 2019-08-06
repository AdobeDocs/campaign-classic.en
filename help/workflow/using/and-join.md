---
title: AND-join
seo-title: AND-join
description: AND-join
seo-description: 
page-status-flag: never-activated
uuid: 8da06111-a998-41c2-a0cf-7707b29b1202
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: efb020cb-cd6c-4fd9-9a76-89e1dc1b8281
index: y
internal: n
snippet: y
---

# AND-join{#and-join}

A join triggers its outbound transition only when all inbound transitions are activated, i.e. when all prior activities are finished. This allows you to make sure that certain activities have finished before continuing to execute the workflow.

The outbound sent population of the activity is determined by choosing a main set among the inbound transitions in the activity.

The outbound transition can only contain one of the inbound transition populations. If the activity is not configured, the outbound transition will randomly select one of the inbound populations.
