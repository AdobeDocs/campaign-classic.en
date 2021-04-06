---
solution: Campaign Classic
product: campaign
title: Synchronizing web applications
description: Synchronizing web applications
audience: integrations
content-type: reference
topic-tags: acs-connector
exl-id: 975bdc94-5da4-45ae-a3bd-e8674b447098
---
# Synchronizing web applications{#synchronizing-web-applications}

In this use case, we will send a communication, using Campaign Standard, that includes a link to a Campaign v7 web application. When the recipient clicks on the link in the email, the web application displays a form containing several fields preloaded with the recipient's data as well as a subscription link to a newsletter. The recipient can update his data as well as subscribe to the service. His profile will be updated in Campaign v7 and the information will be replicated in Campaign Standard.

If you have many services and web applications in Campaign v7, you might choose not to recreate them all in Campaign Standard. ACS Connector allows you to use all your existing Campaign v7 web applications and services and link them to a delivery sent by Campaign Standard.

## Prerequisites {#prerequisites}

To achieve this, you need:

* Recipients stored in Campaign v7 database and synchronized with Campaign Standard. Refer to the [Synchronizing profiles](../../integrations/using/synchronizing-profiles.md) section.
* a service and a web application created and published in Campaign v7.
* the web application must contain a **[!UICONTROL Pre-loading]** activity using the **[!UICONTROL Adobe Campaign encryption]** identification method.

## Creating the web application and service {#creating-the-web-application-and-service}

In Campaign v7, you can create web applications that allow recipients to subscribe to a service. The web application and service are designed and stored in Campaign v7 and you can update this service via a Campaign Standard communication. To learn more on web applications in Campaign v7, refer to [this section](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes).

In Campaign v7, the following objects have been created:

* a newsletter service
* a web application containing a **[!UICONTROL Pre-loading]**, a **[!UICONTROL Page]** and a **[!UICONTROL Storage]** activity.

1. Go to **[!UICONTROL Resources > Online > Web applications]** and select an existing web application.

   ![](assets/acs_connect_lp_2.png)

1. Edit the **[!UICONTROL Preloading]** activity. The **[!UICONTROL Auto-load data referenced in the form]** box is checked and the **[!UICONTROL Adobe Campaign encryption]** identification method is selected. This will allow the web application to preload the form's fields with the data stored in the Adobe Campaign database. See [this document](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

   ![](assets/acs_connect_lp_4.png)

1. Edit the **[!UICONTROL Page]**. Three fields (Name, Email and Phone) have been included, as well as a check box to invite the recipient to subscribe to a newsletter (**[!UICONTROL Newsletter]** service). 

   ![](assets/acs_connect_lp_3.png)

1. Go to **[!UICONTROL Profiles and Target > Services and subscriptions]** and open the **[!UICONTROL Newsletter]** service. This is the service that will be updated from the Campaign Standard communication. You can see that no recipient has subscribed to this service yet.

   ![](assets/acs_connect_lp_5.png)

1. Go to **[!UICONTROL Profiles and Targets > Recipient]** and select a recipient. You can see that he has not subscribed to the service yet.

   ![](assets/acs_connect_lp_6.png)

## Replicating the data {#replicating-the-data}

In order to replicate the needed data between Campaign v7 and Campaign Standard, several replication workflow templates are available. The **[!UICONTROL Profiles replication]** workflow automatically replicates all the Campaign v7 recipients to Campaign Standard. See [Technical and replication workflows](../../integrations/using/acs-connector-principles-and-data-cycle.md#technical-and-replication-workflows). The **[!UICONTROL Landing pages replication]** workflow enables the replication of the web applications we want to use in Campaign Standard.

![](assets/acs_connect_lp_1.png)

To check that the data has been replicated correctly, follow these steps in Campaign Standard:

1. From the home screen, click on **[!UICONTROL Customer profiles]**.

   ![](assets/acs_connect_lp_7.png)

1. Search for your Campaign v7 recipient and check that he appears in Campaign Standard.

   ![](assets/acs_connect_lp_8.png)

1. From the top bar, click on **[!UICONTROL Marketing activities]**, and search for the Campaign v7 web application. It appears as a landing page in Campaign Standard.

   ![](assets/acs_connect_lp_9.png)

1. Click the **[!UICONTROL Adobe Campaign]** logo, in the top left corner, then select **Profiles & audiences > Services** and check that the newsletter service is there as well.

   ![](assets/acs_connect_lp_10.png)

## Designing and sending the email {#designing-and-sending-the-email}

In this part, we'll see how to include a link, in a Campaign Standard email, to the landing page replicated from a Campaign v7 web application.

The steps to create, design and send the email are the same as for a classic email. See the [Adobe Campaign Standard](https://helpx.adobe.com/support/campaign/standard.html) documentation.

1. Create a new email and choose one or more replicated profiles as the audience.
1. Edit your content and insert a **[!UICONTROL Link to a landing page]**. 

   ![](assets/acs_connect_lp_12.png)

1. Select the landing page that was replicated from the Campaign v7 web application.

   ![](assets/acs_connect_lp_13.png)

1. Prepare your email, send your proofs and send the final email.
1. One of the recipients opens the email and clicks on the link to the newsletter subscription.

   ![](assets/acs_connect_lp_14.png)

1. He adds a telephone number and checks the newsletter subscription box.

   ![](assets/acs_connect_lp_15.png)

## Retrieving the updated information {#retrieving-the-updated-information}

When the recipient updates his data from via the web application, Adobe Campaign v7 synchronously retrieves the updated information. It is then replicated from Campaign v7 to Campaign Standard.

1. In Campaign v7, go to **[!UICONTROL Profiles and Target > Services and subscriptions]** and open the **[!UICONTROL Newsletter]** service. You can see that the recipient now appears in the subscribers list.

   ![](assets/acs_connect_lp_16.png)

1. Go to **[!UICONTROL Profiles and Targets > Recipient]** and select the recipient. You can see that the phone number is now stored.

   ![](assets/acs_connect_lp_17.png)

1. In the **[!UICONTROL Subscriptions]** tab, we can also see that he has subscribed to the newsletter service.

   ![](assets/acs_connect_lp_18.png)

1. Wait a few minutes for the profile replication workflow to run.
1. In Campaign Standard, access your recipient profile to check that the updated data has correctly been replicated from Campaign v7.

   ![](assets/acs_connect_lp_19.png)

1. Edit the profile. You can see that the telephone number has been updated.

   ![](assets/acs_connect_lp_20.png)

1. Click on the **[!UICONTROL Subscriptions]** tab. The newsletter service now appears.

   ![](assets/acs_connect_lp_21.png)
