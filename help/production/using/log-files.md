---
title: 日誌檔案
seo-title: 日誌檔案
description: 日誌檔案
seo-description: null
page-status-flag: never-activated
uuid: 266bc067-0218-4b3e-941c-dc5cd0b6a10d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: fac3e3ec-82a7-4087-ba88-2b28b0f69d1c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f018df9a2f7516b92f1f25a757065ef268136a5

---


# 日誌檔案{#log-files}

日誌檔案的組織如下：

![](assets/d_ncs_directory.png)

每個 **nlserver** 模組都生成一個保存在以下目錄中的日誌檔案： **`<installation directory>`/var/`<instance>`/log/`<module>`.log **。

nlserver syslogd **** 模組將日誌保存到磁碟。 此模組與Unix **syslog守護程式類似**，但已經適用於Unix和Windows之間的相容性。 其他Adobe Campaign模組不會將其記錄檔儲存至磁碟；他們通過發送UDP資料包將 **此任務委派給** syslogd模組。

預設情況下，Adobe Campaign平台上安裝了 **syslogd** 模組，但可以使用另一個 **syslog守護程式**。 此模組在日誌目錄中建立日 **志文** 件。

多實例模組的日誌儲存在以下目錄中： **`<installation directory>`/var/default/log/**。 所有例項都共用相同的記錄檔(例如**web.log **)。

其他模組的日誌儲存在以實例命名的子資料夾中。 每個實例都有自己的日誌檔案。

下表列出多執行個體記錄檔：

| 檔案 | 說明 |
|---|---|
| web.log | Web模組日誌（客戶端控制台、報告、SOAP API等） |
| webmdl.log | 來自重定向模組的日誌 |
| watchdog.log | 來自Adobe Campaign流程監控模組的記錄檔 |
| trackinglogd.log | 追蹤記錄檔 |

下表列出單實例日誌檔案：

| 檔案 | 說明 |
|---|---|
| mta.log | mta模組記錄 |
| mtachild.log | 訊息傳送處理記錄檔 |
| wfserver.log | 工作流伺服器模組的日誌 |
| runwf.log | 工作流程執行記錄檔 |
| inMail.log | 彈回郵件模組記錄檔 |
| logins.log | 記錄所有登入Adobe Campaign的嘗試（成功與否） |

>[!CAUTION]
>
>redir目 **錄僅存** 在於重定向伺服器上。 url子 **目錄** ，包含要重新導向之URL的相符項目，而子目錄 **記錄檔則包** 含追蹤記錄。 若要產生追蹤記錄檔， **trackinglogd** 模組必須正在執行。

為了最佳化效能和儲存空間，logins.log檔案會分割為多個檔案，每天一個檔案(logins.yy-mm-dd.log)，最多可保留365個檔案。 serverConf.xml中syslogd(**** maxNumberOfLoginsFiles選項)下的天數可以更改。 請參閱伺服器組態檔 [案上的檔案](../../installation/using/the-server-configuration-file.md#syslogd)。

根據預設，每個模組和每個實例的日誌限制為兩個10 MB的檔案。 第二個檔案稱為： **`<modulename>`_2.log **。 因此，每個模組和每個實例的日誌大小限制為2*10MB。

不過，您可以保留較大的檔案。 若要啟用此功能，請變更conf/serverConf.xml檔 **案syslogd節點中** maxFileSizeMb=&quot;10&quot; **設定的** 值 **** 。 此值表示日誌檔案的最大大小(MB)。

如果您想要在記錄檔中維持更詳細的層級，可以使用 **-verbose參數啟動Adobe Campaign** 模組：

**nlserver啟動`<MODULE>`@`<INSTANCE>`-verbose**
