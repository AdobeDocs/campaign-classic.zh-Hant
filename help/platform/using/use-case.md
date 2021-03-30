---
solution: Campaign Classic
product: campaign
title: 使用案例
description: 使用案例
audience: platform
content-type: reference
topic-tags: filtering-data
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 3%

---


# 使用案例{#use-case}

## 針對訂閱者的電子郵件格式建立篩選{#creating-a-filter-on-the-email-format-of-subscribers}

此使用案例將示範如何建立篩選，以根據收件者電子郵件格式來排序電子報訂閱。

為此，我們需要使用預定義的檔案管理器：這些篩選器連結到文檔類型，並可通過&#x200B;**[!UICONTROL Administration > Configuration > Predefined filters]**&#x200B;節點訪問。 這些資料篩選器可用於應用程式中的每種編輯器（或檔案）類型。

資料篩選的建立方式與預先定義的篩選相同，但是還有一個欄位可供選取要套用篩選的檔案類型。

應用以下步驟：

1. 透過&#x200B;**[!UICONTROL Administration > Configuration > Predefined filters]**&#x200B;節點建立新篩選。
1. 按一下&#x200B;**[!UICONTROL Select link]**&#x200B;表徵圖以選擇相關文檔：

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. 選擇訂閱模式(nms:subscription)，然後按一下&#x200B;**[!UICONTROL OK]**。

   ![](assets/s_ncs_user_filter_select_schema.png)

1. 按一下&#x200B;**[!UICONTROL Edit link]**&#x200B;查看所選文檔的欄位。

   ![](assets/s_ncs_user_filter_edit_schema.png)

   然後，您可以檢視所選檔案的內容：

   ![](assets/s_ncs_user_filter_view_schema.png)

   您可以存取這些欄位，在篩選編輯器的正文中定義篩選條件。 應用程式篩選的定義方式與進階篩選完全相同。 請參閱[建立進階篩選](../../platform/using/creating-filters.md#creating-an-advanced-filter)。

1. 針對訂閱建立新的篩選，以僅顯示未定義電子郵件格式的訂閱：

   ![](assets/s_ncs_user_filter_parameters.png)

1. 按一下&#x200B;**[!UICONTROL Save]**，將篩選新增至此類型清單的預先定義篩選。
1. 您現在可以在收件者描述檔的&#x200B;**[!UICONTROL Subscriptions]**&#x200B;標籤中使用此篩選；按一下&#x200B;**[!UICONTROL Filters]**&#x200B;按鈕可以訪問「未知的電子郵件格式」過濾器。

   ![](assets/s_ncs_user_filter_on_events.png)

   目前篩選器的名稱會顯示在清單上方。 若要取消篩選，請按一下&#x200B;**[!UICONTROL Delete this filter]**&#x200B;圖示。

   ![](assets/s_ncs_user_filter_on_subscriptions.png)

