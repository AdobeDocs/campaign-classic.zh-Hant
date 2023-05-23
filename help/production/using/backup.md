---
product: campaign
title: 備份
description: 備份
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 2%

---

# 備份{#backup}

備份是避免在電腦上出現問題（無論是與物理或系統相關）時丟失資料的關鍵。

資料儲存在兩個不同的位置：

* 物理檔案被儲存在Adobe Campaign目錄，
* 其他資料儲存在資料庫中。

大部分資料都在資料庫中。 這表示要備份的資訊的99%。

## 物理檔案 {#physical-files}

檔案分為幾類：

* 配置檔案，儲存在 **nl6/conf**，使您能夠快速重新配置Adobe Campaign。

* 重定向檔案，儲存在  **nl6/var`<instance-name>`/redir**，位於跟蹤（通常稱為「前面」）伺服器上，並包括以前的所有活動重定向。 它們仍被以前的活動使用。

* 日誌檔案，儲存在 **nl6/var`<instance-name>`/日誌**，可用於跟蹤問題。

因此，要備份的目錄如下：

* nl6/conf

* nl6/var`<instance-name>`/redir（針對每個實例）

* nl6/var`<instance-name>`/log（可選）

* nl6/var`<instance-name>`/relay（可選）


## 資料庫 {#database}

>[!IMPORTANT]
>
>必須備份資料庫。


資料庫包含Adobe Campaign富客戶端控制台中顯示的所有資訊以及所有業務線資料。

您的托管公司，尤其是其資料庫管理員，負責此操作。
