---
product: campaign
title: 定義核准
description: 透過核准，操作員能夠決定管理工作流程的管理決策，或確認其繼續執行
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Approvals
exl-id: 4d413d51-ae5d-4e5e-bfaf-4160a6075281
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 3%

---

# 定義核准 {#defining-approvals}



透過核准，操作人員可以決定管理工作流程決策，或確認繼續執行。

訊息會傳送給一組運運算元，而工作流程會等待回應後再繼續。 工作流程不會停止，且可能會發生其他操作。 例如，可能有多個同時核准待處理。

核准可包含多個供運運算元選擇的選項。 但是，可以將選擇數量限製為一個，以便向操作員提交要執行的任務，例如執行定位。 執行工作之後，運運算元可以回應（接著處理繼續）。 下列範例說明這些核准型別：

![](assets/validation-1.png)

在作業中，所有需要核准的階段均以相同的原則為基礎。

![](assets/validation-1-in-op.png)

核准範例可在以下網址找到： [本節](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).

運運算元可透過下列兩種方式之一進行回應：使用電子郵件訊息中連結的網頁進行驗證，或是透過主控台進行驗證。

>[!NOTE]
>
>儲存回應後，即無法修改回應。

## 依據電子郵件的核准 {#sending-emails}

您可能會收到包含網頁連結的核准訊息，您可透過該連結做出回應。 目標操作員若要收到核准電子郵件，其電子郵件地址必須為完整。 如果不是這種情況，運運算元必須使用主控台進行回應

操作員管理在此詳細說明 [區段](../../platform/using/access-management.md).

核准電子郵件會持續傳送。 預設傳遞範本為 **[!UICONTROL notifyAssignee]**：此檔案會儲存在 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 資料夾。 此情境可自訂，也建議製作復本並變更每個活動的範本。

透過此範本建立的傳遞會儲存在 **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]** 資料夾。

## 透過主控台的核准 {#approval-via-the-console}

在作業中，要核准的元素會顯示在行銷活動控制面板上。

對於技術工作流程，使用者可以核准的任務可以從中的樹狀結構存取 **[!UICONTROL Administration > Production > Objects created automatically > Pending approvals]** 資料夾。

![](assets/validation-node.png)

## 群組 {#groups}

核准會指派給透過篩選條件選取的一組操作員、單一操作員或一組操作員。

1. 對於最簡單的核准形式，作業會在操作員回應後立即完成。 嘗試回應的其他操作員將會收到通知，指出有人已經完成此操作。
1. 如需多個核准，請參閱 [多重核准](#multiple-approval).

核准的運運算元群組應指定為角色或函式，而非已命名的個人。 例如，「行銷活動預算」群組比「Harry&#39;s group」更適合。 我們建議群組內至少要有兩位可核准任務的人。 如此一來，如果一個元件不存在，另一個元件可以回應。

## 到期 {#expirations}

有效期限是指用於不同活動型別中的特定轉變，尤其是在核准中。 您可以使用有效期在指定時間後觸發動作，而不需要回應。 例如，它也可用於追蹤工作流程並將核准指派給不同群組。

活動核准屬性中的第二個索引標籤可讓您定義一或多個有效期。 事實上，您可以定義多種到期型別。

![](assets/expiration.png)

若要新增到期日，請按一下 **[!UICONTROL Add]**. 每個已建立的到期時間都會新增一個轉變。 您可以：

* 按一下清單中的儲存格（或按F2），直接修改一般引數。
* 或按一下「 」以編輯運算式 **[!UICONTROL Detail...]** 按鈕。

>[!NOTE]
>
>不必指定過期順序，因為過期會依時間順序處理。

此 **[!UICONTROL Do not terminate the task]** 選項會在延遲逾時時啟用核准。 此模式可以在保持核准作用中時管理提醒：操作員仍然可以回應。 此選項預設為停用，這表示工作會在到期時被視為已完成，且運運算元可能不會再回應。

您可以建立四種型別的有效期：

* **任務開始後延遲**：計算到期日的方法為將指定的時間長度新增至啟用核准的日期。
* **在指定日期之後延遲**：有效期限是以新增時間長度至您指定的日期來計算。
* **在指定日期之前延遲**：有效期限的計算方式是從您指定的日期減去時間長度。
* **由指令碼計算的到期日**：有效期限是使用JavaScript計算。

  以下範例計算開始傳送日期前24小時的到期時間(識別方式 **vars.deliveryId**)：

  ```
  var delivery = nms.delivery.get(vars.deliveryId)
  var expiration = delivery.scheduling.contactDate
  var oneDay = 1000*60*60*24
  expiration.setTime(expiration.getTime() - oneDay)
  return expiration
  ```

## 多重核准 {#multiple-approval}

多重核准是一種可讓所有核准操作者回應的機制。 系統會為每個回應啟用轉變。

多重核准對於投票或調查機制很有用。 您可以計算答案，並透過新增截止日期在指定時段後處理結果。

## 必要權利 {#required-rights}

群組中的操作者必須至少具備以下許可權，才能回應核准請求：

* 工作流程的寫入許可權。
* 包含要核准之任務的檔案夾的讀寫許可權。

「工作流程執行」群組具有下列許可權。 新增至此群組的操作員有權回應核准請求。
