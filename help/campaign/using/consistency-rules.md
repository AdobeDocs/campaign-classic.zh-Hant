---
title: 一致性規則
seo-title: 一致性規則
description: 一致性規則
seo-description: null
page-status-flag: never-activated
uuid: 9b497460-ba42-4bc7-98e0-55c1b4be5e44
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 9bcb5dc1-8cb4-4781-a8cd-8d072ff28b1a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# 一致性規則{#consistency-rules}

## 關於一致性規則 {#about-consistency-rules}

Adobe Campaign透過促銷活動類型中包含的一組規則，確保溝通一致。 其目標是控制發送給收件者的遞送，如數量、性質、相關性等。

**例如** ，容量規則可以避免消息傳送導致相關平台過載。 例如，包含下載連結的特殊選件不得同時傳送給太多人，以避免伺服器飽和；電話促銷活動不得超過呼叫中心等的處理能力。 For more on this, refer to [Controlling capacity](#controlling-capacity).

## 控制容量 {#controlling-capacity}

在傳送訊息之前，您需要確定您的組織有能力處理傳送（實體基礎架構）、傳送可產生的回應（傳入訊息），以及要與訂閱者聯絡的呼叫數（呼叫中心處理能力）。

若要這麼做，您必須建立類 **[!UICONTROL Capacity]** 型規則。

在下列範例中，我們為電話忠誠度促銷活動建立分類規則。 我們將每天的訊息數限制為20個，即呼叫中心的每日處理能力。 在規則套用至兩個傳送後，我們就可以透過記錄監控消費。

要設計新的容量規則，請執行以下步驟：

1. 在節點 **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** 下，按一下 **[!UICONTROL New]**。
1. 選擇規 **[!UICONTROL Capacity]** 則類型。

   ![](assets/campaign_opt_create_capacity_01.png)

1. 在標籤 **[!UICONTROL Capacity]** 中，建立可用性行：在我們的範例中，這些是可進行呼叫的時段。 選擇24小時的時段，然後輸入150作為初始數量，這表示呼叫中心每天可處理150個呼叫。

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >可用性行僅供參考。 如果在達到容量限制時需要排除消息，請參 [閱本節](#exclude-messages-when-capacity-limit-reached)。

1. 將此規則與類型學關聯，然後將類型學引用到交付中以應用此能力規則。 如需詳細資訊，請參閱[本小節](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery)。
1. 您可以監控來自規則和標籤的 **[!UICONTROL Consumptions]** 消費 **[!UICONTROL Capacity]** 情況。

   在傳送中使用規則時， **[!UICONTROL Consumed]** 和 **[!UICONTROL Remaining]** 欄會提供載入資訊，如下所示：

   ![](assets/campaign_opt_create_capacity_03.png)

   如需詳細資訊，請參閱[本小節](#monitoring-consumption)。

## 定義最大載荷 {#defining-the-maximum-load}

要定義最大載荷，您需要定義可用性行。 若要這麼做，有兩個選項可供使用：您可以人工建立一個或多個可用性行(請參閱逐 [個添加可用性行](#adding-availability-lines-one-by-one))或建立可用性範圍。 這些時段的頻率可以自動化(請參 [閱添加一組可用行](#add-a-set-of-availability-lines))。

### 逐行添加可用行 {#adding-availability-lines-one-by-one}

要建立可用性行，請按一下該按 **[!UICONTROL Add]** 鈕並選擇 **[!UICONTROL Add an availability line]**。 輸入可用期間和可用負載。

![](assets/campaign_opt_create_capacity_02.png)

視需要新增多行以符合您的處理能力。

### 添加一組可用行 {#add-a-set-of-availability-lines}

要定義指定時間的可用期間，請按一下該 **[!UICONTROL Add]** 按鈕並選擇該 **[!UICONTROL Add a set of availability lines]** 選項。 指定每個時段的持續時間和要建立的時段數。

若要自動化頁面建立頻率，請按一下按 **[!UICONTROL Change]** 鈕並定義時段排程。

![](assets/campaign_opt_create_capacity_07.png)

例如，我們定義一個計畫，以在上午9點到下午5點之間每小時10次呼叫的速度為所有工作日建立可用期間。 若要這麼做，請套用下列步驟：

1. 選擇週期類型，以及其有效的天數和小時數：

   ![](assets/campaign_opt_create_capacity_08.png)

1. 指明有效日期：

   ![](assets/campaign_opt_create_capacity_09.png)

1. 核准前先勾選排程：

   ![](assets/campaign_opt_create_capacity_10.png)

工作流 **[!UICONTROL Forecasting]** 程會自動建立所有匹配行。

![](assets/campaign_opt_create_capacity_12.png)

>[!NOTE]
>
>建議您透過檔案匯入來建立可用性行。 此標籤允許您查看和檢查衝減行。

## 達到容量限制時排除消息 {#exclude-messages-when-capacity-limit-reached}

可用性行僅供參考。 要排除多餘消息，請選中該 **[!UICONTROL Exclude from the target messages in excess of capacity]** 選項。 這可防止超出容量。 對於與上例相同的人口，消耗和剩餘能力不得超過初始數量：

![](assets/campaign_opt_create_capacity_04.png)

要處理的消息數將在定義的可用範圍內平均劃分。 這對呼叫中心尤其重要，因為其每天的呼叫數上限有限。 在傳送電子郵件時，選 **[!UICONTROL Do not limit instantaneous delivery capacity]** 項可讓您忽略此可用範圍，並同時傳送電子郵件。

![](assets/campaign_opt_create_capacity_05.png)

>[!NOTE]
>
>在過載的情況下，根據傳送屬性中定義的公式選擇保存的消息。

![](assets/campaign_opt_create_capacity_06.png)

## 監控消費 {#monitoring-consumption}

預設情況下，容量規則僅用於指示用途。 選擇 **[!UICONTROL Exclude messages in excess of capacity from the target]** 選項以防止超出已定義的負載。 在此情況下，使用此排版規則，會自動從傳送中排除多餘的訊息。

若要監控耗用量，請檢視在排版規則 **[!UICONTROL Consumed]** 中標籤欄 **[!UICONTROL Capacity]** 中顯示的值。

![](assets/campaign_opt_create_capacity_04.png)

要查看衝減行，請按一下規 **[!UICONTROL Consumptions]** 則中的標籤。
