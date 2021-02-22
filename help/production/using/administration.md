---
solution: Campaign Classic
product: campaign
title: 管理員
description: 管理員
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 9c78d8f469bade41717eb854e8cec00859c1d4e3
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---


# 管理員{#administration}

自動啟動Adobe Campaign模組（**web**、**mta**、**wfserver**&#x200B;等） 由&#x200B;**nlserver**&#x200B;伺服器提供。

安裝Adobe Campaign會自動配置電腦，使&#x200B;**nlserver**&#x200B;服務在引導序列期間啟動。

以下命令用於手動啟動和關閉Adobe Campaign服務：

* 在Windows中：

   * **net start nlserver6**
   * **net stop nlserver6**

* 在Linux中（以root用戶身份）:

   * **/etc/init.d/nlserver6 start**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>從20.1開始，建議改用下列命令（適用於Linux）:**systemmctl start nlserver** / **systemmctl stop nlserver**

以下是可在Linux中存取的常見管理命令清單（如&#x200B;**Adobe Campaign**）:

* 顯示所有已啟動的Adobe Campaign模組：**/etc/init.d/nlserver6 pdump**&#x200B;或&#x200B;**/etc/init.d/nlserver6 status**

   >[!NOTE]
   >
   >將&#x200B;**-who**&#x200B;參數添加到&#x200B;**pdump**&#x200B;命令中，可以收集有關當前連接（用戶和進程）的資訊。\
   >**/etc/init.d/nlserver6 status**&#x200B;命令（不含&quot;-who&quot;參數）將返回：
   >
   >    * 0（如果正在執行所有進程）。
   >    * 1（如果流程遺失）。
   >    * 2.如果未執行任何程式。
   >    * 其他值（如果有錯誤）。


* 啟動／停止多實例或單實例模組(**web**、**trackinglogd**、**syslogd**、**mta**、**wfserver**、**inmail**):

   **nlserver啟動`<module>[@<instance>]`**

   **nlserver停止`<module>[@<instance>][-immediate][-noconsole]`**

   您也可以使用&#x200B;**nlserver restart`<module>[@<instance>]`**&#x200B;命令重新啟動模組。

   範例:

   **nlserver啟動Web**

   **nlserver啟動mta@my_instance**

   **nlserver stop syslogd**

   **nlserver停止wfserver@my_instance**

   **nlserver stop web -immediate**

   **nlserver重新啟動網路**

   >[!NOTE]
   >
   >* 如果未指定實例，則使用「預設」實例。
   >* 發生緊急情況時，使用&#x200B;**-immediate**&#x200B;選項強制立即停止進程（相當於Unix命令&#x200B;**kill -9**）。
   >* 使用&#x200B;**-noconsole**&#x200B;選項，確保啟動的模組在控制台上不顯示任何內容。 其日誌將通過&#x200B;**syslogd**&#x200B;模組寫入磁碟。
   >* 使用&#x200B;**-verbose**&#x200B;選項可顯示有關進程操作的其他資訊。
   >
   >   範例:
   >
   >   **nlserver重新啟動web -verbose**
   >
   >   **nlserver啟動mta@myinstance -verbose**
   >
   >   此選項會新增其他記錄檔。 建議在您找到所需的資訊後，不使用&#x200B;**-verbose**&#x200B;選項重新啟動程式，以避免過載記錄檔。


* 啟動所有Adobe Campaign程式（相當於啟動&#x200B;**nlserver6**&#x200B;服務）:

   **nlserver watchdog -noconsole**

* 關閉所有Adobe Campaign進程（相當於關閉&#x200B;**nlserver6**&#x200B;服務）:

   **伺服器關閉**

* 當編輯&#x200B;**serverConf.xml**&#x200B;和&#x200B;**config-`<instance>  .xml </instance>`**&#x200B;檔案時，重新載入&#x200B;**nlserver web**&#x200B;模組配置（和web伺服器擴展模組，如果適用）。

   **nlserver config -reload**

   >[!NOTE]
   >
   >某些配置更改不會動態考慮；Adobe Campaign必須關閉，然後重新啟動。

