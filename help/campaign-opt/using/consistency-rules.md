---
product: campaign
title: 一致性規則
description: 一致性規則
audience: campaign
content-type: reference
topic-tags: campaign-optimization
exl-id: 757328fa-4698-4f85-a5fa-074b5152ec45
source-git-commit: 5806690f764d2e5dfb5651597ff68b33bb399b44
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 3%

---

# 一致性規則{#consistency-rules}

![](../../assets/common.svg)

## 關於一致性規則 {#about-consistency-rules}

Adobe Campaign提供行銷活動類型中的一套規則，確保持續的通訊。 其目的是控制傳送給收件者的傳送，例如數量、性質、相關性等。

**容量** 例如，規則可避免傳送訊息時導致相關平台過載。 例如，包含下載連結的特殊優惠方案不得一次傳送給太多使用者，以避免伺服器飽和；電話促銷活動不得超過呼叫中心等的處理能力。 有關詳細資訊，請參閱 [控制容量](#controlling-capacity).

## 控制容量 {#controlling-capacity}

在傳送訊息之前，您需要確定貴組織具備處理傳送（實體基礎架構）的能力、傳送可產生的回應（傳入訊息），以及要向訂閱者進行的呼叫數（客服中心處理能力）。

若要這麼做，您需要建立 **[!UICONTROL Capacity]** 類型規則。

在下列範例中，我們為電話忠誠度促銷活動建立類型規則。 我們將訊息數量限制為每天20個，亦即呼叫中心的每日處理能力。 規則套用至兩個傳送後，我們就可以透過記錄檔監控耗用量。

要設計新的容量規則，請執行以下步驟：

1. 在 **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** 節點，按一下 **[!UICONTROL New]**.
1. 選取 **[!UICONTROL Capacity]** 規則類型。

   ![](assets/campaign_opt_create_capacity_01.png)

1. 在 **[!UICONTROL Capacity]** 頁簽，建立可用性行：在我們的範例中，這些是可進行呼叫的時段。 選擇24小時期間，然後輸入150作為初始數量，這意味著呼叫中心每天可以處理150個呼叫。

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >可用性行僅供參考。 如果您需要在達到容量限制時排除訊息，請參閱 [本節](#exclude-messages-when-capacity-limit-reached).

1. 將此規則與類型相關聯，然後將類型參考至您的傳送，以套用此容量規則。 如需詳細資訊，請參閱[本章節](applying-rules.md#applying-a-typology-to-a-delivery)。
1. 您可以監控規則的耗用量 **[!UICONTROL Consumptions]** 和 **[!UICONTROL Capacity]** 標籤。

   若在傳送中使用規則， **[!UICONTROL Consumed]** 和 **[!UICONTROL Remaining]** 欄會提供有關載入的資訊，如下所示：

   ![](assets/campaign_opt_create_capacity_03.png)

   如需詳細資訊，請參閱[本章節](#monitoring-consumption)。

## 定義最大負載 {#defining-the-maximum-load}

要定義最大載荷，需要定義可用性行。 若要這麼做，有兩個選項可供使用：您可以手動建立一個或多個可用性行(請參閱 [逐個添加可用性行](#adding-availability-lines-one-by-one))或建立可用範圍。 這些時段的頻率可以自動化(請參閱 [添加一組可用行](#add-a-set-of-availability-lines))。

### 逐個添加可用性行 {#adding-availability-lines-one-by-one}

若要建立可用性行，請按一下 **[!UICONTROL Add]** 按鈕並選取 **[!UICONTROL Add an availability line]**. 輸入可用期間和可用負載。

![](assets/campaign_opt_create_capacity_02.png)

視需要新增多行，以符合處理能力。

### 添加一組可用行 {#add-a-set-of-availability-lines}

要定義指定時間的可用期間，請按一下 **[!UICONTROL Add]** 按鈕並選取 **[!UICONTROL Add a set of availability lines]** 選項。 指定每個時段的持續時間和要建立的時段數。

若要自動建立頁面的頻率，請按一下 **[!UICONTROL Change]** 按鈕並定義時段排程。

![](assets/campaign_opt_create_capacity_07.png)

例如，我們將定義一個排程，以在上午9:00至下午5:00之間以每小時10次呼叫的速率建立所有工作日的可用期間。 若要這麼做，請套用下列步驟：

1. 選擇週期類型以及有效的日期和時間：

   ![](assets/campaign_opt_create_capacity_08.png)

1. 指定有效日期：

   ![](assets/campaign_opt_create_capacity_09.png)

1. 核准前，請先檢查排程：

   ![](assets/campaign_opt_create_capacity_10.png)

此 **[!UICONTROL Forecasting]** 工作流程會自動建立所有相符行。

![](assets/campaign_opt_create_capacity_12.png)

>[!NOTE]
>
>建議您透過檔案匯入建立可用性行。 此頁簽允許您查看和檢查衝減行。

## 達到容量限制時排除訊息 {#exclude-messages-when-capacity-limit-reached}

可用性行僅供參考。 若要排除多餘的訊息，請核取 **[!UICONTROL Exclude from the target messages in excess of capacity]** 選項。 這可防止超出容量。 對於與上例中相同的母體，消費和剩餘能力不得超過初始數量：

![](assets/campaign_opt_create_capacity_04.png)

要處理的郵件數將在定義的可用範圍內平均劃分。 這與呼叫中心特別相關，因為其每天的呼叫數上限是有限的。 若是電子郵件傳送， **[!UICONTROL Do not limit instantaneous delivery capacity]** 選項可讓您忽略此可用範圍，並同時傳送電子郵件。

![](assets/campaign_opt_create_capacity_05.png)

>[!NOTE]
>
>如果超載，則根據傳送屬性中定義的公式來選取儲存的訊息。

![](assets/campaign_opt_create_capacity_06.png)

## 監控耗用量 {#monitoring-consumption}

預設情況下，容量規則僅用於指示用途。 選取 **[!UICONTROL Exclude messages in excess of capacity from the target]** 選項，防止超出定義的負載。 在此情況下，會使用此類型規則，自動從傳送中排除多餘的訊息。

若要監控耗用量，請檢視 **[!UICONTROL Consumed]** 欄 **[!UICONTROL Capacity]** 標籤。

![](assets/campaign_opt_create_capacity_04.png)

要查看衝減行，請按一下 **[!UICONTROL Consumptions]** 標籤。
