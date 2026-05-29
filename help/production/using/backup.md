---
product: campaign
title: 備份
description: 備份
feature: Monitoring
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
TQID: https://experienceleague.adobe.com/ZCExecNbs9DnWVoQLpvzlrH7k2eGhBNq7pEiybyQdi4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616a
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 232
ht-degree: 9%

---

# 備份{#backup}

若要避免在電腦上發生問題（無論是實體或系統相關問題）時遺失資料，備份是必要的。

資料會儲存在兩個不同的位置：

* 實體檔案儲存在Adobe Campaign目錄中，
* 其他資料則儲存在資料庫中。

大部分的資料都在資料庫中。 這代表要備份的99%資訊。

## 實體檔案 {#physical-files}

檔案分為幾個類別：

* 組態檔（儲存在&#x200B;**nl6/conf**&#x200B;中）可讓您快速重新設定Adobe Campaign。

* 儲存在&#x200B;**nl6/var/`<instance-name>`/redir**&#x200B;中的重新導向檔案位於追蹤（通常稱為「正面」）伺服器上，且包含所有先前的行銷活動重新導向。 仍由先前的行銷活動使用。

* 儲存在&#x200B;**nl6/var/`<instance-name>`/log**&#x200B;中的記錄檔可用於追蹤問題。

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
