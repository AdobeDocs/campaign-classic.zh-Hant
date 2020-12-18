---
solution: Campaign Classic
product: campaign
title: 增量查詢
description: 進一步瞭解「增量查詢」工作流程活動
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 3%

---


# 增量查詢{#incremental-query}

增量查詢可讓您根據標準定期選擇目標，同時排除已針對此標準定位的人員。

已定位的人口會依工作流程例項和活動儲存在記憶體中，亦即從相同範本開始的兩個工作流程不會共用相同的記錄檔。 另一方面，基於同一工作流實例的相同增量查詢的兩個任務將使用相同的日誌。

查詢的定義方式與標準查詢相同，但其執行是計畫的。

**相關主題：**

* [使用案例：使用增量查詢更新每季清單](../../workflow/using/quarterly-list-update.md)
* [建立查詢](../../workflow/using/query.md#creating-a-query)

>[!CAUTION]
>
>如果增量查詢的結果在其其中一個執行期間等於&#x200B;**0**，則暫停工作流，直到查詢的下次寫程式執行。 因此，在執行下列操作之前，不會處理增量查詢之後的轉換和活動。

操作步驟：

1. 在&#x200B;**[!UICONTROL Scheduling & History]**&#x200B;標籤中，選擇&#x200B;**[!UICONTROL Schedule execution]**&#x200B;選項。 建立任務後，該任務將保持活動狀態，並且僅在計畫為執行查詢指定的時間觸發。 但是，如果禁用該選項，則會立即執行查詢&#x200B;**，並在單行操作中執行查詢。**
1. 按一下 **[!UICONTROL Change]** 按鈕。

   在&#x200B;**[!UICONTROL Schedule editing wizard]**&#x200B;視窗中，您可以設定頻率、事件週期和事件有效期。

   ![](assets/s_user_segmentation_wizard_11.png)

1. 按一下&#x200B;**[!UICONTROL Finish]**&#x200B;保存計畫。

   ![](assets/s_user_segmentation_wizard_valid.png)

1. **[!UICONTROL Scheduling & History]**&#x200B;標籤的下半部分允許您選擇歷史記錄中要考慮的天數。

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

      已定位的收件者可以自定位當日起，記錄最多天數。 如果此值為零，則不會從日誌中清除收件者。

   * **[!UICONTROL Keep history when starting]**

      此選項可讓您在啟用活動時不清除記錄檔。

   * **[!UICONTROL SQL table name]**

      此參數可讓您過載包含歷史記錄資料的預設SQL表。

## 輸出參數{#output-parameters}

* tableName
* 架構
* recCount

這三個值集標識查詢所定位的人口。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是人口的模式（通常是nms:recipient）, **[!UICONTROL recCount]** 是表中的元素數。
