---
product: campaign
title: 設定傳遞
description: 瞭解如何透過專屬的使用案例執行A/B測試
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



一次 [母體已建立](a-b-testing-uc-population-samples.md)，您可以設定傳送。 在此使用案例中，前兩個傳送可讓您傳送不同的內容給母體A和B。第三個傳遞是後援傳遞：會傳送給不屬於A或B的收件者。其內容將由指令碼計算，並將與A或B相同，具體取決於獲得最高開啟率的使用者。 我們需要設定第三次傳送的等待時間，以找出傳送A和B的結果。這就是第三個傳遞包含 **[!UICONTROL Wait]** 活動。

1. 前往 **[!UICONTROL Split]** 活動，並將目的地為母體A的轉變連結至工作流程中已存在的其中一個電子郵件傳送。

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. 連按兩下傳遞以開啟。
1. 使用下拉式清單，選取傳送A的範本。

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. 按一下 **[!UICONTROL Continue]** 以檢視傳遞，然後儲存。

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. 連結的轉變 **[!UICONTROL Split]** 預定母體B至第二封電子郵件傳遞的活動。

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. 開啟傳遞，並在傳遞B中選取範本，然後儲存傳遞。

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. 將預定給剩餘母體的轉變連結至 **[!UICONTROL Wait]** 活動。

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. 開啟 **[!UICONTROL Wait]** 活動並設定5天的等候時間。

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. 連結 **[!UICONTROL Wait]** 活動至 **[!UICONTROL JavaScript code]** 活動。

   ![](assets/use_case_abtesting_createdeliveries_008.png)

您現在可以建立指令碼。 [了解更多](a-b-testing-uc-script.md)。
