---
product: campaign
title: 配置訪問SAP HANA
description: 了解如何在FDA中設定SAP HANA存取權
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# 配置訪問SAP HANA {#configure-access-to-sap-hana}



使用Campaign [同盟資料存取](../../installation/using/about-fda.md) (FDA)處理儲存在外部資料庫中的資訊的選項。 請依照下列步驟來設定存取SAP HANA。

1. 設定 [SAP HANA資料庫](#sap-config)
1. 設定SAP HANA [外部帳戶](#sap-external) 在Campaign

## SAP HANA驅動程式 {#sap-config}

在FDA中連線至SAP HANA外部資料庫需要Adobe Campaign伺服器上的某些額外設定：

1. 根據您使用的作業系統安裝SAP HANA的ODBC驅動程式：

   * **hdb_client_linux_tgz** Linux版。 解壓後，啟動hdbinst命令並按照說明完成驅動程式的安裝。
   * **hdb_client_windows_zip** Windows版。 將檔案解壓縮，然後啟動執行檔： **hdbinst.exe**. 按照嚮導說明完成驅動程式的安裝。

1. 配置ODBC驅動程式。 可在標準檔案中執行設定：/etc/odbc.ini用於常規參數，/etc/odbcinst.ini用於聲明驅動程式。

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      
      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      &quot;InstallDir&quot;對應於 **odbcinst.ini** 檔案。

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. 指定Adobe Campaign伺服器的環境變數：

   * **LD_LIBRARY_PATH**:預設情況下，它應包含指向SAP Hana客戶端(/usr/sap/hdbclient/libodbcHDB.so)的連結。
   * **奧德比尼**:odbc.ini檔案的位置(例如/etc/odbc.ini)。

## SAP HANA外部帳戶{#sap-external}

SAP HANA外部帳戶可讓您將Campaign執行個體連結至SAP HANA外部資料庫。

1. 從促銷活動 **[!UICONTROL Explorer]**，按一下 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 按一下 **[!UICONTROL New]** 選取 **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. 若要設定 **[!UICONTROL SAP Hana]** 外部帳戶，您必須指定：

   * **[!UICONTROL Type]**:SAP Hana

   * **[!UICONTROL Server]**:SAP Hana伺服器的URL

   * **[!UICONTROL Account]**:使用者名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼
