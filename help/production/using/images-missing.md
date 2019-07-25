---
title: Images missing
seo-title: Images missing
description: Images missing
seo-description: 
page-status-flag: never-activated
uuid: 49bf0dcc-f8d5-47ec-9d85-12351bf1a0a8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 663fb547-984b-4fea-b159-75fec5923d9d
index: y
internal: n
snippet: y
---

# Images missing{#images-missing}

In the 17.9 release, several files (icons in particular) have been moved.

For hosted customers, there is no impact. For on-premise installations, please read the following.

**Apache users:**

There is no impact for Apache users if they use the provided **apache_neolane.conf**

**IIS users:**

For IIS users (on Windows), several icons will appear missing in the console after the build update. Additional IIS update steps are required:

1. After the build update, double-click on **iis_neolane_setup.vbs** located in the Campaign installation directory. The default path is C:Program Files (x86)AdobeAdobe Campaign v7tomcat-7conf
1. Restart the IIS site that has been updated by the previous step.

