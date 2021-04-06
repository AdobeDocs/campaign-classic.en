---
solution: Campaign Classic
product: campaign
title: Application objects
description: Application objects
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: fb4798d7-0a2c-455b-86b6-3dcb5fd25c82
---
# Application objects{#application-objects}

Built-in objects should be monitored and preventing them from growing too much is important.

## Sequence of IDs {#sequence-of-ids}

Adobe Campaign uses an ID sequence that has to be consumed accordingly: **xtkNewId**. If the sequence is consumed very quickly (i.e. from 100,000 per day), you must verify that it is consistent with your business requirements, such as sending millions of emails per day. It is possible to define a dedicated sequence for particular tables. You can setup a workflow to monitor ID usage.

When the sequence reaches more than 2 billion (2,147,483,648 is the exact number), it goes back to zero. It must be avoided and creates issues, which is why this sequence must be monitored.

To prevent this with large tables, consider using a specific sequence. This can be done with the **pkSequence** attribute in the schema.

High-frequency workflows that create a lot of logs will consume a lot of IDs. So it is highly recommended to avoid too many logs and high frequencies in workflows.

If the sequence has already cycled, the best solution is to switch to negative IDs, starting from -2,147,483,648.

## Folders {#folders}

There should be less than 1000 folders on any instance. Having more folders than this can cause performance problems with the Campaign client. You can set up a monitoring job to count the number of folders, workflows, etc., and report back on a periodic basis.

This method also highlights users who create too many objects.

## Deliveries {#deliveries}

There should be less than 1000 deliveries on the instance at any time. Having a lot of deliveries consumes database space and creates issues. An instance that creates more than 10 deliveries per day has to be checked against business requirements. Consider using continuous deliveries to create less deliveries. For more on this, refer to [this section](../../workflow/using/continuous-delivery.md).

Deliveries older than two years should be purged from the instance.

## Files {#files}

The number of files on the application server disk should not increase indefinitely.

Import workflows create files and therefore cause disk expansion. This can be prevented by using the standard [File collector](../../workflow/using/file-collector.md) activity. The file collector moves files to a temporary folder and automatically purges them.

If a workflow imports files and doesn't make use of the standard features, it needs to be purged in order to keep disk space to a minimum.

## Transactional data and logs {#transactional-data-and-logs}

Every [workflow](../../workflow/using/data-life-cycle.md#work-table) that imports data into Adobe Campaign causes the size of the database to grow.

Check that cleanup or purge workflows are running and effectively purging records. All transactional data and logs must be purged. The cleanup task purges the standard tables only: tracking and broad logs. Specific tables must be purged by specific workflows. Refer to [this section](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

Watch for aging transactional data by checking the oldest creation date of the records.
