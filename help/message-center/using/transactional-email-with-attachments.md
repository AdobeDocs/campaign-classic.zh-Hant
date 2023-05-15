---
product: campaign
title: 傳送含附件的異動電子郵件
description: 了解如何使用Adobe Campaign，傳送含有個別和/或個人化附件的交易式電子郵件
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Transactional Messaging
exl-id: 755d2364-f6c4-4943-97e8-3ed52a0f2665
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 5%

---

# 使用案例：傳送含附件的交易式電子郵件 {#transactional-email-with-attachments}



此使用案例的目的是即時添加電子郵件附件到外寄派單。

## 主要步驟 {#key-steps}

在此案例中，您將了解如何傳送包含個別和/或個人化附件的交易式電子郵件。 不會在交易式訊息伺服器上預先上傳附件：而是在飛機上產生。

擷取客戶互動或詳細資訊時，您可能需要在程式結束時將此資訊傳回客戶，例如附加至電子郵件的PDF檔案。

以下是此情境的主要步驟：

1. 客戶進入網站，找到他們要購買的產品。
1. 客戶選擇產品並自訂一些選項。
1. 客戶完成交易。
1. 系統會傳送電子郵件給客戶確認交易。 由於不建議在電子郵件中傳送PII（個人識別資訊），因此會產生安全PDF並附加至電子郵件。
1. 客戶會收到包含相關資料的電子郵件及其附件。

在此情況下，系統不會預先建立附件，而是會即時新增至傳出電子郵件，這可提供下列優點：

* 這可讓您個人化附件的內容。
* 如果附件與交易相關聯（如上述範例案例中），它可能包含在客戶處理期間產生的動態資料。
* 附加PDF檔案可最佳化安全性，因為您可以加密檔案並透過HTTPS傳送。

>[!NOTE]
>
>為避免效能問題，如果您包含從個人化URL即時下載的影像作為附件，則每個影像大小預設不應超過100,000位元組。 此建議的臨界值可從 [Campaign Classic選項清單](../../installation/using/configuring-campaign-options.md#delivery).

## 建議 {#important-notes}

在實作此案例之前，請先詳閱以下准則：

* 交易式傳訊例項不應用於儲存、匯出或上傳檔案或資料。 它們只能用於事件資料和相關資訊。 不應將其視為檔案儲存系統。
* 由於無法直接存取Adobe以外的交易式訊息執行個體或伺服器，因此沒有標準方式可在這些伺服器上推送這類檔案（無FTP存取）。
* 在合約上，使用交易式訊息傳送例項上的磁碟空間來儲存任何類型的檔案（甚至是附件）是不正確的。
* 您需要使用其他聯機磁碟系統來托管這些檔案。 您需要此系統的FTP存取權，且必須能夠寫入和刪除檔案。

>[!NOTE]
>
>為避免出現效能問題，建議每封電子郵件不要包含多個附件。建議的臨界值可從 [Campaign Classic選項清單](../../installation/using/configuring-campaign-options.md#delivery).

## 實作 {#implementation}

下圖顯示實作此案例的不同步驟：

![](assets/message-center-uc1.png)

若要即時新增電子郵件附件至交易式訊息，請遵循下列步驟：

1. 從設計附件開始。 如需詳細資訊，請參閱[本節](../../delivery/using/attaching-files.md#attach-a-personalized-file)。

   這可讓您將檔案附加至電子郵件，即使這些檔案並非由執行執行個體托管亦然。

1. 您可以透過SOAP訊息觸發器傳送電子郵件。 在SOAP呼叫中，有URL參數(attachmentURL)。

   有關SOAP請求的詳細資訊，請參見 [事件說明](../../message-center/using/event-description.md).

1. 設計電子郵件時，請按一下 **[!UICONTROL Attachment]**.

1. 在 **[!UICONTROL Attachment definition]** 螢幕中，輸入SOAP附件參數：

   ```
   <%= rtEvent.ctx.attachmentUrl %>
   ```

1. 處理消息時，系統將從遠程位置（第三方伺服器）獲取該檔案，並將其附加到單個消息。

   由於此參數可以是變數，因此應接受透過SOAP呼叫傳送之檔案的完整格式遠端URL變數。

   ![](assets/message-center-uc2.png)
