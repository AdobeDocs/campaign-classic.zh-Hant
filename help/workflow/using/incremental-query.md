---
title: 增量查詢
seo-title: 增量查詢
description: 增量查詢
seo-description: null
page-status-flag: never-activated
uuid: 24d322e8-172c-4faa-8a1f-59085b390a76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 31071cd2-7d97-4a4f-a6cc-5ac5b6178be5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 增量查詢{#incremental-query}

增量查詢可讓您根據標準定期選擇目標，同時排除已針對此標準定位的人員。

已定位的人口會依工作流程例項和活動儲存在記憶體中，亦即從相同範本開始的兩個工作流程不會共用相同的記錄。 另一方面，基於同一工作流實例的相同增量查詢的兩個任務將使用相同的日誌。

查詢的定義方式與標準查詢相同(請參 [閱建立查詢](../../workflow/using/query.md#creating-a-query))，但其執行是計畫的。

>[!CAUTION]
>
>如果增量查詢的結果在其中一個執行期 **間等於** 0，則暫停工作流，直到查詢的下次寫程式執行。 因此，在執行下列操作之前，不會處理增量查詢之後的轉換和活動。

操作步驟：

1. 在標籤 **[!UICONTROL Scheduling & History]** 中，選擇選 **[!UICONTROL Schedule execution]** 項。 建立任務後，該任務將保持活動狀態，並且僅在計畫為執行查詢指定的時間觸發。 但是，如果選項被禁用，則查詢會立即執行， **並且一次執行**。
1. Click the **[!UICONTROL Change]** button.

   在視窗 **[!UICONTROL Schedule editing wizard]** 中，您可以設定頻率、事件週期和事件有效期間的類型。

   ![](assets/s_user_segmentation_wizard_11.png)

1. 按一 **[!UICONTROL Finish]** 下以儲存排程。

   ![](assets/s_user_segmentation_wizard_valid.png)

1. 頁籤的下 **[!UICONTROL Scheduling & History]** 部分允許您選擇歷史記錄中要考慮的天數。

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

      已定位的收件者可以自定位當日起，記錄最多天數。 如果此值為零，則不會從日誌中清除收件者。

   * **[!UICONTROL Keep history when starting]**

      此選項可讓您在啟用活動時不清除記錄檔。

   * **[!UICONTROL SQL table name]**

      此參數可讓您過載包含歷史記錄資料的預設SQL表。

## 增量查詢示例：季度清單更新 {#example-of-an-incremental-query--quarterly-list-update}

在下例中，增量查詢用於自動更新收件者清單。 這些收件者會定位為季節性行銷活動的一部分。

由於這些活動是在每季開始時啟動，以提供相關的體育活動，因此每季都會更新這些清單。 不過，此促銷活動每9個月只能定位一次此處的收件者。 這可讓您省去收件者的資格頻率，並提供多年來不同季節的活動。

![](assets/incremental_query_example.png)

1. 將增量查詢以及清單更新活動新增至新工作流程。
1. 按照創 **[!UICONTROL Incremental query]** 建查詢中指定的方式配 [置活動的頁籤](../../workflow/using/query.md#creating-a-query)。
1. 選取標 **[!UICONTROL Scheduling & History]** 簽，然後指定270天的歷史記錄。 已定位的收件者將不再定位270天，即大約9個月。

   然後按一下 **[!UICONTROL Change...]** 按鈕。

1. 若要確保在每個季節開始前更新清單，請選取 **[!UICONTROL Monthly]**。
1. 在下一個畫面中，選擇3月、6月、9月和12月。 選擇當月20日，然後選擇您要啟動工作流程的時間。
1. 接下來，選擇查詢的有效期。 例如，如果您希望此活動永久活動，請選擇 **[!UICONTROL Permanent validity]**。

   ![](assets/incremental_query_example_2.png)

1. 批准增量查詢後，請按照清單更新中的說明配置清單更 [新活動](../../workflow/using/list-update.md)。

因此，工作流程將會在每季開始前自動啟動。 清單將會更新為新的合格收件者，以接收選件。

## 輸出參數 {#output-parameters}

* tableName
* 架構
* recCount

這三個值集標識查詢所定位的人口。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是人口的模式（通常是nms:recipient）, **[!UICONTROL recCount]** 是表中的元素數。
