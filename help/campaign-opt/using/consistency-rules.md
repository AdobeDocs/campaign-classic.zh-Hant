---
product: campaign
title: 一致性規則
description: 一致性規則
feature: Typology Rules
exl-id: 757328fa-4698-4f85-a5fa-074b5152ec45
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 3%

---

# 一致性規則{#consistency-rules}

![](../../assets/common.svg)

## 關於一致性規則 {#about-consistency-rules}

Adobe Campaign通過競選類型中的一套規則，保證溝通一致。 其目的是控制送給接收者的遞送，如數量、性質、相關性等。

**容量** 例如，規則可以避免消息傳遞所涉及的平台過載。 例如，不能同時將包含下載連結的特殊優惠發送給太多人，以免伺服器飽和；電話活動不得超過呼叫中心的處理能力等。 有關此內容的詳細資訊，請參閱 [控制容量](#controlling-capacity)。

## 控制容量 {#controlling-capacity}

在傳遞消息之前，您需要確保您的組織具有處理傳遞（物理基礎架構）、傳遞可能生成的響應（入站消息）以及要與訂閱者聯繫的呼叫數（呼叫中心處理能力）的能力。

為此，您需要建立 **[!UICONTROL Capacity]** 分類規則。

在以下示例中，我們為電話忠誠促銷活動建立了類型規則。 我們將消息數限制為每天20條，即呼叫中心的日處理能力。 一旦該規則應用於兩個交貨，我們就可以通過日誌來監控消耗量。

要設計新的容量規則，請執行以下步驟：

1. 在 **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** 節點，按一下 **[!UICONTROL New]**。
1. 選擇 **[!UICONTROL Capacity]** 規則類型。

   ![](assets/campaign_opt_create_capacity_01.png)

1. 在 **[!UICONTROL Capacity]** 頁籤，建立可用性行：在我們的示例中，這些是可進行調用的時間段。 選擇一個24小時的時段，並輸入初始數量150，這意味著呼叫中心每天可以處理150個呼叫。

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >可用性行僅供參考。 如果需要在達到容量限制時排除消息，請參閱 [此部分](#exclude-messages-when-capacity-limit-reached)。

1. 將此規則與類型關聯，然後將類型引用到交貨中以應用此容量規則。 如需詳細資訊，請參閱[本章節](applying-rules.md#applying-a-typology-to-a-delivery)。
1. 您可以監視規則中的消耗量 **[!UICONTROL Consumptions]** 和 **[!UICONTROL Capacity]** 頁籤。

   在交貨中使用規則時， **[!UICONTROL Consumed]** 和 **[!UICONTROL Remaining]** 列提供有關負載的資訊，如下所示：

   ![](assets/campaign_opt_create_capacity_03.png)

   如需詳細資訊，請參閱[本章節](#monitoring-consumption)。

## 定義最大載荷 {#defining-the-maximum-load}

要定義最大負荷，需要定義可用性行。 為此，有兩個選項可用：您可以手動建立一個或多個可用性行(請參閱 [逐行添加可用性行](#adding-availability-lines-one-by-one))或建立可用性範圍。 這些時段的頻率可以自動執行(請參閱 [添加一組可用性行](#add-a-set-of-availability-lines))。

### 逐行添加可用性行 {#adding-availability-lines-one-by-one}

要建立可用性行，請按一下 **[!UICONTROL Add]** 按鈕 **[!UICONTROL Add an availability line]**。 輸入可用期和可用負荷。

![](assets/campaign_opt_create_capacity_02.png)

根據需要添加多行以適應您的處理能力。

### 添加一組可用性行 {#add-a-set-of-availability-lines}

要定義給定時間的可用性期間，請按一下 **[!UICONTROL Add]** 按鈕 **[!UICONTROL Add a set of availability lines]** 的雙曲餘切值。 指明每個時段的持續時間和要建立的時段數。

要自動化頁面建立頻率，請按一下 **[!UICONTROL Change]** 按鈕並定義時段計畫。

![](assets/campaign_opt_create_capacity_07.png)

例如，讓我們定義一個計畫，以每小時10次呼叫的速率在上午9點到下午5點之間為所有工作日建立可用性期間。 若要這麼做，請套用下列步驟：

1. 選擇週期類型及其有效的日期和時間：

   ![](assets/campaign_opt_create_capacity_08.png)

1. 指明有效日期：

   ![](assets/campaign_opt_create_capacity_09.png)

1. 在批准前檢查計畫：

   ![](assets/campaign_opt_create_capacity_10.png)

的 **[!UICONTROL Forecasting]** 工作流自動建立所有匹配行。

![](assets/campaign_opt_create_capacity_12.png)

>[!NOTE]
>
>我們建議通過檔案導入建立可用性行。 此標籤允許您查看和檢查衝減行。

## 達到容量限制時排除消息 {#exclude-messages-when-capacity-limit-reached}

可用性行僅供參考。 要排除多餘的消息，請檢查 **[!UICONTROL Exclude from the target messages in excess of capacity]** 的雙曲餘切值。 這防止超出容量。 對於與上例中相同的人口，消耗量和剩餘能力不得超過初始數量：

![](assets/campaign_opt_create_capacity_04.png)

要處理的消息數將在定義的可用性範圍內平均細分。 這對呼叫中心尤其重要，因為其每天的最大呼叫數有限。 如果是電子郵件遞送， **[!UICONTROL Do not limit instantaneous delivery capacity]** 選項，您可以忽略此可用範圍並同時發送電子郵件。

![](assets/campaign_opt_create_capacity_05.png)

>[!NOTE]
>
>在超載的情況下，根據在傳遞屬性中定義的公式來選擇保存的消息。

![](assets/campaign_opt_create_capacity_06.png)

## 監視消耗 {#monitoring-consumption}

預設情況下，能力規則僅用於指示目的。 選擇 **[!UICONTROL Exclude messages in excess of capacity from the target]** 選項，以防止超出定義的負載。 在這種情況下，使用此類型規則將自動從交貨中排除多餘的消息。

要監視消費，請查看在 **[!UICONTROL Consumed]** 列 **[!UICONTROL Capacity]** 的子菜單。

![](assets/campaign_opt_create_capacity_04.png)

要查看衝減行，請按一下 **[!UICONTROL Consumptions]** 的子菜單。
