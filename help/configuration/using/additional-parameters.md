---
product: campaign
title: 其他網頁追蹤引數
description: 深入瞭解網路追蹤的引數
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: d14d94fd-b078-4893-be84-31d37a1d50f5
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# 其他網頁追蹤引數{#additional-parameters}

## 引數的定義 {#definition-of-parameters}

您的Adobe Campaign平台提供兩個TRANSACTION型別Web追蹤引數作為標準：

* **amount**：代表交易的金額，
* **article**：代表交易中的專案數。

這些引數是在&#x200B;**nms：webTrackingLog**&#x200B;結構描述中定義，而且是報表中看到的一些指標。

若要定義其他引數，您必須擴充此結構描述。

**範例**：

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

您可以透過設定追蹤記錄清單（傳遞或收件者）來顯示這些引數的值。

## 重新導向伺服器設定 {#redirection-server-configuration}

在伺服器設定中，您可以定義要納入網頁追蹤引數的最大字元數。

>[!IMPORTANT]
>
>增加要考慮的最大字元數可能會影響平台的網頁追蹤效能。

若要這麼做，請修改&#x200B;**serverConf.xml**&#x200B;檔案中&#x200B;**`<trackinglogd>`**&#x200B;專案的&#x200B;**webTrackingParamSize**&#x200B;屬性。 此檔案儲存在Adobe Campaign安裝目錄的&#x200B;**conf**&#x200B;子目錄中。

**範例**：

預設值為64個字元。 此值可讓您考慮&#x200B;**amount**&#x200B;和&#x200B;**article** (&quot;amount=xxxxxxxx&amp;article=xxxxxxxx&quot;)標準引數。

考量上述擴充功能結構範例中指示的兩個引數（名稱大小+值大小），您可以修改設定以考量100個字元(&quot;amount=xxxxxxxx&amp;article=xxxxxxxx&amp;mode=xxxxxxxxxx&amp;code=xxxxx&quot;)。

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

修改設定後，您必須：

* 停止裝載重新導向模組的網頁伺服器（Apache、IIS等），
* 停止Adobe Campaign伺服器： Windows中的&#x200B;**net stop nlserver6**，Linux中的&#x200B;**/etc/init.d/nlserver6 stop**，

  >[!NOTE]
  >
  >從20.1開始，我們建議改用以下命令（適用於Linux）： **systemctl stop nlserver**

* 在Linux中，使用&#x200B;**ipcrm**&#x200B;命令刪除共用記憶體區段，
* 重新啟動Adobe Campaign伺服器： Windows中的&#x200B;**net start nlserver6**，Linux中的&#x200B;**/etc/init.d/nlserver6 start**

  >[!NOTE]
  >
  >從20.1開始，我們建議改用以下命令（適用於Linux）： **systemctl start nlserver**

* 重新啟動網頁伺服器。

**範例**：考慮Linux下的組態。

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
>對於Linux，如果您增加&#x200B;**webTrackingParamSize**&#x200B;或&#x200B;**maxSharedLogs**&#x200B;引數的大小，您可能需要增加共用記憶體(SHM)的大小。
