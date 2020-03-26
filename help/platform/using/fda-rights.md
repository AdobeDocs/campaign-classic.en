---
title: FDA rights
seo-title: FDA rights
description: FDA rights
seo-description: 
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
---

# FDA rights {#fda-rights}

| &nbsp;| Snowflake  | Redshift | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| Connecting to remote database  | USAGE ON WAREHOUSE and USAGE ON DATABASE privileges  | Creating a user linked to the AWS account  | CREATE SESSION privilege  | CONNECT permission | CONNECT privilege | Creating a user tied to a remote host who has ALL PRIVILEGES |
| Creating tables |  CREATE TABLE ON SCHEMA privilege | CREATE privilege  |  CREATE TABLE privilege |  CREATE TABLE permission | CREATE privilege  | CREATE privilege |
| Creating indexes | No Index support in Snowflake  |  CREATE privilege | INDEX or CREATE ANY INDEX privilege  | ALTER permission  | CREATE privilege  | INDEX privilege |
|  Creating functions |  CREATE FUNCTION ON SCHEMA privilege |  USAGE ON LANGUAGE plpythonu privilege to be able to call external python scripts |  CREATE PROCEDURE or CREATE ANY PROCEDURE privilege |  CREATE FUNCTION permission | USAGE privilege | CREATE ROUTINE privilege |
|  Creating procedures | CREATE PROCEDURE ON SCHEMA privilege  |  USAGE ON LANGUAGE plpythonu privilege to be able to call external python scripts | CREATE PROCEDURE or CREATE ANY PROCEDURE privilege  |  CREATE PROCEDURE permission | USAGE privilege (procedures are functions)  | CREATE ROUTINE privilege |
| Removing objects (tables, indexes, functions, procedures)  |  Owning the object | Owning the object or being a superuser  |  DROP ANY <object> privilege * |  ALTER permission |  Table: owning the table Index: owning the index Function: owning the function | DROP privilege |
| Monitoring executions  | MONITOR privilege on the required object  |  No privilege required to use EXPLAIN command | INSERT and SELECT privilege and necessary privilege to execute the statement for which the EXPLAIN PLAN is based on  | SHOWPLAN permission  | No privilege required to use EXPLAIN statement  | SELECT privilege |
|  Writing data |  INSERT and/or UPDATE privileges (depending on write operation) | INSERT and UPDATE privileges  | INSERT and UPDATE or INSERT and UPDATE ANY TABLE privileges  |  INSERT and UPDATE permissions |  INSERT and UPDATE privileges | INSERT and UPDATE privileges |
| Loading data into tables  |  CREATE STAGE ON SCHEMA, SELECT and INSERT on the target table privileges |  SELECT and INSERT privileges | SELECT and INSERT privileges  | INSERT, ADMINISTER BULK OPERATIONS and ALTER TABLE permissions  |  SELECT and INSERT privileges | FILE privilege |
| Accessing to client data  |  SELECT on (FUTURE) TABLE(S) or VIEW(S) privilege(s) | SELECT privilege  | SELECT or SELECT ANY TABLE privilege  | SELECT permission  | SELECT privilege  | SELECT privilege |
|  Accessing to metadata  | SELECT on INFORMATION_SCHEMA SCHEMA privilege  |  SELECT privilege | No privilege required to use DESCRIBE statement  | VIEW DEFINITION permission  | No privilege required to use "\d table" command  | SELECT privilege |

| &nbsp;|  DB2 UDB  | TeraData | InfiniDB | Sybase IQ / Sybase ASE | Netezza | Greenplum |AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Connecting to remote database**  | CONNECT authority | CONNECT privilege| Creating a user tied to a remote host who has ALL PRIVILEGES| No permission required to use the CONNECT statement | No privilege required | CONNECT privilege | CONNECT privilege |
| **Creating tables** | CREATETAB authority | CREATE TABLE or TABLE keyword | CREATE privilege| RESOURCE authority and CREATE permission| TABLE privilege| CREATE privilege | CREATE privilege |
|**Creating indexes** | INDEX privilege | CREATE INDEX or INDEX keyword | INDEX privilege | RESOURCE authority and CREATE permission| INDEX privilege | CREATE privilege | CREATE privilege|
|  **Creating functions** | IMPLICIT_SCHEMA authority or CREATEIN privilege | CREATE FUNCTION or FUNCTION keyword | CREATE ROUTINE privilege| RESOURCE authority or DBA authority for Java functions | FUNCTION privilege | USAGE privilege | USAGE privilege |
|  **Creating procedures** | IMPLICIT_SCHEMA authority or CREATEIN privilege | CREATE PROCEDURE or PROCEDURE keyword | CREATE ROUTINE privilege| RESOURCE authority| PROCEDURE privilege | USAGE privilege | USAGE privilege |
| **Removing objects (tables, indexes, functions, procedures)**  | DROPIN privilege or CONTROL privilege or owning the object | DROP <&nbsp;object&nbsp;> * or object related keyword| DROP privilege | Owning the object or DBA authority | DROP privilege | Owning the object  | Owning the object  |
| **Monitoring executions** | EXPLAIN authority | No privilege required to use EXPLAIN statement |SELECT privilege | Only a system Administrator can execute sp_showplan| No privilege required to use EXPLAIN statement | No privilege required to use EXPLAIN statement | No privilege required to use EXPLAIN statement |
|  **Writing data** | INSERT and UPDATE privileges or DATAACCESS authority | INSERT and UPDATE privileges | INSERT and UPDATE privileges| INSERT and UPDATE permissions| INSERT and UPDATE privileges | INSERT and UPDATE privileges | INSERT and UPDATE privileges |
| **Loading data into tables**  | LOAD authority | SELECT and INSERT privileges to respectively use COPY TO and COPY FROM statements| FILE privilege| Be the owner of the table or ALTER permission. Depending on the -gl option, LOAD TABLE might only be performed if the user has the DBA authority| SELECT and INSERT privileges| SELECT and INSERT privileges | SELECT and INSERT privileges |
| **Accessing to client data** | INSERT/UPDATE privileges or DATAACCESS authority| SELECT privilege| SELECT privilege | SELECT permission| SELECT privilege | SELECT privilege| SELECT privilege |
|  **Accessing to metadata**  | No authorization required to use DESCRIBE statement| SHOW privilege| SELECT privilege | No permission required to use DESCRIBE statement| No privilege required to use "\d table" command | No privilege required to use "\d table" command | No privilege required to use SHOW command |