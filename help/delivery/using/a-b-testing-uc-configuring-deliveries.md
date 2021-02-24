---
solution: Campaign Classic
product: campaign
title: 設定傳送
description: 瞭解如何透過專屬的使用案例來執行A/B測試。
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 50a10e16f320a67cb4ad0e31c1cbe8a9365b7887
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---


# 在工作流{#step-4--configuring-the-deliveries-in-the-workflow}中配置傳送

下一步是設定傳送。 它們的目的地是在前一個階段建立的三個人口：[步驟2:配置人口樣本](#step-2--configuring-population-samples)。 前兩個傳送可讓您傳送不同的內容給人口A和B。第三批貨物的目的地是既未收到A也未收到B的人口。其內容將由指令碼計算，並會與A或B相同，視哪一個開啟率最高而定。 我們需要設定第三個交貨的等待期，以瞭解交貨A和B的結果。這就是為什麼第三個傳送包含&#x200B;**[!UICONTROL Wait]**&#x200B;活動。

1. 轉至&#x200B;**[!UICONTROL Split]**&#x200B;活動，並將目的地為人口A的轉換連結至工作流程中已有的電子郵件傳送。

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. 連按兩下傳送以開啟。
1. 使用下拉式清單，選取傳送A的範本。

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. 按一下&#x200B;**[!UICONTROL Continue]**&#x200B;以檢視傳送，然後儲存。

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. 將目的地為人口B的&#x200B;**[!UICONTROL Split]**&#x200B;活動的轉換連結至第二個電子郵件傳送。

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. 開啟傳送並選取傳送B中的範本，然後儲存傳送。

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. 將目的地為剩餘人口的轉場連結至&#x200B;**[!UICONTROL Wait]**&#x200B;活動。

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. 開啟&#x200B;**[!UICONTROL Wait]**&#x200B;活動並設定5天的等候期。

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. 將&#x200B;**[!UICONTROL Wait]**&#x200B;活動連結至&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動。

   ![](assets/use_case_abtesting_createdeliveries_008.png)

您現在可以建立指令碼(請參閱[步驟5:建立指令碼](../../delivery/using/a-b-testing-uc-script.md))。
