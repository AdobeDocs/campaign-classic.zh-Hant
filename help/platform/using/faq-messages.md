---
product: campaign
title: 測試並傳送常見問題集
description: Campaign Classic 常見問題集
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 7fc24ef2-b021-440b-b1f2-8c77e2425328
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 98%

---

# 驗證、傳送及追蹤訊息 {#validate-send-track}



## 測試與驗證 {#test-and-validate-before-sending}

瞭解在傳送訊息之前，如何先在 Adobe Campaign 中執行測試和驗證流程。

### 什麼是傳遞分析？ {#what-is-the-delivery-analysis-}

傳遞分析是計算目標母體以及準備傳遞內容的階段。完成傳遞分析後便可傳遞內容。查閱記錄以確定所有事項都正確無誤。

[按一下這裡以瞭解更多](../../delivery/using/steps-validating-the-delivery.md)。

### 為什麼要建立驗證？ {#why-should-i-create-proofs-}

Adobe 強烈建議您先建立驗證訊息，並在正式發送前先行在核准組測試傳送內容。那麼您就可以驗證訊息內容、個人化及傳遞參數。

[按一下這裡以瞭解更多](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

### 如何在 Adobe Campaign 使用種子地址？ {#how-to-use-seed-addresses-in-adobe-campaign-}

種子地址用於鎖定不符合所定義的目標準則的收件者。這些收件者會新增至目標中：可直接於傳遞或行銷活動中匯入或建立這些收件者。如果是直接行銷郵件傳遞，則會在提取期間新增收件者，並在輸出文件中進行混合。

這樣將提供下列好處：

* 使用收件者用戶檔案中的資料隨機替代欄位：例如，您可以在種子地址區段中僅輸入電子郵件地址。
* 工作流程中運用了資料管理功能時，可在種子地址層級輸入傳送中處理的其他資料，以強制執行此值：可作為隨機值替代的另一做法。

[按一下這裡以深入瞭解種子地址](../../delivery/using/about-seed-addresses.md)。

### 如何設定傳送訊息前的核准過程？ {#how-can-i-set-up-an-approval-process-before-sending-messages-}

若要檢測訊息設定中可能出現的錯誤，Adobe 強烈建議您配置傳遞驗證階段。要經常性地透過傳送驗證訊息測試收件者，確保核准內容。每次進行變更時都必須傳送驗證訊息，以核准內容。

[按一下這裡以瞭解更多](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

### 什麼是類型規則？ {#what-is-a-typology-rule-}

為了避免行銷活動之間發生衝突，Adobe Campaign 可以套用特定限制規則來測試各種組合。這樣可確保在遵守公司通訊原則的同時，傳送最符合客戶需求及期望的訊息。

[按一下這裡以瞭解更多](../../campaign-opt/using/about-campaign-typologies.md)。

## 傳送您的訊息。 {#send-your-messages}

瞭解如何使用 Adobe Campaign 於各個頻道中傳送訊息。

### 如何分批次傳送電子郵件？ {#how-can-i-send-emails-in-waves-}

在將內容傳送給較大母體之前，您可以[配置批次](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)以將訊息劃分為幾個批次，以平衡其負載。

### 在 Campaign 建立電子郵件有哪些重要步驟？ {#which-are-the-key-steps-to-create-an-email-in-campaign-}

建立並驗證電子郵件之後，您就可以進行傳送。您可以決定立即向主要目標傳送電子郵件，還是在以後排程傳遞。如有需要，您也可以先行估計目標母體。

[按一下這裡以瞭解更多](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

### 如何排程傳遞？ {#how-to-schedule-a-delivery-}

為了排程傳遞，管理銷售壓力以及避免過度行銷，您可以推延郵件的傳遞。

[按一下這裡以瞭解更多](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending)。

### 我可以將附件新增至電子郵件嗎？ {#can-i-add-an-attachment-to-emails-}

使用 Campaign Classic，您可以在電子郵件加入個人化的附件。

[按一下這裡以深入暸解電子郵件附件](../../delivery/using/attaching-files.md)。

## 追蹤訊息並評估其帶來的影響 {#track-your-messages-and-measure-their-impact}

傳送訊息之後，透過 Adobe Campaign 瞭解如何追蹤和度量產生的影響。

### 如何在電子郵件傳遞中配置追蹤連結？ {#how-can-i-configure-tracked-links-in-an-email-delivery-}

對於每次傳遞，您都可以追蹤訊息是否收到，以及郵件內容中的連結是否被啟用。這樣，您可以在目標傳遞操作實施後，追蹤收件者的行為。

對於訊息的每個 URL，您可以選擇是否啟動追蹤、變更連結標籤、根據報告需求對連結分類等。

[按一下這裡以瞭解更多](../../delivery/using/about-message-tracking.md)如何透過 Campaign Classic 追蹤訊息。

### 我可以在哪裡存取傳遞內容和追蹤記錄？ {#where-can-i-access-delivery-and-tracking-logs-}

了解如何追蹤您的傳遞內容並了解收件者的行為 [從本頁面](../../delivery/using/delivery-dashboard.md).

### 我在哪裡可以取得傳遞報告？ {#where-can-i-get-delivery-reports-}

Adobe Campaign 隨附一組報告，用於監視傳遞信件並追蹤您的訊息。

[按一下這裡瞭解更多內建報告](../../reporting/using/delivery-reports.md)。

### Adobe Campaign 如何選定和管理隔離地址？ {#how-does-adobe-campaign-qualify-and-manage-quarantine-addresses-}

Adobe Campaign 管理隔離地址清單。在執行傳遞分析時，預設情況下將不會向被隔離的收件者的電郵地址傳送內容。例如信箱容量已滿或地址不存在時，您可以隔離電子郵件地址。

[按一下這裡瞭解更多隔離管理](../../delivery/using/understanding-quarantine-management.md)。
