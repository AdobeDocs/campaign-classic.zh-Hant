---
product: campaign
title: 備份
description: 備份
feature: Monitoring
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 2%

---

# 備份{#backup}

若要避免在電腦上發生問題（無論是實體或系統相關問題）時遺失資料，備份是必要的。

資料會儲存在兩個不同的位置：

* 實體檔案儲存在Adobe Campaign目錄中，
* 其他資料則儲存在資料庫中。

大部分的資料都在資料庫中。 這代表要備份的99%資訊。

## 實體檔案 {#physical-files}

檔案分為幾個類別：

* 組態檔，儲存在 **nl6/conf**，讓您快速重新設定Adobe Campaign。

* 重新導向檔案，儲存在  **nl6/var/`<instance-name>`/redir**，位於追蹤（通常稱為「正面」）伺服器上，且包含所有先前的促銷活動重新導向。 仍由先前的行銷活動使用。

* 記錄檔，儲存在 **nl6/var/`<instance-name>`/log**，可用來追蹤問題。

因此，要備份的目錄為：

* nl6/conf

* nl6/var/`<instance-name>`/redir （適用於每個執行個體）

* nl6/var/`<instance-name>`/log （選擇性）

* nl6/var/`<instance-name>`/relay （選擇性）


## 資料庫 {#database}

>[!IMPORTANT]
>
>必須備份資料庫。


此資料庫包含Adobe Campaign豐富型使用者端主控台中顯示的所有資訊，以及所有企業營運資料。

您的託管公司（尤其是其資料庫管理員）應負責此作業。
