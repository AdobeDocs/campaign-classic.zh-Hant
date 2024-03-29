---
product: campaign
title: 其他網頁追蹤引數
description: 深入瞭解網路追蹤的引數
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
exl-id: d14d94fd-b078-4893-be84-31d37a1d50f5
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 1%

---

# 其他網頁追蹤引數{#additional-parameters}

## 引數的定義 {#definition-of-parameters}

您的Adobe Campaign平台提供兩個TRANSACTION型別Web追蹤引數作為標準：

* **數量**：代表交易的金額，
* **文章**：代表交易中的專案數。

這些引數定義於 **nms：webTrackingLog** 綱要，和是報表中看到的一些指標。

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

若要這麼做，請修改 **webTrackingParamSize** 的屬性 **`<trackinglogd>`** 中的元素 **serverConf.xml** 檔案。 此檔案儲存在 **conf** Adobe Campaign安裝目錄的子目錄。

**範例**：

預設值為64個字元。 此值可讓您將 **數量** 和 **文章** (&quot;amount=xxxxxxxx&amp;article=xxxxxxxx&quot;)標準引數。

考量上述擴充功能結構範例中指示的兩個引數（名稱大小+值大小），您可以修改設定以考量100個字元(&quot;amount=xxxxxxxx&amp;article=xxxxxxxx&amp;mode=xxxxxxxxxx&amp;code=xxxxx&quot;)。

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

修改設定後，您必須：

* 停止裝載重新導向模組的網頁伺服器（Apache、IIS等），
* 停止Adobe Campaign伺服器： **網路停止nlserver6** 在Windows， **/etc/init.d/nlserver6停止** 在Linux中，

  >[!NOTE]
  >
  >從20.1版開始，建議您改用下列命令（適用於Linux）： **systemctl停止nlserver**

* 在Linux中，請使用 **ipcrm** 命令，
* 重新啟動Adobe Campaign伺服器： **網路啟動nlserver6** 在Windows， **/etc/init.d/nlserver6開始** 在Linux中，

  >[!NOTE]
  >
  >從20.1版開始，建議您改用下列命令（適用於Linux）： **systemctl啟動nlserver**

* 重新啟動網頁伺服器。

**範例**：考慮Linux下的設定。

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
>對於Linux，如果您將 **webTrackingParamSize** 或 **maxSharedLogs** 引數，您可能需要增加共用記憶體(SHM)的大小。
