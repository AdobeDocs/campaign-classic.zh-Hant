---
product: campaign
title: 核准
description: 核准
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 7ff5da71-ef82-48a2-a608-06a4ca188bb9
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# 核准{#approval}

![](../../assets/common.svg)

**Approval**&#x200B;任務需要運算子的參與。 運算子會獲派任務，並可使用電子郵件中連結的網頁或透過主控台以電子郵件回應。

## 任務分配 {#task-assignment}

依預設，會將核准指派給一組運算子。 此群組代表角色，例如「電子報內容群組」或「電子報目標群組」。 群組中的每個運算子都可以回答，但只考慮第一個回覆（若發生多次核准則除外）。

如有必要，您可以將核准任務指派給單一運算子，或由篩選器定義的一組運算子。

* 要選擇單個運算子，請在&#x200B;**[!UICONTROL Assignment type]**&#x200B;欄位中選擇&#x200B;**[!UICONTROL Operator]**&#x200B;值，並在&#x200B;**[!UICONTROL Assignee]**&#x200B;欄位的下拉清單中選擇相關運算子。

   ![](assets/s_advuser_validation_box_assign.png)

   >[!CAUTION]
   >
   >只有選定的操作員才有權批准該任務。

* 您可以定義一個查詢以篩選核准運算子。 要執行此操作，請在&#x200B;**[!UICONTROL Assignment type]**&#x200B;欄位中選取&#x200B;**[!UICONTROL Filter]**&#x200B;值，然後按一下&#x200B;**[!UICONTROL Advanced parameters...]**&#x200B;連結以定義篩選條件，如下列範例所示：

   ![](assets/s_advuser_validation_box_filter.png)

在單次批准的情況下，激活與操作者選擇相對應的轉變，並完成任務：其他操作員無法回復。

在出現多個核準時，會啟用與每個運算子的選擇相對應的轉變。 當組的所有操作員都作了答復，或者任務已過期時，任務即告完成。

此活動不會封鎖處理，而工作流程可在等待回覆時執行其他工作。

運算子可以從主控台核准指派給該運算子的任務。 具有管理員權限的操作員可以查看和刪除分配給任何操作員的任務，但無法回復這些任務。

修改活動的標題或消息正文不影響當前任務，但是，修改可能的選擇直接影響當前任務，這會自動繼承新的選擇清單。

**** 可從節點存取核准類型 **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** 任務：操作員可以通過此視圖直接訪問批准表單。

![](assets/s_advuser_validation_from_console.png)

## 屬性 {#properties}

可在傳送給審核者的訊息中使用自訂變數。 它們可插入訊息標題或內文。

![](assets/edit_validation.png)

此&#x200B;**[!UICONTROL Title]**&#x200B;欄位包含訊息的標題：這是已傳送電子郵件訊息的主旨。 標題和訊息內文均為JavaScript範本，因此可包含根據工作流程內容計算的值。

編輯器的下半部可讓您定義可能的答案清單。 每個答案都對應一個轉變。 名稱是內部標識符，標籤是將顯示在選項清單中的文本。

按一下&#x200B;**[!UICONTROL Advanced parameters...]**&#x200B;連結，以選取要用於通知運算子的傳送範本。 預設範本（內部名稱&#39;notifyAssignee&#39;）會擷取標題和訊息，並新增用於回應之網頁的連結。

此範本可修改為個人化訊息配置，但最好複製。 不得修改目標定位機制（外部檔案、目標對應），因為通知必須正確運作。

[Defining approvals](defining-approvals.md)中顯示了批准示例。

## 輸出參數 {#output-parameters}

* **[!UICONTROL response]**

   與回應相關的註解

* **[!UICONTROL responseOperator]**

   回應的運算子的識別碼。 此欄位是數值，但是&#x200B;**[!UICONTROL String]**&#x200B;欄位。
