---
title: Deliveries
seo-title: Deliveries
description: Deliveries
seo-description: 
page-status-flag: never-activated
uuid: 233928bb-aebe-411f-a6a7-653cb132605f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 8b1ba0fa-337a-4023-9bb7-c944135b5375
index: y
internal: n
snippet: y
---

# Deliveries{#deliveries}

The workflows detailed below are installed by default.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Internal name</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Reporting aggregates</strong><br /> </td> 
   <td> <strong>reportingAggregates</strong><br /> </td> 
   <td> This workflow updates aggregates used in reports. It is triggered every day at 2am by default.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Billing</strong><br /> </td> 
   <td> <strong>billing</strong><br /> </td> 
   <td> This workflow sends the system activity report to the 'billing' operator by email. It is triggered the 25th of every month by default.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Number of active billing profiles</strong><br /> </td> 
   <td> <strong>billingActiveContactCount</strong><br /> </td> 
   <td> This wokflow counts the number of active profiles. It is triggered every night at 1am by default.<br /> “<strong>Profile</strong>” means a record of information (e.g.: a record in the nmsRecipient table or an external table containing a cookie ID, Customer ID, mobile identifier or other information relevant to a particular channel) representing an end-customer, prospect, or lead. Billing only concerns Profiles that are “active”. A Profile is considered “active” if the Profile has been targeted or communicated within the past 12 months via any channel.<br /> Facebook and Twitter channels are not taken into account.<br /> You can have an overview of the <strong>Number of active profiles</strong> from the <strong>Administration</strong> &gt; <strong>Campaign Management</strong> &gt; <strong>Customer metrics</strong> menu.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Alias cleansing</strong><br /> </td> 
   <td> <strong>aliasCleansing</strong><br /> </td> 
   <td> This workflow standardizes enumeration values. It is triggered every day at 3am by default.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Update for deliverability</strong><br /> </td> 
   <td> <strong>deliverabilityUpdate</strong><br /> </td> 
   <td> This workflow lets you create the list of bounce mail qualification rules, as well as the list of domains and MXs in the platform. This workflow only works if the HTTPS port is open. These lists are not updated unless the Deliverability module is installed.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Database cleanup</strong><br /> </td> 
   <td> <strong>cleanup</strong><br /> </td> 
   <td> This workflow is the database maintenance workflow: it makes different calculations from the statistics and processes, and deletes obsolete data from the database according to the defined configuration in the deployment assistant. It is triggered every day at 4am by default.<br /> For more information, refer to this <a href="../../production/using/database-cleanup-workflow.md">page</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Paused workflows cleanup</strong><br /> </td> 
   <td> <strong>cleanupPausedWorkflows</strong><br /> </td> 
   <td> This workflow analyzes paused workflows that have severity set to normal and triggers warnings and notifications when they have been paused for too long. After a month, paused technical workflows are stopped unconditionally. By default, it is triggered every Monday at 5 am.<br /> For more information, refer to <a href="../../workflow/using/deliveries.md#handling-of-paused-workflows" target="_blank">Handling of paused workflows</a>. </td> 
  </tr> 
  <tr> 
   <td> <strong>Offer notification</strong><br /> </td> 
   <td> <strong>offerMgt</strong><br /> </td> 
   <td> This workflow deploys approved offers onto the online environment, as well as every category contained in the offer catalog.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Preview</strong><br /> </td> 
   <td> <strong>forecasting</strong><br /> </td> 
   <td> This workflow analyzes deliveries saved in the provisional calendar (creates provisional logs). It is triggered every day at 1am by default.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Tracking</strong><br /> </td> 
   <td> <strong>tracking</strong><br /> </td> 
   <td> This workflow performs the recovery and consolidation of tracking information. It also assures the recalculation of tracking and delivery statistics, especially those used by Message Center archiving workflows. By default, it is triggered once per hour. <br /> </td> 
  </tr> 
 </tbody> 
</table>

