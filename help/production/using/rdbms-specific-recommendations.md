---
solution: Campaign Classic
product: campaign
title: RDBMS Specific recommendations
description: RDBMS Specific recommendations
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: a586d70b-1b7f-47c2-a821-635098a70e45
---
# RDBMS Specific recommendations{#rdbms-specific-recommendations}

To help you set up maintenance plans, this section lists some recommendations/best practices adapted to the various RDBMS engines that Adobe Campaign supports. However, these are only recommendations. It is up to you to adapt them to your needs, in keeping with your internal procedure and constraints. Your database administrator has the responsability of building and executing these plans.

## PostgreSQL {#postgresql}

### Detecting large tables {#detecting-large-tables}

1. You can add the following view to your database:

   ```
   create or replace view uvSpace
    as
    SELECT c1.relname AS tablename, c2.relname AS indexname, c2.relpages * 8 / 1024 AS size_mbytes, c2.relfilenode AS filename, 0 AS row_count
    FROM pg_class c1, pg_class c2, pg_index i
    WHERE c1.oid = i.indrelid AND i.indexrelid = c2.oid
    UNION 
    SELECT pg_class.relname AS tablename, NULL::"unknown" AS indexname, pg_class.relpages * 8 / 1024 AS size_mbytes, pg_class.relfilenode AS filename, cast(pg_class.reltuples as integer) AS row_count
    FROM pg_class
    WHERE pg_class.relkind = 'r'::"char"
    ORDER BY 3 DESC, 1, 2 DESC;
   
   ```

1. Running the following command allows you to spot large tables and indexes:

   ```
   select * from uvSpace;
   ```

### Simple maintenance {#simple-maintenance}

Under PostgreSQL, the typical commands you can use are **vacuum full** and **reindex**.

Here is a typical example of an SQL maintenance plan to be executed on a regular basis using these two commands:

```
vacuum full nmsdelivery;
 reindex table nmsdelivery;
 
 vacuum full nmsdeliverystat;
 reindex table nmsdeliverystat;
 
 vacuum full xtkworkflow;
 reindex table xtkworkflow;
 
 vacuum full xtkworkflowevent;
 reindex table xtkworkflowevent;
 
 vacuum full xtkworkflowjob;
 reindex table xtkworkflowjob;
 
 vacuum full xtkworkflowlog;
 reindex table xtkworkflowlog;
 
 vacuum full xtkworkflowtask;
 reindex table xtkworkflowtask;
 
 vacuum full xtkjoblog;
 reindex table xtkjoblog;
 
 vacuum full xtkjob;
 reindex table xtkjob;
 
 vacuum full nmsaddress;
 reindex table nmsaddress;

 vacuum full nmsdeliverypart;
 reindex table nmsdeliverypart;
 
 vacuum full nmsmirrorpageinfo;
 reindex table nmsmirrorpageinfo;

```

>[!NOTE]
>
>* Adobe recommends starting with smaller tables: this way if the process fails on large tables (where the risk of failure is highest), at least part of the maintenance has been completed.
>* Adobe recommands adding the tables specific to your data model which can be subject to significant updates. This can be the case for **NmsRecipient** if you have large daily data replication flows.
>* The **vacuum** and **re-index** commands will lock the table, which pauses some processes while maintenance is carried out.
>* For very large tables (typically above 5 Gb), **vacuum full** can become quite inefficient and take a very long time. Adobe does not recommend using it for the **YyyNmsBroadLogXxx** table.
>* This maintenance operation can be implemented by an Adobe Campaign workflow, using an **[!UICONTROL SQL]** activity (for more on this, refer to [this section](../../workflow/using/architecture.md)). Make sure you schedule maintenance for a low activity time which does not collide with your backup window.
>

### Rebuilding a database {#rebuilding-a-database}

PostgreSQL does not provide an easy way of performing an online table rebuild since **vacuum full** locks the table, thus preventing regular production. This means that maintenance has to be performed when the table is not used. You can either:

* perform maintenance when the Adobe Campaign platform is stopped,
* stop the various Adobe Campaign sub-services likely to write in the table being rebuilt (**nlserver stop wfserver instance_name** to stop the workflow process).

Here is an example of table defragmentation using specific functions to generate the necessary DDL. The following SQL lets you create two new functions: **GenRebuildTablePart1** and **GenRebuildTablePart2**, which can be used to generate the necessary DDL to recreate a table.

* The first function lets you create a work table (** _tmp** here) which is a copy of the original table.
* The second function then deletes the original table and renames the work table and its indexes.
* Using two functions instead of one means that if the first one fails, you don't run the risk of deleting the original table.

