---
product: campaign
title: 增量查詢
description: 瞭解有關增量查詢工作流活動的詳細資訊
feature: Workflows, Targeting Activity
exl-id: abc08232-1a92-41e8-90f1-02e0a673539b
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 3%

---

# 增量查詢{#incremental-query}

![](../../assets/common.svg)

增量查詢允許您根據條件定期選擇目標，同時排除已針對此條件的目標人員。

已目標的填充按工作流實例和活動儲存在記憶體中，即從同一模板啟動的兩個工作流不共用同一日誌。 另一方面，基於同一工作流實例的相同增量查詢的兩個任務將使用相同的日誌。

該查詢的定義方式與標準查詢的定義方式相同，但其執行是計畫的。

**相關主題：**

* [用例：使用增量查詢的季度清單更新](quarterly-list-update.md)
* [建立查詢](query.md#creating-a-query)

>[!CAUTION]
>
>如果增量查詢的結果等於 **0** 在其一個執行期間，該工作流被暫停，直到該查詢的下一次寫程式執行。 因此，在執行以下操作之前，不會處理增量查詢後的轉換和活動。

操作步驟：

1. 在 **[!UICONTROL Scheduling & History]** 頁籤 **[!UICONTROL Schedule execution]** 的雙曲餘切值。 建立任務後，該任務將保持活動狀態，並且僅在計畫指定的時間觸發執行查詢。 但是，如果禁用該選項，則會立即執行查詢 **一下子**。
1. 按一下 **[!UICONTROL Change]** 按鈕。

   在 **[!UICONTROL Schedule editing wizard]** 窗口中，您可以配置頻率、事件循環和事件有效期的類型。

   ![](assets/s_user_segmentation_wizard_11.png)

1. 按一下 **[!UICONTROL Finish]** 來修改標籤元素的屬性。

   ![](assets/s_user_segmentation_wizard_valid.png)

1. 下部 **[!UICONTROL Scheduling & History]** 頁籤允許您選擇歷史記錄中要考慮的天數。

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

      從目標日期起，可以記錄已定目標的收件人的最大天數。 如果此值為零，則不會從日誌中清除接收者。

   * **[!UICONTROL Keep history when starting]**

      此選項允許您在啟用活動時不清除日誌。

   * **[!UICONTROL SQL table name]**

      通過此參數，可以重載包含歷史記錄資料的預設SQL表。

## 輸出參數 {#output-parameters}

* 表名
* 架構
* 記錄計數

這三組值標識查詢所針對的填充。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是人口的模式（通常為nms:recipient）, **[!UICONTROL recCount]** 是表中的元素數。
