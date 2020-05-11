---
title: Customizing the emoticon list
description: Learn how to customize the emoticon list when using Adobe Campaign Classic.
page-status-flag: never-activated
uuid: ddcc2e3b-e251-4a7a-a22a-28701522839f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 2ea2747f-957f-41a9-a03f-20c03fa99116
index: y
internal: n
snippet: y
---

# Customizing the emoticon list {#customize-emoticons}

The emoticon list displayed in the pop-up is ruled by an enumeration.
An enumeration allows you to display values in a list in order to restrict the choices that the user has for a given field.
The emoticon list order can be customized, you can also add other emoticons to your list.
Emoticons are available for email and push for more on this refer to

## Adding a new emoticon {#add-new-emoticon}

>[!NOTE]
>Out-of-the-box enumerations can only be managed by an administrator of your Adobe Campaign Classic console.

1. Choose your new emoticon to add in this [page](https://unicode.org/emoji/charts/full-emoji-list.html). Note that it has to be compatible with the different platforms such as browser and OS.

1. From the **[!UICONTROL Explorer]**, select **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** and click the **[!UICONTROL Emoticon list]** out-of-the-box enumeration.

1. Click **[!UICONTROL Add]**

1. Fill in the fields:
    * **[!UICONTROL U+]**: Code of your new emoticon. You can find the list of emoticons' code in this [page](https://unicode.org/emoji/charts/full-emoji-list.html).

    * **[!UICONTROL Label)**: Label of your new emoticon.

    * **[!UICONTROL Display order]**: Choose here in which order your new emoticon will be displayed. Note that by selecting an existing display order the existing emoticon will be automatically moved to the store.

        >[!NOTE]
        >The emoticon list can not exceed 81 entries.

1. Click **[!UICONTROL Ok]** then **[!UICONTROL Save]** when your configuration is finished.

1. For your changed to be taken into account, you need to clear your cache by selecting **[!UICONTROL File]** > **[!UICONTROL Clear the local cache...]**.

Your new emoticon has now been added to the **[!UICONTROL Emoticon list]** out-of-the-box enumeration. You can change its **[!UICONTROL Display order]** by double-clicking it and move it to the store if you do not need it anymore.
It can now be used in your deliveries. For more information on how to use emoticons in your deliveries, refer to this page.

## Emoticons selection {#emoticons-selection}

You can find below the list of the 81 out-of-the-box emoticons which can be found in the pop-up window when personalizing your deliveries.

| Display order | Code | Label |
|:-:|:-:|:-:|
| 1  | U+1F600 | grinning face |
| 2  | U+1F603 | grinning face with big eyes|
| 3  | U+1F604 | grinning face with smiling eyes |
| 4  | U+1F601 | beaming face with smiling eyes  |
| 5  | U+1F606 | grinning squinting face  |
| 6  | U+1F642 | slightly smiling face    |
| 7  | U+1F631 | face screaming in fear   |
| 8  | U+1F618 | face blowing a kiss  |
| 9  | U+1F61A | kissing face with closed eyes   |
| 10 | U+1F61C | winking face with tongue |
| 11 | U+1F60E | smiling face with sunglasses    |
| 12 | U+1F637 | face with medical mask   |
| 13 | U+1F61D | squinting face with tongue |
| 14 | U+1F917 | hugging face  |
| 15 | U+1F60D | smiling face with heart-eyes |
| 16 | U+1F634 | sleeping  |
| 17 | U+263A  | smiling face  |
| 18 | U+1F44F | clapping hands |
| 19 | U+1F44D | thumbs up |
| 20 | U+1F44E | thumbs down   |
| 21 | U+1F64C | raising hands |
| 22 | U+270C  | victory hand  |
| 23 | U+1F495 | two hearts    |
| 24 | U+2764  | red heart |
| 25 | U+1F5A4 | black hear    |
| 26 | U+1F3D6 | beach with umbrella  |
| 27 | U+1F684 | high-speed train|
| 28 | U+1F6F3 | passenger ship  |
| 29 | U+2708  | airplane  |
| 30 | U+1F697 | automobile    |
| 31 | U+1F6CF | bed  |
| 32 | U+1F30A | water wave    |
| 33 | U+1F334 | palm tree |
| 34 | U+1F4F7 | camera    |
| 35 | U+2600  | sun  |
| 36 | U+1F308 | rainbow   |
| 37 | U+2744  | snowflake |
| 38 | U+1F320 | shooting star |
| 39 | U+1F332 | evergreen tree  |
| 40 | U+1F33C | blossom   |
| 41 | U+1F337 | tulip|
| 42 | U+1F37E | bottle with popping cork |
| 43 | U+1F382 | birthday cake |
| 44 | U+1F381 | wrapped gift  |
| 45 | U+1F389 | party popper  |
| 46 | U+1F388 | balloon   |
| 47 | U+1F38A | confetti bal  |
| 48 | U+2728  | sparkles  |
| 49 | U+1F942 | clinking glasses|
| 50 | U+1F378 | cocktail glass  |
| 51 | U+1F3B5 | Music note    |
| 52 | U+23F3  | hourglass not done   |
| 53 | U+23F0  | alarm clock   |
| 54 | U+1F5D3 | spiral calendar |
| 55 | U+270F  | pencil    |
| 56 | U+1F4CC | pushpin   |
| 57 | U+1F4CD | round pushpin |
| 58 | U+1F553 | four o’clock  |
| 59 | U+1F4CB | clipboard |
| 60 | U+1F514 | bell |
| 61 | U+1F510 | locked with key |
| 62 | U+2705  | check mark button |
| 63 | U+274E  | cross mark button |
| 64 | U+2795  | Plus sign |
| 65 | U+1F4E6 | package   |
| 66 | U+2B50  | star |
| 67 | U+1F3C6 | trophy    |
| 68 | U+1F3C1 | chequered flag |
| 69 | U+1F340 | four leaf clover |
| 70 | U+1F4A1 | light bulb |
| 71 | U+25B6  | play button |
| 72 | U+00A9  | copyright |
| 73 | U+1F355 | pizza|
| 74 | U+1F525 | fire |
| 75 | U+1F6A8 | police car light |
| 76 | U+1F4DA | books|
| 77 | U+1F4B5 | dollar banknote |
| 78 | U+1F4B6 | euro banknote |
| 79 | U+1F4B4 | yen banknote  |
| 80 | U+2709  | envelope  |
| 81 | U+1F6A9 | triangular flag |