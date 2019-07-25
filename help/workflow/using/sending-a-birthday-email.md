---
title: Sending a birthday email
seo-title: Sending a birthday email
description: Sending a birthday email
seo-description: 
page-status-flag: never-activated
uuid: 5d8380c7-2ba0-427c-8b23-159685cd329c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: e80059db-6f4a-4ff0-99fb-bb89739a1cdd
index: y
internal: n
snippet: y
---

# Sending a birthday email{#sending-a-birthday-email}

## Introduction {#introduction}

This use case presents how to plan sending a recurring email to a list of recipients on the day of their birthday.

To set up this use case, we created the following targeting workflow:

![](assets/birthday-workflow_usecase.png)

This (daily run) workflow selects all recipients that have their birthday on the current date.

This use case can also be found in the form of a video. For more on this, refer to the [Creating a workflow](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html) video.

## Identifying recipients whose birthday it is {#identifying-recipients-whose-birthday-it-is}

After configuring the **Scheduler** activity so that the workflow starts every day, identify all of the recipients whose date of birth equals the current date.

To do this, apply the following steps:

1. Drag and drop a **Query** activity into the workflow and double-click it.
1. Click the **Edit query** link and select **Filtering conditions**.

   ![](assets/s_ncs_user_create_exp_exple00.png)

1. Click the first cell of the **Expression** column and click **Edit expression** to open the expression editor.

   ![](assets/s_ncs_user_create_exp_exple.png)

1. Click **Advanced selection** to select the filtering mode.

   ![](assets/s_ncs_user_create_exp_exple_a.png)

1. Select **Edit the formula using an expression** and click **Next** to display the expression editor.
1. In the list of functions, double-click **Day**, which is accessible via the **Date** node. This function returns the number representing the day corresponding to the date passed as a parameter.

   ![](assets/s_ncs_user_create_exp_exple01.png)

1. In the list of available fields, double-click **Birth date**. The upper section of the editor then displays the following formula:

   ```
   Day(@birthDate)
   ```

   Click **Finish** to confirm.

1. In the query editor, in the first cell of the **Operator** column, select **equal to**.

   ![](assets/s_ncs_user_create_exp_exple02.png)

1. Next, click the first cell of the second column (**Value**), and click **Edit expression** to open the expression editor.
1. In the list of functions, double-click **Day**, which is accessible via the **Date** node.
1. Double-click the **GetDate** function to retrieve the current date.

   ![](assets/s_ncs_user_create_exp_exple04.png)

   The upper section of the editor displays the following formula:

   ```
   Day(GetDate())
   ```

   Click **Finish** to confirm.

1. Repeat this procedure to retrieve the month of birth corresponding to the current month. To do this, click the **Add** button and repeat steps 3 to 10, replacing **Day** with **Month**.

   The complete query is as follows:

   ![](assets/s_ncs_user_create_exp_exple03.png)

Link the result of the **Query** activity to an **Email delivery** activity to send an email to the list of all of your recipients on their birthday.

## Including recipients born on February 29th (optional) {#including-recipients-born-on-february-29th--optional-}

If you want to include all recipients who were born on February 29th, this use case presents how to plan sending a recurring email to a list of recipients for their birthday - whether it is a leap year or not.

The main implementation steps for this use case are:

* Selecting recipients
* Selecting whether or not it is a leap year
* Selecting any recipients born on February 29th

To set up this use case, we created the following targeting workflow:

![](assets/birthday-workflow_usecase_1.png)

This (daily run) workflow selects all recipients that have their birthday on the current date.

If the current year **is not a leap year** and the workflow is run on March 1st, we need to select all recipients that would have had their birthday yesterday (February 29th) and add them to the recipients list. In any other case no additional action is required.

### Step 1: Selecting the recipients {#step-1--selecting-the-recipients}

After configuring the **Scheduler** activity so that the workflow starts every day, identify all of the recipients whose anniversary is the current day.

>[!NOTE]
>
>If the current year is a leap year, all of the recipients born on the 29th of February are automatically included.

![](assets/birthday-workflow_usecase_2.png)

Selecting recipients whose birthday corresponds to the current date is presented in the [Identifying recipients whose birthday it is](../../workflow/using/sending-a-birthday-email.md#identifying-recipients-whose-birthday-it-is) section.

### Step 2: Select whether or not it is a leap year {#step-2--select-whether-or-not-it-is-a-leap-year}

The **Test** activity allows you to check whether or not it is a leap year and whether the current date is March 1st.

If the test is verified (the year is not a leap year - there is no February 29th - and the current date is indeed March 1st), the **True** transition is enabled and the recipients born on February 29th will be added to the March 1st delivery. Otherwise, the **False** transition is enabled and only the recipients born on the current date will receive the delivery.

Copy and paste the code below into the **Initialization script** section of the **Advanced** tab.

```

function isLeapYear(iYear)
{
    if(iYear/4 == Math.floor(iYear/4))
    {
        if(iYear/100 != Math.floor(iYear/100))
        {
            // Divisible by 4 only -> Leap Year
            return 1;
        }
        else
        {
            if(iYear/400 == Math.floor(iYear/400))
            {
                // Divisible by 4, 100 and 400 -> Leap year
                return 1;
            }
        }
    }
    // all others: no leap year
    return 0;
}

// Return today's date and time
var currentTime = new Date()
// returns the month (from 0 to 11)
var month = currentTime.getMonth() + 1
// returns the day of the month (from 1 to 31)
var day = currentTime.getDate()
// returns the year (four digits)
var year = currentTime.getFullYear()

// is current year a leap year?
vars.currentIsALeapYear = isLeapYear(year);

// is current date the first of march?
if(month == 3 && day == 1) {
  // today is 1st of march
vars.firstOfMarch = 1;
}

```

![](assets/birthday-workflow_usecase_3.png)

Add the following condition in the **Conditional forks** section:

```

vars.currentIsALeapYear == 0 && vars.firstOfMarch == 1
```

![](assets/birthday-workflow_usecase_4.png)

### Step 3: Select any recipients born on February 29th {#step-3--select-any-recipients-born-on-february-29th}

Create a **Fork** activity and link one of the outbound transitions to a **Query** activity.

In this query, select all of the recipients whose date of birth is February 29th.

![](assets/birthday-workflow_usecase_5.png)

Combine the results with a **Union** activity.

Link the results of the two **Test** activity branches to an **Email delivery** activity to send an email to the list of all of your recipients on their birthday, even to those born on February 29th during a non-leap year.
