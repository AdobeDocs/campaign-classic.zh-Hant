---
product: campaign
title: 記錄檔案
description: 記錄檔案
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 4%

---

# 記錄檔案{#log-files}



記錄檔的組織方式如下：

![](assets/d_ncs_directory.png)

每個 **nlserver** 模組會產生儲存在下列目錄中的記錄檔： **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

此 **nlserver syslogd** 模組會將記錄檔儲存至磁碟。 此模組類似於Unix **syslog精靈**，但已針對Unix和Windows之間的相容性進行調整。 其他Adobe Campaign模組不會將其記錄檔儲存至磁碟，而是將此任務委派至 **syslogd** 模組（透過傳送UDP封包）。

依預設，Adobe Campaign平台具有 **syslogd** 已安裝模組，但可以使用另一個 **syslog精靈**. 此模組會在以下位置建立記錄檔： **記錄** 目錄。

多執行個體模組的記錄會儲存在下列目錄中： **`<installation directory>`/var/default/log/**. 所有執行個體會共用相同的記錄檔(例如 **web.log**)。

其他模組的記錄會儲存在以執行個體命名的子資料夾中。 每個執行個體都有自己的記錄檔。

下表列出多執行處理記錄檔：

| 檔案 | 說明 |
|---|---|
| web.log | Web模組記錄（使用者端主控台、報表、SOAP API等） |
| webmdl.log | 來自重新導向模組的記錄 |
| watchdog.log | Adobe Campaign流程監視模組的記錄 |
| trackinglogd.log | 追蹤記錄 |

下表列出單一執行處理記錄檔：

| 檔案 | 說明 |
|---|---|
| mta.log | mta模組記錄 |
| mtachild.log | 訊息傳遞處理記錄 |
| wfserver.log | 工作流程伺服器模組的記錄 |
| runwf.log | 工作流程執行記錄 |
| inMail.log | 退回郵件模組記錄 |
| logins.log | 將所有登入嘗試記錄到Adobe Campaign （成功與否） |

>[!IMPORTANT]
>
>此 **重新導向** 目錄僅存在於重新導向伺服器上。 此 **url** 子目錄包含要重新導向之URL的相符專案，以及子目錄 **記錄** 包含追蹤記錄。 若要產生追蹤記錄，請 **trackinglogd** 模組必須執行中。

為了達到效能和儲存最佳化，logins.log檔案會分割成多個檔案，每天一個(logins.yy-mm-dd.log)，最多保留365個檔案。 在serverConf.xml中，您可以在syslogd (**maxNumberOfLoginsFiles** 選項)。 請參閱相關的檔案： [伺服器設定檔](../../installation/using/the-server-configuration-file.md#syslogd).

依預設，每個模組和每個執行個體限製為兩個10 MB的檔案。 第二個檔案稱為： **`<modulename>`_2.log**. 因此，記錄檔的大小限製為2&#42;每個模組及每個執行個體各10MB。

不過，您可以保留較大的檔案。 若要啟用此功能，請變更 **maxFileSizeMb=&quot;10&quot;** 在中設定 **syslogd** 的節點 **conf/serverConf.xml** 檔案。 此值代表記錄檔的大小上限（以MB為單位）。

如果您想在記錄中保留更詳細的層級，您可以透過以下啟動Adobe Campaign模組 **-verbose** 引數：

**nlserver start `<MODULE>`@`<INSTANCE>` -verbose**
