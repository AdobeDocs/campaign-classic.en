---
title: Migrate to Adobe Identity Management System (IMS)
description: Learn how to migrate your authentication process to Adobe Identity Management System (IMS)
---
# Migrate to Adobe Identity Management System (IMS) {#migrate-to-ims}

As part of the effort to reinforce security and authentication process, Adobe Campaign highly recommends to migrate end user authentication mode from the login/password native authentication to [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}.

In addition, as part of the effort to reinforce security and authentication process, Adobe Campaign client application now calls Campaign APIs directly using the IMS technical account token. You must migrate your technical operators to Adobe Developer Console.

>[!CAUTION]
>
>This change is already applicable in Campaign Classic v7, and will be **mandatory** to move to Campaign v8. Native user/password authentication is not allowed in Campaign v8. **Adobe recommends to perform this migration starting Campaign v7.3.5 to be able to migrate smoothly to Campaign v8.**
>

## Migration steps {#ims-steps}

Migration to [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} is a security imperative to make your environments secure and standardized, as most of the other Adobe Experience Cloud solutions and apps are already on IMS.

Adobe supports you in this migration effort. You can find detailed context and step by step guidelines in the below articles:

* Migration for end-users authentication is detailed in [this page](migrate-users-to-ims.md).
* Migration for technical operators authentication is detailed in [this page](ims-migration.md).
* Starting Campaign v7.4.1, enable the user interface and API restrictions to remove options and capabilities which are specific to native authentication, as detailed in [this page](impact-ims-migration.md).


## IMS migration compatible versions {#ims-versions}

A prerequisite for this migration is to upgrade your environment to one of the following product version:

* Campaign v7.4.1 (recommended)
* Campaign v7.3.5 
* Campaign v7.3.3.IMS
* Campaign v7.3.2.IMS

These Campaign versions are detailed in the [Release Notes](../../rn/using/latest-release.md).

## Frequently Asked Questions {#ims-migration-faq}

### When can I start the migration? {#ims-migration-start}

A recommendation for the migration to [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} is to upgrade your environment to Campaign Classic v7.4.1 (or an [IMS migration compatible version](#ims-versions)).

You can start IMS migration on your stage environment, once it is upgraded to the latest version, and accordingly plan for production environment.

### What happens after build upgrade to Campaign Classic v7.4.1? {#ims-migration-after-upgrade}

After your environments have been upgraded to Campaign Classic v7.4.1 (or an [IMS migration compatible version](#ims-versions)), you can initiate your transition to [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}. 

### When is the migration complete? {#ims-migration-end}

Once end-user migration and technical operator(s) migration to Adobe Identity Management System (IMS) is done, you must update your environment to remove options which are specific to the native authentication and no longer applicable with IMS authentication. This update is only available starting Campaign v7.4.1. [Learn more](impact-ims-migration.md)



## Useful links {#ims-useful-links}

* [Migration of end-users to IMS](migrate-users-to-ims.md)
* [Migration of technical operators to Adobe Developer console](ims-migration.md)
* [Adobe Campaign Classic v7 latest release notes](../../rn/using/latest-release.md)
* [What is Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}
