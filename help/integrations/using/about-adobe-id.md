---
product: campaign
title: 使用您的Adobe ID連線至Adobe Campaign
description: 進一步瞭解Adobe Campaign中的Adobe IMS實作
feature: Configuration
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 8dad8fa9-674c-433c-af30-8c6d0aadf525
source-git-commit: ffab91fc9fa7e60973fdda930239f5836671a341
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 15%

---

# 關於Adobe ID {#about-adobe-id}

AdobeIdentity Management系統(IMS)可協助管理員建立和管理使用者對應用計畫和服務的存取權。 如需不同型別的Adobe識別碼的詳細資訊，請參閱[此頁面](https://helpx.adobe.com/tw/enterprise/using/identity.html)。

Campaign使用者可以使用其Adobe ID連線至Adobe Campaign主控台，而不使用[原生使用者/密碼驗證](../../platform/using/access-management-operators.md)。 此實作提供下列優點：

* 所有 Experience Cloud 解決方案都可以使用相同的 ID。
* 透過不同的整合使用Adobe Campaign時，會保持連線。
* 比原生登入/密碼更安全的密碼管理原則。
* 使用 Federated ID 帳戶（外部 ID 提供者）。

>[!IMPORTANT]
>
> 請注意，在Campaign v8中，不允許連線使用者/密碼（亦稱為原生驗證）。 **Adobe建議從Campaign v7.3.5開始執行此移轉，以便能夠順利移轉至Campaign v8。**
>
>在[本節](../../technotes/using/ac-ims.md)中瞭解如何移轉至Adobe IMS。
>


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
| [設定IMS](../../integrations/using/configuring-ims.md) | [Experience Cloud常見問題集](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html?lang=zh-Hant) |
| [實作IMS](../../integrations/using/implementing-ims.md) | [存取管理](../../platform/using/access-management.md) |
| [IMS疑難排解](../../integrations/using/ims-troubleshooting.md) | [正在安裝Campaign套件](../../installation/using/installing-campaign-standard-packages.md) |
