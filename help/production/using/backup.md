---
title: Backup
seo-title: Backup
description: Backup
seo-description: 
page-status-flag: never-activated
uuid: 50134154-a671-4534-b48d-a9e2c42e8f1a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 870ab0f2-1bd7-42e7-8d83-a08a520b6587
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

* Redirection files ** nl6/var/`<instancename>`/redir**

  These are on the tracking (often called 'frontal') servers, and include all previous campaign redirections. They are still used by previous campaigns.

* Log files: **nl6/var/`<instancename>`/log**

  These can be used to trace problems.

The directories to be backed up are therefore:

* nl6/conf

* nl6/var/`<instanceName>`/redir (for each instance)

* nl6/var/`<instanceName>`/log (optional)

* nl6/var/`<instanceName>`/relay (optional)  

>[!CAUTION]
>
>It is essential to back up the database.

## Database {#database}

The database contains all of the information displayed in the Adobe Campaign rich client console, as well as all the line-of-business data.

Your hosting company, and their database administrators in particular, are responsible for this operation. 
