---
product: campaign
title: Lost password
description: Lost password
feature: Monitoring, Access Management
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
TQID: https://experienceleague.adobe.com/MaAtheK2WnozPDuEO-qPq2l9u-AOGj5aGu2TgKslgLc
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring (Campaign)
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines (Campaign)
---
# Lost password{#lost-password}

>[!NOTE]
>
>This page only applies for operators connecting to Campaign with native authentication.

You can change or recover a lost password.
There are two possible scenarios:

* [Password lost by an Adobe Campaign operator](#password-lost-by-campaign-operator)
* [Internal password lost](#internal-password-lost) (on-premise customers only)

## Password lost by a Campaign operator {#password-lost-by-campaign-operator}

If an Adobe Campaign operator loses their password, you can change it.

>[!NOTE]
>
>This procedure only applies for operators connecting to Campaign with native authentication. For Adobe IMS authentication, refer to [this documentation](https://helpx.adobe.com/ie/manage-account/using/change-or-reset-password.html){target="_blank"}.

To reset a Campaign password, follow the steps below:

1. Connect via an operator with administrator rights.
1. Right-click an operator.
1. Select **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. Set the operator's new password. We recommend that the operator changes their password when they first reconnect.

## Internal password lost {#internal-password-lost}

>[!NOTE]
>
>This section only applies to on-premise customers only.

If the internal password is lost, you must reinitialize it.

To do this, apply the following procedure:

1. Edit the **/usr/local/neolane/nl6/conf/serverConf.xml** file.

1. Go to the **internalPassword** line.

    ```xml
    <!-- XTK authentication mode internalPassword : Password of internal account -->
    <xtk internalPassword="myPassword"/>
    ```

1. Delete the string in quotes, in this case: `myPassword`. You get the following line:

    ```xml
    <!-- XTK authentication mode internalPassword : Password of internal account -->
    <xtk internalPassword=""/>
    ```

1. Save changes and close the file.

1. Stop the `nlserver` process.

1. Configure the new password. To do this, enter the following commands:

    ```javascript
    nlserver config -internalpassword
    HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
    Enter current password.
    Password: (empty)
    Enter the new password.
    Password: 
    Confirmation 
    ```

1. Start the `nlserver` process.

1. You can now use your new password to connect in **Internal** mode.
