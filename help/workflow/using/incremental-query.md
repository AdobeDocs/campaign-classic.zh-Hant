---
product: campaign
title: 增量查詢
description: 深入了解增量查詢工作流程活動
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: abc08232-1a92-41e8-90f1-02e0a673539b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 3%

---

# 增量查詢{#incremental-query}

增量查詢允許您根據條件定期選擇目標，同時排除已針對此條件定位的人員。

已定位的母體會依工作流程例項和活動儲存在記憶體中，亦即從相同範本啟動的兩個工作流程不會共用相同的記錄。 另一方面，基於同一工作流實例的相同增量查詢的兩個任務將使用相同的日誌。

查詢的定義方式與標準查詢的定義方式相同，但其執行是排程的。

**相關主題：**

* [使用案例：使用增量查詢更新每季清單](../../workflow/using/quarterly-list-update.md)
* [建立查詢](../../workflow/using/query.md#creating-a-query)

>[!CAUTION]
>
>如果增量查詢的結果在其其中一個執行期間等於&#x200B;**0**，則暫停工作流，直到查詢的下一個寫程式執行。 因此，在下列執行之前，不會處理遞增查詢之後的轉變和活動。

操作步驟：

1. 在&#x200B;**[!UICONTROL Scheduling & History]**&#x200B;標籤中，選取&#x200B;**[!UICONTROL Schedule execution]**&#x200B;選項。 建立任務後，該任務將保持活動狀態，並且只會在計畫為執行查詢指定的時間觸發。 但是，如果禁用該選項，則會立即執行&#x200B;**，並以一個go**&#x200B;執行查詢。
1. 按一下 **[!UICONTROL Change]** 按鈕。

   在&#x200B;**[!UICONTROL Schedule editing wizard]**&#x200B;視窗中，您可以設定頻率、事件週期和事件有效期的類型。

   ![](assets/s_user_segmentation_wizard_11.png)

1. 按一下&#x200B;**[!UICONTROL Finish]**&#x200B;以儲存排程。

   ![](assets/s_user_segmentation_wizard_valid.png)

1. **[!UICONTROL Scheduling & History]**&#x200B;標籤的下半部分可讓您選取要在歷史記錄中考慮的天數。

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

      已鎖定目標的收件者，最多可以從其鎖定目標當天起記錄天數。 如果此值為零，則不會從記錄中清除收件者。

   * **[!UICONTROL Keep history when starting]**

      此選項可讓您不在活動啟用時清除記錄檔。

   * **[!UICONTROL SQL table name]**

      此參數可讓您過載包含歷史記錄資料的預設SQL表。

## 輸出參數{#output-parameters}

* tableName
* 綱要
* recCount

這組三個值標識查詢所定位的母體。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是母體（通常為nms:recipient）的模式， **[!UICONTROL recCount]** 是表中的元素數。
