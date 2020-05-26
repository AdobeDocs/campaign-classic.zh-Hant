---
title: 定義審批
description: 運算子可使用核准來決定工作流程，或確認其持續執行。
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 0%

---


# 定義審批 {#defining-approvals}

運算子可使用核准來決定工作流程，或確認其持續執行。

系統會傳送訊息給一組運算子，而工作流程會等待回應再繼續。 工作流不會停止，並且可以執行其他操作。 例如，可能有多個同時核准擱置中。

一個核准可以包含多個選項，讓運算子可以選擇。 但是，可以將選擇的數目限制為一個，以便將要執行的任務提交給操作員（如執行定位）。 然後，操作員可以在執行任務後做出響應（然後繼續處理）。 以下示例說明了這些類型的批准：

![](assets/validation-1.png)

在營運中，所有需要核准的階段都以相同的原則為基礎。

![](assets/validation-1-in-op.png)

您可在本節中找到核准 [範例](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)。

運算子可以以兩種方式回應： 驗證是否使用電子郵件訊息中連結的網頁，或透過主控台。

>[!NOTE]
>
>儲存回應後，就無法加以修改。

## 傳送電子郵件 {#sending-emails}

可以接收包含到可回應的網頁的連結的批准消息。 要讓目標營運商收到核准電子郵件，營運商的電子郵件地址必須完整。 如果不是這樣，運算子必須使用主控台來回應

操作員管理在本節中有詳 [細說明](../../platform/using/access-management.md)。

核准電子郵件會持續傳送。 預設的傳送範本為 **[!UICONTROL notifyAssignee]**: 它會儲存在資料 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 夾中。 您可自訂此藍本，也建議您製作復本並變更每個活動的範本。

透過此範本建立的傳送會儲存在資料 **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]** 夾中。

## 透過主控台核准 {#approval-via-the-console}

在操作中，要核准的元素會顯示在促銷活動控制面板上。

對於技術工作流，用戶可以從資料夾的樹結構訪問用戶可以批准的 **[!UICONTROL Administration > Production > Objects created automatically > Pending approvals]** 任務。

![](assets/validation-node.png)

## 群組 {#groups}

核准會指派給透過篩選條件選取的運算子群組、單一運算子或運算子集。

1. 對於最簡單的核准形式，只要營運商回應，任務就會立即完成。 任何其他嘗試回應的營運商都會收到有人已做過的通知。
1. 如需多項核准，請參閱多 [項核准](#multiple-approval)。

審批的運算元群組應指定為角色或函式，而非指定個人。 例如，「促銷活動預算」群組比「Harry&#39;s group」更好。 我們建議在一個群組中至少要有兩個人可以核准工作。 這樣，如果缺一個，另一個就可以回應。

## 到期日 {#expirations}

過期是用於不同活動類型（尤其是在批准中）的特定轉場。 過期可用來在沒有回應的指定時間段後觸發動作，或追蹤工作流程（例如，將核准指派給不同群組）。

活動核准屬性中的第二個標籤可讓您定義一或多個到期日。 事實上，您可以定義多種過期類型。

![](assets/expiration.png)

若要新增過期時間，請按一下 **[!UICONTROL Add]**。 轉換會新增至所建立的每個到期日。 您可以：

* 通過按一下清單中的單元格（或按F2）直接修改典型參數，
* 或者，按一下按鈕編輯運算 **[!UICONTROL Detail...]** 式。

>[!NOTE]
>
>在按時間順序處理到期日時，不需要指定其順序。

當延 **[!UICONTROL Do not terminate the task]** 遲超出時，此選項會使批准保持活動狀態。 此模式可讓您在啟用核準時管理提醒： 營運商仍可回應。 此選項預設為停用，這表示任務在到期時即視為完成，而運算子可能不再回應。

您可以建立四種到期類型：

* **任務開始後延遲**: 有效期的計算方式是將指定的時間長度新增至核准啟動的日期。
* **在指定日期後延遲**: 到期日的計算方式是將時間長度新增至您指定的日期。
* **在指定日期之前延遲**: 有效期的計算方式是從您指定的日期減去時間長度。
* **按指令碼計算的過期時間**: 有效期是使用JavaScript計算。

   下列範例會計算傳送開始之日24小時前的到期日(由 **vars.deliveryId識別**):

   ```
   var delivery = nms.delivery.get(vars.deliveryId)
   var expiration = delivery.scheduling.contactDate
   var oneDay = 1000*60*60*24
   expiration.setTime(expiration.getTime() - oneDay)
   return expiration
   ```

## 多重核准 {#multiple-approval}

多重核准是一種機制，可讓所有核准營運商回應。 會針對每個回應啟動轉場。

多重核准對投票或調查機制有用。 您可以計算答案，並在指定的時段後，透過新增期限來處理結果。

## 必要權限 {#required-rights}

群組中的營運商至少必須擁有下列權利，才能回應核准請求：

* 工作流程的寫入權限。
* 包含要批准任務的資料夾的讀寫權限。

「工作流執行」組具有這些權限。 新增至此群組的運算子有權回應核准請求。
