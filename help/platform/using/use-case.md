---
product: campaign
title: 使用實例
description: 使用實例
feature: Subscriptions, Email, Data Management
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 85ded096-7d27-41b3-8ef2-93f5ca8def82
hide: true
hidefromtoc: true
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 3%

---

# 使用實例{#use-case}



## 建立訂閱者電子郵件格式的篩選器 {#creating-a-filter-on-the-email-format-of-subscribers}

此使用案例會向您展示如何建立篩選器，以根據收件者電子郵件格式來排序電子報訂閱。

為此，我們需要使用預先定義的篩選器：這些篩選器已連結至檔案型別，並可透過&#x200B;**[!UICONTROL Administration > Configuration > Predefined filters]**&#x200B;節點存取。 這些資料篩選器可用於應用程式中的每種型別的編輯器（或檔案）。

資料篩選的建立方式與預先定義的篩選相同，但有一個額外的欄位可用來選取將套用篩選的檔案型別。

應用以下步驟：

1. 透過&#x200B;**[!UICONTROL Administration > Configuration > Predefined filters]**&#x200B;節點建立新的篩選器。
1. 按一下&#x200B;**[!UICONTROL Select link]**&#x200B;圖示以選取相關檔案：

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. 選取訂閱結構描述(nms：subscription)並按一下&#x200B;**[!UICONTROL OK]**。

   ![](assets/s_ncs_user_filter_select_schema.png)

1. 按一下&#x200B;**[!UICONTROL Edit link]**&#x200B;以檢視所選檔案的欄位。

   ![](assets/s_ncs_user_filter_edit_schema.png)

   然後，您可以檢視所選檔案的內容：

   ![](assets/s_ncs_user_filter_view_schema.png)

   您可以存取這些欄位，以在篩選編輯器內文中定義篩選條件。 應用程式篩選的定義方式與進階篩選完全相同。 請參閱[建立進階篩選器](../../platform/using/creating-filters.md#creating-an-advanced-filter)。

1. 在訂閱上建立新的篩選器，以僅顯示具有未定義電子郵件格式的訂閱：

   ![](assets/s_ncs_user_filter_parameters.png)

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;新增篩選器至此型別清單的預先定義篩選器。
1. 您現在可以在收件者設定檔的&#x200B;**[!UICONTROL Subscriptions]**&#x200B;索引標籤中使用此篩選器；您可以按一下&#x200B;**[!UICONTROL Filters]**&#x200B;按鈕來存取「未知電子郵件格式」篩選器。

   ![](assets/s_ncs_user_filter_on_events.png)

   目前篩選的名稱會顯示在清單上方。 若要取消篩選，請按一下&#x200B;**[!UICONTROL Delete this filter]**&#x200B;圖示。

   ![](assets/s_ncs_user_filter_on_subscriptions.png)
