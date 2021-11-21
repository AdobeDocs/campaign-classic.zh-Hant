---
product: campaign
title: 開始移轉前
description: 開始移轉前
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 1%

---

# 開始移轉前{#before-starting-migration}

![](../../assets/v7-only.svg)

>[!NOTE]
>
>在本文檔中，以示例形式提供了連結到資料庫的命令。 視其設定而定，這些變數可能會有所不同。 請與資料庫管理員聯繫。

## 警告 {#warnings}

* 移轉程式只能由專家使用者執行。 您至少必須得到Adobe Campaign的資料庫專家、系統管理員和應用程式開發人員的協助。
* 開始移轉之前，請先檢查您使用的系統和系統元件是否實際與v7相容。 請參閱 [相容性矩陣](../../rn/using/compatibility-matrix.md).
* 如果您使用Adobe Campaign雲端訊息（中間來源），請先聯絡Adobe，再開始整個移轉程式。
* 開始移轉程式前，請 **必須** 備份資料。
* 移轉程式可能需要數天才能完成。
* Adobe Campaign v7的設定比5.11和6.02版更嚴格。 這主要是為了避免資料損壞等問題，並維護資料庫中的資料完整性。 因此，v5.11和v6.02中提供的某些功能在v7中可能不再有效，因此在遷移後可能需要調整。 在投入生產之前，建議您系統性測試所有設定，尤其是使用Adobe Campaign所需的工作流程。

### 已安裝版本 {#installed-version}

移轉之前，您應安裝目前使用之版本的最新組建。

前往 **[!UICONTROL Help> About]** 功能表(使用 **nlserver pdump** 命令。

### 資料備份 {#data-backup}

開始移轉程式前，請 **必須** 備份資料。

### 環境 {#environment}

* 無法更改資料庫引擎類型(DBMS)。 例如，您無法從PostgreSQL引擎切換到Oracle引擎。 不過，您可以從Oracle8引擎切換為Oracle10引擎。
* 無法從非Unicode資料庫轉到Unicode資料庫。

### 建議 {#recommendation}

由於移轉程式非常敏感，因此強烈建議您在開始此程式之前先徹底閱讀本檔案。

## 移轉步驟 {#migration-steps}

必須執行移轉程式 **all** 伺服器和特定順序。

* 若 **獨立平台** （單機模式），則應用程式將完全遷移。
* 若 **標準平台** （企業），移轉步驟如下：

   1. 移轉行銷伺服器。
   1. 遷移郵件伺服器(mta)。
   1. 遷移重定向和跟蹤伺服器(Apache / IIS)。

* 若 **雲端訊息平台**，則執行伺服器會托管於Adobe Campaign。 請連絡Adobe Campaign以協調不同伺服器之間的移轉。
* 若 **Power Booster或Power Cluster平台**，移轉步驟如下：

   1. 遷移重定向和跟蹤伺服器(Apache / IIS)。
   1. 遷移Power Booster/Cluster伺服器。
   1. 移轉行銷伺服器。

## 用戶密碼 {#user-passwords}

在v7中， **內部** 和 **管理員** 操作員連接必須用密碼保護。 強烈建議為這些帳戶和所有運算子帳戶分配密碼， **移轉前**. 如果您尚未為 **內部**，您將無法連線。 要將密碼分配給 **內部**，輸入以下命令：

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>此 **內部** 所有追蹤伺服器的密碼必須相同。 如需詳細資訊，請參閱 [內部識別碼](../../installation/using/configuring-campaign-server.md#internal-identifier) 和 [權限](../../platform/using/access-management.md) 區段。
