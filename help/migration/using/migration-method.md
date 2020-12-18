---
solution: Campaign Classic
product: campaign
title: 移轉方法
description: 移轉方法
audience: migration
content-type: reference
topic-tags: migration-overview
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 1%

---


# 移轉方法{#migration-method}

## 對環境進行現代化{#modernizing-your-environment}

執行遷移是更新環境（資料庫引擎、作業系統）的機會。 Adobe Campaign強烈建議將生產環境升級至最新版本。

v7仍支援32位元版本的資料庫和作業系統，但Adobe Campaign未來版本將不再支援。 強烈建議您盡快將平台升級至64位元。

在v6.02中，「多時區」模式僅適用於PostgreSQL資料庫引擎。 現在，不論使用何種類型的資料庫引擎，都可提供此功能。 我們強烈建議您將您的基本系統轉換為「多時區」基本系統。 有關詳細資訊，請參閱[時區](../../migration/using/general-configurations.md#time-zones)部分。

>[!IMPORTANT]
>
>Adobe Campaign v7不再支援Adobe Campaign 5.11和6.02支援的部分軟體版本。
>
>如需Adobe Campaign支援版本的詳細資訊，請參閱[相容性矩陣](../../rn/using/compatibility-matrix.md)。

## 關鍵遷移步驟{#key-migration-steps}

移轉至Adobe Campaign v7的一般程式，請參閱[開始移轉](../../migration/using/before-starting-migration.md)一節。

移轉至Adobe Campaign v7的實施步驟，請參閱[移轉至Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md)一節的先決條件。

所需的配置取決於您現有的配置和平台的初始版本。 [General configurations](../../migration/using/general-configurations.md)一節中概述了這些配置。

## 特定配置{#specific-configurations}

Adobe Campaign v7所帶來的變更可能也意味著您必須調整舊版中開發的特定組態。 因此，在遷移之前，可能需要對所有配置執行審計：請連絡Adobe Campaign以取得任何協助。

例如，應特別注意Web應用程式的特定設定、具有SQLdata的架構擴展或現成可用的架構克隆。 有關詳細資訊，請參閱[配置平台](../../migration/using/configuring-your-platform.md)部分。

同樣地，為了回應Adobe Campaign內部安全性的提升，已修改部分內部機制：您必須調整這些對應的配置。
