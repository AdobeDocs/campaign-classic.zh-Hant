---
product: campaign
title: 記錄檔案
description: 記錄檔案
feature: Monitoring
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 2%

---

# 記錄檔案{#log-files}



記錄檔的組織方式如下：

![](assets/d_ncs_directory.png)

每個&#x200B;**nlserver**&#x200B;模組會產生儲存在下列目錄中的記錄檔： **`<installation directory>`/var/`<instance>`/log/`<module>`.log**。

**nlserver syslogd**&#x200B;模組會將記錄檔儲存至磁碟。 此模組類似於Unix **syslog常駐程式**，但已針對Unix與Windows之間的相容性進行調整。 其他Adobe Campaign模組不會將記錄檔儲存至磁碟；它們會傳送UDP封包將此工作委派給&#x200B;**syslogd**&#x200B;模組。

依預設，Adobe Campaign平台已安裝&#x200B;**syslogd**&#x200B;模組，但可以使用其他&#x200B;**syslog精靈**。 此模組會在&#x200B;**log**&#x200B;目錄中建立記錄檔。

多執行個體模組的記錄檔儲存在下列目錄中： **`<installation directory>`/var/default/log/**。 所有執行個體共用相同的記錄檔（例如&#x200B;**web.log**）。

其他模組的記錄會儲存在以執行個體命名的子資料夾中。 每個執行個體都有自己的記錄檔。

下表列出多執行處理記錄檔：

| 檔案 | 說明 |
|---|---|
| web.log | Web模組記錄(使用者端主控台、報表、SOAP API等) |
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
>**redir**&#x200B;目錄只存在於重新導向伺服器上。 **url**&#x200B;子目錄包含符合要重新導向的URL，而子目錄&#x200B;**log**&#x200B;包含追蹤記錄。 若要產生追蹤記錄，必須執行&#x200B;**trackinglogd**&#x200B;模組。

為了達到效能和儲存最佳化，logins.log檔案會分割成多個檔案，每天一個(logins.yy-mm-dd.log)，最多保留365個檔案。 在serverConf.xml中，可以在syslogd （**maxNumberOfLoginsFiles**&#x200B;選項）下變更天數。 請參閱[伺服器組態檔](../../installation/using/the-server-configuration-file.md#syslogd)的檔案。

依預設，每個模組和每個執行個體限製為兩個10 MB的檔案。 第二個檔案名為： **`<modulename>`_2.log**。 因此，每個模組及每個執行個體的記錄檔大小限製為2&#42;10MB。

不過，您可以保留較大的檔案。 若要啟用此功能，請變更&#x200B;**conf/serverConf.xml**&#x200B;檔案的&#x200B;**syslogd**&#x200B;節點中&#x200B;**maxFileSizeMb=&quot;10&quot;**&#x200B;設定的值。 此值代表記錄檔的大小上限（以MB為單位）。

如果您想要在記錄中保留更詳細的層級，可以使用&#x200B;**-verbose**&#x200B;引數啟動Adobe Campaign模組：

**nlserver啟動`<MODULE>`@`<INSTANCE>` -verbose**
