---
product: campaign
title: 關於 Adobe Experience Cloud 觸發程式
description: 開始使用Adobe Experience Cloud Triggers實作
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 2f6a5884e47ce10ce3c281a4377ee37522c52131
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 7%

---

# 使用Campaign和Experience Cloud觸發程式{#about-adobe-experience-triggers}

[!DNL Triggers] 是使用管道的Adobe Campaign與Adobe Analytics之間的整合。 管道會從您的網站擷取使用者的動作或觸發器。 放棄購物車就是一個觸發器範例。 在Adobe Campaign中處理觸發器，以近乎即時地傳送電子郵件。

>[!CAUTION]
>
>這項功能無法立即在產品中使用。針對此實作，您首先需要透過Adobe支援開啟票證。 然後，您就可以依照此中詳述的步驟進行 [頁面](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] 在使用者動作後的短時間內執行行銷動作。 一般回應時間少於1小時。

由於設定最少且未涉及協力廠商，因此可支援更敏捷的整合。
它也支援大量流量，而不會影響行銷活動的效能。 例如，整合每小時可處理100萬個觸發器。

![](assets/do-not-localize/book.png) 瞭解如何 [建立Experience Cloud觸發程式](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html) 識別、定義及監控重要的消費者行為。

## [!DNL Triggers] 架構 {#triggers-architecture}

此 [!DNL pipelined] 程式一律在Adobe Campaign行銷伺服器上執行。 它會連線到管道、擷取事件，並立即處理它們。

![](assets/triggers_2.png)

此 [!DNL pipelined] 程式使用驗證服務登入Experience Cloud並傳送私密金鑰。 驗證服務會傳回權杖。 在擷取事件時，會使用權杖進行驗證。

如需驗證的詳細資訊，請參閱此 [頁面](../../integrations/using/configuring-adobe-io.md).
