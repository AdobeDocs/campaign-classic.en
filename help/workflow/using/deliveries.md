---
product: campaign
title: Deliveries
description: Learn more about default Deliveries workflows
audience: workflow
content-type: reference
topic-tags: technical-workflows
---

# Deliveries{#deliveries}

The workflows detailed below are installed with the **Deliveries** module by default.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Internal name</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Reporting aggregates</span> <br /> </td> 
   <td> <span class="uicontrol">reportingAggregates</span> <br /> </td> 
   <td> This workflow updates aggregates used in reports. It is triggered every day at 2am by default.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Billing</span> <br /> </td> 
   <td> <span class="uicontrol">billing</span> <br /> </td> 
   <td> This workflow sends the system activity report to the 'billing' operator by email. It is triggered the 25th of every month by default.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Billing (active profiles)</span> <br /> </td> 
   <td> <span class="uicontrol">billingActiveContactCount</span> <br /> </td> 
   <td> <p>This wokflow counts the number of active profiles. It is triggered every night at 1am by default.</p> <p>“<strong>Profile</strong>” means a record of information (e.g.: a record in the nmsRecipient table or an external table containing a cookie ID, Customer ID, mobile identifier or other information relevant to a particular channel) representing an end-customer, prospect, or lead. Billing only concerns Profiles that are “active”. A Profile is considered “active” if the Profile has been targeted or communicated within the past 12 months via any channel.</p> <p>Facebook and Twitter channels are not taken into account.</p> <p>You can have an overview of the <span class="uicontrol">Number of active profiles</span> from the <span class="uicontrol">Administration</span> &gt; <span class="uicontrol">Campaign Management</span> &gt; <span class="uicontrol">Customer metrics</span> menu.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Alias cleansing</span> <br /> </td> 
   <td> <span class="uicontrol">aliasCleansing</span> <br /> </td> 
   <td> This workflow standardizes enumeration values. It is triggered every day at 3am by default.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Update for deliverability</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> This workflow lets you create the list of bounce mail qualification rules, as well as the list of domains and MXs in the platform. This workflow only works if the HTTPS port is open. These lists are not updated unless the Deliverability module is installed.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Database cleanup</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>This workflow is the database maintenance workflow: it makes different calculations from the statistics and processes, and deletes obsolete data from the database according to the defined configuration in the deployment assistant. It is triggered every day at 4am by default.</p> <p>For more information, refer to this <a href="../../production/using/database-cleanup-workflow.md">page</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Paused workflows cleanup</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>This workflow analyzes paused workflows that have severity set to normal and triggers warnings and notifications when they have been paused for too long. After a month, paused technical workflows are stopped unconditionally. By default, it is triggered every Monday at 5 am.</p> <p>For more information, refer to <a href="monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">Handling of paused workflows</a>.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Offer notification</span> <br /> </td> 
   <td> <span class="uicontrol">offerMgt</span> <br /> </td> 
   <td> This workflow deploys approved offers onto the online environment, as well as every category contained in the offer catalog.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Forecasting</span> <br /> </td> 
   <td> <span class="uicontrol">forecasting</span> <br /> </td> 
   <td> This workflow analyzes deliveries saved in the provisional calendar (creates provisional logs). It is triggered every day at 1am by default.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Tracking</span> <br /> </td> 
   <td> <span class="uicontrol">tracking</span> <br /> </td> 
   <td> This workflow performs the recovery and consolidation of tracking information. It also assures the recalculation of tracking and delivery statistics, especially those used by Message Center archiving workflows. By default, it is triggered once per hour. <br /> </td> 
  </tr> 
 </tbody> 
</table>

