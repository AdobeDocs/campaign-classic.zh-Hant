---
title: 其他參數
seo-title: 其他參數
description: 其他參數
seo-description: null
page-status-flag: never-activated
uuid: c223c84a-f8fd-43d3-9deb-b1c19d442c65
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 1b2ae224-8406-4506-b589-6e5f6631e87f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# 其他參數{#additional-parameters}

## 參數定義 {#definition-of-parameters}

您的Adobe Campaign平台提供兩個TRANSACTION類型的網路追蹤參數做為標準：

* **金額**:代表交易金額，
* **文章**:表示事務處理中的項數。

這些參數在 **nms:webTrackingLog** 架構中定義，是報告中看到的一些指標。

要定義其他參數，必須擴展此方案。

**範例**:

```
<srcSchema extendedSchema="nms:webTrackingLog" label="Web Tracking"
           mappingType="sql" name="webTrackingLog" 
           namespace="cus" xtkschema="xtk:srcSchema">

  <element name="webTrackingLog">
    <attribute desc="Payment method" label="Payment method" length="10" name="mode" type="string"/>
    <attribute desc="Offer code" label="Offer code" length="5" name="code" type="string"/>
  </element>
</srcSchema>
```

您可以設定追蹤記錄清單（傳送或收件者），以顯示這些參數的值。

## 重定向伺服器配置 {#redirection-server-configuration}

在伺服器設定中，您可以定義要納入網頁追蹤參數的字元數上限。

>[!IMPORTANT]
>
>增加要考慮的字元數目上限可能會影響您平台的網頁追蹤效能。

若要這麼做，請修 **改serverConf.xml檔案中元** 素的webTrackingParamSize **`<trackinglogd>`** 屬 **** 性。 此檔案會儲存在 **Adobe Campaign安裝目** 錄的conf子目錄中。

**範例**:

預設值為64個字元。 此值可讓您考慮 **金額** 和 **文章** (&quot;amount=xxxxxxxx&amp;article=xxxxxxx&quot;)標準參數。

通過考慮上述擴展模式示例中指示的兩個參數（名稱大小+值大小），您可以修改配置以考慮100個字元(&quot;amount=xxxxxxxx&amp;article=xxxxxx&amp;mode=xxxxxxxxx&amp;code=xxxxx&quot;)。

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

修改配置後，您必須：

* 停止承載重定向模組（Apache、IIS等）的Web伺服器，
* 停止Adobe Campaign伺服器：在 **Windows中停止nlserver6** 、 **/etc/init.d/nlserver6在Linux中停止** 、

   >[!NOTE]
   >
   >從20.1開始，建議改用下列命令（適用於Linux）: **systemctl stop nlserver**

* 在Linux中，使用 **ipcrm命令刪除共用內** 存段，
* 重新啟動Adobe Campaign伺服器：在 **Windows中啟動nlserver6** ，在 **Linux中啟動** /etc/init.d/nlserver6

   >[!NOTE]
   >
   >從20.1開始，建議改用下列命令（適用於Linux）:系 **統mctl啟動nlserver**

* 重新啟動Web伺服器。

**範例**:考慮Linux下的配置。

```
adobe@selma:~$ systemctl stop nlserver
adobe@selma:~$ systemctl stop apache2
adobe@selma:~$ ipcs shm

------ Shared Memory Segments --------
key        shmid      owner      perms      bytes      nattch     status      
0x52020679 2097153    adobe   666        93608      8                       

------ Semaphore Arrays --------
key        semid      owner      perms      nsems     
0x52020678 4227081    adobe   666        1         

------ Message Queues --------
key        msqid      owner      perms      used-bytes   messages    

adobe@selma:~$ ipcrm shm 2097153                             
1 resource(s) deleted
adobe@selma:~$ systemctl start nlserver
adobe@selma:~$ systemctl start apache2
```

>[!NOTE]
>
>對於Linux，如果您增加 **webTrackingParamSize** 或 **** maxSharedLogs參數的大小，則可能需要增加共用記憶體(SHM)的大小。

