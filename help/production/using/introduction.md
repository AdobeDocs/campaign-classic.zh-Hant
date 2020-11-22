---
solution: Campaign Classic
product: campaign
title: 簡介
description: 簡介
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 1%

---


# 簡介{#introduction}

本節說明升級Adobe Campaign、用戶端和伺服器端的程式，並說明將現有執行個體轉換為Unicode的程式。

>[!NOTE]
>
>對於代管例項，您必須與Adobe管理員協調。\
>若是內部部署例項，您可以從Adobe顧問獲得協助。

升級必須套用至安裝Adobe Campaign的所有伺服器。

1. 移轉重新導向和追蹤伺服器(Apache/IIS)。
1. 遷移Power Booster/Cluster伺服器。
1. 移轉行銷伺服器。

Adobe Campaign是以伺服器端執行的數個程式為基礎，您在更新期間需要控制這些程式，尤其是：

* 應用程式伺服器(nlserver web)
* 傳送伺服器(nlserver mta)
* 重定向伺服器(webmdl)

>[!NOTE]
>
>如需各種Adobe Campaign程式的詳細資訊，請參 [閱本節](../../installation/using/general-architecture.md#logical-application-layer)。\
>使用Power Booster或Power Cluster類型體系結構時，必須將此過程應用於所有Power Booster/Cluster伺服器。

如果新版本涉及更改資料庫結構，建議按以下順序重新啟動伺服器：

1. 應用程式伺服器(nlserver web)、
1. 重定向伺服器(webmdl),
1. 傳送伺服器(nlserver mta)。

