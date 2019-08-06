---
title: Prerequisites for migration to Adobe Campaign 7
seo-title: Prerequisites for migration to Adobe Campaign 7
description: Prerequisites for migration to Adobe Campaign 7
seo-description: 
page-status-flag: never-activated
uuid: 18804c2e-8121-4027-893c-30aa5c0727cf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 5399a4ec-b906-4831-9752-1ae7edbf85e6
index: y
internal: n
snippet: y
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

