---
product: campaign
title: 設定SAP HANA的存取權
description: 瞭解如何在FDA中設定SAP HANA存取權
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# 設定SAP HANA的存取權 {#configure-access-to-sap-hana}



使用Campaign [同盟資料存取](../../installation/using/about-fda.md) (FDA)選項來處理儲存在外部資料庫中的資訊。 請依照下列步驟設定對SAP HANA的存取權。

1. 設定[SAP HANA資料庫](#sap-config)
1. 在Campaign中設定SAP HANA[外部帳戶](#sap-external)

## SAP HANA驅動程式 {#sap-config}

在FDA中連線至SAP HANA外部資料庫時，需要Adobe Campaign伺服器上的特定額外設定：

1. 根據您使用的作業系統，安裝用於SAP HANA的ODBC驅動程式：

   * 適用於Linux的&#x200B;**hdb_client_linux.tgz**。 解壓縮之後，請啟動hdbinst指令，然後依照指示完成驅動程式的安裝。
   * 適用於Windows的&#x200B;**hdb_client_windows.zip**。 解壓縮檔案並啟動可執行檔： **hdbinst.exe**。 請依照助理員指示完成驅動程式的安裝。

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

     「InstallDir」對應至&#x200B;**odbcinst.ini**&#x200B;檔案的位置。

   * **/etc/odbcinst.ini**

     ```
     [HDBODBC]
     Description = "SmartCloudPT HANA"
     Driver = /usr/sap/hdbclient/libodbcHDB.so
     ```

1. 指定Adobe Campaign伺服器的環境變數：

   * **LD_LIBRARY_PATH**：依預設，它應該包含您SAP Hana使用者端的連結(/usr/sap/hdbclient/libodbcHDB.so)。
   * **ODBCINI**： odbc.ini檔案的位置(例如/etc/odbc.ini)。

## SAP HANA外部帳戶{#sap-external}

SAP HANA外部帳戶可讓您將您的Campaign執行個體連線至SAP HANA外部資料庫。

1. 從行銷活動&#x200B;**[!UICONTROL Explorer]**，按一下&#x200B;**[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 按一下&#x200B;**[!UICONTROL New]**&#x200B;並選取&#x200B;**[!UICONTROL External database]**&#x200B;作為&#x200B;**[!UICONTROL Type]**。

1. 若要設定&#x200B;**[!UICONTROL SAP Hana]**&#x200B;外部帳戶，您必須指定：

   * **[!UICONTROL Type]**： SAP Hana

   * **[!UICONTROL Server]**： SAP Hana伺服器的URL

   * **[!UICONTROL Account]**：使用者名稱

   * **[!UICONTROL Password]**：使用者帳戶密碼
