---
product: campaign
title: 傳送含附件的異動電子郵件
description: 瞭解如何使用Adobe Campaign傳送包含個人和/或個人化附件的異動電子郵件
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Transactional Messaging
exl-id: 755d2364-f6c4-4943-97e8-3ed52a0f2665
source-git-commit: 9e1d49cd1ae89a3bdf42febd48c5a340fe7ec674
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 4%

---

# 使用案例：傳送含附件的異動電子郵件 {#transactional-email-with-attachments}



此使用案例的目的是即時新增電子郵件附件至傳出派單。

## 主要步驟 {#key-steps}

在此案例中，您將瞭解如何傳送包含個別及/或個人化附件的異動電子郵件。 附件不會預先上傳至交易式訊息伺服器，而是會即時產生。

當您擷取客戶互動或詳細資料時，您可能需要在程式結束時將此資訊傳回客戶，例如在附加至電子郵件的PDF檔案中。

以下是此情境的主要步驟：

1. 客戶進入網站，尋找想要購買的產品。
1. 客戶選取產品並自訂一些選項。
1. 客戶完成交易。
1. 系統會傳送電子郵件給客戶，確認交易。 由於不建議在電子郵件中傳送PII （個人識別資訊），因此會產生安全PDF並附加至電子郵件。
1. 客戶會收到包含相關資料的電子郵件及其附件。

在此案例中，附件不是預先建立的，而是即時新增至外寄電子郵件，可提供下列優點：

* 這可讓您個人化附件的內容。
* 如果附件與交易相關聯（如上述範例案例所示），則附件可能包含客戶處理期間產生的動態資料。
* 附加PDF檔案可最佳化安全性，因為您可以加密檔案並透過HTTPS傳送。

## Recommendations和護欄 {#important-notes}

為避免效能問題，電子郵件中包含的影像預設不得超過100 MB。 此限制可從以下網址設定： `NmsDelivery_MaxDownloadedImageSize` 選項。

Adobe也建議限制附加檔案的大小和數量。 依預設，您只能新增一個檔案作為電子郵件的附件。 此臨界值可從 `NmsDelivery_MaxRecommendedAttachments` 選項。

進一步瞭解 [Campaign Classic選項清單](../../installation/using/configuring-campaign-options.md#delivery).

實施此情境之前，請仔細閱讀以下准則：

* 異動訊息執行個體不應用於儲存、匯出或上傳檔案或資料。 它們只能用於事件資料和相關資訊。 不應將其視為檔案儲存系統。
* 由於無法直接存取Adobe外部的交易式訊息執行個體或伺服器，因此沒有標準方式在這些伺服器上推送此類檔案（無FTP存取）。
* 使用交易式訊息執行個體上的磁碟空間來儲存任何型別的檔案（即使是附件也不行）在合約上是不正確的。
* 您需要使用其他線上磁碟系統來託管這些檔案。 您需要具有此系統的FTP存取權，而且您必須能夠寫入和刪除檔案。

>[!NOTE]
>
>為避免出現效能問題，建議每封電子郵件不要包含多個附件。建議的臨界值可從下列位置設定： [Campaign Classic選項清單](../../installation/using/configuring-campaign-options.md#delivery).

## 實作 {#implementation}

下圖顯示實作此情境時的不同步驟：

![](assets/message-center-uc1.png)

若要即時新增電子郵件附件至交易式訊息，請遵循下列步驟：

1. 從設計附件開始。 如需詳細資訊，請參閱[本節](../../delivery/using/attaching-files.md#attach-a-personalized-file)。

   這可讓您將檔案附加至電子郵件，即使它們不是在執行執行個體上託管。

1. 您可以透過SOAP訊息觸發器傳送電子郵件。 在SOAP呼叫中有一個URL引數(attachmentURL)。

   如需有關SOAP請求的詳細資訊，請參閱 [事件說明](../../message-center/using/event-description.md).

1. 設計電子郵件時，按一下 **[!UICONTROL Attachment]**.

1. 在 **[!UICONTROL Attachment definition]** 畫面中，輸入SOAP附件引數：

   ```
   <%= rtEvent.ctx.attachmentUrl %>
   ```

1. 處理訊息時，系統會從遠端位置（協力廠商伺服器）取得檔案，並將其附加至個別訊息。

   由於此引數可以是變數，因此它應該接受檔案的完整格式遠端URL變數（透過SOAP呼叫傳送）。

   ![](assets/message-center-uc2.png)
