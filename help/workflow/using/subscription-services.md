---
title: 訂閱服務
seo-title: 訂閱服務
description: 訂閱服務
seo-description: null
page-status-flag: never-activated
uuid: f8c05f8a-0791-4294-8aa3-69b7325e4d43
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 940bec7e-e3f0-4251-b7fe-72bf188743a7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 訂閱服務{#subscription-services}

訂閱 **服務**-類型活動可讓您針對轉換中指定的人口建立或刪除資訊服務的訂閱。

若要設定活動，請編輯活動並輸入其標籤，然後選取要執行的動作（訂閱或取消訂閱）和相關的服務，如下列範例所示：

![](assets/edit_service_inscription.png)

1. 輸入活動的標籤。
1. 如果 **[!UICONTROL Generate an outbound transition]** 要在執行結束時建立過渡，請選擇此選項。

   一般而言，目標對資訊服務的訂閱會標示定位工作流程的結束，因此預設不會啟動選項。

1. 按一下 **[!UICONTROL Subscription]** 或 **[!UICONTROL Unsubscription]** 者，如果希望向選定資訊服務訂閱或取消訂閱指定的人口。
1. 選擇 **[!UICONTROL Send a confirmation message]** 以通知收件者已訂閱或取消訂閱服務。

   該消息的內容在與資訊服務相關的傳送模板中指定。 For more on this, refer to this [section](../../delivery/using/managing-subscriptions.md).

## 範例：將收件者清單訂閱至電子報 {#example--subscribe-a-list-of-recipients-to-a-newsletter}

在單一作業中，下列工作流程旨在列出符合電子報資格的收件者清單，以便讓住在巴黎的上班族訂閱。

若要這麼做，您也必須排除已訂閱的收件者。

>[!CAUTION]
>
>在手動將收件者訂閱至服務之前，請先確認這些收件者是否接受您的通訊。

![](assets/subscription_services_example.png)

1. 新增下列三個查詢：

   * 一個針對18到60歲的收件者。
   * 第二個目標對象是住在巴黎的收件者。
   * 第三個目標收件者目前未訂閱電子報。

1. 添加交叉點活動以交叉引用不同的結果。
1. 如果您喜歡，請插入清單更新，讓最新訂閱者清單保持最新狀態。
1. 插入訂閱服務活動，然後按兩下此活動以進行設定。
1. 輸入活動標籤並選擇 **[!UICONTROL Subscription]**。

   如果您願意，您可以勾選方塊，通知收件者電子報訂閱 **[!UICONTROL Send a confirmation message]** 情況。

1. 選擇電子報所在的資料夾，然後從出現的清單中選擇電子報。
1. 請保留 **[!UICONTROL Generate outbound transition]** 未勾選狀態，如此此活動將標示工作流程的結束，然後按一下 **[!UICONTROL Ok]**。

在工作流程執行期間，會將所有三個查詢對應的收件者新增至清單，並訂閱電子報。

您可以前往收件者的標籤，檢查訂閱 **[!UICONTROL Subscription]** 是否成功。

## 輸入參數 {#input-parameters}

* tableName
* 架構

每個傳入事件都必須指定由這些參數定義的目標。
