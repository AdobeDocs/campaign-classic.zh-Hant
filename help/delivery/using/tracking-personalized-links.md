---
product: campaign
title: 開始使用個人化連結追蹤
description: 瞭解如何在電子郵件中寫入可個性化的連結，並支援Campaign Classic跟蹤。
feature: Personalization
exl-id: d0e00b40-e7dd-4484-b37c-fd3f3ac70fda
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 7%

---

# 開始使用個人化連結追蹤 {#tracking-personalized-links}

![](../../assets/common.svg)

電子郵件內容中包含個性化的連結需要跟蹤特定語法。

在電子郵件內容(HTML或文本)中使用JavaScript允許您生成動態內容並將其發送到收件人，這有兩個限制：

* 指令碼無法直接訪問資料庫（SQL函式和API函式不可用）,
* Adobe Campaign必須能夠檢測URL，以便跟蹤連結。 [了解更多](detecting-tracking-urls.md)

您可以添加特定的預處理指令來編寫URL指令碼並跟蹤它。 [了解更多](pre-processing-instructions.md)

為了追蹤探測，Adobe Campaign [整潔](https://www.html-tidy.org/) 分析HTML源並檢測模式。 它列出了內容的所有URL，以便可以單獨跟蹤這些URL。 Adobe Campaign再次使用Tidy替換URL(`http://myurl.com`)的URL。

例如，在初始內容中： `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` 替換為： `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

位置：

* &quot;h&quot;表示HTML內容（或文本內容的&quot;t&quot;）。
* 617791是消息ID / broadLog ID（十六進位）。
* 71ffa3是NmsDelivery ID（十六進位）。
* 71ffa8是NmsTrackingUrl ID（十六進位）。
* p1、p2等都是URL中要替換的參數。
