---
product: campaign
title: 備份
description: 備份
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 4b13e310fcee9ba24e83b697fca57bc494505642
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 2%

---

# 備份{#backup}

備份是避免在電腦上出現問題（無論是物理或系統相關）時丟失資料的關鍵。

資料儲存在兩個不同的位置：

* 物理檔案儲存在Adobe Campaign目錄中，
* 其他資料儲存在資料庫中。

大部分資料都在資料庫中。 這表示要備份的資訊的99%。

## 物理檔案 {#physical-files}

檔案分為幾類：

* 組態檔，儲存於 **nl6/conf**，可讓您快速重新設定Adobe Campaign。

* 重定向檔案，儲存於  **nl6/var/`<instance-name>`/redir**，位於追蹤（通常稱為「前沿」）伺服器上，且包含先前所有的促銷活動重新導向。 它們仍用於先前的促銷活動。

* 記錄檔，儲存於 **nl6/var/`<instance-name>`/log**，可用來追蹤問題。

因此，要備份的目錄包括：

* nl6/conf

* nl6/var/`<instance-name>`/redir（針對每個實例）

* nl6/var/`<instance-name>`/log（可選）

* nl6/var/`<instance-name>`/relay（可選）


## 資料庫 {#database}

>[!IMPORTANT]
>
>必須備份資料庫。


資料庫包含Adobe Campaign rich client主控台中顯示的所有資訊，以及所有業務線資料。

您的托管公司，尤其是其資料庫管理員，負責此操作。
