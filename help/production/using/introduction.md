---
product: campaign
title: 簡介
description: 簡介
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 3e39a0d2-ff7e-4233-82bb-2b360f696a33
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---

# 簡介{#introduction}



本節介紹升級Adobe Campaign、使用者端和伺服器端時所要套用的程式，並說明如何切換至現有執行個體的Unicode。

>[!NOTE]
>
>針對託管/受管理服務例項，您必須與您的Adobe管理員協調。\
>若為內部部署例項，您可向Adobe顧問尋求協助。

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
>有關各種Adobe Campaign流程的詳細資訊，請參閱 [本節](../../installation/using/general-architecture.md#logical-application-layer).\
>使用Power Booster或Power Cluster型別架構時，您必須將此程式套用至所有Power Booster/Cluster伺服器。

如果新版本涉及變更資料庫結構，我們建議依下列順序重新啟動伺服器：

1. 應用程式伺服器(nlserver web)、
1. 重新導向伺服器(webmdl)，
1. 傳遞伺服器(nlserver mta)。
