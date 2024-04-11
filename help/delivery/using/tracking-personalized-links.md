---
product: campaign
title: 開始使用個人化連結追蹤
description: 瞭解如何在電子郵件中撰寫可個人化並支援Campaign追蹤的連結
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Personalization
role: User
exl-id: d0e00b40-e7dd-4484-b37c-fd3f3ac70fda
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 7%

---

# 開始使用個人化連結追蹤 {#tracking-personalized-links}

電子郵件內容中包含個人化的連結需要追蹤特定語法。

在電子郵件內容(HTML或文字)中使用JavaScript可讓您產生動態內容並傳送給收件者，但有兩個限制：

* 指令碼無法直接存取資料庫（無法使用SQL函式和API函式），
* Adobe Campaign必須能夠偵測URL，以便追蹤連結。 [了解更多](detecting-tracking-urls.md)

您可以新增特定的前置處理指示，以便為URL編寫指令碼並加以追蹤。 [了解更多](pre-processing-instructions.md)

針對追蹤偵測，Adobe Campaign會嵌入 [整潔](https://www.html-tidy.org/) 以剖析HTML來源並偵測模式。 它會列出內容的所有URL，以便可以個別追蹤。 Adobe Campaign再次使用Tidy取代URL (`http://myurl.com`)，且URL指向Adobe Campaign重新導向伺服器。

例如，在初始內容中： `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` 會以下列專案取代某個特定收件者的收件者： `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

其中：

* 「h」表示HTML內容（或「t」表示文字內容）。
* 617791是訊息ID / broadLog ID （十六進位）。
* 71ffa3是NmsDelivery ID （十六進位）。
* 71ffa8是NmsTrackingUrl ID （十六進位）。
* p1、p2等都是URL中要取代的引數。
