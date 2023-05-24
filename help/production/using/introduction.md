---
product: campaign
title: 簡介
description: 簡介
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 3e39a0d2-ff7e-4233-82bb-2b360f696a33
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---

# 簡介{#introduction}



本節介紹升級Adobe Campaign、使用者端和伺服器端所套用的程式，並說明切換至現有執行個體的Unicode。

>[!NOTE]
>
>針對託管/受管理服務例項，您必須與Adobe管理員協調。\
>對於內部部署執行個體，您可以向Adobe顧問尋求協助。

升級必須套用至安裝Adobe Campaign的所有伺服器。

1. 移轉重新導向和追蹤伺服器(Apache/IIS)。
1. 移轉Power Booster/Cluster伺服器。
1. 移轉行銷伺服器。

Adobe Campaign是以伺服器端執行的幾個程式為基礎，在更新期間您需要控制這些程式，特別是：

* 應用程式伺服器(nlserver web)
* 傳遞伺服器(nlserver mta)
* 重新導向伺服器(webmdl)

>[!CAUTION]
>
>使用者端主控台應與伺服器執行個體位於相同的版本上。

>[!NOTE]
>
>如需各種Adobe Campaign程式的詳細資訊，請參閱 [本節](../../installation/using/general-architecture.md#logical-application-layer).\
>使用Power Booster或Power Cluster型別架構時，您必須將此程式套用至所有Power Booster/Cluster伺服器。

如果新版本涉及變更資料庫結構，我們建議依照下列順序重新啟動伺服器：

1. 應用程式伺服器(nlserver web)、
1. 重新導向伺服器(webmdl)、
1. 傳遞伺服器(nlserver mta)。
