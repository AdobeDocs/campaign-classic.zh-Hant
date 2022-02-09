---
product: campaign
title: 傳送前先檢查
description: 消息準備好後，在發送前執行所有檢查
feature: Deliverability
exl-id: 50d326b0-3c23-4dbf-9df6-d32b48e30f69
source-git-commit: 808f459a0b77b1787fc017c031247ab268b5aafa
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 4%

---

# 發送前執行所有檢查 {#perform-all-checks}

![](../../assets/common.svg)

一旦您的消息準備就緒，請確保其內容在所有設備上都正確顯示，並且不包含任何錯誤，如錯誤的個性化設定或中斷的連結。

在發送郵件之前，還要確保參數和配置與傳遞一致。

## 為什麼驗證是關鍵 {#validation-is-key}

在發送傳遞之前，您需要確保您的收件人將收到您確實要發送的郵件。 為此，您需要驗證消息內容和傳遞參數。

通過此步驟，您可以檢測可能的錯誤並在將錯誤傳送到主目標之前對其進行修復。

顯示驗證交貨的步驟 [此部分](steps-validating-the-delivery.md)。

## 收件匣轉譯 {#inbox-and-email-rendering}

收件箱呈現功能使您能夠在主要電子郵件客戶端上預覽郵件、掃描內容和聲譽、發現收件人閱讀郵件的方式。

**提示**:

* 您可以在接收消息的不同上下文中查看已發送的消息：Web郵件、消息服務、移動等。

* 收件箱呈現功能對於確定您的電子郵件活動是否成功地使其超過主要ISP（Internet服務提供商）和Web郵件服務的過濾器至關重要。 此類工具會將電子郵件的印前拷貝發送到test收件箱網路，這樣您就可以看到這些服務中消息的顯示或呈現方式。 它們還可能包括報告和代碼更正選項，這些選項可幫助您快速識別並做出可改善交付性的修復。

瞭解更多資訊 [此部分](inbox-rendering.md)。

## 校樣消息 {#proof-messages}

通過發送校樣，您可以檢查選擇退出連結、鏡像頁和任何其他連結、驗證消息、驗證影像是否顯示、檢測可能的錯誤等。 您可能還希望檢查不同設備上的設計和呈現。

瞭解更多資訊 [此部分](steps-validating-the-delivery.md#sending-a-proof)。

## 設定A/B測試交貨 {#a-b-testing-deliveries}

如果您有幾個用於電子郵件傳遞的內容，則可以使用A/B測試來確定哪個版本將對目標群體產生最大影響。

**提示**:

* 將不同版本發送給您的某些收件人

* 選擇成功率最高的，並將其發送到目標的其他部分

瞭解更多資訊 [此部分](get-started-a-b-testing.md)。

## 確保您的郵件已送達 {#make-sure-your-message-is-delivered}

最後一步，盡可能多地利用Adobe Campaign Classic的力量，確保你的資訊確實能送達相關收件人。

### 完成驗證過程

您可以定義一個包含Adobe Campaign運算子和組的完整驗證流程，以驗證目標和消息內容。 這將確保充分監測和控制該運動的各種進程：目標、內容、預算、提取和發送證據。 根據用戶的權限，用戶將獲得通知、接收證明並能夠驗證或拒絕消息。 瞭解更多資訊 [此部分](../../campaign/using/marketing-campaign-approval.md)。

### 使用波

可以逐漸增加使用波發送的體積。 這將避免您的郵件被標籤為垃圾郵件或您希望限制每天的郵件數。 使用波次，您可以將交貨分成幾批，而不是同時發送大量郵件。 瞭解更多資訊 [此部分](steps-sending-the-delivery.md#sending-using-multiple-waves)。

### 排定消息的優先順序

您可以通過說明優先順序來設定交貨的發送順序。 若要這麼做：

1. 編輯交貨屬性，然後選擇 **[!UICONTROL Delivery]** 頁籤。

1. 定義按比例從 **[!UICONTROL Very low]** 至 **[!UICONTROL Very high]**。

>[!NOTE]
>
>無法定義從傳遞內發送消息的順序。

### 設定IP關聯

為了更好地控制出站SMTP通信，可以通過定義可用於每個關聯的特定IP地址來管理關聯。 這允許您將特定交貨的電子郵件數量限制到電腦或輸出地址。 例如，您可以對每個國家/地區或子域使用一個關聯。 然後，您可以為每個國家建立一個類型學，並將每個相關性連結到相應的類型學。

您可以：

* 在serverConf.xml配置檔案中定義IP關聯。 [了解更多](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* 對於每個IPAfinity元素，聲明可以使用的IP地址。 [了解更多](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* 在 [類型學](../../campaign-opt/using/about-campaign-typologies.md) 你選擇的，用 **[!UICONTROL Managing affinities with IP addresses]** 將遞送連結到管理所述親和性的遞送伺服器(MTA)的欄位。 [了解更多](../../campaign-opt/using/applying-rules.md#control-outgoing-smtp-traffic)。

* 發送電子郵件後，檢查報頭，以驗證發送的IP地址。 您的電子郵件管理員應幫助您獲取標題資訊。

* 對於SMS傳遞，請確保SMS通道具有專用關聯限於 **一個** 應用程式伺服器容器。 [了解更多](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

>[!NOTE]
>
>這些步驟大多只能由專家用戶執行。

### 使用類型

您可以使用分類規則根據特定條件排除目標的一部分。 這樣可確保在遵守公司通訊原則的同時，傳送最符合客戶需求及期望的訊息。例如，您可以過濾未達到新聞稿目標的收件人。 瞭解更多資訊 [在此示例中](../../campaign-opt/using/filtering-rules.md)。

### 避免附件

附件仍然是惡意軟體數量激增的最常見的載體之一，尤其是在批量發送時。 包括指向文檔的安全連結，而不是附加文檔。 這確保了額外的安全層以防止意外的重新分發，並大大降低了由於郵件大小或安全原因而在入站電子郵件網關上拒絕郵件的可能性。
