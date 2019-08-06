---
title: Test
seo-title: Test
description: Test
seo-description: 
page-status-flag: never-activated
uuid: 95926b62-dd44-4e04-9c2a-b688b0a83afd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 687513e0-3ee9-4d70-ba94-b445637b248f
index: y
internal: n
snippet: y
---

# Test{#test}

A **Test** type activity activates the first transition that satisfies the condition associated with it. If no condition is satisfied and if the **Use the default fork** option is activated, the default transition will be activated.

A condition is a JavaScript expression that must be evaluated to 'true' or 'false'. To enter the expression, click the icon to the right of the name of the condition, and then select **Edit...**.

![](assets/edit_test.png)

For more information on all the additional JavaScript functions and SOAP methods of the applicative server accessible via workflow JavaScript, refer to [JSAPI documentation](http://docs.campaign.adobe.com/doc/AC/en/jsapi/p-1.html).

You can also insert variables directly from this editor.

Conditions can be added, deleted, or ordered from the activity property edit window, but can also be modified from the transition.

If the result of a calculation is to be reused by different conditions, it is possible to calculate it in the initialization script of the activity. The result must be stored in a variable of the task to be accessed by the condition scripts (task.vars.xxx).
