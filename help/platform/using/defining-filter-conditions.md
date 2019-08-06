---
title: Defining filter conditions
seo-title: Defining filter conditions
description: Defining filter conditions
seo-description: 
page-status-flag: never-activated
uuid: e8c738ca-d5ac-4722-a99a-ed6a7a996e2b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: creating-queries
discoiquuid: 6b88e3fc-72ee-4bbf-9700-265223161cc8
index: y
internal: n
snippet: y
---

# Defining filter conditions{#defining-filter-conditions}

## Choosing the operator {#choosing-the-operator}

Within filtering conditions, you need to link two values together using an operator.

![](assets/query_editor_nveau_96.png)

Below is a list of the operators available:

<table> 
 <thead> 
  <tr> 
   <th> Operator<br /> </th> 
   <th> Purpose<br /> </th> 
   <th> Example<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Equal to</strong><br /> </td> 
   <td> Returns a result identical to the data entered in the second Value column.<br /> </td> 
   <td> <strong>Last name (@lastName) equal to 'Jones'</strong>, will return only recipients whose last name is Jones.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Greater than</strong><br /> </td> 
   <td> Returns a value greater than the value entered.<br /> </td> 
   <td> <strong>Age (@age) greater than 50</strong>, will return all values greater than '50', i.e. '51', '52', etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Less than</strong><br /> </td> 
   <td> Returns a value smaller than the value entered.<br /> </td> 
   <td> <strong>Creation date (@created) before 'DaysAgo(100)'</strong>, will return all recipients created less than 100 days ago.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Greater than or equal to</strong><br /> </td> 
   <td> Returns all values equal to or greater than the value entered.<br /> </td> 
   <td> <strong>Age (@age) greater than or equal to '30'</strong>, will return all recipients aged 30 or more.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Less than or equal to</strong><br /> </td> 
   <td> Returns all values equal to or lower than the value entered.<br /> </td> 
   <td> <strong>Age (@age) less than or equal to '60'</strong>, will return all recipients aged 60 or less.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Not equal to</strong><br /> </td> 
   <td> Returns all values not identical to the value entered.<br /> </td> 
   <td> <strong>Language (@language) to equal to 'English'</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Starts with</strong><br /> </td> 
   <td> Returns the results starting with the value entered.<br /> </td> 
   <td> <strong>Account # (@account) starts with '32010'.</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Does not start with</strong><br /> </td> 
   <td> Returns the results not starting with the value entered<br /> </td> 
   <td> <strong>Account # (@account) does not start with '20'</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Contains</strong><br /> </td> 
   <td> Returns the results containing at least the value entered.<br /> </td> 
   <td> <strong>Email domain (@domain) contains 'mail'</strong>, will return all domain names that contain 'mail'. So the 'gmail.com' domain will also be returned.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Does not contain</strong><br /> </td> 
   <td> Returns results not containing the value entered.<br /> </td> 
   <td> <strong>Email domain (@domain) does not contain 'vo'</strong>. In this case, domain names which contain 'vo' will not be returned. The 'voila.fr' domain name will not appear in the results.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Like</strong><br /> </td> 
   <td> <strong>Like</strong> is very similar to the <strong>Contains</strong> operator. It lets you insert a <strong>%</strong> wild card character in the value.<br /> </td> 
   <td> <strong>Last name (@lastName) like 'Jon%s'</strong>. Here, the wild card character is used as a "joker" to find the name "Jones", should the operator have forgotten the missing letter between the 'n' and the 's'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Not like</strong><br /> </td> 
   <td> Is similar to <strong>Like</strong>. Lets you not recover the entered value. Here too, the entered value must contain the <strong>%</strong> wild card character.<br /> </td> 
   <td> <strong>Last name (@lastName) not like 'Smi%h'</strong>. Here, the recipients whose last name is 'Smi%h' will not be returned.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Is empty</strong><br /> </td> 
   <td> In this case, the result we are looking for matches an empty value in the second Value column.<br /> </td> 
   <td> <strong>Mobile (@mobilePhone) is empty</strong> returns all recipients who do not have a mobile number.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Is not empty</strong><br /> </td> 
   <td> Works in reverse to the <strong>Is empty</strong> operator. It is not necessary to enter data in the second Value column.<br /> </td> 
   <td> <strong>Email (@email) is not empty</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Is included in</strong><br /> </td> 
   <td> Returns results included in the values indicated. These values have to be separated by a comma.<br /> </td> 
   <td> <strong>Birth date (@birthDate) is included in '12/10/1979,12/10/1984'</strong>, will return the recipients born between these dates. <br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Is not included in</strong><br /> </td> 
   <td> Works like the <strong>Is included in</strong> operator. Here, we want to exclude recipients based on the values entered.<br /> </td> 
   <td> <strong>Birth date (@birthDate) is not included in '12/10/1979,12/10/1984'</strong>. Unlike in the previous example, recipients born within these dates will not be returned.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Using AND, OR, EXCEPT {#using-and--or--except}

For queries using several filtering conditions, you need to define links between the conditions. There are three possible links:

* **And** lets you combine two filtering conditions,
* **Or** lets you offer an alternative,
* **Except** lets you define an exception.

Click **And** (offered by default) and choose from the drop-down list.

![](assets/query_condition_modif_01.png)

* **And**: adds a condition and enables overfiltering.
* **Or**: adds a condition and enables overfiltering.

  The following example lets you find recipients whose email domain contains "orange.co.uk" OR whose post code starts with "NW".

  ![](assets/query_condition_modif_02.png)

* **Except**: if you have two filters and the first one does not return a value, this type of link creates an exception.

  In the following example, we want to return recipients whose email domain contains "orange.co.uk" EXCEPT if the recipient's last name is "Smith".

  ![](assets/query_condition_modif_03.png)

This example shows a filter which lets you display: recipients who either speak Spanish, OR are women with mobile numbers, OR recipients without an account number and whose company name starts with the letter "N".

![](assets/query_editor_nveau_31.png)

## Prioritizing conditions {#prioritizing-conditions}

This section explains how to prioritize conditions thanks to the blue arrows in the toolbar.

* The arrow pointing to the right lets you add a level of parentheses to the filter.
* The arrow pointing to the left lets you delete a selected parenthesis level from the filter.

  ![](assets/query_condition_modif_04.png)

* The vertical arrows let you move a condition, thereby changing their execution sequence.

This example shows you how to use the arrow to delete a parenthesis level. Start from the following filtering condition: **City equal to London OR gender equal to male and mobile not indicated OR account # starts with "95" and company name starts with "A"**.

Place your cursor on the **Gender (@gender) equal to Male** filtering condition and click the **Remove a parenthesis level** arrow.

![](assets/query_editor_nveau_32.png)

The **Gender (@gender) equal to Male** condition has been taken out of its parenthesis. It has moved to the same level as the "City equal to London" condition. These conditions are linked together (**And**).

## Selecting data to extract {#selecting-data-to-extract}

The available fields vary from one table to another. All fields are stored in a main node known as the **Main element**. In the following example, the available fields are in the recipient table. Fields are always displayed alphabetically.

The detail the selected field is visible at the bottom of the window. For example, the **Email domain** field is a **Calculated SQL field** and its extension is **(@domain)**.

![](assets/query_editor_nveau_59.png)

>[!NOTE]
>
>Use the **Search** tool to find an available field.

Double-click an available field to add it to the output columns. At the end of the query, each selected field creates a column in the **Data preview** window.

![](assets/query_editor_nveau_01.png)

Advanced fields are not displayed by default. Click **Display advanced fields** in the bottom right-hand corner of the available fields to display everything. Click again to return to the former view.

For example, in the recipient table, the advanced fields are **Boolean 1**, **Boolean 2**, **Boolean 3**, **Foreign key of "Folder" link**, etc.

The following example shows the advanced fields of the recipient table.

![](assets/query_editor_nveau_53.png)

The various categories of fields:

<table> 
 <thead> 
  <tr> 
   <th> Icon<br /> </th> 
   <th> Description<br /> </th> 
   <th> Examples<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_47.png" /> </td> 
   <td> Simple field<br /> </td> 
   <td> Email, gender, etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_48.png" /> </td> 
   <td> Primary key. This SQL field is a way of identifying a record in a table.<br /> </td> 
   <td> Identifier recipients are primary keys and identifiers are unique by definition.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_02.png" /> </td> 
   <td> Foreign key. Used as a link to another table.<br /> </td> 
   <td> Recipient foreign key, service foreign key, etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_46.png" /> </td> 
   <td> Calculated field. This type of field is calculated on request using the values in the database.<br /> </td> 
   <td> Age, email domain, etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_49.png" /> </td> 
   <td> Field containing long texts.<br /> </td> 
   <td> Comment, full address, etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_50.png" /> </td> 
   <td> Indexed SQL field. <br /> </td> 
   <td> Full name, ISO code, etc. <br /> </td> 
  </tr> 
 </tbody> 
</table>

Link to a table and collection element:

<table> 
 <thead> 
  <tr> 
   <th> Icon<br /> </th> 
   <th> Description<br /> </th> 
   <th> Example<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_51.png" /> </td> 
   <td> Links to a table in particular. These coincide with 1-1 type associations. An occurrence of the source table can coincide with only one occurrence of the target table. For example, only one recipient can be linked to a country.<br /> </td> 
   <td> Folder, State, Country, etc. <br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_52.png" /> </td> 
   <td> Collection element on a specific table. These coincide with 1-N type associations. One source table occurrence can coincide with several occurrences of the target table, but one occurrence of the target table can coincide with only one occurrence of the source table. For example, one recipient can subscribe to 'n' subscription letters.<br /> </td> 
   <td> Subscriptions, lists, exclusion logs, etc.<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* Use the **Add** button (above the side icon bar) to add an output column in which we wish to edit the expression. For more on editing an expression, refer to [Building expressions](../../platform/using/defining-filter-conditions.md#building-expressions).
>* Delete an output column by clicking the red 'x' (**Delete**).
>* Change the order of the output columns using the arrows.
>* The **Distribution of values** serves as a way to view the distributon of the values of the field selected (for example, the distributions linked to recipient towns, recipient languages, etc.).
>

## Creating calculated fields {#creating-calculated-fields}

If necessary, add a column during data formatting. A calculated field adds a column to the data preview section. Click **Add a calculated field**.

![](assets/query_editor_nveau_43.png)

There are four types of calculated fields:

* **Fixed string**: lets you add a string of characters.

  ![](assets/query_editor_nveau_60.png)

* **String with JavaScript tags**: the value of the calculated field combines a string of characters and JavaScript directives.

  ![](assets/query_editor_nveau_61.png)

* **JavaScript expression**: the value of the calculated field is the result of a JavaScript function evaluation. The returned value can be typed (number, date, etc.).

  ![](assets/query_editor_nveau_62.png)

* **Enumerations**: This type of field lets you use/modify the content of one of the output columns in a new column.

  It's possible to use the source value of a column and give it a destination value. This destination value will be displayed in the new output column.

  An example of adding calculated field type **Enumerations** is available, refer to [this section](../../workflow/using/designing-queries.md#adding-an-enumeration-type-calculated-field).

  The **Enumerations** type calculated field can include 4 conditions:

    * **Keep the source value** restores the source value to the target without changing it.
    * **Use the following value** lets you enter a default destination value for non-defined source values.
    * **Generate a warning and continue** warns the user that the source value cannot be changed.
    * **Generate an error and reject the line** prevents the line from being calculated and imported.

>[!NOTE]
>
>Click the **Detail of calculated field** to view the detail of the inserted field.  
>To remove this calculated field, click the **Remove the calculated field** cross.

## Building expressions {#building-expressions}

The expression editing tool lets you calculate aggregates, generate function, or edit a formula using an expression.

The following example shows you how to run a count on a primary key.

Apply the following steps:

1. Click **Add** in the **Data to extract** window. In the **Formula type** window, select a type of formula to enter the expression.

   There are several types of formulas available: **Field only**, **Aggregate**, **Expression**.

   Select **Process on an aggregate function**, and **Count**. Click **Next**.

   ![](assets/query_editor_nveau_54.png)

1. The primary key is calculated.

   ![](assets/query_editor_nveau_88.png)

Here is a detailed view of the choices available in the **Formula types** window: 

![](assets/query_editor_nveau_05.png)

1. **Field only** lets you return to the **Field to select** window.
1. **Aggregate (Process on an aggregate function)**. Here are some examples of aggregate use:

    * **Count** lets you run a primary key count.
    * **Sum** lets you add up all purchases made by a customer over one year.
    * **Maximum value** lets you find the customers having purchased the most "n" products.
    * **Minimum value** lets you sort through customers and find those having subscribed to an offer most recently.
    * **Average**. This function lets you calculate the average age of your recipients.

      The **Distinct** box lets you recover unique and non-zero values of a column. For example, you can recover all of a recipient's tracking logs and these tracking logs are changed to the value 1 since they all concern the same recipient.

1. **Expression** opens the **Edit the expression** window. This lets you detect telephone numbers with too many figures, likely to be input errors.

   ![](assets/query_editor_nveau_71.png)

   For a list of all available functions, refer to [List of functions](../../platform/using/defining-filter-conditions.md#list-of-functions).

## List of functions {#list-of-functions}

If an **Expression** type formula is chosen, you will be taken to the "edit the expression" window. Various categories of functions can be associated to the available fields: **Aggregates**, **String**, **Date**, **Numerical**, **Currency**, **Geomarketing**, **Windowing function** and **Others**.

The expression editor looks like this:

![](assets/s_ncs_user_filter_define_expression.png)

It lets you select fields in the database tables and add advanced functions to them. The following functions are available:

1. Aggregates

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Name</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Avg</strong><br /> </td> 
   <td> Returns the average of a number type column<br /> </td> 
   <td> Avg(
    <value>
     )
     <br /> 
    </value></td> 
  </tr> 
  <tr> 
   <td> <strong>Count</strong><br /> </td> 
   <td> Counts the non-null values of a column<br /> </td> 
   <td> Count(
    <value>
     )
     <br /> 
    </value></td> 
  </tr> 
  <tr> 
   <td> <strong>CountAll</strong><br /> </td> 
   <td> Counts the values returned (all fields)<br /> </td> 
   <td> CountAll()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Countdistinct</strong><br /> </td> 
   <td> Counts the distinct non-null values of a column<br /> </td> 
   <td> Countdistinct(
    <value>
     )
     <br /> 
    </value></td> 
  </tr> 
  <tr> 
   <td> <strong>Max</strong><br /> </td> 
   <td> Returns the maximum value of a number, string, or date type column<br /> </td> 
   <td> Max(
    <value>
     )
     <br /> 
    </value></td> 
  </tr> 
  <tr> 
   <td> <strong>Min</strong><br /> </td> 
   <td> Returns the minimum value of a number, string or date type column<br /> </td> 
   <td> Min(
    <value>
     )
     <br /> 
    </value></td> 
  </tr> 
  <tr> 
   <td> <strong>StdDev</strong><br /> </td> 
   <td> Returns the standard deviation of a number, string or date column<br /> </td> 
   <td> StdDev(
    <value>
     )
     <br /> 
    </value></td> 
  </tr> 
  <tr> 
   <td> <strong>Sum</strong><br /> </td> 
   <td> Returns the sum of the values of a number, string, or date type column<br /> </td> 
   <td> Sum(
    <value>
     )
     <br /> 
    </value></td> 
  </tr> 
 </tbody> 
</table>

1. String

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Name</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull2</strong><br /> </td> 
   <td> Indicates if all parameters are non-null and not empty<br /> </td> 
   <td> AllNonNull2(
    <string>
     , 
     <string>
      )
      <br /> 
     </string>
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull3</strong><br /> </td> 
   <td> Indicates if all parameters are non-null and not empty<br /> </td> 
   <td> AllNonNull3(
    <string>
     , 
     <string>
      , 
      <string>
       )
       <br /> 
      </string>
     </string>
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>Ascii</strong><br /> </td> 
   <td> Returns the ASCII value of the first character in the string.<br /> </td> 
   <td> Ascii(
    <string>
     )
     <br /> 
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>Char</strong><br /> </td> 
   <td> Returns the character corresponding to the 'n' ASCII code<br /> </td> 
   <td> Char(
    <number>
     )
     <br /> 
    </number></td> 
  </tr> 
  <tr> 
   <td> <strong>Charindex</strong><br /> </td> 
   <td> Returns the position of string 2 in string 1.<br /> </td> 
   <td> Charindex(
    <string>
     , 
     <string>
      )
      <br /> 
     </string>
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>GetLine</strong><br /> </td> 
   <td> Returns the nth (from 1 to n) line of the string<br /> </td> 
   <td> GetLine(
    <string>
     )
     <br /> 
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>IfEquals</strong><br /> </td> 
   <td> Returns the third parameter if the first two parameters are equal. If not, returns the last parameter<br /> </td> 
   <td> IfEquals(
    <string>
     , 
     <string>
      , 
      <string>
       , 
       <string>
        )
        <br /> 
       </string>
      </string>
     </string>
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>IsMemoNull</strong><br /> </td> 
   <td> Indicates if the memo passed as a parameter is null<br /> </td> 
   <td> IsMemoNull(
    <memo>
     )
     <br /> 
    </memo></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords</strong><br /> </td> 
   <td> Concatenates the strings passed as parameters. Adds spaces between the strings if necessary.<br /> </td> 
   <td> JuxtWords(
    <string>
     , 
     <string>
      )
      <br /> 
     </string>
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords3</strong><br /> </td> 
   <td> Concatenates the strings passed as parameters. Adds spaces between the strings if necessary<br /> </td> 
   <td> JuxtWords3(
    <string>
     , 
     <string>
      , 
      <string>
       )
       <br /> 
      </string>
     </string>
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>LPad</strong><br /> </td> 
   <td> Returns the completed string on the left<br /> </td> 
   <td> LPad(
    <string>
     , 
     <number>
      , 
      <caractère>
       )
       <br /> 
      </caractère>
     </number>
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>Left</strong><br /> </td> 
   <td> Returns the first n characters of the string<br /> </td> 
   <td> Left(
    <string>
     , 
     <number>
      )
      <br /> 
     </number>
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>Length</strong><br /> </td> 
   <td> Returns the length of the string<br /> </td> 
   <td> Length(
    <string>
     )
     <br /> 
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>Lower</strong><br /> </td> 
   <td> Returns the string in lowercase<br /> </td> 
   <td> Lower(
    <string>
     )
     <br /> 
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>Ltrim</strong><br /> </td> 
   <td> Removes spaces to the left of the string<br /> </td> 
   <td> Ltrim(
    <string>
     )
     <br /> 
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>Md5Digest</strong><br /> </td> 
   <td> Returns an hexadecimal representation of the MD5 key of a string<br /> </td> 
   <td> Md5Digest(
    <string>
     )
     <br /> 
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>MemoContains</strong><br /> </td> 
   <td> Specifies whether the memo contains the string passed as a parameter<br /> </td> 
   <td> MemoContains(
    <memo>
     , 
     <string>
      )
      <br /> 
     </string>
    </memo></td> 
  </tr> 
  <tr> 
   <td> <strong>RPad</strong><br /> </td> 
   <td> Returns the completed string on the right<br /> </td> 
   <td> RPad(
    <string>
     , 
     <number>
      , 
      <character>
       )
       <br /> 
      </character>
     </number>
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>Right</strong><br /> </td> 
   <td> Returns the last n characters of the string<br /> </td> 
   <td> Right(
    <string>
     )
     <br /> 
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>Rtrim</strong><br /> </td> 
   <td> Removes spaces to the right of the string<br /> </td> 
   <td> Rtrim(
    <string>
     )
     <br /> 
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>Smart</strong><br /> </td> 
   <td> Returns the string with the first letter of each word in capitals<br /> </td> 
   <td> Smart(
    <string>
     )
     <br /> 
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>Substring</strong><br /> </td> 
   <td> Extracts the substring starting at character n1 of the string and of length n2<br /> </td> 
   <td> Substring(
    <string>
     , 
     <offset>
      , 
      <length>
       )
       <br /> 
      </length>
     </offset>
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>ToString</strong><br /> </td> 
   <td> Converts the number to a string<br /> </td> 
   <td> ToString(
    <number>
     )
     <br /> 
    </number></td> 
  </tr> 
  <tr> 
   <td> <strong>Upper</strong><br /> </td> 
   <td> Returns the string in capitals<br /> </td> 
   <td> Upper(
    <string>
     )
     <br /> 
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>VirtualLink</strong><br /> </td> 
   <td> Returns the foreign key of a link passed as a parameter if the other two parameters are equal<br /> </td> 
   <td> VirtualLink(
    <number>
     , 
     <number>
      , 
      <number>
       )
       <br /> 
      </number>
     </number>
    </number></td> 
  </tr> 
  <tr> 
   <td> <strong>VirtualLinkStr</strong><br /> </td> 
   <td> Returns the foreign (text) key of a link passed as a parameter if the other two parameters are equal<br /> </td> 
   <td> VirtualLinkStr(
    <string>
     , 
     <number>
      , 
      <number>
       )
       <br /> 
      </number>
     </number>
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>dataLength</strong><br /> </td> 
   <td> Returns the string size<br /> </td> 
   <td> dataLength(
    <string>
     )
     <br /> 
    </string></td> 
  </tr> 
 </tbody> 
</table>

1. Date

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Name</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AddDays</strong><br /> </td> 
   <td> Adds a number of days to a date<br /> </td> 
   <td> AddDays(
    <date>
     , 
     <number>
      )
      <br /> 
     </number>
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>AddHours</strong><br /> </td> 
   <td> Adds a number of hours to a date<br /> </td> 
   <td> AddHours(
    <date>
     , 
     <number>
      )
      <br /> 
     </number>
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>AddMinutes</strong><br /> </td> 
   <td> Adds a number of minutes to a date<br /> </td> 
   <td> AddMinutes(
    <date>
     , 
     <number>
      )
      <br /> 
     </number>
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>AddMonths</strong><br /> </td> 
   <td> Adds a number of months to a date<br /> </td> 
   <td> AddMonths(
    <date>
     , 
     <number>
      )
      <br /> 
     </number>
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>AddSeconds</strong><br /> </td> 
   <td> Adds a number of seconds to a date<br /> </td> 
   <td> AddSeconds(
    <date>
     , 
     <number>
      )
      <br /> 
     </number>
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>AddYears</strong><br /> </td> 
   <td> Adds a number of years to a date<br /> </td> 
   <td> AddYears(
    <date>
     , 
     <number>
      )
      <br /> 
     </number>
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>DateOnly</strong><br /> </td> 
   <td> Returns the date only (with time at 00:00)*<br /> </td> 
   <td> DateOnly(
    <date>
     )
     <br /> 
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>Day</strong><br /> </td> 
   <td> Returns the number representing the day of the date<br /> </td> 
   <td> Day(
    <date>
     )
     <br /> 
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>DayOfYear</strong><br /> </td> 
   <td> Returns the number of the day in the year of the date<br /> </td> 
   <td> DayOfYear(
    <date>
     )
     <br /> 
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>DaysAgo</strong><br /> </td> 
   <td> Returns the date corresponding to the current date minus n days<br /> </td> 
   <td> DaysAgo(
    <number>
     )
     <br /> 
    </number></td> 
  </tr> 
  <tr> 
   <td> <strong>DaysAgoInt</strong><br /> </td> 
   <td> Returns the date (integer yyyymmdd) corresponding to the current date minus n days<br /> </td> 
   <td> DaysAgoInt(
    <number>
     )
     <br /> 
    </number></td> 
  </tr> 
  <tr> 
   <td> <strong>DaysDiff</strong><br /> </td> 
   <td> Number of days between two dates<br /> </td> 
   <td> DaysDiff(
    <end date="">
     , 
     <start date="">
      )
      <br /> 
     </start>
    </end></td> 
  </tr> 
  <tr> 
   <td> <strong>DaysOld</strong><br /> </td> 
   <td> Returns the age in days of a date<br /> </td> 
   <td> DaysOld(
    <date>
     )
     <br /> 
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>GetDate</strong><br /> </td> 
   <td> Returns the current system date of the server<br /> </td> 
   <td> GetDate()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Hour</strong><br /> </td> 
   <td> Returns the hour of the date<br /> </td> 
   <td> Hour(
    <date>
     )
     <br /> 
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>HoursDiff</strong><br /> </td> 
   <td> Returns the number of hours between two dates<br /> </td> 
   <td> HoursDiff(
    <end date="">
     , 
     <start date="">
      )
      <br /> 
     </start>
    </end></td> 
  </tr> 
  <tr> 
   <td> <strong>Minute</strong><br /> </td> 
   <td> Returns the minutes of the date<br /> </td> 
   <td> Minute(
    <date>
     )
     <br /> 
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>MinutesDiff</strong><br /> </td> 
   <td> Returns the number of minutes between two dates<br /> </td> 
   <td> MinutesDiff(
    <end date="">
     , 
     <start date="">
      )
      <br /> 
     </start>
    </end></td> 
  </tr> 
  <tr> 
   <td> <strong>Month</strong><br /> </td> 
   <td> Returns the number representing the month of the date<br /> </td> 
   <td> Month(
    <date>
     )
     <br /> 
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>MonthsAgo</strong><br /> </td> 
   <td> Returns the date corresponding to the current date minus n months<br /> </td> 
   <td> MonthsAgo(
    <number>
     )
     <br /> 
    </number></td> 
  </tr> 
  <tr> 
   <td> <strong>MonthsDiff</strong><br /> </td> 
   <td> Returns the number of months between two dates<br /> </td> 
   <td> MonthsDiff(
    <end date="">
     , 
     <start date="">
      )
      <br /> 
     </start>
    </end></td> 
  </tr> 
  <tr> 
   <td> <strong>MonthsOld</strong><br /> </td> 
   <td> Returns the age in months of a date<br /> </td> 
   <td> MonthsOld(
    <date>
     )
     <br /> 
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>Second</strong><br /> </td> 
   <td> Returns the seconds of the date<br /> </td> 
   <td> Second(
    <date>
     )
     <br /> 
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>SecondsDiff</strong><br /> </td> 
   <td> Returns the number of seconds between two dates<br /> </td> 
   <td> SecondsDiff(
    <end date="">
     , 
     <start date="">
      )
      <br /> 
     </start>
    </end></td> 
  </tr> 
  <tr> 
   <td> <strong>SubDays</strong><br /> </td> 
   <td> Subtracts a number of days from a date<br /> </td> 
   <td> SubDays(
    <date>
     , 
     <number>
      )
      <br /> 
     </number>
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>SubHours</strong><br /> </td> 
   <td> Subtracts a number of hours from a date<br /> </td> 
   <td> SubHours(
    <date>
     , 
     <number>
      )
      <br /> 
     </number>
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>SubMinutes</strong><br /> </td> 
   <td> Subtracts a number of minutes from a date<br /> </td> 
   <td> SubMinutes(
    <date>
     , 
     <number>
      )
      <br /> 
     </number>
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>SubMonths</strong><br /> </td> 
   <td> Subtracts a number of months from a date<br /> </td> 
   <td> SubMonths(
    <date>
     , 
     <number>
      )
      <br /> 
     </number>
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>SubSeconds</strong><br /> </td> 
   <td> Subtracts a number of seconds from a date<br /> </td> 
   <td> SubSeconds(
    <date>
     , 
     <number>
      )
      <br /> 
     </number>
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>SubYears</strong><br /> </td> 
   <td> Subtracts a number of years from a date<br /> </td> 
   <td> SubYears(
    <date>
     , 
     <number>
      )
      <br /> 
     </number>
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>ToDate</strong><br /> </td> 
   <td> Converts a date + time as a date<br /> </td> 
   <td> ToDate(
    <date time="">
     )
     <br /> 
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>ToDateTime</strong><br /> </td> 
   <td> Converts a string to a date + time<br /> </td> 
   <td> ToDateTime(
    <string>
     )
     <br /> 
    </string></td> 
  </tr> 
  <tr> 
   <td> <strong>TruncDate</strong><br /> </td> 
   <td> Rounds a date+time to the nearest second<br /> </td> 
   <td> TruncDate(@lastModified, 
    <number of="" seconds="">
     )
     <br /> 
    </number></td> 
  </tr> 
  <tr> 
   <td> <strong>TruncDateTZ</strong><br /> </td> 
   <td> Rounds a date + time to a given precision expressed in seconds<br /> </td> 
   <td> TruncDateTZ(
    <date>
     , 
     <number of="" seconds="">
      , 
      <time zone="">)<br /> </time>
     </number>
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>TruncQuarter</strong><br /> </td> 
   <td> Rounds a date off to the quarter<br /> </td> 
   <td> TruncQuarter(
    <date>
     )
     <br /> 
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>TruncTime</strong><br /> </td> 
   <td> Rounds the time part up to the nearest second<br /> </td> 
   <td> TruncTime(
    <date>
     , 
     <number of="" seconds="">
      )
      <br /> 
     </number>
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> Rounds a date off to the week<br /> </td> 
   <td> TruncWeek(
    <date>
     )
     <br /> 
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>TruncYear</strong><br /> </td> 
   <td> Rounds a date + time to January 1st of the year<br /> </td> 
   <td> TruncYear(
    <date>
     )
     <br /> 
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> Returns the number representing the day in the week of the date<br /> </td> 
   <td> WeekDay(
    <date>
     )
     <br /> 
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>Year</strong><br /> </td> 
   <td> Returns the number representing the year of the date<br /> </td> 
   <td> Year(
    <date>
     )
     <br /> 
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>YearAnd Month</strong><br /> </td> 
   <td> Returns the number representing the year and month of the date<br /> </td> 
   <td> YearAndMonth(
    <date>
     )
     <br /> 
    </date></td> 
  </tr> 
  <tr> 
   <td> <strong>YearsDiff</strong><br /> </td> 
   <td> Returns the number of years between the two dates<br /> </td> 
   <td> YearsDiff(
    <end date="">
     , 
     <start date="">
      )
      <br /> 
     </start>
    </end></td> 
  </tr> 
  <tr> 
   <td> <strong>YearsOld</strong><br /> </td> 
   <td> Returns the age in years of a date<br /> </td> 
   <td> YearsOld(
    <date>
     )
     <br /> 
    </date></td> 
  </tr> 
 </tbody> 
</table>

   &#42;Note that the **Dateonly** function takes into account the server's timezone, not the operator's.

1. Numerical

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Name</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Abs</strong><br /> </td> 
   <td> Returns the absolute value of a number<br /> </td> 
   <td> Abs(
    <number>
     )
     <br /> 
    </number></td> 
  </tr> 
  <tr> 
   <td> <strong>Ceil</strong><br /> </td> 
   <td> Returns the lowest integer greater than or equal to a number<br /> </td> 
   <td> Ceil(
    <number>
     )
     <br /> 
    </number></td> 
  </tr> 
  <tr> 
   <td> <strong>Floor</strong><br /> </td> 
   <td> Returns the greatest integer greater than or equal to a number<br /> </td> 
   <td> Floor(
    <number>
     )
     <br /> 
    </number></td> 
  </tr> 
  <tr> 
   <td> <strong>Greatest</strong><br /> </td> 
   <td> Returns the greater of two numbers<br /> </td> 
   <td> Greatest(
    <number>
     , 
     <number>
      )
      <br /> 
     </number>
    </number></td> 
  </tr> 
  <tr> 
   <td> <strong>Least</strong><br /> </td> 
   <td> Returns the smaller of two numbers<br /> </td> 
   <td> Least(
    <number>
     , 
     <number>
      )
      <br /> 
     </number>
    </number></td> 
  </tr> 
  <tr> 
   <td> <strong>Mod</strong><br /> </td> 
   <td> Returns the remainder of the integer division of n1 by n2<br /> </td> 
   <td> Mod(
    <nombre>
     , 
     <number>
      )
      <br /> 
     </number>
    </nombre></td> 
  </tr> 
  <tr> 
   <td> <strong>Percent</strong><br /> </td> 
   <td> Returns the ratio of two numbers expressed as a percentage<br /> </td> 
   <td> Percent(
    <number>
     , 
     <number>
      )
      <br /> 
     </number>
    </number></td> 
  </tr> 
  <tr> 
   <td> <strong>Random</strong><br /> </td> 
   <td> Returns the random value<br /> </td> 
   <td> Random()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Round</strong><br /> </td> 
   <td> Rounds off a number to n decimals<br /> </td> 
   <td> Round(
    <number>
     , 
     <number decimals="" of="">
      )
      <br /> 
     </number>
    </number></td> 
  </tr> 
  <tr> 
   <td> <strong>Sign</strong><br /> </td> 
   <td> Returns the sign of the number<br /> </td> 
   <td> Sign(
    <number>
     )
     <br /> 
    </number></td> 
  </tr> 
  <tr> 
   <td> <strong>ToDouble</strong><br /> </td> 
   <td> Converts an integer to a float<br /> </td> 
   <td> ToDouble(
    <number>
     )
     <br /> 
    </number></td> 
  </tr> 
  <tr> 
   <td> <strong>ToInt64</strong><br /> </td> 
   <td> Converts a float to a 64 bit integer<br /> </td> 
   <td> ToInt64(
    <number>
     )
     <br /> 
    </number></td> 
  </tr> 
  <tr> 
   <td> <strong>ToInteger</strong><br /> </td> 
   <td> Converts a float to an integer<br /> </td> 
   <td> ToInteger(
    <number>
     )
     <br /> 
    </number></td> 
  </tr> 
  <tr> 
   <td> <strong>Trunc</strong><br /> </td> 
   <td> Truncates n1 to n2 decimals<br /> </td> 
   <td> Trunc(
    <n1>
     , 
     <n2>
      )
      <br /> 
     </n2>
    </n1></td> 
  </tr> 
 </tbody> 
</table>

1. Currency

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Name</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ConvertCurrency</strong><br /> </td> 
   <td> Converts an amount in a source currency to an amount in a target currency<br /> </td> 
   <td> ConvertCurrency(
    <amount>
     , 
     <source currency="" />, 
     <target currency="">
      , 
      <conversion date="">
       )
       <br /> 
      </conversion>
     </target>
    </amount></td> 
  </tr> 
  <tr> 
   <td> <strong>FormatCurrency</strong><br /> </td> 
   <td> Formats the amount displayed based on the selected currency settings<br /> </td> 
   <td> FormatCurrency(
    <amount>
     , 
     <currency>
      )
      <br /> 
     </currency>
    </amount></td> 
  </tr> 
 </tbody> 
</table>

1. Geomarketing

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Name</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Distance</strong><br /> </td> 
   <td> Returns the distance between two points defined by their longitude and latitude, expressed in degrees.<br /> </td> 
   <td> Distance(
    <longitude a="">
     , 
     <latitude a="">
      , 
      <longitude b="">
       , 
       <latitude b="">
        )
        <br /> 
       </latitude>
      </longitude>
     </latitude>
    </longitude></td> 
  </tr> 
 </tbody> 
</table>

1. Others

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Name</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Case</strong><br /> </td> 
   <td> Returns value 1 if the condition is true. If not, it returns value 2.<br /> </td> 
   <td> Case(When(
    <condition>
     , 
     <value>
      ), Else(
      <value>
       ))
       <br /> 
      </value>
     </value>
    </condition></td> 
  </tr> 
  <tr> 
   <td> <strong>ClearBit</strong><br /> </td> 
   <td> Deletes the Flag in the value<br /> </td> 
   <td> ClearBit(
    <identifier>
     , 
     <flag>
      )
      <br /> 
     </flag>
    </identifier></td> 
  </tr> 
  <tr> 
   <td> <strong>Coalesce</strong><br /> </td> 
   <td> Returns value 2 if value 1 is zero or null, otherwise returns value 1<br /> </td> 
   <td> Coalesce(
    <value>
     , 
     <value>
      )
      <br /> 
     </value>
    </value></td> 
  </tr> 
  <tr> 
   <td> <strong>Decode</strong><br /> </td> 
   <td> Returns value 3 if value 1 = value 2. If not returns value 4.<br /> </td> 
   <td> Decode(
    <value>
     , 
     <value>
      , 
      <value>
       , 
       <value>
        )
        <br /> 
       </value>
      </value>
     </value>
    </value></td> 
  </tr> 
  <tr> 
   <td> <strong>Else</strong><br /> </td> 
   <td> Returns value 1 (may only be used as a parameter of the case function)<br /> </td> 
   <td> Else(
    <value>
     )
     <br /> 
    </value></td> 
  </tr> 
  <tr> 
   <td> <strong>GetEmailDomain</strong><br /> </td> 
   <td> Extracts the domain from an e-mail address<br /> </td> 
   <td> GetEmailDomain(
    <value>
     )
     <br /> 
    </value></td> 
  </tr> 
  <tr> 
   <td> <strong>GetMirrorURL</strong><br /> </td> 
   <td> Retrieves the URL of the mirror page server<br /> </td> 
   <td> GetMirrorURL(
    <value>
     )
     <br /> 
    </value></td> 
  </tr> 
  <tr> 
   <td> <strong>Iif</strong><br /> </td> 
   <td> Returns value 1 if the expression is true. If not, returns value 2<br /> </td> 
   <td> Iif(
    <condition>
     , 
     <value>
      , 
      <value>
       )
       <br /> 
      </value>
     </value>
    </condition></td> 
  </tr> 
  <tr> 
   <td> <strong>IsBitSet</strong><br /> </td> 
   <td> Indicates whether the Flag is in the value<br /> </td> 
   <td> IsBitSet(
    <identifier>
     , 
     <flag>
      )
      <br /> 
     </flag>
    </identifier></td> 
  </tr> 
  <tr> 
   <td> <strong>IsEmptyString</strong><br /> </td> 
   <td> Returns value 2 if string 1 is empty, otherwise returns value 3<br /> </td> 
   <td> IsEmptyString(
    <value>
     , 
     <value>
      , 
      <value>
       )
       <br /> 
      </value>
     </value>
    </value></td> 
  </tr> 
  <tr> 
   <td> <strong>NoNull</strong><br /> </td> 
   <td> Returns the empty string if the argument is NULL<br /> </td> 
   <td> NoNull(
    <value>
     )
     <br /> 
    </value></td> 
  </tr> 
  <tr> 
   <td> <strong>RowId</strong><br /> </td> 
   <td> Returns the line number<br /> </td> 
   <td> RowId<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>SetBit</strong><br /> </td> 
   <td> Forces the Flag in the value<br /> </td> 
   <td> SetBit(
    <identifier>
     , 
     <flag>
      )
      <br /> 
     </flag>
    </identifier></td> 
  </tr> 
  <tr> 
   <td> <strong>ToBoolean</strong><br /> </td> 
   <td> Converts a number into a Boolean<br /> </td> 
   <td> ToBoolean(
    <number>
     )
     <br /> 
    </number></td> 
  </tr> 
  <tr> 
   <td> <strong>When</strong><br /> </td> 
   <td> Returns value 1 if the expression is true. If not, it returns value 2 (may only be used as a parameter of the case function)<br /> </td> 
   <td> When(
    <condition>
     , 
     <value>
      )
      <br /> 
     </value>
    </condition></td> 
  </tr> 
 </tbody> 
</table>

1. Windowing functions

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Name</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Desc</strong><br /> </td> 
   <td> Applies a descending sort<br /> </td> 
   <td> Desc(
    <value>
     )
     <br /> 
    </value></td> 
  </tr> 
  <tr> 
   <td> <strong>OrderBy</strong><br /> </td> 
   <td> Sorts the result within the partition<br /> </td> 
   <td> OrderBy(
    <value>
     )
     <br /> 
    </value></td> 
  </tr> 
  <tr> 
   <td> <strong>PartitionBy</strong><br /> </td> 
   <td> Partitions the result of a query on a table<br /> </td> 
   <td> PartitionBy(
    <value>
     )
     <br /> 
    </value></td> 
  </tr> 
  <tr> 
   <td> <strong>RowNum</strong><br /> </td> 
   <td> Generates a line number based on the table partition and on a sorting sequence.<br /> </td> 
   <td> RowNum(PartitionBy(
    <value>
     ), OrderBy(
     <value>
      ))
      <br /> 
     </value>
    </value></td> 
  </tr> 
 </tbody> 
</table>

