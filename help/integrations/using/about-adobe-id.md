---
product: campaign
title: 使用您的Adobe ID連線至Adobe Campaign
description: 進一步瞭解Adobe Campaign中的Adobe IMS實作
feature: Configuration
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 8dad8fa9-674c-433c-af30-8c6d0aadf525
source-git-commit: 49271e291953483ee14709b26ec053217a336718
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 20%

---

# 關於Adobe ID {#about-adobe-id}

AdobeIdentity Management系統(IMS)可協助管理員建立和管理使用者對應用計畫和服務的存取權。 如需不同型別的AdobeID的詳細資訊，請參閱 [此頁面](https://helpx.adobe.com/cn/enterprise/using/identity.html).

Campaign使用者可使用其Adobe ID連線至Adobe Campaign主控台，而非使用 [原生使用者/密碼驗證](../../platform/using/access-management-operators.md). 此實作提供下列優點：

* 所有 Experience Cloud 解決方案都可以使用相同的 ID。
* 透過不同的整合使用Adobe Campaign時，會保持連線。
* 比原生登入/密碼更安全的密碼管理原則。
* 使用 Federated ID 帳戶（外部 ID 提供者）。

<!--
>[!IMPORTANT]
>
>If you are connecting to Campaign through Adobe Identity Service (IMS), you need to upgrade to the latest build to be able to connect to Campaign after **June 30, 2021**. This upgrade is mandatory for both Campaign server and client console. 
>
>Depending on your current version, you must upgrade to one of the following releases: 
>
> * [Campaign [!DNL Gold Standard] 11](../../rn/using/gold-standard.md)
> * [Campaign 21.1.4](../../rn/using/latest-release.md)
>
>[Learn more about IMS updates](../../technotes/using/ims-updates.md)
-->

## 更多資源

| 有用的頁面 | 其他資源 |
|---|---|
| [設定IMS](../../integrations/using/configuring-ims.md) | [Experience Cloud常見問題集](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html) |
| [實作IMS](../../integrations/using/implementing-ims.md) | [存取管理](../../platform/using/access-management.md) |
| [ims疑難排解](../../integrations/using/ims-troubleshooting.md) | [安裝Campaign套件](../../installation/using/installing-campaign-standard-packages.md) |