```
 -- --------------------------------------------------------------------------
 -- Generate the CREATE TABLE DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenTableDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecFld RECORD;
 vstrDDL text;
 vstrFields text;
 vstrNsTable text;
 vstrTableSpace text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 SELECT
 pg_catalog.quote_ident(n.nspname) || '.' || pg_catalog.quote_ident(c.relname),
 pg_catalog.quote_ident(t.spcname)
 INTO
 vstrNsTable, vstrTableSpace
 FROM
 pg_namespace n, pg_class c left outer join pg_tablespace t on c.reltablespace = t.oid
 WHERE
 n.oid = c.relnamespace AND
 c.relname = vstrTable;
 
 vstrDDL = 'CREATE TABLE ' || vstrNsTable || '_tmp(';
 
 vstrFields = ;
 FOR vrecFld IN
 SELECT
 pg_catalog.quote_ident(a.attname) ||
 ' ' || t.typname ||
 case when t.typname='varchar' then '(' || cast(a.atttypmod-4 as text) || ')'
 when t.typname='numeric' then '(' || cast((a.atttypmod-4)/65536 as text) || ',' || cast((a.atttypmod-4)%65536 as text) || ')'
 else end ||
 case when a.attnotnull then ' not null' else end ||
 case when a.atthasdef then ' default '|| d.adsrc else end as DDL
 FROM
 pg_type t, pg_class c, pg_attribute a LEFT OUTER JOIN pg_attrdef d ON d.adrelid=a.attrelid and d.adnum=a.attnum
 WHERE 
 a.attnum > 0 AND
 a.attrelid = c.oid AND
 t.oid = a.atttypid AND
 c.relname = vstrTable
 ORDER BY
 a.attnum
 LOOP
 IF vstrFields <> THEN
 vstrFields = vstrFields || ',' || chr(10) || ' ';
 ELSE
 vstrFields = vstrFields || chr(10) || ' ';
 END IF;
 vstrFields = vstrFields || vrecFld.DDL;
 END LOOP;
 
 vstrDDL = vstrDDL || vstrFields || chr(10) || ')';
 if vstrTableSpace <> then
 vstrDDL = vstrDDL || ' TABLESPACE ' || vstrTableSpace;
 end if;
 vstrDDL = vstrDDL || ';' || chr(10);
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the CREATE INDEX DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 viFld integer;
 vstrFld text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
 SELECT
 i.indkey, i.indisunique,
 pg_catalog.quote_ident(c.relname) as tablename,
 pg_catalog.quote_ident(ic.relname) as indexname,
 pg_catalog.quote_ident(t.spcname) as tablespace
 FROM
 pg_class c, pg_index i, pg_class ic left outer join pg_tablespace t on ic.reltablespace = t.oid
 WHERE
 i.indexrelid = ic.oid AND
 i.indrelid = c.oid AND
 c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'CREATE ';
  if vrecIndex.indisunique then
  vstrDDL = vstrDDL || 'UNIQUE ';
  end if;
  vstrDDL = vstrDDL ||
   'INDEX ' ||vrecIndex.indexname || '_tmp ON ' ||
   vrecIndex.tablename || '_tmp(';
 
  FOR viFld IN array_lower(vrecIndex.indkey, 1) .. array_upper(vrecIndex.indkey, 1) LOOP
  SELECT pg_catalog.quote_ident(a.attname) INTO vstrFld 
  FROM 
   pg_attribute a, pg_class c
  WHERE 
   a.attnum = vrecIndex.indkey[viFld] AND
   a.attrelid = c.oid AND c.relname=vstrTable;
  
  vstrDDL = vstrDDL || vstrFld;
  if viFld <> array_upper(vrecIndex.indkey, 1) then
   vstrDDL = vstrDDL || ', ';
  end if;
  END LOOP;
  vstrDDL = vstrDDL || ')';
 
  if vrecIndex.tablespace <> then
  vstrDDL = vstrDDL || 'TABLESPACE ' || vrecIndex.tablespace;
  end if;
  vstrDDL = vstrDDL || ';' || chr(10);
 
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the ALTER INDEX RENAME for a table
 -- --------------------------------------------------------------------------
 create or replace function GenRenameIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
  SELECT
  pg_catalog.quote_ident(n.nspname) as namespace,
  pg_catalog.quote_ident(ic.relname) as indexname
  FROM
  pg_namespace n, pg_class c, pg_index i, pg_class ic
  WHERE
  i.indexrelid = ic.oid AND
  n.oid = ic.relnamespace AND
  i.indrelid = c.oid AND
  c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'ALTER INDEX ' || vrecIndex.namespace || '.' || vrecIndex.indexname ||
    '_tmp RENAME TO ' || vrecIndex.indexname ||
    ';' || chr(10);
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Build a copy of a table, with index
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart1(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = ;
 
 SELECT GenTableDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 vstrDDL = vstrDDL|| 'INSERT INTO ' || vstrTable || '_tmp SELECT * FROM ' || vstrTable || ';'||chr(10);
 SELECT GenIndexDDL(vstrTable) INTO vstrTmp;
 
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 vstrDDL = vstrDDL|| 'VACUUM ANALYSE '|| vstrTable || '_tmp;' ||chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
 
 -- --------------------------------------------------------------------------
 -- Drop the original table and rename the copy
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart2(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = 'DROP TABLE ' || vstrTable||';'|| chr(10);
 vstrDDL = vstrDDL|| 'ALTER TABLE ' || vstrTable || '_tmp RENAME TO ' || vstrTable ||';'|| chr(10);
 
 SELECT GenRenameIndexDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;

```

