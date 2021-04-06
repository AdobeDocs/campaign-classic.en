---
solution: Campaign Classic
product: campaign
title: Extending a schema
description: Learn how to extend a schema
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
---
# Extending a schema{#extending-a-schema}

>[!IMPORTANT]
>
>Some built-in schemas must not be extended: mainly those for which the following settings are defined:   
>**dataSource="file"** and **mappingType="xmlFile"**.   
>The following schemas must not be extended: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publishing**, **nl:monitoring**, **nms:calendar**, **nms:remoteTracking**, **nms:userAgentRules**, **xtk:builder**, **xtk:connections**, **xtk:dbInit**, **xtk:funcList**, **xtk:fusion**, **xtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, **xtk:scriptContext**, **xtk:session**, **xtk:sqlSchema**, **xtk:strings**.
>This list is not exhaustive.

There are two methods for extending an existing schema:

1. Modifying the source schema directly.
1. Creating another schema with the same name but a different namespace. The advantage is that you can extend a table without needing to modify the original schema.

   The root element of the schema must contain the **extendedSchema** attribute with the name of the schema to be extended as its value.

   An extension schema does not have its own schema: the schema generated from the source schema will be filled in with the fields of the extension schema.

   >[!IMPORTANT]
   >
   >You are not allowed to modify the built-in schemas of the application, but rather the schema extension mechanism. Otherwise, modified schemas will not be updated at the time of future upgrades of the application. This can lead to malfunctions in the use of Adobe Campaign.

   **Example**: extension of the **nms:recipient** schema.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   The **nms:recipient** extended schema is filled in with the field populated in the extension schema:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   The **dependingSchemas** attribute on the root element of the schema references the dependences on the extension schemas.

   The **belongsTo** attribute on the field fills in the schema where it is declared.

>[!IMPORTANT]
>
>For the modifications to be taken into account, you need to regenerate schemas. For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.   
>If the modifications impact the structure of the database, you need to run an update. For more on this, refer to the [Updating the database structure](../../configuration/using/updating-the-database-structure.md) section.
