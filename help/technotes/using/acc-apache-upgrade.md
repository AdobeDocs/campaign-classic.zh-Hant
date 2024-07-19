---
product: campaign
title: 技術檔案 — Adobe Campaign - Apache版本安全性更新
description: Adobe Campaign - Apache版本安全性更新
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: 3d2f5d1d-4b31-4cc6-b6fb-13589856e00c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# Adobe Campaign - Apache版本安全性更新 {#apache-update}

>[!CAUTION]
>本文適用於： **Campaign Classic v7 Managed Services**&#x200B;客戶、**Campaign v8**&#x200B;客戶和&#x200B;**Campaign Standard**&#x200B;客戶。

Adobe Campaign可與第三方工具合作，產品相容性將定期更新，以僅實施所支援的版本，並受益於最新的修正和改良。

Adobe Campaign內含Apache Tomcat，可透過HTTP當做應用程式伺服器的進入點，並與Apache Web Server整合。 Apache Software Foundation已發行Apache HTTP Server 2.4.53。此版本解決可能允許遠端攻擊者控制受影響系統的漏洞。 深入瞭解[Apache 2.4.53公告](https://downloads.apache.org/httpd/Announcement2.4.html){target="_blank"}。

Adobe Campaign團隊將在&#x200B;**2022年6月15日**&#x200B;前執行Apache版本安全性升級活動，以減少此Apache弱點並使您的執行個體環境更安全。 此升級適用於所有Campaign Classic v7 Managed Services客戶、Campaign v8和在易受攻擊的Apache HTTP Server版本上執行的Campaign Standard客戶。 如果您受到影響，Adobe已聯絡您，通知您有關此次升級的事宜。

此升級預計會在您正常營業時間以外自動執行，以便您繼續使用Campaign服務而不會造成任何中斷。

您的非生產執行個體將先由Adobe升級，然後再升級您的生產執行個體。 由於這是Adobe所擁有的自動升級程式，因此您不需要採取任何動作。 不過，如果您發生任何問題，請聯絡[Adobe客戶服務](https://experienceleague.adobe.com/?support-solution=Campaign#support)。


>[!NOTE]
>此升級需要重新啟動Apache Web Server。 停機時間在下列時間範圍內不會超過10分鐘。
> 

## 常見問題集 {#apache-faq}

* **為什麼這是強制升級？**

  目前的Apache版本易受攻擊，並存在潛在的安全威脅。 請務必將Campaign執行個體升級至最新適用的Apache版本，以解決安全性風險。

* **哪些客戶是安全性升級的目標？**

  所有使用在舊版Apache上實作之Campaign環境的客戶，都會升級至最新適用的Apache版本。

* **預期的停機時間是多少？**

  預計停機時間少於10分鐘。

* **此安全性升級是否需要客戶採取任何動作？**

  不需要採取任何動作，因為安全性升級會自動執行。

* **在維護期間，對執行中的行銷活動/工作流程有何影響？**

  在維護期間，工作流程和郵件服務將同時停止，且排程的活動將不會執行。 任何進行中的活動或執行中的程式都會在停機期間暫停，直到伺服器重新啟動為止。 活動完成且伺服器重新啟動後，所有服務都會繼續。

* **客戶需要執行哪些驗證？**

  此安全性升級不需要任何特定測試。 如果發現任何問題，請聯絡[Adobe客戶服務](https://experienceleague.adobe.com/?support-solution=Campaign#support)。


* **我可以要求變更排定的安全性升級位置的日期/時間嗎？**

  由於這是安全性修正，強烈建議您調整以符合現有的排程。


如有任何其他問題，請連絡[Adobe客戶服務](https://experienceleague.adobe.com/?support-solution=Campaign#support)。
