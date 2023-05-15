---
product: campaign
title: 管理
description: 管理
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---

# 管理{#administration}



自動啟動Adobe Campaign模組(**web**, **mta**, **wfserver**&#x200B;等) 由提供 **nlserver** 伺服器。

安裝Adobe Campaign會自動設定電腦，以便 **nlserver** 在引導序列期間啟動服務。

以下命令用於手動啟動和關閉Adobe Campaign服務：

* 在Windows中：

   * **net start nlserver6**
   * **net stop nlserver6**

* 在Linux（作為根）中：

   * **/etc/init.d**
   * **/etc/init.d**

>[!NOTE]
>
>從20.1開始，建議改用下列命令（Linux適用）: **systemctl啟動nlserver** / **systemctl停止nlserver**

以下是可在Linux中存取的常用管理命令清單(如 **Adobe Campaign**):

* 顯示所有已啟動的Adobe Campaign模組： **/etc/init.d** 或 **/etc/init.d/nlserver6狀態**

   >[!NOTE]
   >
   >新增 **-who** 參數 **pdump** 命令可讓您收集目前連線（使用者和程式）的資訊。\
   >此 **/etc/init.d/nlserver6狀態** 命令（不含「 — who」參數）將返回：
   >
   >    * 0（如果正在執行所有進程）。
   >    * 1。
   >    * 2（如果未執行任何程式）。
   >    * 如果有錯誤，則另一個值。


* 啟動/停止多執行個體或單執行個體模組(**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail**):

   **nlserver開始`<module>[@<instance>]`**

   **nlserver停止`<module>[@<instance>][-immediate][-noconsole]`**

   您也可以使用 **nlserver重新啟動`<module>[@<instance>]`** 命令重新啟動模組。

   範例:

   **nlserver啟動web**

   **nlserver開始mta@my_instance**

   **nlserver stop syslogd**

   **nlserver停止wfserver@my_instance**

   **nlserver stop web -immediate**

   **nlserver重新啟動web**

   >[!NOTE]
   >
   >* 如果未指定例項，則會使用「預設」例項。
   >* 在發生緊急情況時，請使用 **-immedite** 強制立即停止進程的選項（相當於Unix命令） **殺–9**)。
   >* 使用 **-noconsole** 選項，確保已啟動的模組在主控台上不會顯示任何內容。 其日誌將通過 **syslogd** 模組。
   >* 使用 **-verbose** 選項，以顯示有關流程操作的其他資訊。

      >
      >   範例:
      >
      >   **nlserver重新啟動web -verbose**
      >
      >   **nlserver開始mta@myinstance -verbose**
      >
      >   此選項會新增其他記錄檔。 建議您重新啟動程式，而不要 **-verbose** 選項，以避免記錄超載。


* 啟動所有Adobe Campaign程式(等於啟動 **nlserver6** 服務):

   **nlserver watchdg -noconsole**

* 關閉所有Adobe Campaign進程(相當於關閉 **nlserver6** 服務):

   **nlserver關閉**

* 重新載入 **nlserver web** 模組設定(以及網頁伺服器擴充模組（若適用）) **serverConf.xml** 和 **config-`<instance>  .xml </instance>`** 已編輯檔案。

   **nlserver配置 — reload**

   >[!NOTE]
   >
   >部分配置更改不會動態考慮；Adobe Campaign必須關閉，然後重新啟動。
