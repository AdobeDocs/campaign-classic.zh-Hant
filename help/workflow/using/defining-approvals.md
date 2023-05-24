---
product: campaign
title: 定義核准
description: 透過核准，操作員可以決定管理工作流程的決定或確認其繼續執行
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Approvals
exl-id: 4d413d51-ae5d-4e5e-bfaf-4160a6075281
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 2%

---

# 定義核准 {#defining-approvals}



透過核准，操作人員可以決定管理工作流程決策，或確認繼續執行。

訊息會傳送給一組運運算元，而工作流程會等待回應後再繼續。 工作流程不會停止，而且可能會發生其他操作。 例如，可能有多個同時核准擱置中。

核准可包含多個選項，以供運運算元選擇。 但是，可以將選擇數量限製為一個，以便向操作員提交要執行的任務，例如執行目標定位。 一旦執行工作之後，運運算元就可以回應（然後繼續處理）。 下列範例說明這些核准型別：

![](assets/validation-1.png)

在作業中，所有需要核准的階段均以相同的原則為基礎。

![](assets/validation-1-in-op.png)

核准範例可在以下網址找到： [本節](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).

操作員可透過以下兩種方式之一進行回應：使用電子郵件訊息中連結的網頁進行驗證，或透過主控台進行驗證。

>[!NOTE]
>
>儲存回應後，即無法加以修改。

## 依電子郵件的核准 {#sending-emails}

可能會收到包含網頁連結的核准訊息，您可以透過該連結做出回應。 目標操作員若要收到核准電子郵件，必須填寫操作員電子郵件地址。 如果不是這種情況，運運算元必須使用主控台進行回應

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

要核准的運運算元群組應指定為角色或功能，而不是已命名的個人。 例如，「行銷活動預算」群組比「Harry的群組」更適合。 我們建議一個群組中至少要有兩個可核准任務的人。 如此一來，如果其中一個不存在，另一個可以回應。

## 到期 {#expirations}

有效期限是指用於不同型別活動（尤其是核准）的特定轉變。 您可以使用到期日，在指定時間後觸發動作，而不需要回應。 例如，也可以用它來追蹤工作流程，並將核准指派給不同的群組。

活動核准屬性中的第二個索引標籤可讓您定義一或多個有效期。 事實上，您可以定義多個到期型別。

![](assets/expiration.png)

若要新增到期日，請按一下 **[!UICONTROL Add]**. 所建立的每個到期日都會新增一個轉變。 您可以：

* 按一下清單中的儲存格（或按F2），直接修改一般引數。
* 或按一下「 」以編輯運算式 **[!UICONTROL Detail...]** 按鈕。

>[!NOTE]
>
>不必指定到期的順序，因為會依時間順序處理。

此 **[!UICONTROL Do not terminate the task]** 選項會在延遲逾時時啟用核准。 此模式可讓您在保持核准作用中時管理提醒：操作員仍然可以回應。 此選項預設為停用，這表示任務在到期時被視為已完成，而且操作員可能不再回應。

您可以建立四種到期型別：

* **任務開始後延遲**：計算到期日的方法為將指定的時間長度新增至啟用核准的日期。
* **在指定日期之後延遲**：到期的計算方式為將時間長度新增至您指定的日期。
* **在指定日期之前延遲**：計算有效期限的方法是從您指定的日期減去時間長度。
* **由指令碼計算的到期時間**：到期日會使用JavaScript計算。

   以下範例會在開始傳送日期前24小時計算到期時間(識別方式 **vars.deliveryId**)：

   ```
   var delivery = nms.delivery.get(vars.deliveryId)
   var expiration = delivery.scheduling.contactDate
   var oneDay = 1000*60*60*24
   expiration.setTime(expiration.getTime() - oneDay)
   return expiration
   ```

## 多重核准 {#multiple-approval}

多重核准是一種可讓所有核准操作員回應的機制。 系統會針對每個回應啟用轉變。

多重核准對於投票或調查機制很有用。 您可以新增截止日期，計算回答並在指定時段後處理其結果。

## 必要許可權 {#required-rights}

群組中的操作員必須至少具有以下許可權，才能回應核准請求：

* 工作流程的寫入許可權。
* 包含要核准之任務的檔案夾的讀取和寫入許可權。

「工作流程執行」群組具有下列許可權。 新增至此群組的操作員有權回應核准請求。
