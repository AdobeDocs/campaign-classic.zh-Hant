---
product: campaign
title: 關於 Adobe Experience Cloud 觸發程式
description: 開始使用Adobe Experience Cloud Triggers實作
feature: Triggers
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 7%

---

# 合作使用Campaign與Experience Cloud觸發程式{#about-adobe-experience-triggers}

[!DNL Triggers] 是使用管道的Adobe Campaign與Adobe Analytics之間的整合。 管道會從您的網站擷取使用者的動作或觸發器。 放棄購物車就是一個觸發器例子。 在Adobe Campaign中處理觸發器，以近乎即時地傳送電子郵件。

>[!CAUTION]
>
>這項功能無法立即在產品中使用。針對此實作，請與您的Adobe代表/客戶服務合作。 然後，您便能依照此中詳述的步驟進行 [頁面](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] 在使用者進行動作後的短時間內執行行銷動作。 一般回應時間不到一小時。

由於設定最小且不含第三方，因此可容許更敏捷的整合。
它也能支援大量流量，而不會影響行銷活動的效能。 例如，整合每小時可處理100萬個觸發器。

![](assets/do-not-localize/book.png) 瞭解如何 [建立Experience Cloud觸發器](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html) 識別、定義及監控重要的消費者行為。

## [!DNL Triggers] 架構 {#triggers-architecture}

此 [!DNL pipelined] 程式一律在Adobe Campaign行銷伺服器上執行。 它會連線至管道、擷取事件，並立即處理。

![](assets/triggers_2.png)

此 [!DNL pipelined] 程式使用驗證服務登入Experience Cloud並傳送私密金鑰。 驗證服務會傳回權杖。 Token用於擷取事件時進行驗證。

## 先決條件 {#adobe-io-prerequisites}

開始此實作前，請檢查您是否擁有：

* 有效的 **組織識別碼**：組織ID是Adobe Experience Cloud中的唯一識別碼，用於VisitorID服務和IMS單一登入(SSO)。 [了解更多](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hant)
* a **開發人員存取權** 至您的組織。 組織的系統管理員需要遵循 **將開發人員新增至單一產品設定檔** 詳細程式 [在此頁面中](https://helpx.adobe.com/enterprise/using/manage-developers.html) 為提供開發人員存取權 `Analytics - {tenantID}` 與觸發器相關聯之Adobe Analytics產品的產品設定檔。

## 實施步驟 {#implement}

若要實施Campaign及Experience Cloud觸發程式，請遵循下列步驟：

1. 建立Oauth專案。 [了解更多](oauth-technical-account.md#oauth-service)

1. 在Adobe Campaign中新增您的OAuth專案認證。 [了解更多](oauth-technical-account.md#add-credentials)

1. 將驗證型別更新至設定檔案中的開發人員控制檯專案 **config-&lt; instance-name >.xml** 如下所示：

   ```
   <pipelined ... authType="imsJwtToken"  ... />
   ```

   然後，執行 `config -reload` 以及重新啟動 [!DNL pipelined] 以納入變更。

