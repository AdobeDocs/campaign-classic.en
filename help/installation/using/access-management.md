---
solution: Campaign Classic
product: campaign
title: Access management
description: Learn more about access management best practices.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
---
# Access management {#access-management}

## Webapp operator

Out of the box, the webApp operator is an administrator. To improve security, follow these guidelines:

* Replace the admin named right from this operator with a new one (can be named 'webapp'). For more information, refer to [this page](../../platform/using/access-management.md).

* Add the webApp operator in folders (mainly recipient folders) to grant read/write access to recipients. For more on this, refer to [this page](../../platform/using/access-management.md).

* If using a multi-brand (or multi-geo) instance, you may want to split web application access to different recipient folders. To do so:

    1. Duplicate the webApp operator

    1. Enter a name for each duplicate. For example: webapp_brand, webapp_brand2, etc.

    1. Duplicate a web application template to have one template per brand and edit the properties to change the operator by selecting Use a specific account.  Learn more in [this page](../../web/using/defining-web-forms-properties.md).

## Security groups and admin operators

Create enough security groups to give just enough rights to your operators to let them do what they need, and not more.

Do not use the admin operator (or don't share it). Create one operator per physical user (to have an accurate audit/logging). Add your newly named administrators to the admin group. If you don't use the admin operator, do not delete it, and don't disable it: this operator is used internally to execute processing. But you can ban its [access to the client console](../../platform/using/access-management.md) and restrict its security zone (to localhost).

Avoid adding too many operators in the admin group (or with admin named rights). They are very powerful operators (they can perform all SQL statements, execute commands on the server, etc.).

Adobe Campaign provides three high-level privileges through [named rights](../../platform/using/access-management.md#named-rights):

* **ADMINISTRATION** (admin): gives access to everything and allows to do everything, bypassing all named right checks, so it includes the PROGRAM EXECUTION (createProcess) and SQL named rights

* **PROGRAM EXECUTION** (createProcess): allows executing external programs (on the server)

* **SQL**: allows running SQL scripts on the database (so it can bypass the security model). Note: if you need to perform complex computations (filtering, for example), you can ask your database administrator to create an SQL function and add them to the allow list. Learn more in [this page](../../installation/using/scripting-coding-guidelines.md).

* **Grant them to very few (and trusted) operators**
