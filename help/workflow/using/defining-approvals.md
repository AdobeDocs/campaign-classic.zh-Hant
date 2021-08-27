---
product: campaign
title: 定義核准
description: 通過批准，操作員可以做出管理工作流的決策或確認其繼續執行
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: 4d413d51-ae5d-4e5e-bfaf-4160a6075281
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 2%

---

# 定義核准 {#defining-approvals}

![](../../assets/common.svg)

透過核准，操作人員可以決定管理工作流程決策，或確認繼續執行。

訊息會傳送至一組運算子，而工作流程會等待回應再繼續。 工作流程不會停止，且可進行其他操作。 例如，可能有多個同時待批准。

核准可包含多個選項供運算子選擇。 但是，可以將選擇的數目限制為一個，以便將要執行的任務提交給操作員，例如執行定位。 然後，操作員可以在執行任務後做出響應（然後恢復進程）。 以下範例說明這些類型的核准：

![](assets/validation-1.png)

在操作中，需要批准的所有階段都基於相同的原則。

![](assets/validation-1-in-op.png)

您可以在此[section](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)中找到核准範例。

運算子可透過下列兩種方式之一回應：使用電子郵件訊息中連結的網頁或透過主控台進行驗證。

>[!NOTE]
>
>儲存回應後，即無法修改回應。

## 傳送電子郵件 {#sending-emails}

可以接收包含到網頁的連結的批准消息，通過該連結可以進行響應。 目標運算子若要接收核准電子郵件，運算子電子郵件地址必須完整。 若非如此，運算子必須使用主控台來回應

運算子管理在此[節](../../platform/using/access-management.md)中有詳細說明。

會持續傳送核准電子郵件。 預設的傳送範本為&#x200B;**[!UICONTROL notifyAssignee]**:它儲存在&#x200B;**[!UICONTROL Administration > Campaign management > Technical delivery templates]**&#x200B;資料夾中。 此情境可自訂，也建議製作復本並變更每個活動的範本。

透過此範本建立的傳送會儲存在&#x200B;**[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]**&#x200B;資料夾中。

## 透過主控台核准 {#approval-via-the-console}

在操作中，要核准的元素會顯示在促銷活動控制面板上。

對於技術工作流，可以從&#x200B;**[!UICONTROL Administration > Production > Objects created automatically > Pending approvals]**&#x200B;資料夾的樹結構訪問用戶可以批准的任務。

![](assets/validation-node.png)

## 群組 {#groups}

系統會將核准指派給一組運算子、單一運算子或一組透過篩選條件選取的運算子。

1. 對於最簡單的批准形式，操作員一作出響應，任務就會完成。 其他任何嘗試回應的運算子都會收到通知，通知已有人回應。
1. 有關多個批准，請參閱[多個批准](#multiple-approval)。

批准的運算元組應被指定為角色或職能，而不是指定的個人。 例如，「促銷活動預算」群組比「Harry&#39;s group」更好用。 我們建議在一個組中至少有兩個人可以批准任務。 這樣一來，如果缺一個，另一個就可以回應。

## 過期 {#expirations}

到期日是用於不同活動類型（尤其是核准）的特定轉變。 您可以使用過期時間來在指定時間後觸發動作，而不需要回應。 例如，它也可用於追蹤工作流程並指派核准給不同群組。

活動核准屬性中的第二個索引標籤可讓您定義一或多個到期日。 事實上，您可以定義多個過期類型。

![](assets/expiration.png)

若要新增過期時間，請按一下「**[!UICONTROL Add]**」。 會將轉變新增至所建立的每個過期時間。 您可以：

* 通過按一下清單中的單元格（或按F2）直接修改典型參數，
* 或按一下&#x200B;**[!UICONTROL Detail...]**&#x200B;按鈕來編輯運算式。

>[!NOTE]
>
>不必指定到期日的順序，因為到期日會依時間順序處理。

**[!UICONTROL Do not terminate the task]**&#x200B;選項會在延遲超出時使批准保持活動狀態。 此模式使得在保持批准活動狀態時可以管理提醒：運算子仍可回應。 此選項預設為停用，這表示任務在過期時即視為已完成，操作員可能不會再回應。

您可以建立四種過期類型：

* **任務開始後延遲**:有效期的計算方式為將指定的時間長度新增至啟動核准的日期。
* **指定日期之後的延遲**:有效期的計算方式為將時間長度新增至您指定的日期。
* **指定日期之前的延遲**:有效期的計算方式是從您指定的日期減去時間長度。
* **按指令碼計算的到期日**:有效期是使用JavaScript計算。

   下列範例會計算傳送開始之日24小時前的到期日（以&#x200B;**vars.deliveryId**&#x200B;識別）:

   ```
   var delivery = nms.delivery.get(vars.deliveryId)
   var expiration = delivery.scheduling.contactDate
   var oneDay = 1000*60*60*24
   expiration.setTime(expiration.getTime() - oneDay)
   return expiration
   ```

## 多重核准 {#multiple-approval}

多項核准是一種機制，可讓所有核准運算子回應。 會針對每個回應啟動轉變。

多重核准對投票或調查機制有用。 您可以計算答案，並在指定期間後借由增加截止時間來處理結果。

## 必要權限 {#required-rights}

群組中的運算子必須至少具備下列權利，才能回應核准請求：

* 工作流的寫入權限。
* 對包含要批准的任務的資料夾進行讀寫權限。

「工作流程執行」群組具有這些權限。 新增至此群組的運算子有權回應核准請求。
