---
title: Backup
seo-title: Backup
description: Backup
seo-description: 
page-status-flag: never-activated
uuid: 54545d6b-9f4c-4667-873a-ec024cc6f02a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: a3f0c6bd-0a07-4249-b029-f94e0703c36e
index: y
internal: n
snippet: y
---

# Backup{#backup}

Backing up is essential in order to avoid losing data in the event of a problem (whether physical or system-related) on a machine.

Data is stored in two separate locations:

* physical files are stored in the Adobe Campaign directories,
* other data is stored in the database.

Most of the data is in the database. This represents 99% of the information to be backed up.

## Physical files {#physical-files}

Files are divided into several categories:

* Configuration files, located in **nl6/conf**

  These enable you to reconfigure Adobe Campaign very quickly. 

* Redirection files ** nl6/var/`<instancename> /redir</instancename>`**

  These are on the tracking (often called 'frontal') servers, and include all previous campaign redirections. They are still used by previous campaigns.

* Log files: **nl6/var/`<instancename> /log</instancename>`**

  These can be used to trace problems.

>[!CAUTION]
>
>It is essential to back up the database.

## Database {#database}

The database contains all of the information displayed in the Adobe Campaign rich client console, as well as all the line-of-business data.

Your hosting company, and their database administrators in particular, are responsible for this operation. 
