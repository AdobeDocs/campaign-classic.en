---
product: campaign
title: Backup
description: Backup
feature: Monitoring
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
TQID: https://experienceleague.adobe.com/ZCExecNbs9DnWVoQLpvzlrH7k2eGhBNq7pEiybyQdi4
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring (Campaign)
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines (Campaign)
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
