---
product: campaign
title: 設定母體樣本
description: 瞭解如何透過專屬的使用案例執行A/B測試
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 7%

---

# 設定母體樣本 {#step-2--configuring-population-samples}



## 設定查詢活動 {#configuring-the-query-activity}

* 連按兩下 **[!UICONTROL Query]** 活動。

   ![](assets/use_case_abtesting_createrecipients_001.png)

* 按一下 **[!UICONTROL Edit query]** 連結並選取您要鎖定的收件者。

   ![](assets/use_case_abtesting_createrecipients_002.png)

* 連結 **[!UICONTROL Query]** 活動至 **[!UICONTROL Split]** 活動。

   ![](assets/use_case_abtesting_createrecipients_003.png)

## 設定分割活動 {#configuring-the-split-activity}

此活動可讓您建立多個母體：接收傳送A的母體、接收傳送B的母體，以及剩餘母體。 使用隨機選取可讓您只鎖定每個傳送的部分母體。

1. 建立母體A：

   * 連按兩下 **[!UICONTROL Split]** 活動。

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * 在現有索引標籤中，將標籤變更為母體A。

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * 選取 **[!UICONTROL Limit the selected records]** 選項。

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * 按一下 **[!UICONTROL Edit]** 連結，選取 **[!UICONTROL Activate random sampling]**，然後按一下 **[!UICONTROL Next]**.

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * 將臨界值設定為10%，然後按一下 **[!UICONTROL Finish]**.

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. 建立母體B：

   * 按一下 **[!UICONTROL Add]** 為母體B建立新索引標籤。

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * 和之前一樣，將人口限制在10%。

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. 建立剩餘母體：

   * 移至 **[!UICONTROL General]** 索引標籤。

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * 選取 **[!UICONTROL Generate complement]**。

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * 變更標籤以指定此母體既不包含A也不包含B，然後按一下 **[!UICONTROL OK]** 以關閉活動。

      ![](assets/use_case_abtesting_createrecipients_013.png)

您現在可以建立兩個傳遞範本。 [了解更多](a-b-testing-uc-delivery-templates.md)).
