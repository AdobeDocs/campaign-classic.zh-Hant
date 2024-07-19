---
product: campaign
title: 開始移轉前
description: 開始移轉前
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# 先決條件{#before-starting-migration}



此頁面列出開始移轉程式之前要執行的特定步驟。 如需詳細指引，您也必須參考[此頁面](about-migration.md)。

>[!NOTE]
>
>在本檔案中，指令以範例形式提供。 其可能會因您的設定而異。

1. 檢查您的Adobe Campaign版本：在移轉之前，請安裝您使用的最新版組建版本。
1. 備份您的資料。
1. 檢查您的環境：您無法變更您的資料庫引擎系統(DBMS)。 例如，您無法從PostgreSQL引擎切換至Oracle引擎。 不過，您可以切換至資料庫引擎的最新版本。 請注意，無法從非Unicode資料庫移至Unicode資料庫。

## 移轉步驟 {#migration-steps}

移轉程式必須在&#x200B;**所有**&#x200B;伺服器上以特定順序執行。

* 在&#x200B;**獨立平台** （單一電腦模式）的情況下，應用程式會完整移轉。
* 在&#x200B;**標準平台** （企業）的情況下，移轉步驟如下：

   1. 移轉行銷伺服器。
   1. 移轉郵件伺服器(mta)。
   1. 移轉重新導向與追蹤伺服器(Apache / IIS)。

* 在&#x200B;**雲端傳訊平台**&#x200B;中，執行伺服器是在Adobe Campaign上託管。 請聯絡Adobe Campaign協調不同伺服器之間的移轉。
* 在&#x200B;**Power Booster或Power Cluster平台**&#x200B;的情況下，移轉步驟如下：

   1. 移轉重新導向與追蹤伺服器(Apache / IIS)。
   1. 移轉Power Booster/Cluster伺服器。
   1. 移轉行銷伺服器。

## 使用者密碼 {#user-passwords}

在v7中，**內部**&#x200B;和&#x200B;**管理員**&#x200B;操作員連線必須以密碼保護。 強烈建議在移轉前&#x200B;**指派密碼給這些帳戶及所有操作員帳戶**。 如果您尚未指定&#x200B;**內部**&#x200B;的密碼，將無法連線。 若要指派密碼給&#x200B;**內部**，請輸入下列命令：

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>所有追蹤伺服器的&#x200B;**內部**&#x200B;密碼必須相同。 如需詳細資訊，請參閱[內部識別碼](../../installation/using/configuring-campaign-server.md#internal-identifier)和[許可權](../../platform/using/access-management.md)區段。
