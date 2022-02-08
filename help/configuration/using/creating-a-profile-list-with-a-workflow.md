---
product: campaign
title: 使用工作流程建立設定檔清單
description: 瞭解如何在工作流中建立配置檔案清單
feature: Workflows
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: 8fa50d17a9ff36ccc310860ac93771590cfd76fd
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 10%

---

# 使用工作流程建立設定檔清單{#creating-a-profile-list-with-a-workflow}

![](../../assets/common.svg)

建立 **[!UICONTROL List]** 根據新收件人表鍵入清單，您需要建立將生成清單的目標工作流。

有關「市場活動」中清單的詳細資訊，請參閱 [此部分](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign)。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

要在自定義收件人表中建立目標工作流並更新收件人，請執行以下步驟：

1. 轉到 **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** 的子菜單。
1. 建立新目標工作流。
1. 放置a **查詢** 活動後跟 **清單更新** 的子菜單。

   ![](assets/mapping_create_list_workflow01.png)

1. 按兩下 **查詢** 活動，然後按一下 **[!UICONTROL Edit the query]** 根據新收件人表的架構選擇目標維(在本例中： **個人**)。 按一下 **[!UICONTROL Finish]** 確認。

   ![](assets/mapping_create_list_workflow03.png)

1. 按兩下 **清單更新** 活動，然後選擇 **[!UICONTROL Create the list if necessary (Computed name)]** 按鈕。

   ![](assets/mapping_create_list_workflow02.png)

1. 為新清單選擇建立資料夾。
1. 執行工作流以建立清單。
1. 在樹節點中查看結果，在 **[!UICONTROL List update]** 的子菜單。

   儀表板指定清單所基於的架構，如下所示：

   ![](assets/mapping_list_view.png)
