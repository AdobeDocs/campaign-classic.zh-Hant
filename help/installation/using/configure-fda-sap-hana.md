---
product: campaign
title: 配置訪問SAP HANA
description: 了解如何在FDA中設定SAP HANA存取權
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# 配置對SAP HANA{#configure-access-to-sap-hana}的訪問

使用Campaign [同盟資料存取](../../installation/using/about-fda.md)(FDA)選項來處理儲存在外部資料庫中的資訊。 請依照下列步驟來設定存取SAP HANA。

1. 配置[SAP HANA資料庫](#sap-config)
1. 在Campaign中設定SAP HANA[外部帳戶](#sap-external)

## SAP HANA驅動程式{#sap-config}

在FDA中連線至SAP HANA外部資料庫需要Adobe Campaign伺服器上某些額外設定：

1. 根據您使用的作業系統安裝SAP HANA的ODBC驅動程式：

   * **hdb_client_linux.** tgzfor Linux。解壓後，啟動hdbinst命令並按照說明完成驅動程式的安裝。
   * **hdb_client_windows.** zipfor Windows。將檔案解壓縮，然後啟動執行檔：**hdbinst.exe**。 按照嚮導說明完成驅動程式的安裝。

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

      &quot;InstallDir&quot;對應於&#x200B;**odbcinst.ini**&#x200B;檔案的位置。

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. 指定Adobe Campaign伺服器的環境變數：

   * **LD_LIBRARY_PATH**:預設情況下，它應包含指向SAP Hana客戶端(/usr/sap/hdbclient/libodbcHDB.so)的連結。
   * **ODBCINI**:odbc.ini檔案的位置(例如/etc/odbc.ini)。

## SAP HANA外部帳戶{#sap-external}

SAP HANA外部帳戶可讓您將Campaign執行個體連結至SAP HANA外部資料庫。

1. 在促銷活動&#x200B;**[!UICONTROL Explorer]**&#x200B;中，按一下&#x200B;**[!UICONTROL Administration]**「>」 **[!UICONTROL Platform]**「>」 **[!UICONTROL External accounts]**。

1. 按一下&#x200B;**[!UICONTROL New]**&#x200B;並選擇&#x200B;**[!UICONTROL External database]**&#x200B;作為&#x200B;**[!UICONTROL Type]**。

1. 要配置&#x200B;**[!UICONTROL SAP Hana]**&#x200B;外部帳戶，必須指定：

   * **[!UICONTROL Type]**:SAP Hana

   * **[!UICONTROL Server]**:SAP Hana伺服器的URL

   * **[!UICONTROL Account]**:使用者名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼
