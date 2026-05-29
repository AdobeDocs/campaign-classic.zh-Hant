---
product: campaign
title: 簡介
description: 簡介
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 3e39a0d2-ff7e-4233-82bb-2b360f696a33
TQID: https://experienceleague.adobe.com/L6Ais2NSt-Z29b7Jgz25a6uYInel9V-Hb5kv0u6oSLo
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 194
ht-degree: 1%

---

# 簡介{#introduction}



本節介紹升級Adobe Campaign、使用者端和伺服器端時所要套用的程式，並說明如何切換至現有執行個體的Unicode。

>[!NOTE]
>
>針對託管/受管服務例項，您必須與Adobe管理員協調。\
>若為內部部署例項，您可向Adobe Consultants尋求協助。

升級必須套用至安裝Adobe Campaign的所有伺服器。

1. 移轉重新導向與追蹤伺服器(Apache/IIS)。
1. 移轉Power Booster/Cluster伺服器。
1. 移轉行銷伺服器。

Adobe Campaign是以伺服器端執行的幾個程式為基礎，在更新期間您需要控制這些程式，特別是：

* 應用程式伺服器(nlserver web)
* 傳遞伺服器(nlserver mta)
* 重新導向伺服器(webmdl)

>[!CAUTION]
>
>使用者端主控台應與伺服器執行個體位在相同組建上。

>[!NOTE]
>
>如需各種Adobe Campaign程式的詳細資訊，請參閱[本節](../../installation/using/general-architecture.md#logical-application-layer)。\
>使用Power Booster或Power Cluster型別架構時，您必須將此程式套用至所有Power Booster/Cluster伺服器。

如果新版本涉及變更資料庫結構，我們建議依下列順序重新啟動伺服器：

1. 應用程式伺服器(nlserver web)、
1. 重新導向伺服器(webmdl)，
1. 傳遞伺服器(nlserver mta)。
