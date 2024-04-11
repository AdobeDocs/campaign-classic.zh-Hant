---
product: campaign
title: 傳送前先檢查
description: 訊息準備就緒後，在傳送之前執行所有檢查
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Deliverability
role: User
exl-id: 50d326b0-3c23-4dbf-9df6-d32b48e30f69
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 1%

---

# 傳送前執行所有檢查 {#perform-all-checks}

訊息就緒後，請確定內容在所有裝置上皆正確顯示，且未包含任何錯誤，例如錯誤的個人化或中斷的連結。

在傳送訊息之前，也請確定引數和設定與傳送一致。

## 為何驗證是關鍵 {#validation-is-key}

傳送傳遞前，您必須確保收件者會收到您真正想要傳送的訊息。 為此，您需要驗證訊息內容和傳遞引數。

此步驟可讓您在傳送到主要目標之前，偵測並修正可能的錯誤。

以下說明驗證傳送的步驟 [在本節中](steps-validating-the-delivery.md).

## 收件匣轉譯 {#inbox-and-email-rendering}

收件匣轉譯可讓您預覽主要電子郵件使用者端上的郵件、掃描內容和信譽，以及探索收件者閱讀郵件的方式。

**提示**：

* 您可以在不同的接收內容中檢視已傳送的訊息：網頁郵件、訊息服務、行動裝置等。

* 收件匣轉譯功能對於識別您的電子郵件行銷活動是否成功通過主要ISP （網際網路服務提供者）的篩選器和網頁郵件服務至關重要。 這類工具會將電子郵件的預檢復本傳送至測試收件匣的網路，以便您檢視這些服務中訊息的顯示或呈現方式。 它們也可能包括報表和程式碼更正選項，協助您快速識別並進行修正，以改善傳遞能力。

瞭解更多 [在本節中](inbox-rendering.md).

## 校樣訊息 {#proof-messages}

傳送校樣可讓您檢查選擇退出連結、映象頁面和任何其他連結、驗證訊息、驗證影像是否已顯示、偵測可能的錯誤等。 您可能也會想要檢查您在不同裝置上的設計和演算。

瞭解更多 [在本節中](steps-validating-the-delivery.md#sending-a-proof).

## 設定A/B測試傳送 {#a-b-testing-deliveries}

如果您有數個電子郵件傳送內容，可使用A/B測試來找出哪個版本對目標母體有最大影響。

**提示**：

* 傳送不同版本給部分收件者

* 選取成功率最高的專案，並將其傳送至目標的其餘部分

瞭解更多 [在本節中](get-started-a-b-testing.md).

## 請確定您的訊息已傳送 {#make-sure-your-message-is-delivered}

最後一步就是儘可能提高您的機會，並運用Adobe Campaign Classic的強大功能，確保您的訊息確實會傳送給相關收件者。

### 進行驗證程式

您可以定義涉及Adobe Campaign運運算元和群組的完整驗證程式，以驗證目標和訊息內容。 這將確保完全監控和控制行銷活動的各種流程：目標定位、內容、預算、摘錄和傳送證明。 根據使用者的許可權，使用者會收到通知、收到校樣並能夠驗證或拒絕訊息。 瞭解更多 [在本節中](../../campaign/using/marketing-campaign-approval.md).

### 使用波段

您可以逐步增加使用波段傳送的容量。 這可避免您的郵件被標示為垃圾郵件，或您想要限制每天的郵件數。 使用波段您可以將傳送劃分為幾個批次，而不是同時傳送大量訊息。 瞭解更多 [在本節中](steps-sending-the-delivery.md#sending-using-multiple-waves).

### 排定訊息的優先順序

您可以說明優先層級，設定傳送的傳送順序。 若要這麼做：

1. 編輯傳送屬性，並選取 **[!UICONTROL Delivery]** 標籤。

1. 從某個範圍定義傳遞的優先等級 **[!UICONTROL Very low]** 至 **[!UICONTROL Very high]**.

>[!NOTE]
>
>無法定義從傳送中傳送訊息的順序。

### 設定IP相關性

為了更妥善地控制傳出SMTP流量，您可以定義哪些特定的IP位址可用於每個相關性，以管理相關性。 這可讓您限制特定傳遞至機器或輸出地址的電子郵件數量。 例如，您可以對每個國家或子網域使用一個相似性。 接著，您可以為每個國家/地區建立一個型別，並將每個相似性連結至對應的型別。

您可以：

* 在serverConf.xml組態檔中定義IP相關性。 [了解更多](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* 針對每個IPAffinity元素，宣告可以使用的IP位址。 [了解更多](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* 在 [型別](../../campaign-opt/using/about-campaign-typologies.md) 選擇時，請使用 **[!UICONTROL Managing affinities with IP addresses]** 將傳遞連結到管理該相似性的傳遞伺服器(MTA)的欄位。 [了解更多](../../campaign-opt/using/applying-rules.md#control-outgoing-smtp-traffic)。

* 傳送電子郵件後，檢查標題以確認傳送來自的IP位址。 您的電子郵件管理員應協助您取得標題資訊。

* 對於SMS傳遞，請確定SMS通道具有僅限於以下範圍的專用相似性： **一** 應用程式伺服器容器。 [了解更多](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

>[!NOTE]
>
>這些步驟大多只能由專家使用者執行。

### 使用型別

您可以使用型別規則，根據特定條件排除部分目標。 這可確保在遵守公司通訊政策的同時，傳送最符合客戶需求及期望的訊息。 例如，您可以從電子報的目標篩選未成年的收件者。 瞭解更多 [在此範例中](../../campaign-opt/using/filtering-rules.md).

### 避免附件

附件仍然是惡意程式碼泛濫最常見的媒介之一，尤其是大量傳送時。 加入檔案的安全連結，而非附加檔案。 這可確保額外的安全層級，以防止無意中的再散佈，並大幅減少傳入電子郵件閘道因郵件大小或安全性原因而拒絕郵件的可能性。
