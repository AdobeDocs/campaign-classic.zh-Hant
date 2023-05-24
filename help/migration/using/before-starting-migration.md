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



此頁面列出開始移轉程式之前要執行的特定步驟。 您亦須參考 [此頁面](about-migration.md) 以取得更多指引。

>[!NOTE]
>
>在本檔案中，指令以範例形式提供。 其可能會因您的設定而異。

1. 檢查您的Adobe Campaign版本：在移轉之前，請安裝您目前使用的最新組建版本。
1. 備份您的資料。
1. 檢查環境：您無法變更資料庫引擎系統(DBMS)。 例如，您無法從PostgreSQL引擎切換至Oracle引擎。 不過，您可以切換至資料庫引擎的最新版本。 請注意，無法從非Unicode資料庫移至Unicode資料庫。

## 移轉步驟 {#migration-steps}

移轉程式必須在 **全部** 伺服器和特定順序。

* 若是 **獨立平台** （單一電腦模式），應用程式會整體移轉。
* 若是 **標準平台** （企業），移轉步驟如下：

   1. 移轉行銷伺服器。
   1. 移轉郵件伺服器(mta)。
   1. 移轉重新導向和追蹤伺服器(Apache / IIS)。

* 若是 **Cloud Messaging平台**，執行伺服器託管於Adobe Campaign。 請聯絡Adobe Campaign協調不同伺服器之間的移轉。
* 若是 **Power Booster或Power Cluster平台**，移轉步驟如下：

   1. 移轉重新導向和追蹤伺服器(Apache / IIS)。
   1. 移轉Power Booster/Cluster伺服器。
   1. 移轉行銷伺服器。

## 使用者密碼 {#user-passwords}

在v7中， **內部** 和 **管理員** 操作員連線必須以密碼保護。 我們強烈建議指派密碼給這些帳戶和所有操作員帳戶， **移轉前**. 如果您尚未指定密碼 **內部**，您將無法連線。 若要將密碼指派給 **內部**，輸入下列命令：

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>此 **內部** 所有追蹤伺服器的密碼必須相同。 如需詳細資訊，請參閱 [內部識別碼](../../installation/using/configuring-campaign-server.md#internal-identifier) 和 [許可權](../../platform/using/access-management.md) 區段。
