---
product: campaign
title: 設定SAP HANA的存取權
description: 瞭解如何在FDA中設定SAP HANA存取權
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# 設定SAP HANA的存取權 {#configure-access-to-sap-hana}



使用行銷活動 [同盟資料存取](../../installation/using/about-fda.md) (FDA)選項，用於處理儲存在外部資料庫中的資訊。 請依照下列步驟設定對SAP HANA的存取權。

1. 設定 [SAP HANA資料庫](#sap-config)
1. 設定SAP HANA [外部帳戶](#sap-external) 在Campaign中

## SAP HANA驅動程式 {#sap-config}

在FDA中連線至SAP HANA外部資料庫時，需要Adobe Campaign伺服器上的特定額外設定：

1. 根據您使用的作業系統，安裝用於SAP HANA的ODBC驅動程式：

   * **hdb_client_linux.tgz** 適用於Linux。 解壓縮之後，請啟動hdbinst指令，然後依照指示完成驅動程式的安裝。
   * **hdb_client_windows.zip** 適用於Windows。 解壓縮檔案並啟動可執行檔： **hdbinst.exe**. 請依照精靈的指示完成驅動程式的安裝。

1. 設定ODBC驅動程式。 可在標準檔案中執行設定：/etc/odbc.ini用於一般引數，/etc/odbcinst.ini用於宣告驅動程式。

   * **/etc/odbc.ini**

     ```
     [ODBC]
     InstallDir=/etc/
     
     [HDB]
     Driver=HDBODBC
     servernode=localhost:39013 (this value depend of your server)
     User:SYSTEM
     ```

     「InstallDir」對應至 **odbcinst.ini** 檔案。

   * **/etc/odbcinst.ini**

     ```
     [HDBODBC]
     Description = "SmartCloudPT HANA"
     Driver = /usr/sap/hdbclient/libodbcHDB.so
     ```

1. 指定Adobe Campaign伺服器的環境變數：

   * **LD_LIBRARY_PATH**：依預設，其中應包含您SAP Hana使用者端的連結(/usr/sap/hdbclient/libodbcHDB.so)。
   * **ODBCINI**：odbc.ini檔案的位置(例如/etc/odbc.ini)。

## SAP HANA外部帳戶{#sap-external}

SAP HANA外部帳戶可讓您將您的Campaign執行個體連線至SAP HANA外部資料庫。

1. 從Campaign **[!UICONTROL Explorer]**，按一下 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 按一下 **[!UICONTROL New]** 並選取 **[!UICONTROL External database]** 作為 **[!UICONTROL Type]**.

1. 若要設定 **[!UICONTROL SAP Hana]** 外部帳戶，您必須指定：

   * **[!UICONTROL Type]**： SAP Hana

   * **[!UICONTROL Server]**： SAP Hana伺服器的URL

   * **[!UICONTROL Account]**：使用者名稱

   * **[!UICONTROL Password]**：使用者帳戶密碼
