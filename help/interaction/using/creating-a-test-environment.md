---
title: Creating a test environment
seo-title: Creating a test environment
description: Creating a test environment
seo-description: 
page-status-flag: never-activated
uuid: e65dba89-e34d-404c-8849-8723d113aefa
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
discoiquuid: ec3072ac-55c0-4aae-9cdd-946b55b05870
index: y
internal: n
snippet: y
---

# Creating a test environment{#creating-a-test-environment}

To create a test environment (sandbox mode), apply the following steps:

>[!CAUTION]
>
>Only use this environment creation method for test environments. In all other cases, use the target mapping wizard. For more on this, refer to [Creating an offer environment](../../interaction/using/creating-a-test-environment.md#creating-an-offer-environment).

1. Launch the Adobe Campaign explorer and go to the instance root.
1. Right-click and add a **Generic folder** using the drop-down menus.

   ![](assets/offer_env_creation_001.png)

1. Next, go to the folder you just created and add an **Offer environment** using the right-click menus.

   ![](assets/offer_env_creation_001bis.png)

1. Apply the same process to create the environment sub-folders and elements. 
1. Once your tests have finished and you wish to use the environment in production, duplicate the offers and spaces in your design environment. (Right-click > **Actions** > **Deploy**).

   ![](assets/migration_interaction_5.png)

