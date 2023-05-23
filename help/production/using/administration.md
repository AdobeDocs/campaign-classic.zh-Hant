---
product: campaign
title: 管理
description: 管理
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---

# 管理{#administration}



自動啟動Adobe Campaign模組(**網**。 **門**。 **wf伺服器**&#x200B;等) 由 **nlserver** 伺服器。

安裝Adobe Campaign會自動配置電腦，以便 **nlserver** 服務在啟動序列期間啟動。

以下命令用於手動啟動和關閉Adobe Campaign服務：

* 在Windows中：

   * **nlserver6**
   * **網站停止nlserver6**

* 在Linux（根）中：

   * **/etc/init.d/nlserver6啟動**
   * **/etc/init.d/nlserver6停止**

>[!NOTE]
>
>從20.1開始，建議改用以下命令（對於Linux）: **systmctl啟動nlserver** / **systemctl停止nlserver**

下面列出了在Linux中可訪問的常規管理命令(如 **Adobe Campaign**):

* 顯示所有已啟動的Adobe Campaign模組： **/etc/init.d/nlserver6 pdump** 或 **/etc/init.d/nlserver6狀態**

   >[!NOTE]
   >
   >添加 **— 誰** 參數 **轉儲** 命令，用於收集有關當前連接（用戶和進程）的資訊。\
   >的 **/etc/init.d/nlserver6狀態** 命令（不帶&quot;-who&quot;參數）將返回：
   >
   >    * 執行所有進程時為0。
   >    * 1（如果缺少進程）。
   >    * 2)。
   >    * 另一個值（如果出現錯誤）。


* 啟動/停止多實例或單實例模組(**網**。 **跟蹤日誌**。 **syslog**。 **門**。 **wf伺服器**。 **郵件**):

   **nlserver啟動`<module>[@<instance>]`**

   **nlserver停止`<module>[@<instance>][-immediate][-noconsole]`**

   您還可以使用 **nlserver重新啟動`<module>[@<instance>]`** 命令以重新啟動模組。

   範例:

   **nlserver啟動web**

   **nlserver啟動mta@my_instance**

   **nlserver停止syslogd**

   **nlserver停止wfserver@my_instance**

   **nlserver停止web-immediate**

   **nlserver restart web**

   >[!NOTE]
   >
   >* 如果未指定實例，則將使用「default」實例。
   >* 在發生緊急情況時，使用 **立即** 選項，強制立即停止進程（相當於Unix命令） **殺–9**)。
   >* 使用 **-noconsole** 選項，確保啟動的模組在控制台上不顯示任何內容。 其日誌將通過 **syslog** 中。
   >* 使用 **— 詳細** 按鈕，將選定控制項在Tab鍵次序中下移一個位置。

      >
      >   範例:
      >
      >   **nlserver restart web -verbose**
      >
      >   **nlserver啟動mta@myinstance -verbose**
      >
      >   此選項添加其他日誌。 我們建議在不使用 **— 詳細** 選項，以避免重載日誌。


* 啟動所有Adobe Campaign進程(相當於啟動 **nlserver6** 服務):

   **nlserver監視程式 — noconsole**

* 關閉所有Adobe Campaign進程(相當於關閉 **nlserver6** 服務):

   **伺服器關閉**

* 重新載入 **nlserver web** 模組配置(以及Web伺服器擴展模組（如果適用）) **serverConf.xml** 和 **配置`<instance>  .xml </instance>`** 已編輯檔案。

   **nlserver config -reload**

   >[!NOTE]
   >
   >某些配置更改沒有動態考慮；Adobe Campaign必須關閉，然後重啟。
