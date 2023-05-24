---
product: campaign
title: 傳送前先檢查
description: 訊息準備就緒後，請在傳送前執行所有檢查
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
exl-id: 50d326b0-3c23-4dbf-9df6-d32b48e30f69
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 4%

---

# 傳送前執行所有檢查 {#perform-all-checks}



訊息就緒後，請確定內容在所有裝置上皆正確顯示，且未包含任何錯誤，例如錯誤的個人化或中斷的連結。

在傳送訊息之前，也請確定引數和設定與傳送一致。

## 為何驗證是關鍵 {#validation-is-key}

在傳送傳遞之前，您必須確保收件者會收到您真正想要傳送的訊息。 為此，您需要驗證訊息內容和傳遞引數。

此步驟可讓您在傳送至主要目標之前，偵測並修正可能的錯誤。

以下說明驗證傳送的步驟 [在本節中](steps-validating-the-delivery.md).

## 收件匣轉譯 {#inbox-and-email-rendering}

收件匣轉譯可讓您預覽主要電子郵件使用者端上的郵件、掃描內容和信譽、探索收件者閱讀郵件的方式。

**提示**：

* 您可以在接收訊息的不同內容中檢視已傳送的訊息：網頁郵件、訊息服務、行動裝置等。

* 收件匣轉譯功能對於識別您的電子郵件行銷活動是否成功超越主要ISP （網際網路服務提供者）的篩選器和網頁郵件服務至關重要。 這類工具會將電子郵件的預檢復本傳送至測試收件匣的網路，以便您檢視訊息在這些服務中的顯示或呈現方式。 它們可能還包括報表和程式碼更正選項，可幫助您快速識別並進行修正以改善傳遞能力。

瞭解更多 [在本節中](inbox-rendering.md).

## 校樣訊息 {#proof-messages}

傳送校樣可讓您檢查選擇退出連結、映象頁面和任何其他連結、驗證訊息、驗證影像是否已顯示、偵測可能的錯誤等。 您可能也想要檢查您在不同裝置上的設計和演算。

瞭解更多 [在本節中](steps-validating-the-delivery.md#sending-a-proof).

## 設定A/B測試傳送 {#a-b-testing-deliveries}

如果您的電子郵件傳遞包含數個內容，您可以使用A/B測試來找出哪個版本對目標母體具有最大影響。

**提示**：

* 傳送不同版本給部分收件者

* 選取成功率最高的目標並傳送給目標的其餘部分

瞭解更多 [在本節中](get-started-a-b-testing.md).

## 確定您的訊息已傳送 {#make-sure-your-message-is-delivered}

最後，請儘可能提高您的機會，並運用Adobe Campaign Classic的強大功能，確保您的訊息確實會傳送給相關收件者。

### 進行驗證程式

您可以定義涉及Adobe Campaign運運算元和群組的完整驗證程式，以驗證目標和訊息內容。 這將確保完全監控和控制行銷活動的各種流程：目標定位、內容、預算、摘錄和傳送證明。 根據使用者的許可權，使用者會收到通知、收到校樣並能夠驗證或拒絕訊息。 瞭解更多 [在本節中](../../campaign/using/marketing-campaign-approval.md).

### 使用波段

您可以逐步增加使用波段傳送的數量。 這可避免您的訊息被標示為垃圾訊息，或當您想要限制每天的訊息數量時。 使用波段，您可以將傳送分成幾個批次，而非同時傳送大量訊息。 瞭解更多 [在本節中](steps-sending-the-delivery.md#sending-using-multiple-waves).

### 排定訊息的優先順序

您可以指定優先順序層級，設定傳送的傳送順序。 若要這麼做：

1. 編輯傳送屬性，並選取 **[!UICONTROL Delivery]** 標籤。

1. 從某個範圍定義傳遞的優先順序層級 **[!UICONTROL Very low]** 至 **[!UICONTROL Very high]**.

>[!NOTE]
>
>無法定義從傳遞中傳送訊息的順序。

### 設定IP相關性

為了更好地控制輸出SMTP流量，您可以定義哪些特定IP位址可用於每個相關性，以管理相關性。 這可讓您限制向電腦或輸出地址傳送特定內容的電子郵件數量。 例如，您可以對每個國家或子網域使用一個相似性。 然後，您可以為每個國家/地區建立一個型別，並將每個相似性連結至對應的型別。

您可以：

* 在serverConf.xml組態檔中定義IP相關性。 [了解更多](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* 對於每個IPAffinity元素，宣告可以使用的IP位址。 [了解更多](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* 在 [型別](../../campaign-opt/using/about-campaign-typologies.md) 選擇時，請使用 **[!UICONTROL Managing affinities with IP addresses]** 將傳遞連結至管理上述相似性的傳遞伺服器(MTA)的欄位。 [了解更多](../../campaign-opt/using/applying-rules.md#control-outgoing-smtp-traffic)。

* 傳送電子郵件後，檢查標題以確認傳送的來源IP位址。 您的電子郵件管理員應協助您取得標頭資訊。

* 若為SMS傳遞，請確定SMS頻道具有的專用相關性限製為 **一** 應用程式伺服器容器。 [了解更多](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

>[!NOTE]
>
>這些步驟大多只能由專家使用者執行。

### 使用型別

您可以使用型別規則，根據特定條件排除部分目標。 這樣可確保在遵守公司通訊原則的同時，傳送最符合客戶需求及期望的訊息。例如，您可以從電子報的目標篩選未成年的收件者。 瞭解更多 [在此範例中](../../campaign-opt/using/filtering-rules.md).

### 避免附件

附件仍然是惡意程式碼泛濫最常見的媒介之一，尤其是大量傳送時。 加入檔案的安全連結，而非附加檔案。 這可確保額外的安全層，以防止無意的再散佈，並大幅減少傳入電子郵件閘道因訊息大小或安全性原因而拒絕訊息的可能性。
