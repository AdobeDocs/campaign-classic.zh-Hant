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



記錄檔的組織方式如下：

![](assets/d_ncs_directory.png)

每個 **nlserver** 模組會產生儲存在下列目錄中的記錄檔： **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

此 **nlserver syslogd** 模組會將記錄檔儲存至磁碟。 此模組類似於Unix **syslog精靈**，但已針對Unix和Windows之間的相容性進行了調整。 其他Adobe Campaign模組不會將其記錄檔儲存至磁碟，而是將此任務委派給 **syslogd** 模組，透過傳送UDP封包進行傳送。

依預設，Adobe Campaign平台具有 **syslogd** 已安裝模組，但可以使用另一個 **syslog精靈**. 此模組會在以下位置建立記錄檔： **記錄** 目錄。

多執行個體模組的記錄會儲存在下列目錄中： **`<installation directory>`/var/default/log/**. 所有執行個體會共用相同的記錄檔(例如 **web.log**)。

其他模組的記錄會儲存在以執行個體命名的子資料夾中。 每個執行個體都有自己的記錄檔。

下表列出多執行處理記錄檔：

| 檔案 | 說明 |
|---|---|
| web.log | Web模組記錄（使用者端主控台、報表、SOAP API等） |
| webmdl.log | 來自重新導向模組的記錄 |
| watchdog.log | Adobe Campaign程式監控模組的記錄 |
| trackinglogd.log | 追蹤記錄 |

下表列出單一執行處理記錄檔：

| 檔案 | 說明 |
|---|---|
| mta.log | mta模組記錄 |
| mtachild.log | 訊息傳遞處理記錄 |
| wfserver.log | 工作流程伺服器模組的記錄 |
| runwf.log | 工作流程執行記錄 |
| inMail.log | 退回郵件模組記錄 |
| logins.log | 記錄對Adobe Campaign的所有登入嘗試（成功與否） |

>[!IMPORTANT]
>
>此 **重新導向** 目錄僅存在於重新導向伺服器上。 此 **url** 子目錄包含要重新導向之URL的相符專案，以及子目錄 **記錄** 包含追蹤記錄。 若要產生追蹤記錄，請 **trackinglogd** 模組必須執行中。

為了達到效能和儲存最佳化，logins.log檔案會分割成多個檔案，每天一個(logins.yy-mm-dd.log)，最多保留365個檔案。 天數可以在serverConf.xml中變更，在syslogd (**maxNumberOfLoginsFiles** 選項)。 請參閱以下說明檔案： [伺服器設定檔](../../installation/using/the-server-configuration-file.md#syslogd).

依預設，每個模組和執行個體的記錄檔上限為兩個10 MB檔案。 第二個檔案名為： **`<modulename>`_2.log**. 因此，記錄檔的大小限製為2&#42;每個模組及每個執行個體為10MB。

不過，您可以保留較大的檔案。 若要啟用此功能，請變更 **maxFileSizeMb=&quot;10&quot;** 在中設定 **syslogd** 的節點 **conf/serverConf.xml** 檔案。 此值代表記錄檔的大小上限（以MB為單位）。

如果您想在記錄中保留更詳細的層級，可以使用啟動Adobe Campaign模組 **-verbose** 引數：

**nlserver start `<MODULE>`@`<INSTANCE>` -verbose**
