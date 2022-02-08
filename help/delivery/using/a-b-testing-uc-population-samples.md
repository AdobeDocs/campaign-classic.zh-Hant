---
product: campaign
title: 設定人口樣本
description: 瞭解如何通過專用使用案例執行A/B測試
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
source-git-commit: 90c52ec144a6a3c1b534a80507e38fa3ed64fc83
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 7%

---

# 設定母體樣本 {#step-2--configuring-population-samples}

![](../../assets/common.svg)

## 配置查詢活動 {#configuring-the-query-activity}

* 按兩下 **[!UICONTROL Query]** 的子菜單。

   ![](assets/use_case_abtesting_createrecipients_001.png)

* 按一下 **[!UICONTROL Edit query]** 連結並選擇要瞄準的收件人。

   ![](assets/use_case_abtesting_createrecipients_002.png)

* 連結 **[!UICONTROL Query]** 活動 **[!UICONTROL Split]** 的子菜單。

   ![](assets/use_case_abtesting_createrecipients_003.png)

## 配置拆分活動 {#configuring-the-split-activity}

通過本活動，您可以建立多個群體：接收A的，接收B的，以及剩餘人口。 使用隨機選擇，您只需將每個交貨的部分數量作為目標。

1. 建立人口A:

   * 按兩下 **[!UICONTROL Split]** 的子菜單。

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * 在現有頁籤中，將標籤更改為填充A。

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * 選擇 **[!UICONTROL Limit the selected records]** 的雙曲餘切值。

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * 按一下 **[!UICONTROL Edit]** 連結，選擇 **[!UICONTROL Activate random sampling]**，然後按一下 **[!UICONTROL Next]**。

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * 將閾值設定為10%，然後按一下 **[!UICONTROL Finish]**。

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. 建立人口B:

   * 按一下 **[!UICONTROL Add]** 為填充項B建立新頁籤。

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * 將人口限制為以前的10%。

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. 建立剩餘人口：

   * 移至 **[!UICONTROL General]** 索引標籤。

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * 選取 **[!UICONTROL Generate complement]**。

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * 更改標籤以指定此填充不包括A和B，然後按一下 **[!UICONTROL OK]** 來關閉活動。

      ![](assets/use_case_abtesting_createrecipients_013.png)

現在可以建立兩個交貨模板。 [了解更多](a-b-testing-uc-delivery-templates.md)).
