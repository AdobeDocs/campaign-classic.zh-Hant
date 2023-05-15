---
product: campaign
title: 開始移轉前
description: 開始移轉前
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# 必要條件{#before-starting-migration}



此頁面列出開始移轉程式之前要執行的特定步驟。 您也必須參考 [本頁](about-migration.md) 以取得更多指引。

>[!NOTE]
>
>在本文檔中，命令作為示例提供。 視您的設定而定。

1. 檢查您的Adobe Campaign版本：移轉之前，請安裝您目前使用之版本的最新組建版本。
1. 備份資料。
1. 檢查您的環境：不能更改資料庫引擎系統(DBMS)。 例如，您無法從PostgreSQL引擎切換到Oracle引擎。 不過，您可以切換至資料庫引擎的最新版本。 請注意，不能從非Unicode資料庫轉到Unicode資料庫。

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

>[!CAUTION]
>
>此 **內部** 所有追蹤伺服器的密碼必須相同。 如需詳細資訊，請參閱 [內部識別碼](../../installation/using/configuring-campaign-server.md#internal-identifier) 和 [權限](../../platform/using/access-management.md) 區段。
