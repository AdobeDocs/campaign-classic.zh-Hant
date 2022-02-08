---
product: campaign
title: 其他Web跟蹤參數
description: 瞭解有關Web跟蹤參數的詳細資訊
exl-id: d14d94fd-b078-4893-be84-31d37a1d50f5
source-git-commit: 8fa50d17a9ff36ccc310860ac93771590cfd76fd
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# 其他Web跟蹤參數{#additional-parameters}

![](../../assets/v7-only.svg)

## 參數定義 {#definition-of-parameters}

您的Adobe Campaign平台提供兩個TRANSACTION類型的Web跟蹤參數作為標準：

* **金額**:表示交易金額，
* **文章**:表示事務處理中的項數。

這些參數在 **nms:webTrackingLog** 架構，是報告中看到的一些指標。

要定義其他參數，必須擴展此架構。

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

您可以通過配置跟蹤日誌清單（傳遞或收件人）來顯示這些參數的值。

## 重定向伺服器配置 {#redirection-server-configuration}

在伺服器配置中，可以定義要考慮Web跟蹤參數的最大字元數。

>[!IMPORTANT]
>
>增加要考慮的最大字元數可能會影響平台的Web跟蹤效能。

要執行此操作，請修改 **webTrackingParamSize** 屬性 **`<trackinglogd>`** 元素 **serverConf.xml** 的子菜單。 此檔案保存在 **會議** 的子目錄。

**範例**:

預設值為64個字元。 此值允許您考慮 **金額** 和 **文章** (&quot;amount=xxxxxxx&amp;article=xxxxxxx&quot;)標準參數。

通過考慮上述擴展架構示例中指示的兩個參數（名稱大小+值大小），您可以修改配置以考慮100個字元(「amount=xxxxxxxx&amp;article=xxxxxxx&amp;mode=xxxxxxxx&amp;code=xxxxx」)。

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

修改配置後，必須：

* 停止承載重定向模組（Apache、IIS等）的Web伺服器，
* 停止Adobe Campaign伺服器： **網站停止nlserver6** 在Windows中， **/etc/init.d/nlserver6停止** 在Linux中，

   >[!NOTE]
   >
   >從20.1開始，建議改用以下命令（對於Linux）: **systemctl停止nlserver**

* 在Linux中，使用 **ipcr** 命令，
* 重新啟動Adobe Campaign伺服器： **nlserver6** 在Windows中， **/etc/init.d/nlserver6啟動** 在Linux中，

   >[!NOTE]
   >
   >從20.1開始，建議改用以下命令（對於Linux）: **systmctl啟動nlserver**

* 重新啟動Web伺服器。

**示例**:考慮了Linux下的配置。

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
>對於Linux，如果 **webTrackingParamSize** 或 **maxSharedLogs** 參數時，可能需要增加共用記憶體(SHM)的大小。
