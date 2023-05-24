---
product: campaign
title: 使用案例
description: 使用案例
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 85ded096-7d27-41b3-8ef2-93f5ca8def82
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 3%

---

# 使用案例{#use-case}



## 建立訂閱者電子郵件格式的篩選器 {#creating-a-filter-on-the-email-format-of-subscribers}

此使用案例會向您展示如何建立篩選器，以根據收件者電子郵件格式來排序電子報訂閱。

為此，我們需要使用預先定義的篩選條件：這些篩選條件會連結至檔案型別，並可透過以下方式存取： **[!UICONTROL Administration > Configuration > Predefined filters]** 節點。 這些資料篩選器可用於應用程式中的每種型別的編輯器（或檔案）。

資料篩選的建立方式與預先定義的篩選相同，但有一個額外的欄位可用來選取將套用篩選的檔案型別。

應用以下步驟：

1. 建立新的篩選器，透過 **[!UICONTROL Administration > Configuration > Predefined filters]** 節點。
1. 按一下 **[!UICONTROL Select link]** 圖示以選取相關檔案：

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. 選取訂閱綱要(nms：subscription)，然後按一下 **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. 按一下 **[!UICONTROL Edit link]** 以檢視所選檔案的欄位。

   ![](assets/s_ncs_user_filter_edit_schema.png)

   然後您可以檢視所選檔案的內容：

   ![](assets/s_ncs_user_filter_view_schema.png)

   您可以存取這些欄位，以在篩選編輯器內文中定義篩選條件。 應用程式篩選的定義方式與進階篩選完全相同。 另請參閱 [建立進階篩選](../../platform/using/creating-filters.md#creating-an-advanced-filter).

1. 在訂閱上建立新的篩選器，以僅顯示具有未定義電子郵件格式的訂閱：

   ![](assets/s_ncs_user_filter_parameters.png)

1. 按一下 **[!UICONTROL Save]** 將篩選器新增至此型別清單的預先定義篩選器。
1. 您現在可以在以下位置使用此篩選器： **[!UICONTROL Subscriptions]** 收件者設定檔的索引標籤；您可以按一下 **[!UICONTROL Filters]** 按鈕。

   ![](assets/s_ncs_user_filter_on_events.png)

   目前篩選器的名稱會顯示在清單上方。 若要取消篩選，請按一下 **[!UICONTROL Delete this filter]** 圖示。

   ![](assets/s_ncs_user_filter_on_subscriptions.png)
