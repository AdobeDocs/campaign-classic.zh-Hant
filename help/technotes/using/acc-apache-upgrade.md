---
product: campaign
title: 技術 — Adobe Campaign- Apache版本安全更新
description: Adobe Campaign- Apache版本安全更新
hide: true
hidefromtoc: true
source-git-commit: 086d03cf0ceb5c2db7ded0c2bedb1b0514257d8a
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Adobe Campaign- Apache版本安全更新 {#apache-update}

Campaign Classic可與第三方工具配合使用，並定期更新相容性，以便僅實施受支援的版本，並受益於最新的修復和改進。

Adobe Campaign公司包括Apache Tomcat，它通過HTTP作為應用伺服器的入口點，並與Apache Web伺服器整合。 Apache Software Foundation已發佈Apache HTTP Server 2.4.53。此版本解決了漏洞 — CVE-2021-44790和CVE-2021-44224 — 其中一個漏洞可能使遠程攻擊者能夠控制受影響的系統。 瞭解詳情 [Apache 2.4.53公告](https://downloads.apache.org/httpd/Announcement2.4.html){target=&quot;_blank&quot;}。

Adobe Campaign團隊將通過以下方式執行Apache版本安全升級活動 **2022年5月31日** 來緩解此Apache漏洞並使實例環境更加安全。 此升級適用於所有在易受攻擊的Apache HHTP伺服器版本上運行的Managed Services客戶。 如果您受到影響，Adobe已聯繫您以通知您此升級。

此升級預計會在正常工作時間之外自動運行，以便您繼續使用市場活動服務而不中斷。

在升級您的生產實例之前，我們的團隊將首先升級您的非生產實例。 由於這是一個自動升級過程，因此您不需要執行任何操作。 但是，如果您遇到任何問題，請聯繫 [Adobe客戶關懷](https://experienceleague.adobe.com/?support-solution=Campaign#support)。

由於升級需要重新啟動Apache，因此我們預計停機時間不會超過下面提到的時隙10分鐘。

## 常見問題集 {#apache-faq}

* **為什麼這是強制升級？**

   當前的Apache版本易受攻擊，並且存在潛在的安全威脅。 將市場活動實例升級到最新適用的Apache版本以解決安全風險非常重要。


* **哪些客戶是安全升級的目標客戶？**

   所有在較舊的Apache版本上實施市場活動環境的客戶都將升級到最新的適用的Apache版本。

* **預期的停機時間是多少？**

   預計停機時間不到10分鐘。


* **客戶是否需要執行此安全升級操作？**

   由於安全升級將自動運行，因此不需要執行任何操作。


* **客戶需要運行哪些驗證？**

   此安全升級不需要特定測試。 如果發現任何問題，請聯繫 [Adobe客戶關懷](https://experienceleague.adobe.com/?support-solution=Campaign#support)


* **是否可以請求更改計畫的安全升級插槽的日期/時間？**

   由於這是一種安全解決方案，我們強烈建議您適應現有計畫。


對於其他問題，您可以 [Adobe客戶關懷](https://experienceleague.adobe.com/?support-solution=Campaign#support)。
