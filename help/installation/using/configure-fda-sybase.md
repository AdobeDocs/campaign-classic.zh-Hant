---
product: campaign
title: 設定Sybase IQ的存取權
description: 瞭解如何在FDA中設定Sybase IQ的存取權
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0fdf8259-5cab-4a9d-adb3-6c55ec5c8851
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 1%

---

# 設定Sybase IQ的存取權 {#configure-access-to-sybase-iq}



使用行銷活動 **同盟資料存取** (FDA)選項，用於處理儲存在外部資料庫中的資訊。 請依照下列步驟設定對Sybase IQ的存取權。

1. 設定 [sybase IQ資料庫](#configuring-sybase)
1. 設定Sybase IQ [外部帳戶](#sybase-external) 在Campaign中

## sybase IQ設定 {#configuring-sybase}

若要在FDA中連線至Sybase IQ外部資料庫，需要在Adobe Campaign伺服器上設定下列其他設定。

>[!NOTE]
>
>開始之前，請確定 **unixodbc** 封裝在伺服器上。

1. 安裝 **iq_odbc**. 安裝結束時可能會發生錯誤。 可以忽略此錯誤。

1. 安裝 **iq_client_common**. 安裝結束時可能會發生Java錯誤。 可以忽略此錯誤。

1. 設定ODBC驅動程式。 可在標準檔案中執行設定：/etc/odbc.ini用於一般引數，/etc/odbcinst.ini用於宣告驅動程式：

   * **/etc/odbc.ini** (取代下列值： `<server_alias>` 個字元)：

      ```
      [ODBC Data Sources]
      <server_alias>=libdbodbc.so
      
      [<server_alias>]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      Description=<description>
      Username=<username>
      Password=<password>
      ServerName=<server_name>
      CommLinks=tcpip(host=<host>)
      ```

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      SAP SybaseIQ=Installed
      
      [SAP SybaseIQ]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      ```

1. 在LD_LIBRARY_PATH變數中新增新libodbc16.so程式庫的路徑。 若要這麼做：

   * 如果您使用customer.sh檔案宣告路徑：為LD_LIBRARY_PATH變數新增路徑/opt/sybase/IQ-16_0/lib64。
   * 否則，請使用Unix指令。

## sybase IQ外部帳戶 {#sybase-external}

sybase IQ外部帳戶可讓您將您的Campaign執行個體連線至Sybase IQ外部資料庫。

1. 從Campaign **[!UICONTROL Explorer]**，按一下 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 按一下 **[!UICONTROL New]** 並選取 **[!UICONTROL External database]** 作為 **[!UICONTROL Type]**.

1. 若要設定 **[!UICONTROL Sybase IQ]** 外部帳戶，您必須指定：

   * **[!UICONTROL Type]**: ODBC (Sybase ASE、Sybase IQ)

   * **[!UICONTROL Server]**：對應至ODBC連線(`<server_alias>`)定義於步驟5。 不一定是伺服器本身的名稱。

   * **[!UICONTROL Account]**：使用者名稱

   * **[!UICONTROL Password]**：使用者帳戶密碼

   * **[!UICONTROL Database]**：資料庫名稱

>[!NOTE]
>
>對於Windows，您必須在Adobe Campaign伺服器上安裝Sybase IQ使用者端並建立ODBC連線。 當Adobe Campaign伺服器(nlserver)在Windows中作為服務執行時，請務必建立系統資料來源。
