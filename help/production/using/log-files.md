---
product: campaign
title: 記錄檔案
description: 記錄檔案
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 2%

---

# 記錄檔案{#log-files}



日誌檔案的組織方式如下：

![](assets/d_ncs_directory.png)

每個 **nlserver** module生成保存在以下目錄中的日誌檔案： **`<installation directory>`/var/`<instance>`/log/`<module>`.日誌**。

的 **nlserver syslogd** 模組將日誌保存到磁碟。 此模組與Unix類似 **syslog守護程式**，但是已針對Unix和Windows之間的相容性進行了調整。 其他Adobe Campaign模組不會將日誌保存到磁碟；他們將此任務委派給 **syslog** 模組通過發送UDP資料包。

預設情況下，Adobe Campaign平台 **syslog** 已安裝模組，但可以使用 **syslog守護程式**。 此模組在 **日誌** 的子菜單。

多實例模組的日誌儲存在以下目錄中： **`<installation directory>`/var/default/log////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////**。 同一日誌檔案由所有實例共用(例如 **web.log**)。

其他模組的日誌儲存在以實例命名的子資料夾中。 每個實例都有其自己的日誌檔案。

下表列出了多實例日誌檔案：

| 檔案 | 說明 |
|---|---|
| web.log | Web模組日誌（客戶端控制台、報告、SOAP API等） |
| webmdl.log | 重定向模組中的日誌 |
| watchdog.log | Adobe Campaign進程監測模組的日誌 |
| trackinglogd.log | 追蹤記錄 |

下表列出了單實例日誌檔案：

| 檔案 | 說明 |
|---|---|
| mta.log | mta模組日誌 |
| mtachild.log | 消息傳遞處理日誌 |
| wfserver.log | 工作流伺服器模組的日誌 |
| runwf.log | 工作流執行日誌 |
| inMail.log | 彈出郵件模組日誌 |
| logins.log | 記錄所有登錄嘗試到Adobe Campaign（成功與否） |

>[!IMPORTANT]
>
>的 **重定向** 目錄僅存在於重定向伺服器上。 的 **url** 子目錄包含要重定向的URL和子目錄的匹配項 **日誌** 包含跟蹤日誌。 要生成跟蹤日誌， **跟蹤日誌** 模組必須正在運行。

為了效能和儲存優化， logins.log檔案被拆分為多個檔案，每天一個(logins.yy-mm-dd.log)，最多保留365個檔案。 serverConf.xml中syslogd(**maxNumberOfLoginsFiles** 選項。 請參閱 [伺服器配置檔案](../../installation/using/the-server-configuration-file.md#syslogd)。

預設情況下，每個模組和每個實例的日誌限制為兩個10 MB的檔案。 第二個檔案稱為： **`<modulename>`_2.log**。 因此，日誌的大小限制為2&#42;每個模組和每個實例10MB。

但是，您可以保留較大的檔案。 要啟用此功能，請更改 **maxFileSizeMb=&quot;10&quot;** 的 **syslog** 節點 **conf/serverConf.xml** 的子菜單。 此值表示日誌檔案的最大大小(MB)。

如果希望在日誌中保留更多詳細級別，可以使用 **— 詳細** 參數：

**nlserver啟動 `<MODULE>`@`<INSTANCE>`  — 詳細**
