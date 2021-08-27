---
product: campaign
title: 簡介
description: 簡介
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 3e39a0d2-ff7e-4233-82bb-2b360f696a33
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 1%

---

# 簡介{#introduction}

![](../../assets/v7-only.svg)

本節介紹要應用於升級Adobe Campaign、用戶端和伺服器端的程式，並說明現有執行個體的切換為Unicode。

>[!NOTE]
>
>對於托管例項，您必須與Adobe管理員協調。\
>若為內部部署例項，您可以取得Adobe顧問的協助。

升級必須套用至安裝Adobe Campaign的所有伺服器。

1. 遷移重定向和跟蹤伺服器(Apache/IIS)。
1. 遷移Power Booster/Cluster伺服器。
1. 移轉行銷伺服器。

Adobe Campaign以伺服器端執行的數個程式為基礎，在更新期間您需要處理這些程式，尤其是：

* 應用程式伺服器(nlserver web)
* 傳送伺服器(nlserver mta)
* 重定向伺服器(webmdl)

>[!CAUTION]
>
>用戶端主控台應與伺服器執行個體位於相同的組建。

>[!NOTE]
>
>如需各種Adobe Campaign程式的詳細資訊，請參閱[此區段](../../installation/using/general-architecture.md#logical-application-layer)。\
>使用Power Booster或Power Cluster類型架構時，必須將此過程應用於所有Power Booster/Cluster伺服器。

如果新版本涉及更改資料庫結構，建議按以下順序重新啟動伺服器：

1. 應用程式伺服器(nlserver web),
1. 重定向伺服器(webmdl),
1. 傳送伺服器(nlserver mta)。
