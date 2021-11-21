---
product: campaign
title: 追蹤行銷活動
description: 追蹤行銷活動
audience: campaign
content-type: reference
topic-tags: distributed-marketing
exl-id: 87d1909c-d2eb-47ce-a860-0e78a64d2914
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 2%

---

# 追蹤行銷活動{#tracking-a-campaign}

![](../../assets/v7-only.svg)

中央實體運算子可以在促銷活動套件清單中追蹤促銷活動訂單。

這可讓他們：

* [篩選套件](#filter-packages),
* [編輯套件](#edit-packages),
* [取消包](#cancel-a-package),
* [重新初始化套件](#reinitializing-a-package).

## 篩選套件 {#filter-packages}

從 **[!UICONTROL Campaigns]** 頁簽，您可以顯示 **[!UICONTROL Campaign packages]** 會重新分組所有現有的分散式行銷活動。 您可以篩選此清單，使其只顯示已發佈、延遲、待核准等的促銷活動。 若要這麼做，請按一下此檢視上方區段的連結，或使用 **[!UICONTROL Filter list]** 連結並選取要顯示的促銷活動套件狀態。

![](assets/mkg_dist_catalog_filter.png)

## 編輯套件 {#edit-packages}

此 **[!UICONTROL Campaign packages]** 頁面可讓您檢視每個套件的摘要。

此摘要會顯示下列資訊：標籤、促銷活動類型，以及建立促銷活動的促銷活動名稱，以及資料夾。

按一下套件名稱加以編輯。 您也可以依其本地實體和狀態來檢視訂單。

此資訊也可在 **[!UICONTROL Campaign orders]** 查看列出所有訂單。

![](assets/mkg_dist_catalog_op_command_details.png)

中央運算子可以編輯順序。 執行此作業有兩種方式：

1. 運算子可以按一下訂單名稱加以編輯：這會顯示訂單詳細資訊。

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   此 **[!UICONTROL Edit > General]** 索引標籤可讓您在訂購促銷活動時，檢視本機實體輸入的資訊。

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. 運算子可以按一下促銷活動套件標籤來編輯它並變更特定設定。

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## 取消包 {#cancel-a-package}

中央實體可隨時取消促銷活動套件。

按一下 **[!UICONTROL Cancel]** 行銷活動套件中 **[!UICONTROL Dashboard]**.

![](assets/mkg_dist_cancel_op_from_dashboard.png)

此 **[!UICONTROL Comment]** 欄位可讓您說明取消的正確性。

針對 **本機行銷活動**，取消套件會從可用行銷活動清單中移除該套件。

針對 **協作行銷活動**，取消套件會觸發許多動作：

1. 與此包相關的任何訂單都將被取消，

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. 參考促銷活動已取消，所有作用中的程式（工作流程、傳送）亦已停止，

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. 向所有有關地方實體發送通知。

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

中央實體仍可存取已取消的套件並重新初始化（如有必要，請參閱下方）。 只有當地實體獲得批准並啟動後，才會再次向其提供。 程式包重新初始化過程如下所示。

## 重新初始化套件 {#reinitializing-a-package}

已發佈的促銷活動套件可重新初始化、修改，並可供本機實體使用。

1. 選擇相關包。
1. 按一下 **[!UICONTROL Reinitialize the package to reuse it]** 連結，按一下 **[!UICONTROL OK]**.

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. 按一下 **[!UICONTROL Save]** 按鈕以核准套件重新初始化。

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. 包狀態更改為 **[!UICONTROL Being edited]**. 再次修改、核准及發佈，將其還原至促銷活動套件清單。

>[!NOTE]
>
>您也可以重新初始化已取消的促銷活動套件。
