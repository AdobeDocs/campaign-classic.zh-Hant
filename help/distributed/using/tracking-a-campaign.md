---
product: campaign
title: 追蹤行銷活動
description: 瞭解如何使用Campaign分散式行銷追蹤行銷活動
feature: Distributed Marketing
exl-id: 87d1909c-d2eb-47ce-a860-0e78a64d2914
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 1%

---

# 追蹤行銷活動{#tracking-a-campaign}



中央實體運運算元可追蹤行銷活動套件清單中的行銷活動訂單。

如此可讓他們：

* [篩選封裝](#filter-packages)，
* [編輯套裝](#edit-packages)，
* [取消套裝](#cancel-a-package)，
* [重新初始化封裝](#reinitializing-a-package).

## 篩選封裝 {#filter-packages}

從 **[!UICONTROL Campaigns]** 索引標籤上，您可以顯示 **[!UICONTROL Campaign packages]** ，會將所有現有的分散式行銷活動重新分組。 您可以篩選此清單，使其僅顯示已發佈、延遲、未決核准等行銷活動。 若要這麼做，請按一下此檢視上方區段中的連結，或使用 **[!UICONTROL Filter list]** 連結並選取要顯示的行銷活動套件狀態。

![](assets/mkg_dist_catalog_filter.png)

## 編輯套裝 {#edit-packages}

此 **[!UICONTROL Campaign packages]** 頁面可讓您檢視每個套件的摘要。

此摘要會顯示下列資訊：標籤、行銷活動型別，以及從中建立行銷活動的名稱和資料夾。

按一下封裝名稱以進行編輯。 您也可以依其本機實體及其狀態來檢視訂單。

此資訊也提供在 **[!UICONTROL Campaign orders]** 檢視，其中列出所有訂單。

![](assets/mkg_dist_catalog_op_command_details.png)

中央運運算元可以編輯順序。 有兩種方法可以達成此目的：

1. 運運算元可以按一下訂單名稱來進行編輯：這會顯示訂單詳細資料。

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   此 **[!UICONTROL Edit > General]** 索引標籤可讓您檢視本機實體在訂購行銷活動時輸入的資訊。

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. 操作員可以按一下行銷活動套件標籤以進行編輯並變更某些設定。

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## 取消套裝 {#cancel-a-package}

中央實體可隨時取消行銷活動套件。

按一下 **[!UICONTROL Cancel]** 在行銷活動套件中 **[!UICONTROL Dashboard]**.

![](assets/mkg_dist_cancel_op_from_dashboard.png)

此 **[!UICONTROL Comment]** 欄位可讓您調整取消。

的 **本地行銷活動**，取消套件會將其從可用行銷活動清單中移除。

的 **合作行銷活動**，取消套件會觸發許多動作：

1. 與此封裝相關的任何訂單都會被取消，

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. 參考行銷活動已取消，且所有作用中的流程（工作流程、傳送）都會停止。

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. 會傳送通知給所有相關本機實體。

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

如有必要，中央實體仍可存取及重新初始化已取消的套件（請參閱下文）。 只有當本機實體核准並開始使用它們時，才會再次提供它們。 封裝重新初始化程式如下所示。

## 重新初始化封裝 {#reinitializing-a-package}

已發佈的行銷活動套件可以重新初始化、修改，並供本機實體使用。

1. 選取相關的套件。
1. 按一下 **[!UICONTROL Reinitialize the package to reuse it]** 連結並按一下 **[!UICONTROL OK]**.

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. 按一下 **[!UICONTROL Save]** 按鈕以核准封裝重新初始化。

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. 封裝狀態變更為 **[!UICONTROL Being edited]**. 再次修改、核准並發佈，以將其還原至行銷活動套件清單。

>[!NOTE]
>
>您也可以重新初始化已取消的行銷活動套件。
