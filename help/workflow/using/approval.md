---
product: campaign
title: 核准
description: 核准
feature: Workflows, Approvals
exl-id: 7ff5da71-ef82-48a2-a608-06a4ca188bb9
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# 核准{#approval}



**核准**&#x200B;任務需要運運算元的參與。 操作員會獲得一項任務，且可以透過電子郵件、使用電子郵件訊息中連結的網頁或透過主控台進行回應。

## 任務指派 {#task-assignment}

依預設，核准會指派給一組操作者。 此群組代表一個角色，例如「新聞稿內容群組」或「新聞稿目標群組」。 群組中的每個運運算元都可以回答，但只考慮第一個回覆（多重核准的情況除外）。

如有必要，您可以將核准任務指派給單一運運算元，或由篩選器定義的一組運運算元。

* 若要選取單一運運算元，請在&#x200B;**[!UICONTROL Assignment type]**&#x200B;欄位中選取&#x200B;**[!UICONTROL Operator]**&#x200B;值，並在&#x200B;**[!UICONTROL Assignee]**&#x200B;欄位的下拉式清單中選取相關運運算元。

  ![](assets/s_advuser_validation_box_assign.png)

  >[!CAUTION]
  >
  >只有選取的運運算元才有權核准任務。

* 您可以定義用於篩選核准運運算元的查詢。 若要這麼做，請在&#x200B;**[!UICONTROL Assignment type]**&#x200B;欄位中選取&#x200B;**[!UICONTROL Filter]**&#x200B;值，然後按一下&#x200B;**[!UICONTROL Advanced parameters...]**&#x200B;連結以定義篩選條件，如下列範例所示：

  ![](assets/s_advuser_validation_box_filter.png)

在單一核准的事件中，對應於操作員選擇的轉變已啟用，任務已完成：其他操作員無法回覆。

如果有多個核准，則會啟用與每個運運算元選擇相對應的轉變。 當群組的所有操作者都已回覆或任務已過期時，任務即會完成。

此活動不會阻礙處理，且工作流程可在等待回覆時執行其他工作。

操作員可以從控制檯核准指派給該操作員的工作。 具有管理員許可權的操作員可以檢視和刪除指派給任何操作員的任務，但不能回覆這些任務。

修改活動的標題或訊息本文並不會影響目前的工作，但另一方面，修改可能的選擇會直接影響目前的工作，這會自動繼承新的選擇清單。

可從&#x200B;**[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]**&#x200B;節點存取&#x200B;**核准**&#x200B;型別工作：操作者可直接透過此檢視存取核准表單。

![](assets/s_advuser_validation_from_console.png)

## 屬性 {#properties}

可在傳送給稽核者的訊息中使用自訂變數。 它們可以插入訊息標題或內文中。

![](assets/edit_validation.png)

此&#x200B;**[!UICONTROL Title]**&#x200B;欄位包含訊息的標題：這是已傳送電子郵件訊息的主旨。 標題及訊息內文皆為JavaScript範本，因此可包含根據工作流程內容計算的值。

編輯器下半部分可讓您定義可能的答案清單。 每個答案都有一個對應的轉變。 名稱是內部識別碼，而標籤是將顯示在選項清單中的文字。

按一下&#x200B;**[!UICONTROL Advanced parameters...]**&#x200B;連結以選取要用來通知操作員的傳遞範本。 預設範本（內部名稱「notifyAssignee」）會採用標題和訊息，並將連結新增至用於回答的網頁。

此範本可以修改以個人化訊息版面，但最好製作副本。 不得修改目標定位機制（外部檔案、目標對應），因為通知需要它才能正確運作。

在[定義核准](defining-approvals.md)中顯示核准範例。

## 輸出引數 {#output-parameters}

* **[!UICONTROL response]**

  和回應相關的註解

* **[!UICONTROL responseOperator]**

  已回應的運運算元的識別碼。 此欄位是數值，但是&#x200B;**[!UICONTROL String]**&#x200B;欄位。
