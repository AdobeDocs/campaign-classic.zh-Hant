---
product: campaign
title: 技術 — Adobe Campaign- Apache版本安全更新
description: Adobe Campaign- Apache版本安全更新
hide: true
hidefromtoc: true
exl-id: 3d2f5d1d-4b31-4cc6-b6fb-13589856e00c
source-git-commit: a3eae4e253f66f5a651ffe0458f60b1f8bdf2258
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# Adobe Campaign- Apache版本安全更新 {#apache-update}

>[!CAUTION]
>本文適用於： **Campaign ClassicV7Managed Services** 客戶， **市場活動v8** 客戶及 **Campaign Standard** 客戶。

Adobe Campaign使用第三方工具，並定期更新相容性，以便僅實施受支援的版本，並受益於最新的修復和改進。

Adobe Campaign公司包括Apache Tomcat，它通過HTTP作為應用伺服器的入口點，並與Apache Web伺服器整合。 Apache Software Foundation已發佈Apache HTTP Server 2.4.53。此版本解決了可能允許遠程攻擊者控制受影響系統的漏洞。 瞭解詳情 [Apache 2.4.53公告](https://downloads.apache.org/httpd/Announcement2.4.html){target=&quot;_blank&quot;}。

Adobe Campaign團隊將通過以下方式執行Apache版本安全升級活動 **2022年6月15日** 來緩解此Apache漏洞並使實例環境更加安全。 此升級適用於所有在易受攻擊的Apache HTTP Server版本上運行的Campaign Classicv7Managed Services客戶、活動v8和Campaign Standard客戶。 如果您受到影響，Adobe已聯繫您以通知您此升級。

此升級預計會在正常工作時間之外自動運行，以便您繼續使用市場活動服務而不中斷。

您的非生產實例將首先通過Adobe進行升級，然後升級您的生產實例。 由於這是Adobe擁有的自動升級過程，因此您不需要執行任何操作。 但是，如果您遇到任何問題，請聯繫 [Adobe客戶關懷](https://experienceleague.adobe.com/?support-solution=Campaign#support)。


>[!NOTE]
>此升級需要重新啟動Apache Web伺服器。 在下面提到的時段內，停機時間不超過10分鐘。

## 常見問題集 {#apache-faq}

* **為什麼這是強制升級？**

   當前的Apache版本易受攻擊，並且存在潛在的安全威脅。 必須將市場活動實例升級到最新適用的Apache版本，以解決安全風險。

* **哪些客戶是安全升級的目標客戶？**

   所有使用在較舊的Apache版本上實施的Campaign環境的客戶都升級到最新的適用的Apache版本。

* **預期的停機時間是多少？**

   預計停機時間不到10分鐘。

* **客戶是否需要執行此安全升級操作？**

   由於安全升級將自動運行，因此不需要執行任何操作。

* **在維護窗口期間，對運行的市場活動/工作流有何影響？**

   在維護窗口期間，工作流和郵件服務將同時停止，並且計畫的活動將不會運行。 任何正在進行的活動或正在運行的進程在停機期間將暫停，直到伺服器重新啟動。 活動完成並重新啟動伺服器後，所有服務都將恢復。

* **客戶需要運行哪些驗證？**

   此安全升級不需要特定測試。 如果發現任何問題，請聯繫 [Adobe客戶關懷](https://experienceleague.adobe.com/?support-solution=Campaign#support)。


* **是否可以請求更改計畫的安全升級插槽的日期/時間？**

   由於這是一種安全解決方案，我們強烈建議您適應現有計畫。


對於其他問題，您可以 [Adobe客戶關懷](https://experienceleague.adobe.com/?support-solution=Campaign#support)。
