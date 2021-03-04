---
solution: Campaign Classic
product: campaign
title: Pre-processing instructions for tracked URLs
description: Learn more about pre-processing instructions to use to script the URL of an email and still have it tracked.
audience: delivery
content-type: reference
topic-tags: tracking-messages
---

# Pre-processing instructions {#pre-processing-instructions}

The <%@ instructions instructions are not JavaScript, this syntax is specific to Adobe Campaign.

They only apply in the context of delivery content. It is the only way to script the URL of an email and still have it tracked (besides URL parameters). They can be seen as an automatic copy/paste applied during the delivery analysis before detecting the links to track.

There are three types of instructions:

* "**include**": mainly to factorize some cod in options, personalization blocks, external files, or pages
* "**value**": to give access to fields of the delivery, delivery variables and custom objects loaded in the delivery
* "**foreach**": to loop an array loaded as a custom object.

They can be tested directly from the delivery wizard. They apply in the content preview and when you click the tracking button to see the list of the URLs.

## <%@ include {#<%@-include}

The following examples are among the most commonly used:

* Including the mirror page link: `<%@ include view="MirrorPage" %>`
* Mirror page URL: "View as a `<a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page"`
* Out-of-the-box unsubscription url: `<%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>`
* Other examples:
  * `<%@ include file='http://www.google.com' %>`
  * `<%@ include file='file:///X:/france/service/test.html' %>`
  * `<%@ include option='NmsServer_URL' %>`

Use the personalization button in the delivery wizard to get the correct syntax.

## <%@ value {#<%@-value}

This instruction gives access to parameters of the delivery that are constant for all recipients.

Syntax:

`<%@ value object="myObject" xpath="@myField" index="1" %>`

Where:

* "object": name of the object (example: delivery, provider, and so on).
* "xpath": xpath of the field.
* "index" (optional): if "object" is an array (for extra script objects), item index in the array (Starts at 0).

Object can be:

* "delivery": for the current delivery (see details and restrictions in the subsection below).
* "provider": for the current delivery provider/routing (nms:externalAccount).
* An extra script object: if an object is loaded in the context through: **Properties** > **Personalization** > **Add objects in the execution context**.
* Item of the foreach loop: see [Foreach](#<%@-foreach) section below.

### "delivery" object {#delivery-object}

For email personalization, the delivery object is accessible in two ways:

* In JavaScript. For example: `<%= delivery.myField %>`.

  In the JavaScript object delivery custom fields are not supported. They work in the preview, but not in the MTA because the MTA can only access the out-of-the-box delivery schema.

* Through `<%@ value object="delivery"` pre-processing.

For the `<%@ value object="delivery" xpath="@myCustomField" %>` instruction, there is another limitation for deliveries sent via mid-sourcing. The custom field @myCustomField must be added to the nms:delivery schema on both marketing and mid-sourcing platforms.

>[!NOTE]
>
>For delivery parameters/variables, use the following syntax (using the delivery object):
>
>`<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>`

### <%@ value in a Javascript section {#<%@-value-in-javascript}

To allow using <%@ value in script sections, two special objects are replaced with <% and %>:

* `<%@ value object='startScript' %>`
* `<%@ value object='endScript' %>`

For example:

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## <%@ foreach {#<%@-foreach}

This instruction allows iteration on an array of objects loaded in the delivery to track individual links related to the objects.

Syntax:

`<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>`

Where:

* "object": name of the object to start from, typically an extra script object, but it can be a delivery.
* "xpath" (optional): xpath of the collection to loop on. Default is ".", meaning that object is the array to loop on.
* "index" (optional): if xpath is not "." and object is an array itself, item index of object (starts at 0).
* "item" (optional): name of a new object accessible with <%@ value inside the foreach loop. Default with the link name in the schema.

Example:

In the delivery properties/personalization, load an array of articles and a relation table between recipient and articles.

Displaying links to these articles can be done simply with a Javascript as follows:

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

With that solution, the links to all the articles are tracked without distinction. You can know that a recipient has clicked an article link, but you cannot know on which article.

The solution is to:

1. Pre-load all the possible articles in an extra script array of the delivery - articleList[] - which means there must be a finite number of possible articles.
1. Write a JavaScript function at the beginning of the content.

    ```
    <%@ value object='startScript' %>
    function displayArticle(articleId)
    {
      <%@ foreach object="articleList" item="article" %>
        if( articleId == <% value object="article" xpath="@id" %> ) 
        {
          <%@ value object='endScript' %>
            <a href="http://nl.net?a.jsp?article=<%@ value object="article" xpath="@id" %>">article</a>
          <%@ value object='startScript' %>
        } 
      <%@ end @%>
    }
    <%@ value object='endScript' %>
    ```
1. Display the article by calling the function.

    ```
    <%
    for(var i=0; i<recipient.rcpArticle.length; i++ )
    {
     displayArticle(recipient.rcpArticle[i].article.@id)
    }
    %>
    ```

