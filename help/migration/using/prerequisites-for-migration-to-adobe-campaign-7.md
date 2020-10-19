---
title: Prerequisites for migration to Adobe Campaign 7
seo-title: Prerequisites for migration to Adobe Campaign 7
description: Prerequisites for migration to Adobe Campaign 7
seo-description: 
page-status-flag: never-activated
uuid: 9f4e4cdf-5338-4597-9d9d-5a3bd13033c7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: a3bbd8cc-97c6-4b08-adbf-76ab77b97262
---

# Prerequisites for migration to Adobe Campaign 7{#prerequisites-for-migration-to-adobe-campaign}

Before running any migration, consult the [Before starting migration](../../migration/using/before-starting-migration.md) and [Configuring your platform](../../migration/using/configuring-your-platform.md) sections.

When migrating from v6.02 to Adobe Campaign v7, some files delivered beforehand are not delivered.

If a client error appears, you have to either update your dashboards with the new Adobe Campaign v7 code, or manually copy the following files from the v6.02 instance to the v7 instance:

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
