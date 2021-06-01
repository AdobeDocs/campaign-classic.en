---
product: campaign
title: Testing tracking
description: Testing tracking
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: 16ad36b7-c13e-4b77-86ca-41c9ef174172
---
# Testing tracking{#testing-tracking}

You can test tracking on mirror pages, email logs and links. To do this:

1. Create a new email delivery that will be used for testing.
1. Specify the user that will receive the email. Since this user will have to open the email and click the links it contains, make sure you select a test recipient address that you control.
1. Add a mirror page (MirrorPage) personalization block in the email content.
1. Send the delivery containing a link to the mirror page.
1. Once you have received the email, open it and click the mirror page link.
1. After you are correctly redirected to the mirror page, access the **Administration > Technical workflows** folder and open the **Tracking** workflow.
1. Start the workflow, right click the **Scheduler** activity and select **Execute pending task now**.
1. Wait around 30 seconds, then select the **Audit** tab. Ensure that at least one tracking log record is found.

   Click **Refresh** if you do not see any new logs.

1. Go to the profile page of the recipient you used for the test, and select the **Tracking** tab. Some records should appear with the **Mirror Page** value in the **Type** column.

   >[!NOTE]
   >
   >The recipient's profile page is located in the **Profiles and Targets > Recipients** folder by default.

   To check the email log tracking, look for the values **Open** and **[!UICONTROL Email click]** in the **Type** column.

   If the open logs do not appear, go to the delivery and access its **Properties** to make sure that both **Activate tracking** and **[!UICONTROL Opens tracking]** options are checked.
