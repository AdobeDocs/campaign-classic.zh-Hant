---
product: campaign
title: 偵測追蹤URL
description: 深入瞭解追蹤URL的建議模式
feature: Monitoring
role: User, Developer, Data Engineer
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 2%

---

# 偵測追蹤 URL

## 非偵測範例

`<%= getURL("http://mynewsletter.com") %>`運作並透過電子郵件傳送網頁的實際內容給收件者。 但系統不會追蹤任何連結。 原因在於MTA在傳送前會針對每封電子郵件執行`"<%=getURL(..."`。 每個收件者的URL可能不同，因此Adobe Campaign無法得知要追蹤的URL，也無法為其指派標籤ID。

如果所有收件者的下載頁面都相同，最佳實務是執行下列動作：

`<%@ include url="http://mynewsletter.com" %>`

在此情況下，頁面會在分析期間、追蹤偵測之前下載。 它可讓Adobe Campaign探索連結、指派標籤ID及追蹤連結。

## 建議的模式

處理`<%@`指示後，要追蹤的URL語法如下： `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>Adobe不支援所有其他模式，應避免使用，以防止潛在的安全性缺口。

## 不安全的模式

將個人化連結新增至您的內容時，請一律避免URL的主機名稱部分有任何個人化專案，以避免潛在的安全性缺口。 在[本頁](../../installation/using/privacy.md#url-personalization)中瞭解更多。

例如，`<a href="http://<%=myURL%>">`語法是&#x200B;**不安全**，必須避免。

* 如果Adobe Campaign產生的連結包含一或多個引數，使用此語法可能會導致安全性問題。
* 整備可能會錯誤地修補某些連結，這可能隨機發生。 典型症狀是可在電子郵件校樣中看到，但預覽中看不到的HTML片段。
* URL的逸出有問題，URL中的某些字元可能會導致問題。
* 名稱為ID的引數不能與重新導向URL中的引數相衝突。
* 因此，追蹤的興趣會限製為傳送的統計資料，因為Adobe Campaign會以不同方式追蹤「myURL」的所有可能值。
