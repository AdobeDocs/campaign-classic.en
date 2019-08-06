---
title: Email enrichment with custom date fields
seo-title: Email enrichment with custom date fields
description: Email enrichment with custom date fields
seo-description: 
page-status-flag: never-activated
uuid: eaecd535-159c-4b55-ae3b-36c692935bbe
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: 002fd70b-c50f-4bee-aacf-e248680b950b
index: y
internal: n
snippet: y
---

# Email enrichment with custom date fields{#email-enrichment-with-custom-date-fields}

In this example, we want to send an email with custom data fields to recipients who will celebrate their birthdays this month. The email will include a coupon valid one week before and after their birthdays.

We need to target recipients from a list who will celebrate their birthdays this month with a **Split** activity. Then, using the** Enrichment** activity, the custom data field will act as validity dates in the email for the customer's special offer.

![](assets/uc_enrichment.png)

To create this example, apply the following steps:

1. In the **Targeting and workflows** tab of your campaign, drag and drop a **Read list** activity to target your list of recipients.
1. The list to be processed can be specified explicitly, computed by a script or localized dynamically, according to options selected and parameters defined here.

   ![](assets/uc_enrichment_1.png)

1. Add a **Split** activity to differentiate recipients who will celebrate their birthdays this month from other recipients.
1. To split your list, in the **Filtering of selected records** category, select **Add a filtering condition on the inbound population**. Then, click **Edit**.

   ![](assets/uc_enrichment_2.png)

1. Select **Filtering conditions** then click the **Edit expression** button to filter the month of the recipient's birthday.

   ![](assets/uc_enrichment_3.png)

1. Click **Advanced Selection** then **Edit the formula using an expression** and add the following expression: Month(@birthDate).
1. In the **Operator** column, select the **equal to** .
1. Further filter your condition, by adding the **Value** month of the current date: Month(GetDate()).

   This will query recipients whose birthday's month corresponds to the current month.

   ![](assets/uc_enrichment_4.png)

1. Click **Finish**. Then, in the** General** tab of your **Split** activity, click the **Generate complement** in the **Results** category.

   With the **Complement** result, you can add a delivery activity or update a list. Here, we just added an **End** activity.

   ![](assets/uc_enrichment_6.png)

You now need to configure your **Enrichment** activity:

1. Add an **Enrichment** activity after your subset to add your custom date fields.

   ![](assets/uc_enrichment_7.png)

1. Open your **Enrichment** activity. In the **Complementary information** category, click **Add data**.

   ![](assets/uc_enrichment_8.png)

1. Select **Data linked to the filtering dimension** then **Data of the filtering dimension**.
1. Click the **Add** button. 

   ![](assets/uc_enrichment_9.png)

1. Add a **Label**. Then, in the **Expression** column, click **Edit expression**.

   ![](assets/uc_enrichment_10.png)

1. First, we need to target the week before the birthdate as the **Validity start date** with the following **Expression**: SubDays([target/@birthDate], 7).

   ![](assets/uc_enrichment_11.png)

1. Then, to create the custom date field **Validity end date** which will target the week after the birthdate, you need to add the **Expression**: AddDays([target/@birthDate], 7).

   You can add a label to your expression.

   ![](assets/uc_enrichment_12.png)

1. Click **Ok**. Your enrichment is now ready.

After your **Enrichment** activity, you can add a delivery. In this case, we added an email delivery to send recipients a special offer with validity dates to customers celebrating their birthdays this month.

1. Drag and drop an **Email delivery** activity after your **Enrichment** activity.

   ![](assets/uc_enrichment_15.png)

1. Double-click your **Email delivery** activity to start personalizing your delivery.
1. Add a **Label** to your delivery and click **Continue**.
1. Click **Save** to create your email delivery.
1. Check in the** Approval** tab of the email delivery **Properties** that the **Confirm delivery before sending option** is checked.

   Then, start your workflow to enrich your outbound transition with the targeted information.

   ![](assets/uc_enrichment_18.png)

You can now start designing your email delivery with the custom date fields created in the **Enrichment** activity.

1. Double-click your **Email delivery** activity.
1. Add your target extensions to your email. It should be inside the following expression in order to configure the format of your validity dates:

   ```
   <%=
           formatDate(targetData.alias of your expression,"%2D.%2M")  %>
   ```

1. Click ![](assets/uc_enrichment_16.png) . Select **Target extension** then the previously created custom validity dates with the **Enrichment** activity to add your extension to the formatDate expression.

   ![](assets/uc_enrichment_19.png)

1. Configure your email content as needed.

   ![](assets/uc_enrichment_17.png)

1. Preview your email to check if your custom date fields were correctly configured

   ![](assets/uc_enrichment_20.png)

Your email is now ready. You can start sending your proofs and confirm you delivery to send your birthday emails.
