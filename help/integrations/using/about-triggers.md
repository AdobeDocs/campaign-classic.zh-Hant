---
solution: Campaign Classic
product: campaign
title: 關於 Adobe Experience Cloud 觸發程式
description: 開始使用Adobe Experience Cloud觸發器實作
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: d7de46abb71ca25ef765c6fb5443f6e338fba56e
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 11%

---


# 開始使用Adobe Experience Cloud觸發器{#about-adobe-experience-triggers}

[!DNL Triggers] 是Adobe Campaign與Adobe Analytics使用管道的整合。管線會從您的網站擷取使用者的動作或觸發器。 放棄購物車是觸發的範例。 Adobe Campaign會處理觸發器，以即時傳送電子郵件。

>[!CAUTION]
>
>這項功能無法立即在產品中使用。此實作需要 Adobe Consulting 參與。請洽詢您的Adobe代表以瞭解更多資訊

[!DNL Triggers] 在使用者動作後的短時間內執行行銷動作。一般的回應時間不到1小時。

它可讓整合更加靈活，因為組態最小，而且不涉及協力廠商。
它也支援高流量，而不會影響行銷活動的效能。 例如，整合每小時可處理一百萬個觸發器。

## [!DNL Triggers] 架構  {#triggers-architecture}

[!DNL pipelined]程式一律會在Adobe Campaign行銷伺服器上執行。 它會連線至管線、擷取事件並立即處理。

![](assets/triggers_2.png)

[!DNL pipelined]程式使用驗證服務登入Experience Cloud，並傳送私密金鑰。 驗證服務傳回Token。 擷取事件時，會使用Token來驗證。

有關身份驗證的詳細資訊，請參閱此[頁](../../integrations/using/configuring-adobe-io.md)。
