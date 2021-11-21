---
product: campaign
title: 偵測追蹤 URL
description: 進一步了解追蹤URL的建議模式
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# 偵測追蹤 URL

## 非偵測範例

`<%= getURL("http://mynewsletter.com") %>` 工作，並透過電子郵件將網頁的實際內容傳送給收件者。 但是，這些連結都不會被追蹤。 原因是MTA會執行 `"<%=getURL(..."` 傳送前填入每個電子郵件。 每個收件者的URL可能不同，因此Adobe Campaign無法知道要追蹤的URL，並為其指派標籤ID。

當要下載的頁面對所有收件者相同時，最佳作法是執行下列動作：

`<%@ include url="http://mynewsletter.com" %>`

在此情況下，會在分析期間，在追蹤偵測之前下載頁面。 它可讓Adobe Campaign探索連結、指派標籤ID及追蹤連結。

## 建議模式

處理後 `<%@` 說明中，要追蹤的URL具有下列語法： `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>Adobe不支援所有其他模式，應避免這些模式，以防止潛在的安全漏洞。

## 不安全模式

將個人化連結新增至內容時，請一律避免URL的主機名稱部分出現任何個人化，以避免潛在的安全漏洞。 在[本頁](../../installation/using/privacy.md#url-personalization)中瞭解更多。

例如， `<a href="http://<%=myURL%>">` 語法為 **不安全** 必須避免。

* 如果Adobe Campaign產生的連結包含一或多個參數，使用此語法可能會導致安全性問題。
* 整齊可能會錯誤地修補某些連結，而這可能是隨機發生的。 典型症狀是電子郵件校樣中可見但預覽中無法顯示的HTML。
* URL逸出有問題，URL中的某些字元可能會造成問題。
* 您不能有名為ID的參數與重新導向URL中的參數發生衝突。
* 接著，追蹤的興趣會限於傳送的統計資料，因為Adobe Campaign追蹤&quot;myURL&quot;的所有可能值的方式不同。
