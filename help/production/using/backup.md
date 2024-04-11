---
product: campaign
title: Backup
description: Backup
feature: Monitoring
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
---
# Backup{#backup}

Backing up is essential in order to avoid losing data in the event of a problem (whether physical or system-related) on a machine.

Data is stored in two separate locations:

* physical files are stored in the Adobe Campaign directories,
* other data is stored in the database.

Most of the data is in the database. This represents 99% of the information to be backed up.

## Physical files {#physical-files}

Files are divided into several categories:

* Configuration files, stored in **nl6/conf**, enable you to reconfigure Adobe Campaign very quickly. 

* Redirection files, stored in  **nl6/var/`<instance-name>`/redir**, are on the tracking (often called 'frontal') servers, and include all previous campaign redirections. They are still used by previous campaigns.

* Log files, stored in **nl6/var/`<instance-name>`/log**, can be used to trace problems.

The directories to be backed up are therefore:

* nl6/conf

* nl6/var/`<instance-name>`/redir (for each instance)

* nl6/var/`<instance-name>`/log (optional)

* nl6/var/`<instance-name>`/relay (optional)  


## Database {#database}

>[!IMPORTANT]
>
>It is imperative to back up the database.


The database contains all of the information displayed in the Adobe Campaign rich client console, as well as all the line-of-business data.

Your hosting company, and their database administrators in particular, are responsible for this operation.
