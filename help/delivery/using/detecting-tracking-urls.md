---
solution: Campaign Classic
product: campaign
title: 偵測追蹤 URL
description: 進一步瞭解要追蹤URL的建議模式
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 768fe62db4efd1217c22973c7e5dc31097d67bae
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 2%

---


# 偵測追蹤 URL

## 非偵測範例

`<%= getURL("http://mynewsletter.com") %>` 工作，並透過電子郵件將網頁的實際內容傳送給收件者。但是，這些連結都不會受到追蹤。 其原因是MTA在傳送前會先針對每封電子郵件執行`"<%=getURL(..."`。 每個收件者的URL可能不同，因此Adobe Campaign無法知道要追蹤的URL，並指派標籤ID。

當要下載的頁面對所有收件者都相同時，最佳實務是：

`<%@ include url="http://mynewsletter.com" %>`

在這種情況下，會在分析期間，在追蹤偵測之前下載頁面。 它可讓Adobe Campaign發現連結、指派標籤ID並追蹤連結。

## 建議的模式

在處理`<%@`指令後，要追蹤的URL具有下列語法：`<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>所有其他模式都不受Adobe支援，應避免出現潛在的安全漏洞。

## 無擔保模式

在將個人化連結新增至您的內容時，請務必避免URL的主機名稱部分有任何個人化，以避免潛在的安全性缺口。 進一步瞭解[本頁](../../installation/using/privacy.md#url-personalization)。

例如，`<a href="http://<%=myURL%>">`語法為&#x200B;**notsecure**，必須避免。

* 如果Adobe Campaign產生的連結包含一或多個參數，使用此語法可能會導致安全性問題。
* Tidy可能會錯誤地修補某些連結，這些連結會隨機發生。 典型的症狀是HTML片段，在電子郵件校樣中可見，但在預覽中不可見。
* 逸出URL有問題，URL中的某些字元可能會造成問題。
* 您不能有名為ID的參數與重新導向URL中的參數衝突。
* 接著，追蹤的興趣會限制在傳送的統計資料上，因為Adobe Campaign會以不同的方式追蹤&quot;myURL&quot;的所有可能值。
