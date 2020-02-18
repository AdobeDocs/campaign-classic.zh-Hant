---
title: 管理
seo-title: 管理
description: 管理
seo-description: null
page-status-flag: never-activated
uuid: 376efec1-1647-43b4-b72f-2603214c7cc6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 860be8be-f28c-4836-b4fb-e91c6a4616c6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3801665574d0cdc9c0caf46fb2f0eede38f1b2cc

---


# 管理{#administration}

自動啟動Adobe Campaign模組(**web**、 **mta**、 **wfserver**&#x200B;等)由nlserver服務 **器提供** 。

安裝Adobe Campaign會自動設定機器，讓nlserver **** service在引導序列期間啟動。

以下命令用於手動啟動和關閉Adobe Campaign服務：

* 在Windows中：

   * **net start nlserver6**
   * **net stop nlserver6**

* 在Linux（作為根）中：

   * **/etc/init.d/nlserver6 start**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>從20.1開始，建議改用下列命令（適用於Linux）: **systemctl啟動nlserver** / **systemctl停止nlserver**

以下是可在Linux(如 **Adobe Campaign**)中存取的常見管理命令清單：

* 顯示所有已啟動的Adobe Campaign模組： **/etc/init.d/nlserver6 pdump** 或 **/etc/init.d/nlserver6狀態**

   >[!NOTE]
   >
   >將 **-who** 參數新增至 **pdump** 命令，可讓您收集目前連線（使用者和程式）的資訊。\
   >/etc/init.d/ **nlserver6 status** 命令（不含&quot;-who&quot;參數）將返回：
   >
   >    * 0（如果正在執行所有進程）。
   >    * 1（如果流程遺失）。
   >    * 2.如果未執行任何程式。
   >    * 其他值（如果有錯誤）。


* 啟動／停止多實例或單實例模組(**Web**、 **Logd**、 **syslogd**、Trackingta、 **Wserver、InmailLignard、LightLignSup、InMailLignServer、********** InLignS):

   **nlserver啟動`<module>[@<instance>]`**

   **nlserver停止`<module>[@<instance>][-immediate][-noconsole]`**

   您也可以使用 **nlserver restart命`<module>[@<instance>]`**令重新啟動模組。

   例如：

   **nlserver啟動Web**

   **nlserver啟動mta@my_instance**

   **nlserver stop syslogd**

   **nlserver停止wfserver@my_instance**

   **nlserver停止Web -immediate**

   **nlserver重新啟動網路**

   >[!NOTE]
   > 
   >    * 如果未指定實例，則使用「預設」實例。
   >    * 發生緊急情況時，使用 **-immediate** 選項強制立即停止進程(相當於Unix命 **令kill -9**)。
   >    * 使用 **-noconsole** 選項，確保啟動的模組在控制台上不顯示任何內容。 其日誌將通過syslogd模組寫入 **磁碟** 。
   >    * 使用 **-verbose選項** ，顯示有關進程操作的其他資訊。
      >    
      >      
      例如：
      >    
      >      
      **nlserver重新啟動web -verbose**
      >    
      >      
      **nlserver啟動mta@myinstance -verbose**
      >    
      >      
      此選項會新增其他記錄檔。 我們建議您在找到所需資訊後，在不使用 **-verbose** 選項的情況下重新啟動程式，以避免過載記錄檔。


* 啟動所有Adobe Campaign程式(相當於啟動 **nlserver6服務** ):

   **nlserver watchdog -noconsole**

* 關閉所有Adobe Campaign程式(相當於關閉 **nlserver6服務** ):

   **伺服器關閉**

* 編輯 **serverConf.xml和** config- **檔案時，重新載入nlserver web** module配置(和web server extension模組（如果適用） **`<instance>  .xml </instance>`**。

   **nlserver config -reload**

   >[!NOTE]
   >
   >某些配置更改不會動態考慮；Adobe Campaign必須關閉，然後重新啟動。

