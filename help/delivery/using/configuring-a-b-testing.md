---
product: campaign
title: 設定 A/B 測試
description: 瞭解如何在Campaign中設定A/B測試
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 3%

---

# 設定 A/B 測試 {#configuring-a-b-testing}



本節詳細說明如何建立工作流程以執行A/B測試。

1. 建立新的工作流程，然後設定 [查詢](../../workflow/using/query.md) 目標定位所需母體的活動。

1. 新增 [Split](../../workflow/using/split.md) 活動，將目標母體分割成多個子集。

1. 開啟活動，然後視需要設定每個子集。 如需如何設定的詳細資訊 **[!UICONTROL Split]** 活動，請參閱 [本節](../../workflow/using/split.md).

   在此範例中，我們要測試電子報的2個新主題，將每個主題展示給目標人口的10%。

   ![](assets/ab-testing-split.png)

1. 新增轉變，以向其餘母體傳送具有目前主題的Newsletter。 若要這麼做，請啟動 **[!UICONTROL Generate complement]** 選項來自 **[!UICONTROL General]** 標籤。

   ![](assets/ab-testing-complement.png)

1. 對於每個子集，新增要測試的傳遞版本。

   ![](assets/ab-testing-delivery.png)

您現在可以開始工作流程。 傳送後，您將能夠追蹤傳送記錄中三個子集的行為，以檢視哪個主題最成功。

工作流程也可讓您藉由自動識別執行得更好的傳送變體，然後將其傳送至剩餘母體，來自動化您的流程。 如需詳細資訊，請參閱此專屬檔案： [使用案例](a-b-testing-use-case.md).