The following example can be used in a workflow to rebuild the required tables rather than using the **vacuum/rebuild** command:

```
function sqlGetMemo(strSql)
 {
 var res = sqlSelect("s, m:memo", strSql);
 return res.s.m.toString();
 }

 function RebuildTable(strTable)
 {
 // Rebuild a table_tmp
 var strSql = sqlGetMemo("select GenRebuildTablePart1('"+strTable+"')");
 logInfo("Rebuilding table '"+strTable+"'...");
 // logInfo(strSql);
 sqlExec(strSql);
 
 // If fails, there is an exception thrown and so we do not delete the original table
 strSql = sqlGetMemo("select GenRebuildTablePart2('"+strTable+"')");
 logInfo("Swapping table '"+strTable+"'...");
 //logInfo(strSql);
 sqlExec(strSql);
 }
 
 RebuildTable('nmsrecipient');
 RebuildTable('nmsrcpgrlrel');
 // ... other tables here

```

## Oracle {#oracle}

Please contact your database administrator to find out about the procedures best suited to your version of Oracle.

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>For Microsoft SQL Server, you can use the maintenance plan detailed on [this page](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html).

The example below concerns Microsoft SQL Server 2005. If you are using another version, contact your database administrator to find out about maintenance procedures.

1. First, connect to Microsoft SQL Server Management Studio, with a login with administrator rights.
1. Go to the **[!UICONTROL Management > Maintenance Plans]** folder, right-click on it and choose **[!UICONTROL Maintenance Plan Wizard]** 
1. Click **[!UICONTROL Next]** when the first page comes up.
1. Select the type of maintenance plan you want to create (separate schedules for each task or single schedule for the whole plan), then click the **[!UICONTROL Change...]** button.
1. In the **[!UICONTROL Job schedule properties]** window, select the desired execution settings and click **[!UICONTROL OK]** , then click **[!UICONTROL Next]** .
1. Select the maintenance tasks you want to perform, then click **[!UICONTROL Next]** .

   >[!NOTE]
   >
   >We recommend performing at least the maintenance tasks shown below. You may also select the statistics update task, although it is already carried out by the database cleanup workflow.

1. In the drop-down list, select the database which you want to run the **[!UICONTROL Database Check Integrity]** task on.
1. Select the database and click **[!UICONTROL OK]** , then click **[!UICONTROL Next]** .
1. Configure the maximum size allocated to your database, then click **[!UICONTROL Next]** .

   >[!NOTE]
   >
   >If the size of the database exceeds this threshold, the maintenance plan will try to delete unused data to free up space.

1. Reorganize or rebuild the index:

    * If the index fragmentation rate is between 10% and 40%, a reorganization is recommended.

      Choose which databases and objects (tables or views) you want to reorganize, then click **[!UICONTROL Next]** .

      >[!NOTE]
      >
      >Depending on your configuration you can choose either the previously selected tables, or all tables in your database.

    * If the index fragmentation rate is higher than 40%, a rebuild is recommended.

      Select the options you want to apply to the index rebuild task, then click **[!UICONTROL Next]** .

      >[!NOTE]
      >
      >The rebuild index process is more constricting in terms of processor use and it locks the database resources. Tick the **[!UICONTROL Keep index online while reindexing]** option if you want the index to be available during the rebuild.

1. Select the options you want to display in the activity report, then click **[!UICONTROL Next]** .
1. Check the list of tasks configured for the maintenance plan, then click **[!UICONTROL Finish]** .

   A summary of the maintenance plan and the statuses of its various steps is displayed.

1. Once the maintenance plan is complete, click **[!UICONTROL Close]** .
1. In the Microsoft SQL Server explorer, double-click the **[!UICONTROL Management > Maintenance Plans]** folder.
1. Select the Adobe Campaign maintenance plan: the various steps are detailed in a workflow.

   Note that an object has been created in the **[!UICONTROL SQL Server Agent > Jobs]** folder. This object lets you start the maintenance plan. In our example there is only one object since all the maintenance tasks are part of the same plan.

   >[!IMPORTANT]
   >
   >For this object to run, the Microsoft SQL Server agent must be enabled.

**Configuring a separate database for working tables**

>[!NOTE]
>
>This configuration is optional.

The **WdbcOptions_TempDbName** option allows you to configure a separate database for working tables on Microsoft SQL Server. This optimizes backups and replication.

This option can be used if you want working tables (for example, the tables created during the execution of a workflow) to be created on another database.

When you set the option to "tempdb.dbo.", working tables will be created on the default temporary database of Microsoft SQL Server. The database administrator needs to allow write access to the tempdb database.

If the option is set, it will be used on all Microsoft SQL Server databases that are configured in Adobe Campaign (main database and external accounts). Note that if two external accounts share the same server, conflicts can happen (as the tempdb will be unique). In the same way, if two Campaign instances use the same MSSQL server, there could be conflicts if they use the same tempdb.
