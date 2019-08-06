---
title: Configuring your platform
seo-title: Configuring your platform
description: Configuring your platform
seo-description: 
page-status-flag: never-activated
uuid: 0df64f44-8905-4930-8349-14184f9c1a6b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: c57e5988-8214-46cc-9d48-8c15f75c15e0
index: y
internal: n
snippet: y
---

# Configuring your platform{#configuring-your-platform}

Certain major changes in Adobe Campaign v7 require a configuration to ensure its effective operation. These parameters may be necessary before or after migrating. The concerned changes and their configuration mode are presented in this section.

During migration, the **NmsRecipient** table is rebuilt from the schemas definition. Any change made to the SQL structure of this table outside of Adobe Campaign will be lost.

Example elements to check:

* If you have added a column (or an index) into the **NmsRecipient** table but you have not detailed it in the schema, this will not be saved.
* The **tablespace** attribute takes back its values by default, in other words those defined in the deployment wizard.
* If you have added a reference view to the NmsRecipient table, you must delete it before migrating.

This warning also concerns Oracle users: if you have added the **usetimestamptz:1** option during a postupgrade (see [Time zones](../../migration/using/configuring-your-platform.md#time-zones)), all tables containing at least one **date+time** field are rebuilt.

## Before the migration {#before-the-migration}

When migrating to Adobe Campaign v7, the following elements must be configured. These elements must be addressed before starting the **postupgrade**.

* Timezones

  During a migration from a v5.11 platform, you must specify the timezone to use during the postupgrade.

  If you wish to use the "multi timezone" mode, refer to the [Time zones](../../migration/using/configuring-your-platform.md#time-zones) section.

  If you use Oracle as a database, check that the Oracle timezone files have properly been synched between the application server and the database server. For more on this, refer to the [Oracle](../../migration/using/configuring-your-platform.md#oracle) section.

  In addition, during a migration from a v.5.11 platform, in MySQL, you must perform additional configurations. For more information, refer to the [MySQL](../../migration/using/configuring-your-platform.md#mysql-) section.

* Security zones

  For security reasons, the Adobe Campaign platform is no longer accessible by default: you must configure the security zones, which requires collecting the user IP addresses before the migration.

  For more information, refer to the [Security](../../migration/using/configuring-your-platform.md#security) section.

* Syntax

  Certain syntaxes in JavaScript may be accepted in versions 5.11 and 6.02 and no longer accepted in the v7 version, due to the use of a new interpreter. For more information, refer to the [JavaScript](../../migration/using/configuring-your-platform.md#javascript) section.

  Similarly, a new syntax is introduced in Adobe Campaign v7 to replace the SQLData based syntax. If you use code elements with this syntax, you must adapt them. For more information, refer to the [SQLData](../../migration/using/configuring-your-platform.md#sqldata) section.

* Passwords

  You must configure the **Admin** and **Internal** passwords. For more information, refer to the [User passwords](../../migration/using/configuring-your-platform.md#user-passwords) section.

* Tree structure

  If migrating from a v5.11 platform, you must reorganize the tree structure folders according to Adobe Campaign v6 norms. For more information, refer to the [Adobe Campaign v7 tree structure](../../migration/using/configuring-your-platform.md#adobe-campaign-v7-tree-structure) section.

* Interaction

  If you use **Interaction**, you must delete all 6.02 schema references that no longer exist in v7. For more information, refer to the [Interaction](../../migration/using/configuring-your-platform.md#interaction) section.

## After the migration {#after-the-migration}

After running **postupgrade**, the following elements must be taken into account and the corresponding configurations carried out.

* Mirror pages

  Mirror page personalization block has changed with v6.x. This new version improves security when accessing these pages.

  If you used the v5 personalization block in your messages, the mirror page display will fail. Adobe highly recommends to use the new personalization block when inserting mirror page in your messages.

  However, as a temporary solution (and as the mirror pages are still live), you can turn back to the old personalization block to avoid this problem by changing the option **XtkAcceptOldPasswords** and set it to **1**. This will not affect the usage of the new v6.x personalization block.

* Syntax

  If you encounter any errors related to the syntax, during the postupgrade, you must temporarily activate the **allowSQLInjection** option in the **serverConf.xml** file, as this gives you time to rewrite the code. Once the code is adapted, be sure to reactivate the security. For more on this, refer to the [SQLData](../../migration/using/configuring-your-platform.md#sqldata) section.

* Conflicts

  The migration is performed through a postupgrade and conflicts may appear in reports, forms or web applications. These conflicts can be resolved from the console.

  See the [Conflicts](../../migration/using/configuring-your-platform.md#conflicts) section.

* Tomcat

  If you customized the installation folder, make sure to check it is correctly updated after the migration. For further details, refer to the [Tomcat](../../migration/using/configuring-your-platform.md#tomcat) section.

* Reports

  All out-of-the-box reports currently use the v6.x rendering engine. If you had added JavaScript code into the reports, some elements may be altered.

  Consult the [Reports](../../migration/using/configuring-your-platform.md#reports) section.

* Web Applications

  After the postupgrade, if you have any problems connecting to your identified Web applications, you must activate the **allowUserPassword** and **sessionTokenOnly** options in the **serverConf.xml** file. Remember to then deactivate these two options. For more information, refer to the [Identified web applications](../../migration/using/configuring-your-platform.md#identified-web-applications) section.

  Depending on the type of Web applications and their configuration, you must perform additional manipulations to ensure they work correctly.

  See the [Web applications](../../migration/using/configuring-your-platform.md#web-applications) section.

  If migrating from a v5.11 platform, additional configurations must be carried out: for more information, refer to the [Web applications](../../migration/using/configuring-your-platform.md#web-applications) section.

* Security zones.

  Before starting the server, you must configure the security zones. For more information, refer to [this section](../../installation/using/configuring-campaign-server.md#defining-security-zones) and the [Security](../../migration/using/configuring-your-platform.md#security) section.

* Schemas

  In Red Hat, you may encounter errors when editing certain schemas. For more on this, refer to the [Red-Hat](../../migration/using/configuring-your-platform.md#red-hat) section.

* Workflows

  If migrating from a v5.11 platform, you must control the workflows runtime directory. For more on this, refer to the [Workflows](../../migration/using/configuring-your-platform.md#workflows) section.

* Tracking

  If migrating from a v5.11 platform, you must configure the tracking mode. For more on this, refer to the [Tracking](../../migration/using/configuring-your-platform.md#tracking) section.

* Home page

  If migrating from a v6.02 platform, you may define additional parameters to keep your old home page from v6.02. For more on this, refer to the [User friendliness: Home page and navigation](../../migration/using/configuring-your-platform.md#user-friendliness--home-page-and-navigation) section.

* Interaction

  If you use **Interaction**, you must adjust any parameters after the migration. For more on this, refer to the [Interaction](../../migration/using/configuring-your-platform.md#interaction) section.

