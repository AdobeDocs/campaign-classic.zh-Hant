---
solution: Campaign Classic
product: campaign
title: 配置對SAP HANA的訪問
description: 瞭解如何設定FDA的SAP HANA存取權
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# 配置對SAP HANA的訪問 {#configure-access-to-sap-hana}

使用Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA)選項來處理儲存在外部資料庫中的資訊。 請依照下列步驟來設定對SAP HANA的存取。

1. 配置 [SAP HANA資料庫](#sap-config)
1. 在Campaign中設定SAP HANA [外部帳戶](#sap-external) 。

## SAP HANA驅動程式 {#sap-config}

在FDA中連線至SAP HANA外部資料庫需要Adobe Campaign伺服器上的某些額外設定：

1. 根據您使用的作業系統，安裝SAP HANA的ODBC驅動程式：

   * **hdb_client_linux.tgz** for Linux。 解壓縮後，啟動hdbinst命令並按照說明完成驅動程式安裝。
   * **hdb_client_windows.zip** for Windows。 解壓縮檔案並啟動可執行檔： **hdbinst.exe**。 按照嚮導說明完成驅動程式的安裝。

1. 配置ODBC驅動程式。 配置可在標準檔案中執行：/etc/odbc.ini代表一般參數，/etc/odbcinst.ini代表聲明驅動程式。

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      
      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      &quot;InstallDir&quot;與 **odbcinst.ini檔案的位置對應** 。

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. 指定Adobe Campaign伺服器的環境變數：

   * **LD_LIBRARY_PATH**:依預設，應包含SAP Hana用戶端(/usr/sap/hdbclient/libodbcHDB.so)的連結。
   * **ODBCINI**:odbc.ini檔案的位置(例如/etc/odbc.ini)。

## SAP HANA外部帳戶{#sap-external}

SAP HANA外部帳戶可讓您將Campaign例項連接至SAP HANA外部資料庫。

1. 在促銷 **[!UICONTROL Explorer]**&#x200B;活動中，按 **[!UICONTROL Administration]** 一下「>」 **[!UICONTROL Platform]** 「>」 **[!UICONTROL External accounts]**。

1. 按一 **[!UICONTROL New]** 下並選 **[!UICONTROL External database]** 擇為 **[!UICONTROL Type]**。

1. 若要設定外 **[!UICONTROL SAP Hana]** 部帳戶，您必須指定：

   * **[!UICONTROL Type]**:SAP Hana

   * **[!UICONTROL Server]**:SAP Hana伺服器的URL

   * **[!UICONTROL Account]**:用戶名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼
