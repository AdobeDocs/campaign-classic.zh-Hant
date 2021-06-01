---
product: campaign
title: 追蹤行銷活動
description: 追蹤行銷活動
audience: campaign
content-type: reference
topic-tags: distributed-marketing
exl-id: 87d1909c-d2eb-47ce-a860-0e78a64d2914
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 2%

---

# 追蹤行銷活動{#tracking-a-campaign}

中央實體運算子可以在促銷活動套件清單中追蹤促銷活動訂單。

這可讓使用者：

* [篩選套件](#filter-packages),
* [編輯套件](#edit-packages)、
* [取消包](#cancel-a-package),
* [重新初始化套件](#reinitializing-a-package)。

## 篩選器包{#filter-packages}

從&#x200B;**[!UICONTROL Campaigns]**&#x200B;標籤中，您可以顯示&#x200B;**[!UICONTROL Campaign packages]**&#x200B;清單，該清單會重新分組所有現有的Distributed Marketing促銷活動。 您可以篩選此清單，使其只顯示已發佈、延遲、待核准等的促銷活動。 若要這麼做，請按一下此檢視上方區段的連結，或使用&#x200B;**[!UICONTROL Filter list]**&#x200B;連結並選取要顯示的促銷活動套件狀態。

![](assets/mkg_dist_catalog_filter.png)

## 編輯包{#edit-packages}

**[!UICONTROL Campaign packages]**&#x200B;頁面可讓您檢視每個套件的摘要。

此摘要會顯示下列資訊：標籤、促銷活動類型，以及建立促銷活動的促銷活動名稱，以及資料夾。

按一下套件名稱加以編輯。 您也可以依其本地實體和狀態來檢視訂單。

**[!UICONTROL Campaign orders]**&#x200B;檢視中也提供此資訊，列出所有訂單。

![](assets/mkg_dist_catalog_op_command_details.png)

中央運算子可以編輯順序。 執行此作業有兩種方式：

1. 運算子可以按一下訂單名稱加以編輯：這會顯示訂單詳細資訊。

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   **[!UICONTROL Edit > General]**&#x200B;標籤可讓您檢視本機實體在訂購促銷活動時所輸入的資訊。

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. 運算子可以按一下促銷活動套件標籤來編輯它並變更特定設定。

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## 取消包{#cancel-a-package}

中央實體可隨時取消促銷活動套件。

按一下促銷活動套件&#x200B;**[!UICONTROL Dashboard]**&#x200B;中的&#x200B;**[!UICONTROL Cancel]**。

![](assets/mkg_dist_cancel_op_from_dashboard.png)

**[!UICONTROL Comment]**&#x200B;欄位可讓您證明取消的正確性。

若為&#x200B;**本機促銷活動**，取消套件會將其從可用行銷活動清單中移除。

對於&#x200B;**協作促銷活動**，取消套件會觸發許多動作：

1. 與此包相關的任何訂單都將被取消，

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. 參考促銷活動已取消，所有作用中的程式（工作流程、傳送）亦已停止，

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. 向所有有關地方實體發送通知。

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

中央實體仍可存取已取消的套件並重新初始化（如有必要，請參閱下方）。 只有當地實體獲得批准並啟動後，才會再次向其提供。 程式包重新初始化過程如下所示。

## 重新初始化包{#reinitializing-a-package}

已發佈的促銷活動套件可重新初始化、修改，並可供本機實體使用。

1. 選擇相關包。
1. 按一下&#x200B;**[!UICONTROL Reinitialize the package to reuse it]**&#x200B;連結，然後按一下&#x200B;**[!UICONTROL OK]**。

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;按鈕，核准套件重新初始化。

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. 包狀態更改為&#x200B;**[!UICONTROL Being edited]**。 再次修改、核准及發佈，將其還原至促銷活動套件清單。

>[!NOTE]
>
>您也可以重新初始化已取消的促銷活動套件。
