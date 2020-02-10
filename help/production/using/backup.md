---
title: 備份
seo-title: 備份
description: 備份
seo-description: null
page-status-flag: never-activated
uuid: 50134154-a671-4534-b48d-a9e2c42e8f1a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 870ab0f2-1bd7-42e7-8d83-a08a520b6587
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a11a73b0679c0a65dc10f71869bf2a6c6efc008

---


# 備份{#backup}

備份是避免在電腦發生問題（無論是物理問題還是與系統相關）時丟失資料的關鍵。

資料會儲存在兩個不同的位置：

* 實體檔案會儲存在Adobe Campaign目錄中，
* 其他資料儲存在資料庫中。

大部分資料都在資料庫中。 這佔要備份資訊的99%。

## 物理檔案 {#physical-files}

檔案可分為幾類：

* 配置檔案，位 **於nl6/conf**

   這些功能可讓您迅速重新設定Adobe Campaign。

* 重定向檔案** nl6/var/`<instancename>`/redir**

   這些位於追蹤（通常稱為「正面」）伺服器上，並包含所有先前的促銷活動重新導向。 舊版促銷活動仍會使用它們。

* 日誌檔案： **nl6/var/`<instancename>`/log**

   這些可用於跟蹤問題。

因此，要備份的目錄包括：

* nl6/conf

* nl6/var/`<instanceName>`/redir（用於每個實例）

* nl6/var/`<instanceName>`/log（可選）

* nl6/var/`<instanceName>`/relay（可選）

>[!CAUTION]
>
>備份資料庫至關重要。

## 資料庫 {#database}

資料庫包含Adobe Campaignrich client主控台中顯示的所有資訊，以及所有業務線資料。

您的代管公司，尤其是其資料庫管理員，負責此項作業。
