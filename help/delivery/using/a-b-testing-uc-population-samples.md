---
product: campaign
title: 設定母體樣本
description: 瞭解如何透過專屬的使用案例執行A/B測試
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: A/B Testing
role: User
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 4%

---

# AB測試：設定母體樣本 {#step-2--configuring-population-samples}

## 設定查詢活動 {#configuring-the-query-activity}

* 連按兩下&#x200B;**[!UICONTROL Query]**&#x200B;活動。

  ![](assets/use_case_abtesting_createrecipients_001.png)

* 按一下&#x200B;**[!UICONTROL Edit query]**&#x200B;連結，並選取您要鎖定的收件者。

  ![](assets/use_case_abtesting_createrecipients_002.png)

* 將&#x200B;**[!UICONTROL Query]**&#x200B;活動連結至&#x200B;**[!UICONTROL Split]**&#x200B;活動。

  ![](assets/use_case_abtesting_createrecipients_003.png)

## 設定分割活動 {#configuring-the-split-activity}

此活動可讓您建立多個母體：接收傳送A的母體、接收傳送B的母體，以及剩餘母體。 使用隨機選取可讓您只鎖定每次傳送的部分母體。

1. 建立母體A：

   * 連按兩下&#x200B;**[!UICONTROL Split]**&#x200B;活動。

     ![](assets/use_case_abtesting_createrecipients_004.png)

   * 在現有索引標籤中，將標籤變更為母體A。

     ![](assets/use_case_abtesting_createrecipients_005.png)

   * 選取&#x200B;**[!UICONTROL Limit the selected records]**&#x200B;選項。

     ![](assets/use_case_abtesting_createrecipients_006.png)

   * 按一下&#x200B;**[!UICONTROL Edit]**&#x200B;連結，選取&#x200B;**[!UICONTROL Activate random sampling]**，然後按一下&#x200B;**[!UICONTROL Next]**。

     ![](assets/use_case_abtesting_createrecipients_007.png)

   * 將臨界值設為10%，然後按一下&#x200B;**[!UICONTROL Finish]**。

     ![](assets/use_case_abtesting_createrecipients_008.png)

1. 建立母體B：

   * 按一下&#x200B;**[!UICONTROL Add]**&#x200B;為母體B建立新索引標籤。

     ![](assets/use_case_abtesting_createrecipients_009.png)

   * 和之前一樣，將母體限製為10%。

     ![](assets/use_case_abtesting_createrecipients_010.png)

1. 建立剩餘母體：

   * 前往&#x200B;**[!UICONTROL General]**&#x200B;標籤。

     ![](assets/use_case_abtesting_createrecipients_011.png)

   * 選取 **[!UICONTROL Generate complement]**。

     ![](assets/use_case_abtesting_createrecipients_012.png)

   * 變更標籤以指定此母體既不包含A也不包含B，然後按一下&#x200B;**[!UICONTROL OK]**&#x200B;以關閉活動。

     ![](assets/use_case_abtesting_createrecipients_013.png)

您現在可以建立兩個傳遞範本。 [深入瞭解](a-b-testing-uc-delivery-templates.md))。
