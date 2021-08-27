---
product: campaign
title: 記錄檔案
description: 記錄檔案
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 1%

---

# 記錄檔案{#log-files}

![](../../assets/v7-only.svg)

記錄檔的組織方式如下：

![](assets/d_ncs_directory.png)

每個&#x200B;**nlserver**&#x200B;模組都生成保存在以下目錄中的日誌檔案：**`<installation directory>`/var/`<instance>`/log/`<module>`.log**。

**nlserver syslogd**&#x200B;模組將日誌保存到磁碟。 此模組與Unix **syslog守護程式**&#x200B;類似，但已針對Unix和Windows之間的相容性進行了調整。 其他Adobe Campaign模組不會將其記錄檔儲存至磁碟；他們通過發送UDP資料包將此任務委派給&#x200B;**syslogd**&#x200B;模組。

預設情況下，Adobe Campaign平台上安裝了&#x200B;**syslogd**&#x200B;模組，但可以使用另一個&#x200B;**syslog守護程式**。 此模組將在&#x200B;**log**&#x200B;目錄中建立日誌檔案。

多實例模組的日誌儲存在以下目錄中：**`<installation directory>`/var/default/log/**。 所有執行個體會共用相同的記錄檔(例如&#x200B;**web.log**)。

其他模組的記錄會儲存在以執行個體命名的子資料夾中。 每個執行個體都有其專屬的記錄檔。

下表列出多執行個體記錄檔：

| 檔案 | 說明 |
|---|---|
| web.log | Web模組記錄（用戶端主控台、報表、SOAP API等） |
| webmdl.log | 來自重定向模組的日誌 |
| watchdog.log | 來自Adobe Campaign程式監控模組的記錄 |
| trackinglogd.log | 追蹤記錄 |

下表列出了單實例日誌檔案：

| 檔案 | 說明 |
|---|---|
| mta.log | mta模組記錄 |
| mtachild.log | 訊息傳送處理記錄檔 |
| wfserver.log | 工作流伺服器模組的日誌 |
| runwf.log | 工作流程執行記錄檔 |
| inMail.log | 退回郵件模組日誌 |
| logins.log | 記錄所有嘗試登入Adobe Campaign（成功與否） |

>[!IMPORTANT]
>
>**redir**&#x200B;目錄僅存在於重定向伺服器上。 **url**&#x200B;子目錄包含要重新導向之URL的相符項目，而子目錄&#x200B;**log**&#x200B;包含追蹤記錄。 若要產生追蹤記錄，**trackinglogd**&#x200B;模組必須執行。

為達到效能和儲存最佳化， logins.log檔案會分割為多個檔案，每天一個檔案(logins.yy-mm-dd.log)，最多可保留365個檔案。 在syslogd（**maxNumberOfLoginsFiles**&#x200B;選項）下，可以在serverConf.xml中更改天數。 請參閱[伺服器配置檔案](../../installation/using/the-server-configuration-file.md#syslogd)上的文檔。

依預設，每個模組和每個執行個體的記錄檔數限制為兩個10 MB的檔案。 第二個檔案稱為：**`<modulename>`_2.log**。 因此，每個模組和每個執行個體的日誌大小限制為2*10MB。

不過，您可以保留較大的檔案。 要啟用此功能，請更改&#x200B;**conf/serverConf.xml**&#x200B;檔案的&#x200B;**syslogd**&#x200B;節點中&#x200B;**maxFileSizeMb=&quot;10&quot;**&#x200B;設定的值。 此值表示日誌檔案的最大大小(MB)。

如果您想在記錄中保留更多的詳細程度，可以使用&#x200B;**-verbose**&#x200B;參數啟動Adobe Campaign模組：

**nlserver開 `<MODULE>`始@`<INSTANCE>` -verbose**
