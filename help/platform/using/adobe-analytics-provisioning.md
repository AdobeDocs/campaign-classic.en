---
solution: Campaign Classic
product: campaign
title: Adobe Analytics connector
description: Learn more about Adobe Analytics connector provisioning
feature: Overview
role: User, Admin
level: Beginner
---
# Adobe Analytics Connector provisioning {#adobe-analytics-connector-provisioning}

![](../../assets/common.svg)

ACC supports both IMS User Login Configuration and IMS Technical Account Configuration.

Which IMS config is used in the different scenario is mentioned in the following list -

Configuring Integration from New UI
If the user is IMS Logged-in with ACC Client Console. The configuration will be based on the user's bearer token.
This means -
If you want to include evar A in the campaign's configuration but your user does not have access to evar A. You will not be able to include it in the campaign's configuration because NLSERVER will use your credentials to authorize with analytics apis.
If the user is logged in via ACC's built-in login/password. The configuration will be based on IMS Technical Account's bearer token.
This means -
In this case, the campaign will use the IMS Technical Account User's credentials to authorize with analytics and the access roles coming from this user will apply
Analytics Configuration UI is designed to work on both the above IMS Credentials and by-design, it will use Logged-In User's IMS Credentials if present else fallback to IMS Technical User Credentials.
Back-end workflows
backend workflows will always use IMS Technical Account Configuration no matter user is IMS Logged-In or not.

## Create an Adobe Analytics Product profile {#analytics-product-profile}

Product Profile determines the level of access a user has on Analytics Components. Do the steps mentioned below to configure a product profile for Adobe Analytics.

For more information on the Admin console, refer to the documentation.

1. From the [Admin console](https://adminconsole.adobe.com/), select your Adobe Analytics **[!UICONTROL Product]**.

    ![](assets/do-not-localize/triggers_1.png)

1. Click **[!UICONTROL New Profile]**.

    ![](assets/do-not-localize/triggers_2.png)

1. Add a **[!UICONTROL Product profile name]**, we suggest using the following syntax: `Analytics Classic`. Then, click **[!UICONTROL Next]**.
   
   This **[!UICONTROL Product profile]** should be used exclusively for Analytics Connector to prevent mid-configuration errors.

1. Open your newly created **[!UICONTROL Product profile]** and select the **[!UICONTROL Permissions]** tab.

    ![](assets/do-not-localize/triggers_3.png)

1. Configure the different capabilities clicking **[!UICONTROL Edit]** and select the permissions to assign to your **[!UICONTROL Product profile]** by clicking the plus (+) icon. 

   For more information on how to manage permissions, refer to the [Admin console documentation](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html).

1. For the **[!UICONTROL Report Suites]** capability, add the **[!UICONTROL Report Suites]** you need to use later on.
      
      If you don't have any report suites, you can create it following [these steps](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html).

    ![](assets/do-not-localize/triggers_4.png)

1. For the **[!UICONTROL Metrics]** capability, add the **[!UICONTROL Metrics]** you will need to configure later on.

1. For the **[!UICONTROL Dimensions]** capability, add the **[!UICONTROL Dimensions]** you will need to configure later on.

1. For the **[!UICONTROL Report Suite Tools]** capability, add the following permissions:

   * **[!UICONTROL Data Warehouse]**
   * **[!UICONTROL Site Catalyst]**
   * **[!UICONTROL Report Suite Read]**
   * **[!UICONTROL Report Suite Write]**
   * **[!UICONTROL Report suite Mgmt]**
   * **[!UICONTROL Conversion variables]**
   * **[!UICONTROL Success events]**
   * **[!UICONTROL Custom data Warehouse report]**
   * **[!UICONTROL Data sources manager]**
   * **[!UICONTROL Classifications]**

1. For the **[!UICONTROL Analytics Tools]** capability, add the following permissions:

   * **[!UICONTROL Code Manager - Web services]**
   * **[!UICONTROL Logs - Web services]**
   * **[!UICONTROL Permissions (Read and Write)]**
   * **[!UICONTROL Web services]**
   * **[!UICONTROL Web service access]**
   * **[!UICONTROL Calculated metric creation]**
   * **[!UICONTROL Segment creation]**

Your Product profile is now configured. You then need to create the Adobe I/O project.

## Create Adobe I/O Project {#create-adobe-io}

The new way of integrating with Analytics is through IMS Technical User Token since ACC is a single-tenant user-facing service. This is an IMS-based authentication and the ACC server-provided authentication details are of no relevance here. To onboard and configure the IMS Configuration for Technical Account. Please perform the following steps -

Pre-requisite
 Make sure that the provisioning team must have System Administrator Privileges for the customer's IMS Org as reflected here.

Make sure that you have already created and configured an analytics product profile. If you don't already have a product profile, please refer to the steps here to create and configure one.
Product profile is assigned to Technical Account User so that Campaign has access to analytics components. Read more here about analytics product profile.
Steps

1. Access Adobe I/O and log in as System Administrator of the IMS Organization.
   For more information on Admin roles, refer to this [page](https://helpx.adobe.com/enterprise/using/admin-roles.html).
   
1. Click **[!UICONTROL Create a new project]**.

    ![](assets/do-not-localize/triggers_5.png)

1. Click **[!UICONTROL Add to Project]** and select **[!UICONTROL API]**.

    ![](assets/do-not-localize/triggers_6.png)

1. Select [!DLN Adobe Analytics] and click **[!UICONTROL Next]**.

    ![](assets/do-not-localize/triggers_7.png)

1. Choose **[!UICONTROL Service Account (JWT)]** as authentication type and click **[!UICONTROL Next]**.

    ![](assets/do-not-localize/triggers_8.png)

1. Select the **[!UICONTROL Option 1: Generate a Key-Pair]** option and click **[!UICONTROL Generate a Key-Pair]**.

   The config.zip file will then be automatically downloaded.

    ![](assets/do-not-localize/triggers_9.png)

1. Click **[!UICONTROL Next]**. 

    ![](assets/do-not-localize/triggers_10.png)

1. Select the **[!UICONTROL Product profile]** created in the previous steps detailed in this [section](#analytics-product-profile).

1. Then, click **[!UICONTROL Save Configured API]**.

    ![](assets/do-not-localize/triggers_11.png)

1. From your project, select [!DNL Adobe Analytics] and copy the following information under **[!UICONTROL Service Account (JWT)]**:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

    ![](assets/do-not-localize/triggers_12.png)

1. Paste these Service Account credentials to the nlserver using the following command: 

   ```
   nlserver config -instance:<instanceName> -setimsjwtauth::<ImsOrgId>/<ClientId>/<TechnicalAccountId>/<ClientSecret>/<$(base64 -w0 /path/to/private.key)>
   ```

You can now start using the Analytics connector and track your customer behaviors.
