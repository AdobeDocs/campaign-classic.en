---
product: campaign
title: Generate personalized PDF documents
description: Learn how to generate personalized PDF documents
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Personalization
role: User
hide: true
exl-id: e5239d99-256b-412b-be20-f64f822da9c3
TQID: https://experienceleague.adobe.com/5hETJLlKZ9iWu2k1nW-RMeDlzpSm7wFwfe3QwSEZCa4
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
    internal-label: Customer experience
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer (Campaign)
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages (Campaign)
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging (Campaign)
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design (Campaign)
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing (Campaign)
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability (Campaign)
---
# Generate personalized PDF documents{#generating-personalized-pdf-documents}

## About variable PDF documents {#about-variable-pdf-documents}

Adobe Campaign lets you generate variable PDF documents for email attachments from LibreOffice or Microsoft Word documents.

The following extensions are supported: ".docx", ".doc", and ".odt".

To personalize your documents, the same JavaScript functionalities as for email personalization are available.

You need to activate the **[!UICONTROL "The content of the file is personalized and converted to PDF during the delivery of each message"]** option. This option is accessible when you attach the file to the delivery email. For more on attaching a calculated file, refer the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/attaching-files.html){target="_blank"}.

Example of an invoice header personalization:

![](assets/s_ncs_pdf_simple.png)

To generate dynamic tables or include images via a URL, you need to follow a specific process.

## Generate dynamic tables {#generating-dynamic-tables}

The procedure for generating dynamic tables is as follows:

* Create a table with three lines and as many columns as necessary, then configure its layout (borders, etc.).
* Place your cursor on the table and click the **[!UICONTROL Table > Table properties]** menu. Go to the **[!UICONTROL Table]** tab and enter a name beginning with **NlJsTable**.
* In the first cell of the first line, define a loop ("for", for example) that enables iteration on the values you want to display in the table.
* In each cell of the second line of the table, insert scripts that return the values to display.
* Close the loop in the third and last line of the table.

  Example of a dynamic table definition:

  ![](assets/s_ncs_pdf_table.png)

## Insert external images {#inserting-external-images}

The insertion of external images is useful if, for instance, you want to personalize a document with an image whose URL is entered in a field of the recipient.

To do this, you need to configure a personalization block, then include a call to the personalization block in the attachment.

**Example: insert a personalized logo depending on the recipient's country**

**Step 1: create the attachment:**

* Insert the call to the personalization block: **<%@ include view="blockname" %>**.
* Insert your content (personalized or not) into the body of the file.

![](assets/s_ncs_open_office_blocdeperso.png)

**Step 2: create the personalization block:**

* Go to the **[!UICONTROL Resources > Campaign management > Personalization blocks]** menu of the Adobe Campaign console.
* Create a new "My Logo" personalization block with "My_Logo" as an internal name.
* Click on the **[!UICONTROL Advanced parameters...]** link then check the **[!UICONTROL "The content of the block is included in an attachment"]** option. This lets you copy the definition of the personalization block directly into the content of the OpenOffice file.

  ![](assets/s_ncs_pdf_bloc_option.png)

  You need to differentiate two types of declarations within the personalization block:

  * The Adobe Campaign code of the personalization fields for which the "open" and "closed" chevrons must be replaced with escape characters (respectively `&lt;` and `&gt;`).
  * The entire OpenOffice XML code will be copied into the OpenOffice document.

In the example, the personalization block looks like this:

```
<% if (recipient.country.label == "Germany") { %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_germany.png />
</draw:frame>
<% } else
if (recipient.country.label == "USA")
{ %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_USA.png />
</draw:frame>
<% } %>
```

Depending on the recipient's country, personalization is visible in the document linked to the delivery:

![](assets/s_ncs_pdf_result.png)
