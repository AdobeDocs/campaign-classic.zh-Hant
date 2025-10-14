---
product: campaign
title: 設定 A/B 測試
description: 瞭解如何在Campaign中設定A/B測試
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: A/B Testing
role: User
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 3%

---

# 設定 A/B 測試 {#configuring-a-b-testing}

本節詳細說明如何建立工作流程以執行A/B測試。

1. 建立新的工作流程，然後設定查詢活動以定位所需的母體。 請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html){target="_blank"}。

1. 新增分割活動，將目標母體分割成多個子集。 請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html){target="_blank"}。

1. 開啟活動，然後視需要設定每個子集。 如需如何設定&#x200B;**[!UICONTROL Split]**&#x200B;活動的詳細資訊，請參閱[本節](../../workflow/using/split.md)。

   在此範例中，我們要測試電子報的2個新主題，每個主題會向目標人口的10%進行簡報。

   ![](assets/ab-testing-split.png)

1. 新增轉變，以向其餘母體傳送具有目前主旨的Newsletter。 若要這麼做，請從「**[!UICONTROL Generate complement]**」標籤啟動「**[!UICONTROL General]**」選項。

   ![](assets/ab-testing-complement.png)

1. 對於每個子集，新增要測試的傳遞版本。

   ![](assets/ab-testing-delivery.png)

您現在可以開始工作流程。 傳送後，您將能夠在傳送記錄中追蹤三個子集的行為，以檢視哪個主題最成功。

工作流程也可讓您藉由自動識別表現較佳的傳送變體，然後將其傳送至剩餘母體，來自動化您的流程。 如需詳細資訊，請參閱此專屬的[使用案例](a-b-testing-use-case.md)。
