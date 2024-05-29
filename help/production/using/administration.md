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

Adobe Campaign模組的自動啟動(**網頁**， **mta**， **wfserver**、等) 由 **nlserver** 伺服器。

安裝Adobe Campaign會自動設定電腦，讓 **nlserver** 服務會在開機順序期間啟動。

下列命令可用來手動啟動及關閉Adobe Campaign服務：

* 在Windows中：

   * **網路啟動nlserver6**
   * **網路停止nlserver6**

* 在Linux中（作為根）：

   * **/etc/init.d/nlserver6開始**
   * **/etc/init.d/nlserver6停止**

>[!NOTE]
>
>從20.1版開始，建議您改用下列命令（適用於Linux）： **systemctl啟動nlserver** / **systemctl停止nlserver**

以下為可在Linux中存取的常見管理命令清單(如 **Adobe Campaign**)：

* 顯示所有啟動的Adobe Campaign模組： **/etc/init.d/nlserver6 pdump** 或 **/etc/init.d/nlserver6狀態**

  >[!NOTE]
  >
  >新增 **-who** 的引數 **pdump** 命令可讓您收集有關目前連線（使用者和程式）的資訊。\
  >此 **/etc/init.d/nlserver6狀態** 命令（不含「 — who」引數）將傳回：
  >
  >    * 如果正在執行所有處理序，則為0。
  >    * 如果缺少程式，則為1。
  >    * 如果未執行任何程式，則為2。
  >    * 如果發生錯誤則為另一個值。
  >

* 啟動/停止多執行個體或單執行個體模組(**網頁**， **trackinglogd**， **syslogd**， **mta**， **wfserver**， **inmail**)：

  **nlserver start`<module>[@<instance>]`**

  **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

  您也可以使用 **nlserver重新啟動`<module>[@<instance>]`** 重新啟動模組的命令。

  例如：

  **nlserver start web**

  **nlserver啟動mta@my_instance**

  **nlserver停止syslogd**

  **nlserver stop wfserver@my_instance**

  **nlserver stop web -immediate**

  **nlserver重新啟動web**

  >[!NOTE]
  >
  >* 如果未指定例項，則會使用「預設」例項。
  >* 發生緊急情況時，請使用 **-immediate** 強製程式立即停止的選項（相當於Unix指令） **kill -9**)。
  >* 使用 **-noconsole** 選項，確保啟動的模組不會在主控台上顯示任何內容。 記錄檔將透過 **syslogd** 模組。
  >* 使用 **-verbose** 選項來顯示程式動作的額外資訊。
  >
  >   例如：
  >
  >   **nlserver重新啟動web -verbose**
  >
  >   **nlserver啟動mta@myinstance -verbose**
  >
  >   此選項會新增其他記錄。 我們建議在不使用的情況下，再次啟動流程。 **-verbose** 選項，以便在找到所需資訊後避免讓記錄超載。

* 啟動所有Adobe Campaign程式(相當於啟動 **nlserver6** 服務)：

  **nlserver watchdog -noconsole**

* 關閉所有Adobe Campaign處理序(等於關閉 **nlserver6** 服務)：

  **nlserver關機**

* 重新載入 **nlserver web** 模組組態（以及Web伺服器擴充功能模組，如果適用），當 **serverConf.xml** 和 **config-`<instance>  .xml </instance>`** 檔案已編輯。

  **nlserver設定 — reload**

  >[!NOTE]
  >
  >部分設定變更不會動態列入考量；Adobe Campaign必須關閉再重新啟動。
