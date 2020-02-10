---
title: 遷移方法
seo-title: 遷移方法
description: 遷移方法
seo-description: null
page-status-flag: never-activated
uuid: 6b954d5b-cfa3-43c6-ac3d-da9185e9e9d1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-overview
discoiquuid: 3ac779a7-1f91-4c1c-a439-10d01697326a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4437d2ea4e4044245a2b9a5a870267cd1f1c0bc9

---


# 遷移方法{#migration-method}

## 現代化您的環境 {#modernizing-your-environment}

執行遷移是更新環境（資料庫引擎、作業系統）的機會。 Adobe Campaign強烈建議將生產環境升級至最新版本。

v7仍支援32位元版本的資料庫和作業系統，但Adobe Campaign未來版本將不再支援。 強烈建議您盡快將平台升級至64位元。

在v6.02中，「多時區」模式僅適用於PostgreSQL資料庫引擎。 現在，不論使用何種類型的資料庫引擎，都可提供此功能。 我們強烈建議您將您的基本系統轉換為「多時區」基本系統。 有關詳細資訊，請參閱時 [區部分](../../migration/using/general-configurations.md#time-zones) 。

>[!CAUTION]
>
>Adobe Campaign v7不再支援Adobe Campaign 5.11和6.02支援的部分軟體版本。
>
>如需Adobe Campaign支援版本的詳細資訊，請參閱相容性 [表](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。

## 關鍵移轉步驟 {#key-migration-steps}

移轉至Adobe Campaign v7的一般程式，請參閱「開始移轉之 [前」一節](../../migration/using/before-starting-migration.md) 。

移轉至Adobe Campaign v7的實施步驟詳見移 [轉至Adobe Campaign 7的先決條件](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) 。

所需的配置取決於您現有的配置和平台的初始版本。 這些在「常規配置」 [部分中概述](../../migration/using/general-configurations.md) 。

## 特定配置 {#specific-configurations}

Adobe Campaign v7所帶來的變更可能也意味著您必須調整舊版中開發的特定組態。 因此，在遷移之前，可能需要對所有配置執行審計：請連絡Adobe Campaign以取得任何協助。

例如，應特別注意Web應用程式的特定設定、具有SQLdata的架構擴展或現成可用的架構克隆。 如需詳細資訊，請參閱「設 [定平台](../../migration/using/configuring-your-platform.md) 」一節。

同樣地，為了回應Adobe Campaign內部安全性的提升，已修改部分內部機制：您必須調整這些對應的配置。
