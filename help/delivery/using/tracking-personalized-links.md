---
solution: Campaign Classic
product: campaign
title: 開始使用個人化連結追蹤
description: 瞭解如何在電子郵件中編寫可個人化且支援Campaign Classic追蹤的連結。
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 768fe62db4efd1217c22973c7e5dc31097d67bae
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 6%

---


# 開始使用個人化連結追蹤 {#tracking-personalized-links}

包含個人化的電子郵件內容中的連結需要追蹤特定的語法。

在電子郵件內容（HTML或文字）中使用JavaScript可讓您產生動態內容並傳送給收件者，但有兩個限制：

* 指令碼無法直接訪問資料庫（SQL函式和API函式不可用）,
* Adobe Campaign必須能夠偵測URL，才能追蹤連結。 [進一步了解](detecting-tracking-urls.md)

您可以在這些URL中新增[特定的預處理指示](pre-processing-instructions.md)

預處理指令。

為了追蹤偵測，Adobe Campaign內嵌[Tidy](http://www.html-tidy.org/)以剖析HTML來源並偵測模式。 它會列出內容的所有URL，以便個別追蹤。 Adobe Campaign再次使用「整潔」將URL(`http://myurl.com`)替換為指向Adobe Campaign重定向伺服器的URL。

例如，在初始內容中：`http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>`會替換為：`http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

其中：

* 「h」意指HTML內容（或文字內容的「t」）。
* 617791是消息ID / broadLog ID（十六進位）。
* 71ffa3是NmsDelivery ID（十六進位）。
* 71ffa8是NmsTrackingUrl ID（十六進位）。
* p1、p2等都是URL中要替代的參數。
