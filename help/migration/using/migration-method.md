---
product: campaign
title: 移轉方法
description: 移轉方法
audience: migration
content-type: reference
topic-tags: migration-overview
exl-id: dd4d068b-f414-448f-8d9a-eedf44e7b6e6
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 1%

---

# 移轉方法{#migration-method}

![](../../assets/v7-only.svg)

## 最新化環境 {#modernizing-your-environment}

執行遷移是更新環境（資料庫引擎、作業系統）的機會。 Adobe Campaign強烈建議將生產環境升級至最新版本。

v7仍支援32位元版本資料庫和作業系統，但未來版本的Adobe Campaign將不再支援。 強烈建議您盡快將平台升級至64位元。

在v6.02中，「多時區」模式僅適用於PostgreSQL資料庫引擎。 現在，無論使用何種類型的資料庫引擎，都可提供此功能。 強烈建議您將基礎轉換為「多時區」基礎。 如需詳細資訊，請參閱 [時區](../../migration/using/general-configurations.md#time-zones) 區段。

>[!IMPORTANT]
>
>Adobe Campaign 5.11和6.02中支援的部分軟體版本不再支援Adobe Campaign v7。
>
>如需Adobe Campaign支援版本的詳細資訊，請參閱 [相容性矩陣](../../rn/using/compatibility-matrix.md).

## 重要移轉步驟 {#key-migration-steps}

移轉至Adobe Campaign v7的一般程式於 [開始移轉前](../../migration/using/before-starting-migration.md) 區段。

移轉至Adobe Campaign v7的實作步驟將於 [移轉至Adobe Campaign 7的必要條件](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) 區段。

所需的設定取決於您現有的設定和平台的初始版本。 這些概述於 [一般配置](../../migration/using/general-configurations.md) 區段。

## 特定配置 {#specific-configurations}

Adobe Campaign v7帶來的變更也可能意味著您必須調整在舊版中開發的特定設定。 因此，在移轉前，可能需要對所有設定執行稽核：請聯絡Adobe Campaign以取得任何協助。

例如，應特別注意Web應用程式的特定設定、具有SQLdata的架構擴展或現成的架構克隆。 如需詳細資訊，請參閱 [設定您的平台](../../migration/using/configuring-your-platform.md) 區段。

同樣，為了應對Adobe Campaign內加強的安全，一些內部機制也作了修改：您必須調整這些對應的設定。
