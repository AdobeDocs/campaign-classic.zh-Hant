---
solution: Campaign Classic
product: campaign
title: 配置人口樣本
description: 瞭解如何透過專屬的使用案例來執行A/B測試。
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 50a10e16f320a67cb4ad0e31c1cbe8a9365b7887
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 2%

---


# 配置人口樣本{#step-2--configuring-population-samples}

## 配置查詢活動{#configuring-the-query-activity}

* 按兩下&#x200B;**[!UICONTROL Query]**&#x200B;活動。

   ![](assets/use_case_abtesting_createrecipients_001.png)

* 按一下&#x200B;**[!UICONTROL Edit query]**&#x200B;連結，並選取您要定位的收件者。

   ![](assets/use_case_abtesting_createrecipients_002.png)

* 將&#x200B;**[!UICONTROL Query]**&#x200B;活動連結至&#x200B;**[!UICONTROL Split]**&#x200B;活動。

   ![](assets/use_case_abtesting_createrecipients_003.png)

## 配置拆分活動{#configuring-the-split-activity}

此活動可讓您建立數個人口族群：接收遞送A的遞送B的遞送B的遞送B的遞送A和剩餘的人口。 使用隨機選擇可讓您只鎖定每個傳送的部分人口。

1. 建立人口A:

   * 按兩下&#x200B;**[!UICONTROL Split]**&#x200B;活動。

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * 在現有標籤中，將標籤變更為填入A。

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * 選擇&#x200B;**[!UICONTROL Limit the selected records]**&#x200B;選項。

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * 按一下&#x200B;**[!UICONTROL Edit]**&#x200B;連結，選擇&#x200B;**[!UICONTROL Activate random sampling]** ，然後按一下&#x200B;**[!UICONTROL Next]**。

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * 將閾值設定為10%，然後按一下&#x200B;**[!UICONTROL Finish]**。

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. 建立人口B:

   * 按一下&#x200B;**[!UICONTROL Add]**&#x200B;為人口B建立新頁籤。

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * 將人口限制為先前的10%。

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. 建立剩餘人口：

   * 移至 **[!UICONTROL General]** 索引標籤。

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * 選取 **[!UICONTROL Generate complement]**。

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * 變更標籤以指定此人口族群不包含A或B，然後按一下&#x200B;**[!UICONTROL OK]**&#x200B;以關閉活動。

      ![](assets/use_case_abtesting_createrecipients_013.png)

您現在可以建立兩個傳送範本(請參閱[步驟3:建立兩個傳送範本](../../delivery/using/a-b-testing-uc-delivery-templates.md))。
