---
title: 傳送前先檢查
seo-title: 傳送前先檢查
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 3%

---


# 傳送前先執行所有檢查 {#perform-all-checks}

當訊息準備就緒後，請確定其內容在所有裝置上都正確顯示，且不包含任何錯誤，例如錯誤的個人化或損壞的連結。

在傳送訊息之前，請確定參數和設定與傳送一致。

## 驗證為何是關鍵 {#validation-is-key}

在傳送傳送內容之前，您必須確保收件者會收到您真正想要傳送的訊息。 為此，您需要驗證訊息內容和傳送參數。

此步驟可讓您偵測可能的錯誤並加以修正，然後再傳送至主要目標。

本節將介紹驗證傳送 [的步驟](../../delivery/using/steps-validating-the-delivery.md)。

## 收件箱呈現 {#inbox-and-email-rendering}

收件匣轉換功能可讓您在主要電子郵件用戶端上預覽訊息、掃描內容和信譽，以及瞭解收件者閱讀訊息的方式。

**提示**:

* 您可以在接收郵件的不同上下文中查看發送的郵件：webmail、訊息服務、行動等。

* 收件匣轉換功能對於識別您的電子郵件促銷活動是否成功超過主要ISP（網際網路服務供應商）和網路郵件服務的篩選至關重要。 此類工具會將電子郵件的預檢副本傳送至測試收件匣網路，讓您瞭解訊息在這些服務間的顯示或呈現方式。 它們也可能包含報表和程式碼修正選項，可協助您快速識別並進行修正，以改善傳遞性。

在本節 [中進一步瞭解](../../delivery/using/inbox-rendering.md)。

## 校對訊息 {#proof-messages}

傳送校樣可讓您檢查選擇退出連結、鏡像頁面和任何其他連結、驗證訊息、確認影像已顯示、偵測可能的錯誤等。 您也可能想要檢查不同裝置上的設計和演算。

在本節 [中進一步瞭解](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

## 設定A/B測試傳送 {#a-b-testing-deliveries}

如果您有數個內容要傳送電子郵件，您可以使用A/B測試來找出哪個版本對目標群體的影響最大。

**提示**:

* 將不同的版本傳送給您的部分收件者

* 選取成功率最高的成功率，並將它傳送至目標的其他部分

在本節 [中進一步瞭解](../../workflow/using/a-b-testing.md)。

## 確定訊息已傳送 {#make-sure-your-message-is-delivered}

最後一個步驟是，將您的機會發揮到最大，並運用Adobe Campaign Classic的強大功能，確保您的訊息確實能傳送給相關的收件者。

### 進行驗證程式

您可以定義包含Adobe Campaign運算子和群組的完整驗證程式，以驗證目標和訊息內容。 這將確保對促銷活動的各種程式進行完整監控：鎖定、內容、預算、擷取和傳送證明。 視其權限而定，使用者會收到通知、收到校樣，並可驗證或拒絕訊息。 在本節 [中進一步瞭解](../../campaign/using/marketing-campaign-approval.md#approval-process)。

### 使用波

您可以使用波浪遞增音量。 這樣可避免您的訊息被標示為垃圾訊息，或您想要限制每天的訊息數目。 使用波，您可以將傳送分成數批，而不是同時傳送大量訊息。 在本節 [中進一步瞭解](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)。

### 排定訊息的優先順序

您可以指明優先順序，以設定傳送的傳送順序。 若要這麼做：

1. 編輯傳送屬性，並選取標 **[!UICONTROL Delivery]** 簽。

1. 定義從到的按比例分配的優先順序 **[!UICONTROL Very low]** 別 **[!UICONTROL Very high]**。

>[!NOTE]
>
>無法定義從傳送內傳送訊息的順序。

### 設定IP相關性

要更好地控制出站SMTP通信，您可以通過定義每個相關性可以使用哪些特定IP地址來管理相關性。 這可讓您限制特定傳送給電腦或輸出地址的電子郵件數。 例如，您可以針對每個國家／地區或子網域使用一個相似性。 然後，您可以依國家／地區建立一種類型學，並將每個相似性連結至對應的類型學。

您可以：

* 在serverConf.xml配置檔案中定義IP相關性。 [進一步瞭解](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* 對於每個IPAffinity元素，請聲明可使用的IP位址。 [進一步瞭解](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* 在您選 [擇的](../../campaign/using/about-campaign-typologies.md) 「類型」中 **[!UICONTROL Managing affinities with IP addresses]** ，使用欄位將傳送連結至管理上述相似性的傳送伺服器(MTA)。 [進一步瞭解](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic).

* 傳送電子郵件後，請檢查標題以確認傳送的IP位址。 您的電子郵件管理員應協助您取得標題資訊。

>[!NOTE]
>
>這些步驟大部分只能由專家使用者執行。

### 使用類型

您可以使用分類規則根據特定條件排除部分目標。 這樣可確保在遵守公司通訊原則的同時，傳送最符合客戶需求及期望的訊息。例如，您可以篩選未到電子報目標年齡的收件者。 在此範例 [中進一步瞭解](../../campaign/using/filtering-rules.md)。

### 避免附件

附件仍然是惡意軟體擴散最常見的載體之一，尤其是批量發送附件時。 加入檔案的安全連結，而非附加檔案。 這可確保額外的安全層，以防止意外的重新分發，並大幅降低因訊息大小或安全性原因，在傳入電子郵件閘道中拒絕訊息的機率。
