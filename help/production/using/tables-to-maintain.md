---
product: campaign
title: Tables to maintain
description: Tables to maintain
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 194f12de-4671-4a56-8cdc-cd5e3dac147b
---
# Tables to maintain{#tables-to-maintain}

![](../../assets/v7-only.svg)

The list of tables to maintain depends on your version of Adobe Campaign, how you use it and on the datamodel configuration.

The following list contains only the tables most subject to fragmentation. The impacts are as follows:

* overconsumption of disk space, thus affecting database access,
* indexes which have not been regularly updated, which slows down query performance.

## Adobe Campaign tables {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Table name </strong><br /> </th> 
   <th> <strong>Size</strong><br /> </th> 
   <th> <strong>Main type of activity</strong><br /> </th> 
   <th> <strong>Comments</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NmsDelivery<br /> </td> 
   <td> Small<br /> </td> 
   <td> Updates<br /> </td> 
   <td> There is one record per delivery action. A single record can be updated several times to reflect delivery progress, so indexes on this table tend to fragment rapidly. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> Medium<br /> </td> 
   <td> Insertions, updates, deletions<br /> </td> 
   <td> Work table which records are inserted into during delivery preparation. They are then updated during delivery and finally deleted once the delivery is complete.<br /> This table tends to fragment rapidly even though its average size is fairly limited.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> Large<br /> </td> 
   <td> Insertions, deletions<br /> </td> 
   <td> This table contains the information needed to generate personalized mirror pages. It contains a memo (CLOB) field, and as such will tend to be very large. The volume is directly proportional to the history of mirror pages kept. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> Medium<br /> </td> 
   <td> Insertions, updates, deletions<br /> </td> 
   <td> This table contains statistics on the delivery process. Its records are regularly updated. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> Medium<br /> </td> 
   <td> Updates, insertions<br /> </td> 
   <td> This table contains information on email addresses. It is frequently updated as part of the quarantine process (records are created at the first delivery error, updated when the counters change and deleted once delivery is successful). <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> Small<br /> </td> 
   <td> Updates<br /> </td> 
   <td> There is one record per workflow instance, so very few records. However the table it is regularly updated to reflect status and progress.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> Small<br /> </td> 
   <td> Insertions, updates, deletions<br /> </td> 
   <td> Each execution of a workflow activity leads to the creation of a record in this table. The purge mechanism deletes them once they are expired.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> Small<br /> </td> 
   <td> Insertions, updates, deletions<br /> </td> 
   <td> Each transition activated between tasks in a workflow leads to the creation of a record in this table. The purge mechanism deletes them once they are expired. <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> Very small <br /> </td> 
   <td> Insertions, updates, deletions<br /> </td> 
   <td> This table is specific to the workflow engine. It enables the sending of commands to workflows (Start, Stop, Pause, for instance). Although it is small, this table is taken into account during the purge of transactional tables linked to workflows.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> Largest<br /> </td> 
   <td> Insertions, updates, deletions<br /> </td> 
   <td> This is the largest table in the system. There is one record per message sent, and these records are inserted, updated to track the delivery status, and deleted when the history is purged. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog<br /> </td> 
   <td> Large<br /> </td> 
   <td> Insertions, deletions<br /> </td> 
   <td> Tracking logs are inserted and deleted when the history is purged, but they are not updated. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> Small<br /> </td> 
   <td> Updates<br /> </td> 
   <td> This table contains information used for qualifying SMTP errors. It is fairly small, but will be massively updated, so indexes on this table tend to fragment rapidly. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> Medium<br /> </td> 
   <td> Insertions, updates, deletions<br /> </td> 
   <td> This table contains the aggregates on SMTP errors sorted by domain. It initially contains detailed information which is aggregated by the cleanup task once it becomes outdated. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid (on a mid-sourcing instance)<br /> </td> 
   <td> Large<br /> </td> 
   <td> Insertions, updates, deletions<br /> </td> 
   <td> Only when the 5.10 (or later) instance is used as a mid-sourcing instance. This is one of the largest table in the database. There is one record per message sent, and these records are inserted, updated to track the delivery status, and deleted when the history is purged. When using mid-sourcing, the recommendation is to limit the history (usually less than two months), so this table remains reasonable in terms of size (less than 30 Go for 60 million rows, data+index), but it is very important to rebuild it from time to time. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp (when the NmsRecipient table is used) <br /> </td> 
   <td> Large<br /> </td> 
   <td> Insertions, updates, deletions<br /> </td> 
   <td> This is the largest table in the system. There is one record per message sent, and these records are inserted, updated to track the delivery status, and deleted when the history is purged. Note that in 5.10, this table is smaller than the equivalent in 4.05 (NmsBroadLog) since the SMTP message text is factorized in the NmsBroadLogMsg table in the 5.10 version. However, it remains essential to re-index this table regularly (every other week to start with), and completely rebuild it from time to time (once a month, or when performance is impacted). <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx (when an external recipient table is used)<br /> </td> 
   <td> Large<br /> </td> 
   <td> Insertions, updates, deletions<br /> </td> 
   <td> Same as NmsBroadLogRcp but with an external recipient table. Please adapt Yyy and Xxx with the values in your delivery mapping. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp (when the NmsRecipient table is used) <br /> </td> 
   <td> Large<br /> </td> 
   <td> Insertions, deletions<br /> </td> 
   <td> Tracking logs are inserted and deleted when the history is purged, but they are not updated. The volume depends on the length of data retention. <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXxx (when the external recipient table is used)<br /> </td> 
   <td> Large<br /> </td> 
   <td> Insertions, deletions<br /> </td> 
   <td> Same as NmsTrackingLogRcp but with an external recipient table. Please adapt Yyy and Xxx with the values used in your delivery mapping. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent (Message Center execution instance)<br /> </td> 
   <td> Large<br /> </td> 
   <td> Insertions, updates, deletions<br /> </td> 
   <td> Similar to the other broadlog tables, but with the NmsRtEvent instead of NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent( Message Center execution instance)<br /> </td> 
   <td> Large<br /> </td> 
   <td> Insertions, deletions<br /> </td> 
   <td> Similar to the other trackingLog tables, but with the NmsRtEvent table instead of NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent (Message Center execution instance)<br /> </td> 
   <td> Large<br /> </td> 
   <td> Insertions, updates, deletions<br /> </td> 
   <td> Table containing the Message Center event queue. The status of these events is updated by Message Center as they are processed. Deletions are carried out during the purge. We advise you to regularly recreate the index of this table and rebuild it.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto (Message Center control instance)<br /> </td> 
   <td> Large<br /> </td> 
   <td> Insertions, updates, deletions<br /> </td> 
   <td> Similar to NmsRtEvent. This table archives every event from all the execution instances. It is used by no real time process, only by reports.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> Very small<br /> </td> 
   <td> Insertions, updates, deletions<br /> </td> 
   <td> Tables that include mobile applications and their configuration.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp<br /> </td> 
   <td> Large<br /> </td> 
   <td> Insertions, updates<br /> </td> 
   <td> Table that includes the identifiers of mobile devices (addresses) used to send the notification (similar to a recipient table).<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> Large<br /> </td> 
   <td> Insertions, updates, deletions<br /> </td> 
   <td> Similar to the other broadlog tables, but with the NmsappSubscriptionRcp instead of NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogAppSubRcp<br /> </td> 
   <td> Large<br /> </td> 
   <td> Insertions, deletions<br /> </td> 
   <td> Similar to the other trackingLog tables, but with the NmsappSubscriptionRcp table instead of NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkSessionInfo<br /> </td> 
   <td> Small<br /> </td> 
   <td> Insertions, deletions<br /> </td> 
   <td> Table that includes user sessions. The number of insertions and deletions is very important.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Customer tables {#customer-tables}

In addition to the list above, tables containing created by customers (which do not exist in the Adobe Campaign datamodel) during platform setup can also be subject to fragmentation, especially if they are frequently updated during data loading or synchronization procedures. These tables can be part of the default Adobe Campaign data model (for instance **NmsRecipient**). In this case, it is up to the administrator of the Adobe Campaign platform to conduct an audit of its specific database model to find these custom tables. These tables aren't necessarily mentioned explicitly in our maintenance procedures.
