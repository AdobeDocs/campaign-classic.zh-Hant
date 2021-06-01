---
product: campaign
title: 開始使用個人化連結追蹤
description: 了解如何在電子郵件中撰寫可個人化的連結，並支援Campaign Classic中的追蹤。
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: d0e00b40-e7dd-4484-b37c-fd3f3ac70fda
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 7%

---

# 開始使用個人化連結追蹤 {#tracking-personalized-links}

包含個人化的電子郵件內容中的連結需要追蹤特定語法。

在電子郵件內容（HTML或文字）中使用JavaScript，可讓您產生動態內容並傳送給收件者，但有兩個限制：

* 指令碼無法直接訪問資料庫（SQL函式和API函式不可用）,
* Adobe Campaign必須能夠偵測URL，才能追蹤連結。 [瞭解更多](detecting-tracking-urls.md)

您可以新增特定的預先處理指示，以編寫URL的指令碼並加以追蹤。 [瞭解更多](pre-processing-instructions.md)

為了追蹤偵測，Adobe Campaign內嵌[Tidy](http://www.html-tidy.org/)以剖析HTML來源並偵測模式。 它會列出內容的所有URL，以便個別追蹤。 Adobe Campaign再次使用「整齊」，將URL(`http://myurl.com`)取代為指向Adobe Campaign重新導向伺服器的URL。

例如，在初始內容中：`http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>`取代為：`http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

其中：

* &quot;h&quot;表示HTML內容（或文字內容為&quot;t&quot;）。
* 617791是訊息ID / broadLog ID（十六進位）。
* 71ffa3是NmsDelivery ID（十六進位）。
* 71ffa8是NmsTrackingUrl ID（十六進位）。
* p1、p2等都是URL中要取代的參數。
