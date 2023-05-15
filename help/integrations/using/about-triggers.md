---
product: campaign
title: 關於 Adobe Experience Cloud 觸發程式
description: 開始使用Adobe Experience Cloud Triggers實作
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 8%

---

# 使用Campaign和Experience Cloud觸發程式{#about-adobe-experience-triggers}



[!DNL Triggers] 是Adobe Campaign與Adobe Analytics之間，使用管道的整合。 管道會從您的網站擷取使用者的動作或觸發器。 放棄購買是觸發的範例。 觸發器會在Adobe Campaign中處理，以近乎即時傳送電子郵件。

>[!CAUTION]
>
>這項功能無法立即在產品中使用。針對此實作，您必須先開啟支援Adobe的票證。 然後，您就能依照 [頁面](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] 在使用者動作後的短時間內執行行銷動作。 一般回應時間不到1小時。

它可提供更靈活的整合，因為設定極低，不涉及協力廠商。
它也支援高流量，而不會影響行銷活動的效能。 例如，整合每小時可處理100萬個觸發器。

## [!DNL Triggers] 架構 {#triggers-architecture}

此 [!DNL pipelined] 程式一律在Adobe Campaign行銷伺服器上執行。 它會連線至管道、擷取事件並立即處理。

![](assets/triggers_2.png)

此 [!DNL pipelined] 程式使用驗證服務登入Experience Cloud並傳送私密金鑰。 驗證服務會傳回Token。 擷取事件時，會使用Token來驗證。

有關身份驗證的詳細資訊，請參閱 [頁面](../../integrations/using/configuring-adobe-io.md).
