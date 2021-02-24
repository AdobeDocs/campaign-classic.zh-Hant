---
solution: Campaign Classic
product: campaign
title: 偵測追蹤URL
description: 進一步瞭解要追蹤URL的建議模式。
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---


# 偵測追蹤URL

## 非偵測範例

`<%= getURL("http://mynewsletter.com") %>` 工作，並透過電子郵件將網頁的實際內容傳送給收件者。但是，這些連結都不會受到追蹤。 其原因是MTA在傳送前會先針對每封電子郵件執行`"<%=getURL(..."`。 每個收件者皆可使用不同的URL，因此Adobe Campaign無法知道要追蹤的URL，並指派標籤ID給他們。

當要下載的頁面對所有收件者都相同時，最佳實務是：

`<%@ include url="http://mynewsletter.com" %>`

在這種情況下，會在分析期間，在追蹤偵測之前下載頁面。 它可讓Adobe Campaign發現連結、指派標籤ID並追蹤連結。

## 建議的模式

在處理`<%@`指令後，要追蹤的URL具有下列語法：`<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>Adobe不支援所有其他模式，因此應避免出現潛在的安全性缺口。

## http://&lt;%=myURL%>模式上的警告

`<a href="http://<%=myURL%>">`語法不安全，因為：

* Tidy可能會錯誤地修補某些連結，這些連結會隨機發生。 典型的症狀是HTML片段，在電子郵件校樣中可見，但在預覽中不可見。
* 逸出URL有問題，URL中的某些字元可能會造成問題。
* 您不能有名為ID的參數與重新導向URL中的參數衝突。
* 追蹤的興趣會限制在傳送的統計資料上，因為Adobe Campaign會以不同方式追蹤&quot;myURL&quot;的所有可能值。

請參閱[本頁](https://helpx.adobe.com/campaign/kb/acc-security.html#privacy)以瞭解詳細資訊。

