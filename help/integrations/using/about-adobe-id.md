---
product: campaign
title: 在Campaign中使用Adobe ID
description: 進一步瞭解Adobe IMS整合
feature: Configuration
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 8dad8fa9-674c-433c-af30-8c6d0aadf525
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 24%

---

# 關於Adobe ID{#about-adobe-id}

AdobeIdentity Management系統(IMS)可協助管理員建立和管理使用者對應用計畫和服務的存取權。 如需不同型別的AdobeID的詳細資訊，請參閱 [此頁面](https://helpx.adobe.com/enterprise/using/identity.html).

Campaign使用者可使用其Adobe ID連線至Adobe Campaign主控台。 此整合具備以下優勢︰

* 所有 Experience Cloud 解決方案都可以使用相同的 ID。
* 使用不同整合中的 Adobe Campaign 時，可以記憶連線。
* 更安全的密碼管理原則。
* 使用 Federated ID 帳戶（外部 ID 提供者）。


>[!IMPORTANT]
>
>如果您是透過Adobe身分服務(IMS)連線至Campaign，您需要升級至最新組建版本，才能在下列時間後連線至Campaign **2021年6月30日**. Campaign伺服器和使用者端主控台都必須進行此升級。
>
>根據您目前的版本，您必須升級至下列其中一個版本：
>
> * [Campaign [!DNL Gold Standard] 11](../../rn/using/gold-standard.md)
> * [Campaign 21.1.4](../../rn/using/latest-release.md)
>
>[進一步瞭解IMS更新](../../technotes/using/ims-updates.md)


## 更多資源

| 有用的頁面 | 其他資源 |
|---|---|
| [設定IMS](../../integrations/using/configuring-ims.md) | [Experience Cloud常見問題集](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html) |
| [實作IMS](../../integrations/using/implementing-ims.md) | [存取管理](../../platform/using/access-management.md) |
| [ims疑難排解](../../integrations/using/ims-troubleshooting.md) | [安裝Campaign套件](../../installation/using/installing-campaign-standard-packages.md) |
