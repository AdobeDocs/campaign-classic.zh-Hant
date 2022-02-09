---
product: campaign
title: 定義核准
description: 通過審批，操作員可以做出管理工作流的決策或確認其繼續執行
feature: Approvals
exl-id: 4d413d51-ae5d-4e5e-bfaf-4160a6075281
source-git-commit: 3af4f259b80b3e03c81ee278b470ef6ffe3fe4d0
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 2%

---

# 定義核准 {#defining-approvals}

![](../../assets/common.svg)

透過核准，操作人員可以決定管理工作流程決策，或確認繼續執行。

消息將發送到一組運算子，而工作流在恢復之前等待響應。 工作流未停止，可以執行其他操作。 例如，可能有多個同時審批等待。

審批可以包含多個選項供操作員選擇。 但是，可以將選擇數限制為一個，以便將要執行的任務提交給操作員，例如執行目標。 然後，操作員可以在執行任務後作出響應（然後該過程繼續）。 以下示例說明了這些類型的審批：

![](assets/validation-1.png)

在操作中，所有需要批准的階段都基於同一原則。

![](assets/validation-1-in-op.png)

可在中找到批准示例 [此部分](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)。

操作員可以通過以下兩種方式之一進行響應：使用電子郵件中連結的網頁或通過控制台驗證。

>[!NOTE]
>
>保存響應後，不能修改響應。

## 通過電子郵件批准 {#sending-emails}

可以接收包含到網頁的連結的批准消息，通過該網頁可以進行響應。 要使目標操作員接收批准電子郵件，必須填寫操作員電子郵件地址。 如果不是這樣，操作員必須使用控制台響應

操作員管理在此中詳述 [節](../../platform/using/access-management.md)。

批准電子郵件會持續發送。 預設交貨模板為 **[!UICONTROL notifyAssignee]**:它保存在 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 的子菜單。 此方案可以自定義，還建議製作副本並更改每個活動的模板。

通過此模板建立的交貨儲存在 **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]** 的子菜單。

## 通過控制台審批 {#approval-via-the-console}

在操作中，要批准的元素將顯示在市場活動控制面板上。

對於技術工作流，可以從中的樹結構訪問用戶可以批准的任務 **[!UICONTROL Administration > Production > Objects created automatically > Pending approvals]** 的子菜單。

![](assets/validation-node.png)

## 組 {#groups}

將批准分配給通過過濾條件選擇的一組運算子、單個運算子或一組運算子。

1. 對於最簡單的批准形式，只要操作員響應，任務就會完成。 任何其他試圖響應的操作員都會收到有人已經響應的通知。
1. 有關多個批准，請參閱 [多個審批](#multiple-approval)。

審批的運算子組應指定為角色或函式，而不是指定個人。 例如，「活動預算」組比「Harry&#39;s組」更可取。 我們建議在一個組中至少有兩個可以批准任務的人。 這樣，如果一個人缺席，另一個人就能做出反應。

## 過期 {#expirations}

過期是在不同類型的活動中使用的特定轉換，特別是在批准中。 您可以使用過期來在給定時間後觸發操作，而不進行響應。 例如，它還可用於追蹤工作流，並將批准分配給其他組。

活動批准屬性中的第二個頁籤允許您定義一個或多個過期時間。 實際上，您可以定義多個到期類型。

![](assets/expiration.png)

要添加新過期，請按一下 **[!UICONTROL Add]**。 將轉換添加到所建立的每個過期。 您可以：

* 通過按一下清單中的單元格（或按F2）直接修改典型參數，
* 或通過按一下 **[!UICONTROL Detail...]** 按鈕

>[!NOTE]
>
>在按時間順序處理到期時，無需指定其順序。

的 **[!UICONTROL Do not terminate the task]** 選項在延遲超出時使批准處於活動狀態。 此模式允許在保留批准活動時管理提醒：運營商仍然可以響應。 預設情況下，此選項處於禁用狀態，這意味著任務在到期時被視為已完成，並且操作員可能不再響應。

您可以建立四種過期類型：

* **任務開始後延遲**:通過將指定的時間長度添加到激活審批的日期來計算到期時間。
* **指定日期後的延遲**:通過將時間長度添加到您指定的日期來計算到期時間。
* **在給定日期之前延遲**:通過從指定的日期中減去時間長度計算到期時間。
* **按指令碼計算到期時間**:到期時間是使用JavaScript計算的。

   以下示例計算在開始交貨之日(由 **vars.deliveryId**):

   ```
   var delivery = nms.delivery.get(vars.deliveryId)
   var expiration = delivery.scheduling.contactDate
   var oneDay = 1000*60*60*24
   expiration.setTime(expiration.getTime() - oneDay)
   return expiration
   ```

## 多個審批 {#multiple-approval}

多個批准是一種機制，使所有批准操作員都能做出響應。 為每個響應激活轉換。

多項批准對投票或調查機制有用。 您可以通過添加截止時間來計算答案並在指定時段後處理其結果。

## 所需權限 {#required-rights}

組中的操作員至少必須具有以下權限才能響應批准請求：

* 寫入工作流權限。
* 包含要審批的任務的資料夾的讀寫權限。

「工作流執行」組具有這些權限。 添加到此組的操作員有權響應批准請求。
