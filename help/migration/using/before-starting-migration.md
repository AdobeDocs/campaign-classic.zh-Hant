---
title: 開始移轉前
description: 開始移轉前
page-status-flag: never-activated
uuid: b9325510-2fa5-4be4-9cf0-f37232bbbd8c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: d8877378-fb43-4f32-91c6-60f2f788f916
translation-type: tm+mt
source-git-commit: 99d766cb6234347ea2975f3c08a6ac0496619b41
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 1%

---


# 開始移轉前{#before-starting-migration}

>[!NOTE]
>
>在本文檔中，以示例形式給出了連結到資料庫的命令。 這些值可能因其配置而異。 請連絡您的資料庫管理員。

## 警告 {#warnings}

* 移轉程式只能由專家使用者執行。 您至少必須有Adobe Campaign的資料庫專家、系統管理員和應用程式開發人員協助。
* 開始移轉之前，請先檢查您使用的系統和系統元件是否與v7相容。 請參閱相 [容性矩陣](../../rn/using/compatibility-matrix.md)。
* 如果您使用Adobe Campaign Cloud訊息（中部採購），請在開始整個移轉程式之前先與Adobe聯絡。
* 在開始移轉程式之前，您 **必須** 備份您的資料。
* 移轉程式可能需要數天才能完成。
* Adobe Campaign v7在組態上比5.11和6.02版更嚴格。 這主要是為了避免資料損毀等問題，並保留資料庫中的資料完整性。 因此，v5.11和v6.02中提供的某些功能在v7中可能不再起作用，因此在遷移後可能需要調整。 在投入生產之前，我們建議您系統性地測試所有組態，尤其是使用Adobe Campaign所需的工作流程。

### 已安裝版本 {#installed-version}

在移轉之前，您應安裝目前使用之最新版本。

使用nlserver pdump命令轉到客戶端控 **[!UICONTROL Help> About]** 制台上的菜單，檢查服 **務器上的版本** 。

### 資料備份 {#data-backup}

在開始移轉程式之前，您 **必須** 備份您的資料。

### 環境 {#environment}

* 無法更改資料庫引擎類型(DBMS)。 例如，不能從PostgreSQL引擎切換到Oracle引擎。 但是，您可以從Oracle 8引擎切換到Oracle 10引擎。
* 無法從非Unicode資料庫轉換為Unicode資料庫。

### 建議 {#recommendation}

由於移轉程式很敏感，我們強烈建議在開始此程式之前先徹底閱讀本檔案。

## 移轉步驟 {#migration-steps}

遷移過程必須在所有伺服器 **上** ，並且按特定順序執行。

* 如果是獨立平台 **** （單機器模式），則會完整移轉應用程式。
* 對於標準平 **台** （企業），遷移步驟如下：

   1. 移轉行銷伺服器。
   1. 遷移郵件伺服器(mta)。
   1. 移轉重新導向和追蹤伺服器(Apache / IIS)。

* 如果是雲端傳訊平 **台**，執行伺服器會裝載在Adobe Campaign。 請連絡Adobe Campaign以協調不同伺服器之間的移轉。
* 在Power Booster或 **Power Cluster平台中**，遷移步驟如下：

   1. 移轉重新導向和追蹤伺服器(Apache / IIS)。
   1. 遷移Power Booster/Cluster伺服器。
   1. 移轉行銷伺服器。

## 使用者密碼 {#user-passwords}

在v7中，內 **部** 和管 **理員運** 算子連線必須以密碼保全。 我們強烈建議在移轉之前，先為這些帳戶和所有運算元帳戶指 **派密碼**。 如果您未為內部指定 **密碼**，將無法連接。 要為內部分配密 **碼**，請輸入以下命令：

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>所有 **追蹤伺服器** 的內部密碼必須相同。 如需詳細資訊，請參閱「內部識 [別碼](../../installation/using/campaign-server-configuration.md#internal-identifier) 」和「 [關於權限](../../platform/using/access-management.md#about-permissions) 」區段。

