---
product: campaign
title: 傳送前先檢查
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: 50d326b0-3c23-4dbf-9df6-d32b48e30f69
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 4%

---

# 在發送前執行所有檢查 {#perform-all-checks}

![](../../assets/common.svg)

在您的訊息準備就緒後，請確定其內容在所有裝置上皆正確顯示，且不會包含任何錯誤，例如錯誤的個人化或中斷的連結。

傳送訊息前，也請確定參數和設定與傳送一致。

## 驗證為何是關鍵 {#validation-is-key}

在傳送傳遞前，您必須確保收件者會收到您確實想要傳送的訊息。 若要這麼做，您需要驗證訊息內容和傳送參數。

此步驟可讓您在傳送至主要目標之前，偵測可能的錯誤並加以修正。

會顯示驗證傳送的步驟 [在本節](steps-validating-the-delivery.md).

## 收件匣轉譯 {#inbox-and-email-rendering}

收件匣轉譯可讓您在主要電子郵件用戶端上預覽訊息、掃描內容和信譽、探索收件者閱讀訊息的方式。

**提示**:

* 您可以在可接收郵件的不同內容中檢視已傳送的郵件：網站郵件、訊息服務、行動等。

* 收件匣轉譯功能對於識別您的電子郵件促銷活動是否成功超過主要ISP（網際網路服務提供者）和網路郵件服務的篩選器至關重要。 這類工具會將電子郵件的飛行前副本傳送至測試收件匣網路，讓您了解訊息在這些服務中的顯示或呈現方式。 它們也可能包含報表和程式碼修正選項，可協助您快速識別並進行修正，以改善傳遞能力。

深入了解 [在本節](inbox-rendering.md).

## 校樣訊息 {#proof-messages}

傳送校樣可讓您檢查選擇退出連結、鏡像頁面和任何其他連結、驗證訊息、確認影像已顯示、偵測可能的錯誤等。 您也可能想要檢查您的設計和在不同裝置上呈現。

深入了解 [在本節](steps-validating-the-delivery.md#sending-a-proof).

## 設定A/B測試傳送 {#a-b-testing-deliveries}

如果您有數個電子郵件傳送內容，您可以使用A/B測試來找出哪個版本對目標母體影響最大。

**提示**:

* 將不同的版本傳送給您的部分收件者

* 選取成功率最高的，並將其傳送至目標的其餘部分

深入了解 [在本節](get-started-a-b-testing.md).

## 確認訊息已傳送 {#make-sure-your-message-is-delivered}

最後一步，請盡可能提高您的機會並運用Adobe Campaign Classic的強大功能，確保您的訊息確實會傳送給相關的收件者。

### 執行驗證程式

您可以定義完整驗證程式，涉及Adobe Campaign運算子和群組，以驗證目標和訊息內容。 這將確保全面監控及控制促銷活動的各種程式：鎖定目標、內容、預算、擷取和傳送校樣。 系統會根據使用者的權限通知使用者、接收校樣，並能驗證或拒絕訊息。 深入了解 [在本節](../../campaign/using/marketing-campaign-approval.md).

### 使用波段

您可以使用波數逐步增加傳送的音量。 這樣可避免您的郵件被標示為垃圾訊息，或您想要限制每天的郵件數量。 使用波段，您可以將傳送分為數個批次，而非同時傳送大量訊息。 深入了解 [在本節](steps-sending-the-delivery.md#sending-using-multiple-waves).

### 排定訊息的優先順序

您可以指出優先順序層級，以設定傳送的傳送順序。 若要這麼做：

1. 編輯傳送屬性，並選取 **[!UICONTROL Delivery]** 標籤。

1. 定義傳送的優先順序層級，從 **[!UICONTROL Very low]** to **[!UICONTROL Very high]**.

>[!NOTE]
>
>無法定義從傳送內傳送訊息的順序。

### 設定IP相關性

為了更好地控制出站SMTP流量，您可以通過定義可用於每個相關性的特定IP地址來管理相關性。 這可讓您將特定傳送的電子郵件數量限制在電腦或輸出地址。 例如，您可以對每個國家/地區或子網域使用一個相關性。 接著，您可以為每個國家建立一個類型，並將每個相關性連結至對應的類型。

您可以：

* 在serverConf.xml設定檔案中定義IP相關性。 [了解更多](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* 對於每個IPAfinity元素，聲明可使用的IP地址。 [了解更多](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* 在 [類型](../../campaign-opt/using/about-campaign-typologies.md) 使用 **[!UICONTROL Managing affinities with IP addresses]** 欄位，將傳遞連結至管理所述相關性的傳遞伺服器(MTA)。 [深入瞭解](../../campaign-opt/using/applying-rules.md#control-outgoing-smtp-traffic)。

* 傳送電子郵件後，檢查標題以確認傳送的來源IP位址。 您的電子郵件管理員應可協助您取得標題資訊。

>[!NOTE]
>
>這些步驟大多只能由專家使用者執行。

### 使用類型

您可以使用類型規則，根據特定條件排除部分目標。 這樣可確保在遵守公司通訊原則的同時，傳送最符合客戶需求及期望的訊息。例如，您可以篩選未到電子報目標的收件者。 深入了解 [在此範例中](../../campaign-opt/using/filtering-rules.md).

### 避免附件

附件仍然是防止惡意軟體擴散的最常見載體之一，尤其是批量發送時。 包括指向文檔的安全連結，而不是附加文檔。 這可確保額外的安全層，以防止無意的重新分發，並大大降低因郵件大小或安全原因而在入站電子郵件網關處拒絕郵件的機會。
