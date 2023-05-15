---
product: campaign
title: 其他網路追蹤參數
description: 進一步了解網頁追蹤的參數
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: d14d94fd-b078-4893-be84-31d37a1d50f5
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# 其他網路追蹤參數{#additional-parameters}

## 參數定義 {#definition-of-parameters}

您的Adobe Campaign平台提供兩個TRANSACTION類型的網頁追蹤參數作為標準：

* **金額**:代表交易金額，
* **文章**:代表交易記錄中的項目數。

這些參數定義於 **nms:webTrackingLog** 結構描述中顯示的指標，以及。

若要定義其他參數，您必須擴充此結構。

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

您可以設定追蹤記錄清單（傳遞者或收件者），以顯示這些參數的值。

## 重定向伺服器配置 {#redirection-server-configuration}

在伺服器設定中，您可以定義要納入網頁追蹤參數的字元數上限。

>[!IMPORTANT]
>
>增加要考慮的字元數上限可能會影響平台的網頁追蹤效能。

要執行此操作，請修改 **webTrackingParamSize** 屬性 **`<trackinglogd>`** 元素 **serverConf.xml** 檔案。 此檔案會儲存在 **conf** Adobe Campaign安裝目錄的子目錄。

**範例**:

預設值為64個字元。 此值可讓您將 **金額** 和 **文章** (&quot;amount=xxxxxxxx&amp;article=xxxxxxxx&quot;)標準參數。

考慮到上述擴充功能架構範例中指出的兩個參數（名稱大小+值大小），您可以修改設定，將100個字元納入考量(&quot;amount=xxxxxxxxxxx&amp;article=xxxxxxx&amp;mode=xxxxxxxxx&amp;code=xxxxx&quot;)。

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

修改設定後，您必須：

* 停止承載重定向模組（Apache、IIS等）的Web伺服器，
* 停止Adobe Campaign伺服器： **net stop nlserver6** 在Windows中， **/etc/init.d** 在Linux中，

   >[!NOTE]
   >
   >從20.1開始，建議改用下列命令（Linux適用）: **systemctl停止nlserver**

* 在Linux中，使用 **ipcrm** 命令，
* 重新啟動Adobe Campaign伺服器： **net start nlserver6** 在Windows中， **/etc/init.d** 在Linux中，

   >[!NOTE]
   >
   >從20.1開始，建議改用下列命令（Linux適用）: **systemctl啟動nlserver**

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
>對於Linux，如果您增加 **webTrackingParamSize** 或 **maxSharedLogs** 參數時，您可能需要增加共用記憶體(SHM)的大小。
