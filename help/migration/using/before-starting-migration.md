---
product: campaign
title: 開始移轉前
description: 開始移轉前
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 1%

---

# 開始移轉前{#before-starting-migration}

>[!NOTE]
>
>在本文檔中，以示例形式提供了連結到資料庫的命令。 視其設定而定，這些變數可能會有所不同。 請與資料庫管理員聯繫。

## 警告 {#warnings}

* 移轉程式只能由專家使用者執行。 您至少必須得到Adobe Campaign的資料庫專家、系統管理員和應用程式開發人員的協助。
* 開始移轉之前，請先檢查您使用的系統和系統元件是否實際與v7相容。 請參閱[相容性矩陣](../../rn/using/compatibility-matrix.md)。
* 如果您使用Adobe Campaign雲端訊息（中間來源），請先聯絡Adobe，再開始整個移轉程式。
* 開始移轉程式之前，您&#x200B;**必須**&#x200B;備份資料。
* 移轉程式可能需要數天才能完成。
* Adobe Campaign v7的設定比5.11和6.02版更嚴格。 這主要是為了避免資料損壞等問題，並維護資料庫中的資料完整性。 因此，v5.11和v6.02中提供的某些功能在v7中可能不再有效，因此在遷移後可能需要調整。 在投入生產之前，建議您系統性測試所有設定，尤其是使用Adobe Campaign所需的工作流程。

### 已安裝版本{#installed-version}

移轉之前，您應安裝目前使用之版本的最新組建。

使用&#x200B;**nlserver pdump**&#x200B;命令，前往用戶端主控台上的&#x200B;**[!UICONTROL Help> About]**&#x200B;功能表，檢查伺服器上的版本。

### 資料備份{#data-backup}

開始移轉程式之前，您&#x200B;**必須**&#x200B;備份資料。

### 環境 {#environment}

* 無法更改資料庫引擎類型(DBMS)。 例如，您無法從PostgreSQL引擎切換到Oracle引擎。 不過，您可以從Oracle8引擎切換為Oracle10引擎。
* 無法從非Unicode資料庫轉到Unicode資料庫。

### 建議 {#recommendation}

由於移轉程式非常敏感，因此強烈建議您在開始此程式之前先徹底閱讀本檔案。

## 遷移步驟{#migration-steps}

遷移過程必須在&#x200B;**all**&#x200B;伺服器上按特定順序執行。

* 在&#x200B;**獨立平台**（單機模式）的情況下，應用程式將完全遷移。
* 若是&#x200B;**標準平台**（企業版），則移轉步驟如下：

   1. 移轉行銷伺服器。
   1. 遷移郵件伺服器(mta)。
   1. 遷移重定向和跟蹤伺服器(Apache / IIS)。

* 若為&#x200B;**雲端傳訊平台**，執行伺服器會托管於Adobe Campaign。 請連絡Adobe Campaign以協調不同伺服器之間的移轉。
* 若是&#x200B;**Power Booster或Power Cluster平台**，則遷移步驟如下：

   1. 遷移重定向和跟蹤伺服器(Apache / IIS)。
   1. 遷移Power Booster/Cluster伺服器。
   1. 移轉行銷伺服器。

## 用戶密碼{#user-passwords}

在v7中，**internal**&#x200B;和&#x200B;**admin**&#x200B;運算子連接必須用密碼保護。 強烈建議在遷移&#x200B;**之前為這些帳戶和所有運算子帳戶分配密碼，**。 如果尚未為&#x200B;**internal**&#x200B;指定密碼，則無法連接。 要將密碼分配給&#x200B;**internal**，請輸入以下命令：

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>所有追蹤伺服器的&#x200B;**內部**&#x200B;密碼必須相同。 如需詳細資訊，請參閱[內部識別碼](../../installation/using/configuring-campaign-server.md#internal-identifier)和[權限](../../platform/using/access-management.md)區段。
