---
product: campaign
title: 偵測追蹤 URL
description: 深入瞭解追蹤URL的建議模式
feature: Monitoring
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# 偵測追蹤 URL

## 非偵測範例

`<%= getURL("http://mynewsletter.com") %>` 會運作，並透過電子郵件將網頁的實際內容傳送給收件者。 但是沒有追蹤任何連結。 原因在於會執行MTA `"<%=getURL(..."` 每封電子郵件在傳送前的URL值。 每個收件者的識別碼可能不同，因此Adobe Campaign無法得知用於追蹤的URL，也無法為其指派標籤ID。

當所有收件者的下載頁面都相同時，最佳實務是執行下列動作：

`<%@ include url="http://mynewsletter.com" %>`

在此情況下，頁面會在分析期間、追蹤偵測之前下載。 它可讓Adobe Campaign探索連結、指派標籤ID及追蹤連結。

## 建議的模式

處理之後 `<%@` 指示中，要追蹤的URL的語法如下： `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>Adobe不支援所有其他模式，應避免使用，以防止潛在的安全性差距。

## 不安全的模式

將個人化連結新增至您的內容時，請一律避免URL的主機名稱部分有任何個人化，以避免潛在的安全性缺口。 在[本頁](../../installation/using/privacy.md#url-personalization)中瞭解更多。

例如， `<a href="http://<%=myURL%>">` 語法為 **不安全** 而且必須避免。

* 如果Adobe Campaign產生的連結包含一或多個引數，使用此語法可能會導致安全性問題。
* Tidy可能會不正確地修補某些連結，而這會隨機發生。 典型症狀是一段HTML，可在電子郵件校樣中看到，但預覽中看不到。
* URL的逸出有問題，URL中的某些字元可能會導致問題。
* 名稱為ID的引數不能與重新導向URL中的引數相衝突。
* 因此，追蹤的興趣會限製為傳送的統計資料，因為Adobe Campaign會以不同方式追蹤「myURL」的所有可能值。
