---
product: campaign
title: 開始使用個人化連結追蹤
description: 了解如何在電子郵件中撰寫可個人化的連結，並支援Campaign中的追蹤
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Personalization
exl-id: d0e00b40-e7dd-4484-b37c-fd3f3ac70fda
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 7%

---

# 開始使用個人化連結追蹤 {#tracking-personalized-links}



包含個人化的電子郵件內容中的連結需要追蹤特定語法。

在電子郵件內容(HTML或文字)中使用JavaScript，可讓您產生動態內容並傳送給收件者，但有兩項限制：

* 指令碼無法直接訪問資料庫（SQL函式和API函式不可用）,
* Adobe Campaign必須能夠偵測URL，才能追蹤連結。 [了解更多](detecting-tracking-urls.md)

您可以新增特定的預先處理指示，以編寫URL的指令碼並加以追蹤。 [了解更多](pre-processing-instructions.md)

為了追蹤偵測，Adobe Campaign內嵌 [整潔](https://www.html-tidy.org/) 來剖析HTML來源並偵測模式。 它會列出內容的所有URL，以便個別追蹤。 Adobe Campaign再次使用整齊功能來取代URL(`http://myurl.com`)，且URL指向Adobe Campaign重新導向伺服器。

例如，在初始內容中： `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` 會以下列方式取代某個特定收件者： `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

其中：

* &quot;h&quot;表示HTML內容（或文字內容為&quot;t&quot;）。
* 617791是訊息ID / broadLog ID（十六進位）。
* 71ffa3是NmsDelivery ID（十六進位）。
* 71ffa8是NmsTrackingUrl ID（十六進位）。
* p1、p2等都是URL中要取代的參數。
