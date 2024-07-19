---
product: campaign
title: 管理
description: 管理
feature: Monitoring
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: b7dedddc080d1ea8db700fabc9ee03238b3706cc
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 1%

---

# 管理{#administration}

自動啟動Adobe Campaign模組（**網頁**、**mta**、**wfserver**&#x200B;等） 由&#x200B;**nlserver**&#x200B;伺服器提供。

安裝Adobe Campaign會自動設定電腦，讓&#x200B;**nlserver**&#x200B;服務在開機順序期間啟動。

下列命令可用來手動啟動及關閉Adobe Campaign服務：

* 在Windows中：

   * **網路啟動nlserver6**
   * **網路停止nlserver6**

* 在Linux中（作為根）：

   * **/etc/init.d/nlserver6開始**
   * **/etc/init.d/nlserver6停止**

>[!NOTE]
>
>從20.1開始，建議您改用下列命令（適用於Linux）： **systemctl start nlserver** / **systemctl stop nlserver**

以下是可在Linux中存取的常見管理命令清單(如&#x200B;**Adobe Campaign**)：

* 顯示所有已啟動的Adobe Campaign模組： **/etc/init.d/nlserver6 pdump**&#x200B;或&#x200B;**/etc/init.d/nlserver6狀態**

  >[!NOTE]
  >
  >將&#x200B;**-who**&#x200B;引數新增至&#x200B;**pdump**&#x200B;命令可讓您收集有關目前連線（使用者和處理序）的資訊。\
  >**/etc/init.d/nlserver6 status**&#x200B;命令（不含「 — who」引數）將傳回：
  >
  >    * 如果正在執行所有處理序，則為0。
  >    * 如果缺少程式，則為1。
  >    * 如果未執行任何程式，則為2。
  >    * 如果發生錯誤則為另一個值。
  >

* 啟動/停止多重執行個體或單一執行個體模組(**web**，**trackinglogd**，**syslogd**，**mta**，**wfserver**，**inmail**)：

  **nlserver啟動`<module>[@<instance>]`**

  **nlserver停止`<module>[@<instance>][-immediate][-noconsole]`**

  您也可以使用&#x200B;**nlserver restart`<module>[@<instance>]`**&#x200B;命令來重新啟動模組。

  例如：

  **nlserver啟動web**

  **nlserver啟動mta@my_instance**

  **nlserver停止syslogd**

  **nlserver停止wfserver@my_instance**

  **nlserver stop web -immediate**

  **nlserver重新啟動web**

  >[!NOTE]
  >
  >* 如果未指定例項，則會使用「預設」例項。
  >* 發生緊急狀況時，請使用&#x200B;**-immediate**&#x200B;選項強制立即停止處理序（相當於Unix命令&#x200B;**kill -9**）。
  >* 使用&#x200B;**-noconsole**&#x200B;選項，確保啟動的模組不會在主控台上顯示任何內容。 其記錄檔將透過&#x200B;**syslogd**&#x200B;模組寫入磁碟。
  >* 使用&#x200B;**-verbose**&#x200B;選項可顯示程式動作的額外資訊。
  >
  >   例如：
  >
  >   **nlserver重新啟動web -verbose**
  >
  >   **nlserver啟動mta@myinstance -verbose**
  >
  >   此選項會新增其他記錄。 我們建議您在找到所需資訊後，不使用&#x200B;**-verbose**&#x200B;選項而再次啟動處理程式，以避免記錄超載。

* 啟動所有Adobe Campaign處理序（相當於啟動&#x200B;**nlserver6**&#x200B;服務）：

  **nlserver watchdog -noconsole**

* 關閉所有Adobe Campaign處理序（等於關閉&#x200B;**nlserver6**&#x200B;服務）：

  **nlserver關機**

* 編輯&#x200B;**serverConf.xml**&#x200B;和&#x200B;**config-`<instance>  .xml </instance>`**&#x200B;檔案時，重新載入&#x200B;**nlserver web**&#x200B;模組組態（以及web伺服器延伸模組，如果適用）。

  **nlserver設定 — 重新載入**

  >[!NOTE]
  >
  >部分設定變更不會動態列入考量；Adobe Campaign必須關閉再重新啟動。
