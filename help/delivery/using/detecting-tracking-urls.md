---
product: campaign
title: 偵測追蹤 URL
description: 瞭解有關跟蹤URL的建議模式的詳細資訊
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# 偵測追蹤 URL

## 非檢測示例

`<%= getURL("http://mynewsletter.com") %>` 通過電子郵件將網頁的實際內容發送給收件人。 但是，這些連結都沒有被追蹤。 原因是MTA執行 `"<%=getURL(..."` 發送前的每個電子郵件。 每個收件人的URL可能不同，因此Adobe Campaign無法知道用於跟蹤的URL並為其分配標籤ID。

當要下載的頁面對所有收件人相同時，最佳做法是執行以下操作：

`<%@ include url="http://mynewsletter.com" %>`

在這種情況下，在分析期間在跟蹤檢測之前下載頁面。 它使Adobe Campaign能夠發現連結、分配標籤ID並跟蹤它們。

## 推薦模式

處理後 `<%@` 說明，要跟蹤的URL具有以下語法： `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>所有其他模式都不受Adobe支援，應避免出現潛在的安全漏洞。

## 無擔保模式

在向內容添加個性化連結時，始終避免在URL的主機名部分中出現任何個性化設定，以避免潛在的安全漏洞。 在[本頁](../../installation/using/privacy.md#url-personalization)中瞭解更多。

例如， `<a href="http://<%=myURL%>">` 語法 **不安全** 必須避免。

* 如果Adobe Campaign生成的連結包含一個或多個參數，則使用此語法可能會導致安全問題。
* Tidy可以錯誤地修補某些連結，這可能是隨機的。 典型症狀是在電子郵件校樣中可見但在預覽中看不到的HTML。
* URL的轉義有問題，URL中的某些字元可能會導致問題。
* 不能有名為ID的參數與重定向URL中的參數衝突。
* 跟蹤的興趣隨後被限制在遞送統計上，因為Adobe Campaign對&quot;myURL&quot;的所有可能值的跟蹤都有不同。
