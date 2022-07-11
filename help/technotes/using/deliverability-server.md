---
product: campaign
title: Migrate to the new deliverability server
description: Learn how to implement Campaign deliverability server
hide: yes
hidefromtoc: yes
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
---
# Campaign Deliverability Server {#acc-deliverability}

Starting Campaign Classic v7 21.1 release, Adobe Campaign proposes a new deliverability server which bring high availability and addresses security compliance issues. Campaign Classic now synchronizes the deliverability rules, broadlogs and suppression address from and to new deliverability server. 

As a Campaign Classic customer, you must implement the new deliverability server.

>[!NOTE]
>
>For any questions about these changes, contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## What changed?{#acc-deliverability-changes}

Adobe is decommissioning older data centers due to security compliance reasons. Adobe Campaign Classic clients need to migrate to the new deliverability service, hosted on Amazon Web Service (AWS).

This new server guarantees a high availability (99.9)​, and provides secure and authenticated endpoints to enable campaign servers to fetch the required data: rather than connecting to the database for every request, the new deliverability server caches the data to serve the requests where possible. This mechanism improves the response time.​

## Are you impacted?{#acc-deliverability-impacts}

If you are using the old Adobe Campaign deliverability server, and your environment was implemented on a lower build than Campaign 21.1.1, you are impacted. You need to upgrade to Campaign 21.1 (or more).

Learn how to check your version [in this section](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## How to update?{#acc-deliverability-update}

As a **hosted customer**, Adobe will be working with you to upgrade your instance(s) to the newer version, and create the project in Adobe Developer Console.

As an **on-premise/hybrid customer**, you need to upgrade to one of the newer versions to benefit from the new deliverability server. Once all instances are upgraded, you will be able to [implement the new integration](#implementation-steps) to Adobe deliverability server, and ensure a seamless transition.

## Implementation steps {#implementation-steps}

As part of the new deliverability server integration, Campaign needs to communicate with Adobe Shared Services via an Identity Management Service (IMS) based authentication. The preferred way is to use the Adobe Developer based Gateway Token (also called Technical Account Token or Adobe IO JWT).


>[!WARNING]
>
>These steps should only be carried out by Hybrid and On-premise implementations.
>

### Prerequisites{#prerequisites}

Before starting the implementation, check your instance configuration.

1. Open Campaign client console and log on to Adobe Campaign as an Administrator.
1. Browse to **Administration > Platform > Options**.
1. Check the `DmRendering_cuid` option value is filled. 

    * If the option is filled, you can start the implementation.
    * If no value is filled, contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) to get your CUID.

        This option must be filled on all your Campaign instances (MKT, MID, RT, EXEC) with the same value.

### Step 1: Create/update your Adobe Developer Project {#adobe-io-project}

1. Access [Adobe Developer Console](https://developer.adobe.com/console/home) and log in with the Developer access of your Organization.

    >[!NOTE]
    >
    > Make sure you are logged into the correct Organization portal.

1. Select **[!UICONTROL Create new project]**.
    ![](assets/New-Project.png) 


    >[!CAUTION]
    >
    >If you are already using Adobe IO JWT authentication functionality for another integration, such as Analytics connector, or Adobe Triggers, then you must update your project by adding **Campaign API** to that project.
1. Choose **[!UICONTROL Add API]**.
    ![](assets/Add-API.png) 
1. In the **[!UICONTROL Add an API]** window, select **[!UICONTROL Adobe Campaign]**.
    ![](assets/AC-API.png) 
<!--1. Choose **[!UICONTROL Service Account (JWT)]** as the authentication type.-->
1. If your Client ID was empty, select **[!UICONTROL Generate a key pair]** to create a public and private key pair.
    ![](assets/Generate-a-key-pair.png) 

    The keys will then be automatically downloaded with a default expiry date of 365 days. Once expired, you will need to create a new key pair and update the integration in the configuration file. Using the Option 2, you can choose to manually create and upload your **[!UICONTROL Public key]** with a longer expiry date.
    ![](assets/New-key-pair.png) 

    >[!CAUTION]
    >
    >You should save the `config.zip` file when the download prompt comes up since you will not be able to download it again.

1. Click **[!UICONTROL Next]**.
1. Choose any existing **[!UICONTROL Product profile]** or create a new one if needed. No permission is required for this **[!UICONTROL Product profile]**. For more information on **[!UICONTROL Product Profiles]**, refer to [this page](https://helpx.adobe.com/enterprise/using/manage-developers.html).
    ![](assets/Product-Profile-API.png) 
    
    Then, click **[!UICONTROL Save configured API]**. 

1. From your project, select **[!UICONTROL Adobe Campaign]** and copy the following information under **[!UICONTROL Service Account (JWT)]**

    ![](assets/Config-API.png) 

    * **[!UICONTROL Client ID]**
    * **[!UICONTROL Client Secret]**
    * **[!UICONTROL Technical account ID]**
    * **[!UICONTROL Organization ID]**

>[!CAUTION]
>
>Adobe Developer certificate will expire after 12 months. You need to generate a new key pair every year.

### Step 2: Add the project credentials in Adobe Campaign {#add-credentials-campaign}

The private key should be encoded in base64 UTF-8 format. 

To do so:

1. Use the private key generated in the steps above.
1. Encode the private key using the following command: `base64 ./private.key > private.key.base64`. This will save the base64 content to a new file `private.key.base64`.

    >[!NOTE]
    >
    >Extra lines can sometimes be automatically added when copy/pasting the private key. Remember to remove it before encoding your private key.

1. Copy the contents from the file `private.key.base64`.
1. Login via SSH to each container where the Adobe Campaign instance is installed and add the Project credentials in Adobe Campaign by running the following command as `neolane` user. This will insert the **[!UICONTROL Technical Account]** credentials in the instance configuration file.

    ```
    nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
    ```

1. You must stop and then restart the server in order for the modification to be taken into account. You can also run a `config -reload` command.

### Step 3: Enable the new deliverability server

You can now enable the new deliverability server. To perform this:

1. Open the client console and log on to Adobe Campaign as an Administrator.
1. Browse to **Administration > Platform > Options**.
1. Access the `NewDeliverabilityServer_FeatureFlag` option and set the value to `1`. This configuration should be performed on all your Campaign instances (MKT, MID, RT, EXEC).

### Step 4: Validate your configuration

To check the integration is successful, follow the steps below:


1. Open the client console and log on to Adobe Campaign.
1. Browse to **Administration > Production > Technical workflows**.
1. Restart the **Update for deliverability** (deliverabilityUpdate) workflow. This should be performed on all your Campaign instances (MKT, MID, RT, EXEC). 
1. Check logs: the workflow should execute without errors. 

For more guidance, contact [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
