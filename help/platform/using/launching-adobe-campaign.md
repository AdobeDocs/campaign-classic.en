---
product: campaign
title: Launching Adobe Campaign
description: Launching Adobe Campaign
feature: Access Management, Permissions
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
TQID: https://experienceleague.adobe.com/qpZM0jaN1ht6QfReQBy1c7jONGdc2PQ0ORepDaVficQ
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
    internal-label: Profiles and audiences
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
    internal-label: Profiles
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
    internal-label: Audiences
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
    internal-label: Query Editor
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
---
# Launch Adobe Campaign {#launching-adobe-campaign}

Campaign Client console is a rich client which enables you to connect to your Campaign application server(s). Learn how to download and configure the client console in [this page](../../installation/using/installing-the-client-console.md).

>[!CAUTION]
>
>Check your system and tools compatibility with Adobe Campaign Client Console in the [Compatibility matrix](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

## Start Adobe Campaign {#starting-adobe-campaign}

You can start Adobe Campaign by selecting **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

The client console connection window lets you select or configure existing databases and connect to them using a user name and password:

![](assets/acc-logon.png)

## Connect to Adobe Campaign {#connecting-to-adobe-campaign}

### Connect with your Adobe ID

Campaign users connect to the Adobe Campaign console using their Adobe ID, through Adobe Identity Management System (IMS). They can use same ID all Adobe solutions. The connection is saved when using Adobe Campaign with other solutions. Learn more about Adobe IMS [on this page](https://helpx.adobe.com/enterprise/using/identity.html).

To configure Campaign Classic v7 connection with Adobe Identity Management Service (IMS), refer to [this page](../../integrations/using/about-adobe-id.md).

Once the configuration is done, learn how to connect to Campaign with your Adobe ID in the [Campaign v8 (console) documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/connect){target=_blank}.


### Connect with a login/password

You can also connect with a dedicated login/password. This connection is known as the Campaign 'Native Authentication':

1. Enter the operator account identifier in the **[!UICONTROL Login]** field.

   Your identifier is given by the administrator of your Adobe Campaign platform.

1. Enter your password in the **[!UICONTROL Password]** field.

   The first time you access the database, your password is the one given to you by the administrator. Once you are connected, you can change your password via the **[!UICONTROL Tools > Change password...]** menu. Details on operators and connections are available in [Access management](../../platform/using/access-management.md).

1. Click **[!UICONTROL LOG IN]** to confirm.

You can now access [Adobe Campaign workspace](../../platform/using/adobe-campaign-workspace.md).

## Set up connections {#setting-up-connections}

You can access the server connection settings via the link above the input zone.

![](assets/s_ncs_user_connections_management.png)

Learn how to set up connections in the [Campaign v8 (console) documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/connect#create-your-connection){target=_blank}. 

## Operators and permissions {#operators-and-permissions}

The identifiers and passwords of operators with access to the software and their respective permissions are defined by your Adobe Campaign system administrator in the **[!UICONTROL Administration > Access management > Operators]** node of the Adobe Campaign tree.

This functionality is detailed in the [Access management](../../platform/using/access-management.md) section.

## Get your Adobe Campaign version {#getting-your-campaign-version}

The **[!UICONTROL Help > About...]** menu lets you access the following information:

* **version** number for Campaign client console and application server
* **build** number for Campaign client console and application server
* a link to contact Adobe Customer Care
* links to Adobe Privacy Policy, Terms of Use and Cookies Policy

![](assets/about-acc.png)

Whenever you reach out to Adobe Customer Care team, you need to provide the version number and build number of your Adobe Campaign client console and application server.

