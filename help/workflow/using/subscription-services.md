---
product: campaign
title: 訂閱服務
description: 瞭解有關訂閱服務工作流活動的詳細資訊
feature: Workflows, Targeting Activity, Subscription Services Activity
exl-id: 1b526d1c-4a33-45a1-98f4-dcb803c8d228
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 2%

---

# 訂閱服務{#subscription-services}

![](../../assets/v7-only.svg)

A **訂閱服務**-type活動允許您為轉換中指定的人口建立或刪除對資訊服務的訂閱。

要配置它，請編輯活動並輸入其標籤，然後選擇要執行的操作（訂閱或取消訂閱）和相關服務，如下例所示：

![](assets/edit_service_inscription.png)

1. 輸入活動的標籤。
1. 選擇 **[!UICONTROL Generate an outbound transition]** 在執行結束時建立過渡。

   通常，目標對資訊服務的訂閱會標籤目標工作流的結束，這就是預設情況下未激活選項的原因。

1. 按一下 **[!UICONTROL Subscription]** 或 **[!UICONTROL Unsubscription]** 如果要訂閱或取消訂閱選定資訊服務中指定的填充，請執行以下操作：
1. 選擇 **[!UICONTROL Send a confirmation message]** 通知收件人他們已訂閱或未訂閱服務。

   此消息的內容在與資訊服務相關的傳遞模板中指定。 如需詳細資訊，請參閱本[區段](../../delivery/using/managing-subscriptions.md)。

## 示例：訂閱新聞簡報的收件人清單 {#example--subscribe-a-list-of-recipients-to-a-newsletter}

在單個操作中，以下工作流旨在列出符合新聞稿條件的收件人名單，以居住在巴黎的工作人員為對象，以便他們訂閱。

為此，您還必須排除已訂閱的收件人。

>[!CAUTION]
>
>在手動訂閱服務收件人之前，請驗證這些收件人是否接受從您接收通信。

![](assets/subscription_services_example.png)

1. 添加以下三個查詢：

   * 一個針對18至60歲的受者。
   * 第二個目標是生活在巴黎的受助者。
   * 第三個目標收件人目前未訂閱該新聞稿。

1. 添加交叉點活動以交叉引用不同的結果。
1. 如果需要，請插入清單更新以使最新訂閱者清單保持最新。
1. 插入訂閱服務活動，然後按兩下該活動以配置它。
1. 輸入活動標籤並選擇 **[!UICONTROL Subscription]**。

   如果您願意，可通過檢查 **[!UICONTROL Send a confirmation message]** 框。

1. 選擇新聞稿所在的資料夾，然後從顯示的清單中選擇新聞稿。
1. 離開 **[!UICONTROL Generate outbound transition]** 選中，以便此活動將標籤工作流的結尾，然後按一下 **[!UICONTROL Ok]**。

在工作流執行期間，與所有三個查詢對應的收件人將添加到清單並訂閱新聞稿。

通過轉到 **[!UICONTROL Subscription]** 頁籤。

## 輸入參數 {#input-parameters}

* 表名
* 架構

每個入站事件都必須指定由這些參數定義的目標。
