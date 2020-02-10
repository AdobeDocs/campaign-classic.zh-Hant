---
title: 核准
seo-title: 核准
description: 核准
seo-description: null
page-status-flag: never-activated
uuid: 49285790-5aa7-4e15-a657-42e4f78be518
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: a0090c78-5873-446d-8d5f-b0f94ff5d373
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 核准{#approval}

「核 **準** 」任務需要操作員的參與。 操作員會獲得指派的任務，並可以通過電子郵件、使用電子郵件消息中連結的網頁或通過控制台進行響應。

## 任務分配 {#task-assignment}

依預設，會將核准指派給一組運算子。 此群組代表角色，例如「電子報內容群組」或「電子報定位群組」。 群組中的每個運算元都可回答，但只會考慮第一個回覆（若發生多次核准則除外）。

如有必要，您可以將核准工作指派給單一運算元或由篩選器定義的運算元集。

* 要選擇單個運算子，請在字 **[!UICONTROL Operator]** 段中選擇 **[!UICONTROL Assignment type]** 值，然後在欄位的下拉清單中選擇相關運 **[!UICONTROL Assignee]** 算符。

   ![](assets/s_advuser_validation_box_assign.png)

   >[!CAUTION]
   >
   >只有所選的營運商才能獲得核准工作的授權。

* 您可以定義查詢來篩選批准運算子。 若要這麼做，請在欄 **[!UICONTROL Filter]** 位中選取值 **[!UICONTROL Assignment type]** ，然後按一下連結以 **[!UICONTROL Advanced parameters...]** 定義篩選條件，如下列範例所示：

   ![](assets/s_advuser_validation_box_filter.png)

在單次核准的情況下，激活與操作者選擇相對應的轉換並完成任務：其他運算子無法回覆。

在發生多個許可的情況下，啟用對應於每個運算子選擇的轉換。 當群組的所有運算子都已回覆，或任務已過期時，就會完成工作。

此活動不會封鎖處理，而工作流程可在等待回覆時執行其他工作。

操作員可以從控制台批准分配給該操作員的任務。 具有管理員權限的運算子可以檢視和刪除指派給任何運算子的工作，但無法回覆這些工作。

修改活動的標題或消息主體不會影響當前任務，但是，另一方面，修改可能的選擇直接影響當前任務，這些任務將自動繼承新的選擇清單。

**可從節點訪問** 「批准類型」任 **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** 務：營運商可透過此檢視直接存取核准表單。

![](assets/s_advuser_validation_from_console.png)

## 屬性 {#properties}

自訂變數可用於傳送給審核者的訊息中。 它們可以插入到消息標題或正文中。

![](assets/edit_validation.png)

此 **[!UICONTROL Title]** 欄位包含訊息的標題：這是所傳送電子郵件的主旨。 標題和訊息內文都是JavaScript範本，因此可包含根據工作流程內容計算的值。

編輯器的下半部分可讓您定義可能的答案清單。 每個答案都對應一個轉場。 名稱是內部識別碼，標籤是將顯示在選項清單中的文字。

按一下 **[!UICONTROL Advanced parameters...]** 連結，以選取要用於通知營運商的傳送範本。 預設範本（內部名稱&#39;notifyAssignee&#39;）會擷取標題和訊息，並新增用於回答的網頁連結。

您可以修改此範本以個人化訊息版面，但最好複製。 不得修改定位機制（外部檔案、定位對應），因為通知必須正確運作。

「定義審批」中顯示了 [審批實例](../../workflow/using/executing-a-workflow.md#defining-approvals)。

## 輸出參數 {#output-parameters}

* **[!UICONTROL response]**

   與回應相關的注釋

* **[!UICONTROL responseOperator]**

   回應的運算子識別碼。 此欄位是數值，但是欄 **[!UICONTROL String]** 位。

