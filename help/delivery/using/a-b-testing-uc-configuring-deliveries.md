---
product: campaign
title: 配置交貨
description: 瞭解如何通過專用使用案例執行A/B測試
feature: A/B Testing
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# 在工作流中配置交貨 {#step-4--configuring-the-deliveries-in-the-workflow}

![](../../assets/common.svg)

一次 [群體建立](a-b-testing-uc-population-samples.md)，您可以配置交貨。 在此使用例中，前兩個交貨使您能夠將不同的內容發送到人口A和人口B。第三種是回退式交貨：將發送給不屬於A和B的接收者。其內容將由指令碼計算，並且與A或B相同，具體取決於開啟率最高的是哪個。 我們需要為第三次交貨配置等待期，以查明交貨A和B的結果。這就是為什麼第三個交貨 **[!UICONTROL Wait]** 的子菜單。

1. 轉到 **[!UICONTROL Split]** 活動，並將目標為填充A的轉換連結到工作流中已有的電子郵件遞送。

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. 按兩下交貨以將其開啟。
1. 使用下拉清單，選擇交貨A的模板。

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. 按一下 **[!UICONTROL Continue]** 查看交貨，然後保存。

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. 連結 **[!UICONTROL Split]** 目標為人口B的活動，轉到第二個電子郵件傳送。

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. 開啟交貨，在交貨B中選擇模板，然後保存交貨。

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. 將目的地為剩餘人口的過渡連結到 **[!UICONTROL Wait]** 的子菜單。

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. 開啟 **[!UICONTROL Wait]** 並配置5天的等待期。

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. 連結 **[!UICONTROL Wait]** 活動 **[!UICONTROL JavaScript code]** 的子菜單。

   ![](assets/use_case_abtesting_createdeliveries_008.png)

現在可以建立指令碼。 [了解更多資訊](a-b-testing-uc-script.md)。
