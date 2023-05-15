---
product: campaign
title: 設定傳送
description: 透過專屬的使用案例了解如何執行A/B測試
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# 在工作流程中設定傳送 {#step-4--configuring-the-deliveries-in-the-workflow}



一次 [建立母體](a-b-testing-uc-population-samples.md)，您可以設定傳送。 在此使用案例中，前兩個傳送可讓您將不同的內容傳送至母體A和B。第三個傳送是後退傳送：它會傳送給不屬於A或B的收件者。其內容將由指令碼計算，且會與A或B相同，視哪個開啟率最高者而定。 我們需要設定第三個傳送的等待期，以了解傳送A和B的結果。這就是為什麼第三個傳送包含 **[!UICONTROL Wait]** 活動。

1. 前往 **[!UICONTROL Split]** 活動，並將目的地為母體A的轉變連結至工作流程中已進行的其中一個電子郵件傳送。

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. 連按兩下傳送以開啟。
1. 使用下拉式清單，選取傳送A的範本。

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. 按一下 **[!UICONTROL Continue]** 若要檢視傳送，請儲存。

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. 連結 **[!UICONTROL Split]** 目的地為母體B的活動，傳送至第二個電子郵件。

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. 開啟傳送並選取傳送B中的範本，然後儲存傳送。

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. 將目的地為剩餘母體的轉變連結至 **[!UICONTROL Wait]** 活動。

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. 開啟 **[!UICONTROL Wait]** 活動並設定5天的等候期間。

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. 連結 **[!UICONTROL Wait]** 活動 **[!UICONTROL JavaScript code]** 活動。

   ![](assets/use_case_abtesting_createdeliveries_008.png)

您現在可以建立指令碼。 [了解更多](a-b-testing-uc-script.md)。
