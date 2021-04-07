---
solution: Campaign Classic
product: campaign
title: Images missing
description: Images missing
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
---
# Images missing{#images-missing}

In the 17.9 release, several files (icons in particular) have been moved.

For hosted customers, there is no impact. For on-premise installations, please read the following.

**Apache users:**

There is no impact for Apache users if they use the provided **apache_neolane.conf**.

**IIS users:**

For IIS users (on Windows), several icons will appear missing in the console after the build update. Additional IIS update steps are required:

1. After the build update, double-click **iis_neolane_setup.vbs** located in the Campaign installation directory. The default path is C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Restart the IIS site that has been updated by the previous step.
