---
title: Adobe Campaign Classic data model description
description: This document describes the basics of the Adobe Campaign Classic data model.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
---

# Campaign data model description{#data-model-description}

Adobe Campaign comes with a pre-defined data model. This section gives some details on the built-in tables of the Adobe Campaign data model and their interaction.

To access the description of each table, go to **[!UICONTROL Admin > Configuration > Data schemas]**, select a resource from the list and click the **[!UICONTROL Documentation]** tab.

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>The physical and logical structure of the data carried in the application is described in XML. It obeys a grammar specific to Adobe Campaign, called a schema. For more on Adobe Campaign schemas, read out this [section](../../configuration/using/about-schema-reference.md).

## Description of the main tables {#description-main-tables}

Adobe Campaign relies on a relational database containing tables that are linked together.

The following diagram shows the joins between the main business tables of the Adobe Campaign data model with the main fields shown for each.

![](assets/data-model_diagram.png)

![](assets/data-model_simplified-diagram.png)

The basic structure of the Adobe Campaign data model can be described as follows.

### NmsRecipient {#NmsRecipient}

The data model relies on a main table which is by default the Recipient table (**NmsRecipient**). This table enables to store all the marketing profiles.

This table matches the nms:recipient schema.

It is the default table used for the recipients of deliveries. As a result, it contains the information required for deliveries via the various channels:

* sEmail: email address.
* iEmailFormat: preferred format for emails (1 for Text, 2 for HTML and 0 if undefined).
* sAddress1, sAddress2, sAddress3, sAddress4, sZipCode, sCity are used to build the postal address (in keeping with the XPZ 10-011 AFNOR standard from May 1997).
* sPhone, sMobilePhone, sFax contain the phone, mobile phone and fax numbers respectively.
* iBlackList is the default opt-out flag used for the profiles (1 means "unsubscribed", 0 otherwise).

The iFolderId field is the foreign key that links the recipient to its execution folder. Refer to the description of the XtkFolder table below for further details.

The sCountryCode field is the 3166-1 Alpha 2 ISO code (2 characters) of the country associated with the recipient. This field is actually a foreign key on the country reference table (NmsCountry), which contains the country labels and other country code data. If the country is not populated, the value 'XX' is stored (and is used in place of a zero ID record).

For more on the Recipient table, see this [section](../../configuration/using/default-recipient-table.md).

### NmsGroup {#NmsGroup}

This table matches the **nms:group** schema.

It enables you to create **statical groups of recipients**. There is a many-to-many relation between recipients and groups. For example, one recipient can belong to several groups and one group can contain several recipients. Groups can be created manually, via an import or via delivery targeting. Groups are often used as delivery targets. There is a unique index on the field representing the internal name of the sName group. The group is linked to a folder (The key is iFolderId. See the description of the XtkFolder table below).

### NmsRcpGrpRel {#NmsRcpGrpRel}

The NmsRcpGrpRel relationship table only contains the two fields corresponding to the identifiers of the iRecipientId and iGroupId linked tables.

### NmsService {#NmsService}

This table matches the **nms:service** schema.

Services are entities which are similar to groups (static recipient groupings), except that they circulate more information and enable easy management of subscriptions and unsubscriptions via forms.

There is a unique index on the field representing the internal name of the sName service. The service is linked to a folder (The key is iFolderId. See the description of the XtkFolder table below). Finally, the iType field specifies the delivery channel of this service (0 for email, 1 for SMS, 2 for telephone, 3 for direct mail and 4 for fax).

### NmsSubscription {#NmsSubscription}

This table matches the **nms:subscription** schema.

It enables you to manage recipient subscriptions to information services.

### NmsSubHisto {#NmsSubHisto}

This table matches the **nms:subHisto** schema.

If the subscriptions are managed using web forms or the interface of the application, all susbcriptions and unsubscriptions are historized in the NmsSubHisto table. The iAction field specifies the action (0 for unsubscription and 1 for subscription) performed on the date stored in the tsDate field.

### NmsDelivery {#NmsDelivery}

This table matches the **nms:delivery** schema.

Each record in this table represents a **delivery action** or a **delivery template**. It contains all the necessary parameters for performing deliveries (the target, the content, etc.). Delivery (broadcast) logs (NmsBroadLog) and associated tracking URLs (NmsTrackingUrl) are created during the analysis phase (see below for further details on both of these tables).

There is a unique index on the field representing the internal name of the sInternalName delivery or scenario. The delivery is linked to an execution folder (The foreign key is iFolderProcessId. See the description of the XtkFolder table below).

### XtkFolder {#XtkFolder}

It contains **all the folders in the tree** visible in the **Navigation** tab of the console.

The folders are typed: The value of the sModel field specifies the type of data that can be contained in the folder. This field also enables the client console to display the data correctly with the corresponding forms. The possible values for this field are defined in the navTree.

The tree is managed by the iParentId and iChildCount fields. The sFullName field gives the full path of the folder in the tree. Finally, there is a unique index on the field representing the internal name of the sName folder.

## Delivery and tracking {#delivery-and-tracking}

### NmsBroadLogMsg {#NmsBroadLogMsg}

This table matches the **nms:broadLogMsg** schema.

It is an extension of the delivery log table.
