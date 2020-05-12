---
title: 使用Adobe Campaign Classic將附件新增至交易訊息
description: 瞭解如何使用Adobe Campaign Classic傳送包含個人及／或個人化附件的交易式電子郵件
page-status-flag: never-activated
uuid: 4452d839-318a-49d8-8abb-4ba04c803e9f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: 7b8ab9d6-e47e-46d8-99df-da793486654c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 24a50fcaad4d9081e5504652eb5b73aa7db1e65f
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 0%

---


# 使用案例： 傳送含附件的交易式電子郵件{#transactional-email-with-attachments}

此使用案例的目的是即時將電子郵件附件添加到出站派單。

## 關鍵步驟 {#key-steps}

在此案例中，您將學習如何傳送包含個別及／或個人化附件的交易式電子郵件。 附件不會預先上載到Transactional Messaging伺服器上： 而是即時產生。

當您擷取客戶互動或詳細資訊時，您可能需要在程式結束時將此資訊傳回給客戶，例如附在電子郵件的PDF檔案。

以下是此方案的主要步驟：

1. 客戶進入網站，尋找想要購買的產品。
1. 客戶選擇產品並自訂一些選項。
1. 客戶完成交易。
1. 系統會傳送電子郵件給客戶確認交易。 由於不建議在電子郵件中傳送PII（個人識別資訊），因此會產生安全的PDF並附加至電子郵件。
1. 客戶收到包含相關資料的電子郵件及其附件。

在此案例中，附件不是預先建立的，而是即時新增至傳出電子郵件，提供下列優點：

* 這可讓您個人化附件的內容。
* 如果附件與事務關聯（如上述示例方案中所述），則附件可能包含在客戶流程期間生成的動態資料。
* 附加PDF檔案可最佳化安全性，因為您可以加密檔案並透過HTTPS傳送。

## 建議 {#important-notes}

在實施此藍本之前，請仔細閱讀以下准則：

* 「交易訊息」例項不應用於儲存、匯出或上傳檔案或資料。 它們只能用於事件資料和相關資訊。 它們不應被視為檔案儲存系統。
* 由於Adobe以外無法直接存取「交易訊息」例項或伺服器，因此沒有標準方式將這些檔案推送至這些伺服器（無FTP存取）。
* 使用事務性消息傳遞實例上的磁碟空間來儲存任何類型的檔案（甚至是附件）在合約中是不正確的。
* 您需要使用另一個聯機磁碟系統來托管這些檔案。 您需要此系統的FTP存取權，而且您必須能夠寫入和刪除檔案。

## 實作 {#implementation}

下圖顯示實施此方案時的不同步驟：

![](assets/message-center-uc1.png)

要即時將電子郵件附件添加到事務性郵件，請執行以下步驟：

1. 從設計附件開始。 For more on this, see [this section](../../delivery/using/attaching-files.md#attach-a-personalized-file).

   這可讓您將檔案附加至電子郵件，即使這些檔案並非由執行例項代管。

1. 您可以透過SOAP訊息觸發器傳送電子郵件。 在SOAP呼叫中，有URL參數(attachmentURL)。

   有關SOAP請求的詳細資訊，請參閱事 [件說明](../../message-center/using/event-description.md)。

1. 設計電子郵件時，按一下 **[!UICONTROL Attachment]**。

1. 在螢幕 **[!UICONTROL Attachment definition]** 中，輸入SOAP附件參數：

   ```
   <%= rtEvent.ctx.attachementUrl %>
   ```

1. 處理消息時，系統將從遠程位置（第三方伺服器）獲取檔案並將其附加到單個消息。

   由於此參數可以是變數，因此它應接受您檔案的完整格式遠端URL變數，並透過SOAP呼叫傳送。

   ![](assets/message-center-uc2.png)
