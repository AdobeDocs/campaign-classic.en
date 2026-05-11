---
product: campaign
title: Extend a schema
description: Learn how to extend a schema
role: Developer
feature: Schema Extension
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
TQID: https://experienceleague.adobe.com/w-Pe9dOgxIRB0KnOggStMDqzaNkCFGsh-5sOISc-t2E
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
---
# Extend a schema{#extending-a-schema}

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

   The **dependingSchemas** attribute on the root element of the schema references the dependencies on the extension schemas.

   The **belongsTo** attribute on the field fills in the schema where it is declared.

>[!IMPORTANT]
>
>For the modifications to be taken into account, you need to regenerate schemas. For more on this, refer to [this page](../../configuration/using/regenerating-schemas.md).   
>If the modifications impact the structure of the database, you need to run an update. For more on this, refer to [this page](../../configuration/using/updating-the-database-structure.md).
