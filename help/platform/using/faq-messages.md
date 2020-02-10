---
title: 測試並傳送常見問答集
seo-title: 驗證、傳送及追蹤訊息
description: Campaign Classic常見問答集
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 994ec35e37a1c26e83a8dd2ae31f6594cadd4c45

---


# 驗證、傳送及追蹤訊息 {#validate-send-track}

## 測試與驗證 {#test-and-validate-before-sending}

了解在傳送訊息之前，如何先在 Adobe Campaign 中執行測試和驗證流程。

### What is the delivery analysis? {#what-is-the-delivery-analysis-}

傳遞分析是計算目標母體以及準備傳遞內容的階段。完成傳遞分析後便可傳遞內容。查閱記錄以確定所有事項都正確無誤。

[按一下這裡以了解更多資訊](../../delivery/using/steps-validating-the-delivery.md)。

### Why should I create proofs? {#why-should-i-create-proofs-}

Adobe強烈建議建立證明訊息，以在將您的傳送傳送至主要目標之前，先在核准群組上測試傳送。 那麼您就可以驗證訊息內容、個人化及傳遞參數。

[按一下這裡以了解更多資訊](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。您也可以觀看[此短片](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/managing-seed-and-proofs.html)。

### How to use seed addresses in Adobe Campaign? {#how-to-use-seed-addresses-in-adobe-campaign-}

種子地址用於鎖定不符合所定義的目標準則的收件者。這些收件者會新增至目標中：可直接於傳遞或行銷活動中匯入或建立這些收件者。如果是直效行銷郵件傳遞，則會在摘取期間新增收件者，並在輸出文件中進行混合。

這樣將提供下列好處：

* 使用收件者用戶檔案中的資料隨機替代欄位：例如，您可以在種子地址區段中僅輸入電子郵件地址。
* 工作流程中運用了資料管理功能時，可在種子地址層級輸入傳送中處理的其他資料，以強制執行此值：可作為隨機值替代的另一做法。

[按一下這裡以深入了解種子地址](../../delivery/using/about-seed-addresses.md)。

### How can I set up an approval process before sending messages? {#how-can-i-set-up-an-approval-process-before-sending-messages-}

若要檢測訊息設定中可能出現的錯誤，Adobe 強烈建議您設定傳遞驗證階段。要經常性地透過傳送驗證訊息測試收件者，確保核准內容。每次進行變更時都必須傳送驗證訊息，以核准內容。

[按一下這裡以了解更多資訊](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

### What is a typology rule? {#what-is-a-typology-rule-}

為了避免行銷活動之間發生衝突，Adobe Campaign 可以套用特定限制規則來測試各種組合。這樣可確保在遵守公司通訊原則的同時，傳送最符合客戶需求及期望的訊息。

[按一下這裡以了解更多資訊](../../campaign/using/about-campaign-typologies.md)。

## 傳送您的訊息。{#send-your-messages}

了解如何使用 Adobe Campaign 於各個通路中傳送訊息。

### How can I send emails in waves? {#how-can-i-send-emails-in-waves-}

在將內容傳送給較大母體之前，您可以[設定批次](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)以將訊息劃分為幾個批次，以平衡其負載。

### Which are the key steps to create an email in Campaign? {#which-are-the-key-steps-to-create-an-email-in-campaign-}

建立並驗證電子郵件之後，您就可以進行傳送。您可以決定立即將電子郵件傳送至主要目標，或排程稍後的傳送。 如有需要，您也可以先行估計目標母體。

[按一下這裡以了解更多資訊](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

### How to schedule a delivery? {#how-to-schedule-a-delivery-}

為了排程傳遞，管理銷售壓力以及避免過度行銷，您可以推延郵件的傳遞。

[按一下這裡以了解更多資訊](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending)。

### Can I add an attachment to emails? {#can-i-add-an-attachment-to-emails-}

有了Campaign Classic，您可以在電子郵件中新增個人化附件。

[按一下這裡以進一步瞭解電子郵件附件](../../delivery/using/attaching-files.md)。

## 追蹤訊息並評估其帶來的影響 {#track-your-messages-and-measure-their-impact}

傳送訊息之後，透過 Adobe Campaign 了解如何追蹤和度量產生的影響。

### How can I configure tracked links in an email delivery? {#how-can-i-configure-tracked-links-in-an-email-delivery-}

對於每次傳遞，您都可以追蹤訊息是否收到，以及郵件內容中的連結是否被點擊。這樣，您可以在目標傳遞行動實施後，追蹤收件者的行為。

對於訊息的每個 URL，您可以選擇是否啟動追蹤、變更連結標籤、根據報表需求對連結分類等。

[按一下這裡以深入了解](../../delivery/using/about-message-tracking.md)如何透過 Campaign Classic 追蹤訊息。

### Where can I access delivery and tracking logs? {#where-can-i-access-delivery-and-tracking-logs-}

[透過本頁面](../../delivery/using/monitoring-a-delivery.md)了解如何追蹤您發送的郵件，了解收件者的行為。

### Where can I get delivery reports? {#where-can-i-get-delivery-reports-}

Adobe Campaign 隨附一組報表，用於監視傳遞信件並追蹤您的訊息。

[按一下這裡以深入了解內建報表](../../reporting/using/reports-on-deliveries.md#delivery-reports)。

### How does Adobe Campaign qualify and manage quarantine addresses? {#how-does-adobe-campaign-qualify-and-manage-quarantine-addresses-}

Adobe Campaign 管理隔離地址的清單。在執行傳遞分析時，預設情況下將不會向被隔離的收件者的電郵地址傳送內容。例如信箱容量已滿或地址不存在時，您可以隔離電子郵件地址。

[按一下這裡以深入了解隔離管理](../../delivery/using/understanding-quarantine-management.md)。
