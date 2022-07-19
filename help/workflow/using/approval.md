---
product: campaign
title: 核准
description: 核准
feature: Workflows, Approvals
exl-id: 7ff5da71-ef82-48a2-a608-06a4ca188bb9
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# 核准{#approval}

![](../../assets/v7-only.svg)

安 **批准** 任務需要操作員的參與。 操作員被分配一個任務，並可以通過電子郵件、使用電子郵件中連結的網頁或通過控制台進行響應。

## 任務分配 {#task-assignment}

預設情況下，批准會分配給一組運算子。 此組表示角色，如「新聞稿內容組」或「新聞稿目標組」。 組中的每個操作員都可以回答，但只考慮第一個答復（在多次批准的情況下除外）。

如有必要，您可以將批准任務分配給單個運算子或由篩選器定義的一組運算子。

* 要選擇單個運算子，請選擇 **[!UICONTROL Operator]** 值 **[!UICONTROL Assignment type]** 欄位，並在 **[!UICONTROL Assignee]** 的子菜單。

   ![](assets/s_advuser_validation_box_assign.png)

   >[!CAUTION]
   >
   >只有所選操作員才有權批准該任務。

* 您可以定義用於篩選批准運算子的查詢。 要執行此操作，請選擇 **[!UICONTROL Filter]** 值 **[!UICONTROL Assignment type]** ，然後按一下 **[!UICONTROL Advanced parameters...]** 連結以定義篩選條件，如以下示例所示：

   ![](assets/s_advuser_validation_box_filter.png)

在單次審批的情況下，激活與操作員選擇相對應的轉換並完成任務：其他運算子無法答復。

在多個批准的情況下，啟用與每個運算子的選擇相對應的轉換。 任務在組的所有運算子都已答復或任務已過期時完成。

此活動不會阻止處理，並且工作流可以在等待答復時執行其他任務。

操作員可以從控制台批准分配給該操作員的任務。 具有管理員權限的操作員可以查看和刪除分配給任何操作員的任務，但無法答復它們。

修改活動的標題或消息正文不會影響當前任務，但是，另一方面，修改可能的選項會直接影響當前任務，而當前任務會自動繼承新的選項清單。

**批准** 類型任務可從 **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** 節點：操作員可以通過此視圖直接訪問批准表單。

![](assets/s_advuser_validation_from_console.png)

## 屬性 {#properties}

自定義變數可用於發送到審閱者的消息中。 它們可以插入到消息標題或正文中。

![](assets/edit_validation.png)

此 **[!UICONTROL Title]** 欄位包含消息的標題：這是已發送電子郵件的主題。 標題和消息正文是JavaScript模板，因此可以包含根據工作流上下文計算的值。

編輯器的下半部分允許您定義可能的答案清單。 每個答案都對應一個轉換。 名稱是內部標識符，標籤是將顯示在選項清單中的文本。

按一下 **[!UICONTROL Advanced parameters...]** 連結，以選擇要用於通知運算子的傳遞模板。 預設模板（內部名稱&#39;notifyAssignee&#39;）獲取標題和消息，並向用於應答的網頁添加一個連結。

此模板可修改為個性化消息佈局，但最好複製。 不能修改目標機制（外部檔案、目標映射），因為通知需要它才能正常運行。

審批示例如所示 [定義審批](defining-approvals.md)。

## 輸出參數 {#output-parameters}

* **[!UICONTROL response]**

   與響應相關的注釋

* **[!UICONTROL responseOperator]**

   響應的運算子的標識符。 此欄位是數值，但是 **[!UICONTROL String]** 的子菜單。
