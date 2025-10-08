---
product: campaign
title: Adobe Campaign workspace
description: Learn how to use and customize Campaign workspace
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 5f689679-7148-4abd-a9bf-185854c64b13
---
# Adobe Campaign workspace{#adobe-campaign-workspace}

## Explore Adobe Campaign interface {#about-adobe-campaign-interface}

Once you are connected to the database, you will access the Adobe Campaign home page, which is a dashboard: it is made up of links and shortcuts which let you access capabilities, depending on your installation as well as general platform configurations.

From the central section of the home page, you can use links to access Campaign online documentation portal, forum and the support website.

![](assets/d_ncs_user_interface_home.png)

![](assets/do-not-localize/how-to-video.png) Discover Campaign workspace in [video](#video)

>[!NOTE]
>
>Adobe Campaign capabilities available on your instance depend on modules and add-ons installed. Some of them may also not be available, depending on your permissions and specific configurations.  
>
>Before installing any module or add-on, you need to check your license agreement or contact your Adobe account executive.

### Console and web access {#console-and-web-access}

The Adobe Campaign platform is accessible via a console or via an internet browser. See the compatible browsers in the [compatibility matrix](../../rn/using/compatibility-matrix.md#Browsers).

The web access interface is similar to the console interface. From a browser, you can use the same navigation and display features as in the console, but you can perform only a reduced set of actions on campaigns. For example, you can view and cancel campaigns, but you cannot modify campaigns. For a given operator, a campaign will show up with the following options in the console:

![From the dashboard of a campaign, the operator can view and cancel a campaign, but also modify it, and add deliveries, documents, and tasks to it.](assets/operation_from_console.png)

Whereas with web access, the options will mainly enable viewing:

![From a browser, the same operator can only view and cancel the campaign.](assets/operation_from_web.png)

Learn more about [using the web interface](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

### Languages {#languages}

The language is selected when installing your Adobe Campaign Classic instance.

![](assets/language.png)

You can choose between five different languages:

* English (UK)
* English (US)
* French
* German
* Japanese

The language you chose for your Adobe Campaign Classic instance might impact date and time formats. For more on this, refer to the [Campaign v8 (console) documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.

For more information on how to create an instance, refer to this [page](../../installation/using/creating-an-instance-and-logging-on.md).

>[!CAUTION]
>
>The language cannot be changed after the instance creation. 

## Navigation basics {#navigation-basics}

### Browse pages {#browsing-pages}

The various functionalities of the platform are broken down into core capabilities: use the links that you see in the top section of the interface to access them. 

![](assets/overview_home.png)

The list of core capabilities you can access depends on the packages and add-ons you have installed and on your access rights.

Each capability includes a set of functionalities based on task related needs and use context. For instance, the **[!UICONTROL Profiles and targets]** link gets you to the recipient lists, subscription services, existing targeting workflows and the shortcuts for creating these elements.

The lists are available via the **[!UICONTROL Lists]** link in the left-hand section of the **[!UICONTROL Profiles and Targets]** interface.

![](assets/recipient_list_overview.png)

### Use tabs {#using-tabs}

* When you click a core capability or a link, the relevant page replaces the current page. To go back to the previous page, click the **[!UICONTROL Back]** button on the toolbar. To return to the home page, click the **[!UICONTROL Home]** button. 

  ![](assets/d_ncs_user_interface_back_home_buttons.png)

* In the case of a menu or a shortcut to a display screen (such as a web application, program, delivery, report, etc.), the matching page is displayed in another tab. This enables you to browse from one page to the other using the tabs.

  ![](assets/d_ncs_user_interface_tabs.png)

### Create an element {#creating-an-element}

Each core capability section lets you browse among the available elements. To do this, use the shortcuts in the **[!UICONTROL Browsing]** section. The **[!UICONTROL Other choices]** link lets you access all other pages, regardless of environment.

You can create a new element (delivery, Web application, workflow, etc.) using the shortcuts in the **[!UICONTROL Create]** section on the left of the screen. Use the **[!UICONTROL Create]** button above the list to add new elements to the list.

For example, on the delivery page, use the **[!UICONTROL Create]** button to create a new delivery.

![](assets/d_ncs_user_interface_tab_add_del.png)


## Use Adobe Campaign explorer {#using-adobe-campaign-explorer}

The Adobe Campaign explorer is accessible via the toolbar icon. It lets you access the Adobe Campaign all the Adobe Campaign capabilities, configuration screens and a more detailed view of some of the platform elements.

To learn more about Adobe Campaign explorer, refer to these pages in the Campaign v8 (console) documentation: 

* [Campaign user interface overview](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-ui#ac-explorer-ui){target=_blank}

* [Campaign UI settings](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/configuration/ui-settings){target=_blank} 

* [Manage folders and views in the explorer](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/configuration/folders-and-views){target=_blank}.


## Work with lists {#manage-and-customize-lists}

In Campaign client console, data is displayed in lists. You can adapt these lists to your needs. For example, you can add columns, filter data, count records, save and share your settings.

>[!NOTE]
>
>To learn how to manage and customize lists in Adobe Campaign, please refer to the [Campaign v8 (console) documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/configuration/ui-settings#customize-lists){target=_blank}.

## Manage enumerations{#managing-enumerations} 

An enumeration (also called an itemized list) is a predefined list of values you can use to fill in certain fields. Enumerations help standardize field values, making data entry more consistent and simplifying queries. 

When defined, values are displayed in a drop-down list. A value can be selected directly or entered using predictive input, which suggests and completes matching entries. Some fields include predefined enumerations, and additional enumerations can be created if required.

Learn more how to **work with enumerations** in [Adobe Campaign v8 (console) documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}.

## Tutorial video {#video}

This video presents Campaign Classic workspace.

>[!VIDEO](https://video.tv.adobe.com/v/35130?quality=12)
