---
product: campaign
title: Types of maintenance
description: Types of maintenance
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 08e179aa-fd83-4c0a-879e-ab7aec168d92
---
# Types of maintenance{#types-of-maintenance}

## Application maintenance {#application-maintenance}

Adobe Campaign provides a built-in workflow which lets you schedule certain database maintenance tasks: the **database cleanup workflow**. This workflow carries out the following tasks:

* deletion of expired records,
* deletion of orphaned records and status reinitialization for expired objects,
* updating the database statistics.

>[!IMPORTANT]
>
>Please note that the cleanup task deals mostly with application level maintenance, not with RDBMS level maintenance (with the exception of statistics update). However, maintenance operations will be required on the database. Even if the database cleanup workflow runs successfully, this does not mean that the database is optimally tuned.

## Technical maintenance {#technical-maintenance}

The database cleanup workflow does not include any database maintenance tool: it is up to you to organize maintenance. To do this, you can either:

* work with your Database Administrator to set up database maintenance with third-party tools,
* use the Adobe Campaign workflow engine to schedule and track these maintenance activities.

These maintenance procedures must be carried out on a regular basis and should include the following:

* re-index frequently updated tables,
* compact/rebuild the tables to avoid fragmentation.

### Maintenance schedule {#maintenance-schedule}

You need to find the appropriate slots for performing these maintenance activities. They can heavily impact the database performance while running or even block the application (due to locking).

These tasks are typically run once a week during a period of low activity that does not collide with backups, data reloading or aggregate calculation. Some systems which are highly solicited require more frequent maintenance.

More in-depth maintenance, such as full table rebuilds, can be performed once a month, preferably with applications fully stopped since the system is unusable anyway.

### Rebuilding a table {#rebuilding-a-table}

Several strategies are available:

<table> 
 <thead> 
  <tr> 
   <th> Operations </th> 
   <th> Description </th> 
   <th> Benefits </th> 
   <th> Drawbacks </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Online defragmentation<br /> </td> 
   <td> Most database engines provide defragmentation methods.<br /> </td> 
   <td> Simply use the database defragmentation method. These methods typically take care of integrity issues by locking the data during defragmentation.<br /> </td> 
   <td> Depending on the database, these defragmentation methods can be provided as an RDBMS option (Oracle) and aren't always the most efficient way of dealing with larger tables.<br /> </td> 
  </tr> 
  <tr> 
   <td> Dump and restore<br /> </td> 
   <td> Dump the table to a file, delete the table in the database and restore from the dump.<br /> </td> 
   <td> This is the easiest way to defragment a table. Also the only solution when the database is almost full.<br /> </td> 
   <td> Since the table is deleted and recreated, the application cannot be left online, even in read only mode (the table is not available during the restore phase).<br /> </td> 
  </tr> 
  <tr> 
   <td> Duplicate, rename and drop<br /> </td> 
   <td> This creates a copy of a table and its indexes, then drops the existing one and renames the copy to take its place.<br /> </td> 
   <td> This method is faster than the first approach since it generates less IOs (no copy as a file and read from this file).<br /> </td> 
   <td> Requires twice the amount of space.<br /> All active processes writing to the table during the process must be stopped. However, reading processes will not be affected, since the table is swapped at the last moment once rebuilt. <br /> </td> 
  </tr> 
 </tbody> 
</table>
