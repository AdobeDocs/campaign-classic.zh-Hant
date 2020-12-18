---
solution: Campaign Classic
product: campaign
title: 配置對Sybase IQ的訪問
description: 瞭解如何在FDA中配置對Sybase IQ的訪問
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# 配置對Sybase IQ {#configure-access-to-sybase-iq}的訪問

使用Campaign **Federated Data Access**(FDA)選項來處理儲存在外部資料庫中的資訊。 按照以下步驟配置對Sybase IQ的訪問。

1. 配置[Sybase IQ資料庫](#configuring-sybase)
1. 在Campaign中配置Sybase IQ [外部帳戶](#sybase-external)

## Sybase IQ配置{#configuring-sybase}

在FDA中連接到Sybase IQ外部資料庫需要在Adobe Campaign伺服器上進行以下其他配置。

>[!NOTE]
>
>在啟動之前，請確定&#x200B;**unixodbc**&#x200B;軟體包在伺服器上。

1. 安裝&#x200B;**iq_odbc**。 安裝結束時可能會發生錯誤。 此錯誤可以忽略。

1. 安裝&#x200B;**iq_client_common**。 安裝結束時可能會發生Java錯誤。 此錯誤可以忽略。

1. 配置ODBC驅動程式。 配置可在標準檔案中執行：/etc/odbc.ini，用於常規參數，/etc/odbcinst.ini，用於聲明驅動程式：

   * **/etc/odbc.ini** (以您自己的方式 `<server_alias>` 取代字元等值):

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

1. 在LD_LIBRARY_PATH變數中添加新libodbc16.so庫的路徑。 若要這麼做：

   * 如果您使用customer.sh檔案來宣告您的路徑：為LD_LIBRARY_PATH變數添加路徑/opt/sybase/IQ-16_0/lib64。
   * 否則，請使用Unix命令。

## Sybase IQ外部帳戶{#sybase-external}

Sybase IQ外部帳戶允許您將Campaign實例連接到Sybase IQ外部資料庫。

1. 在促銷活動&#x200B;**[!UICONTROL Explorer]**&#x200B;中，按一下&#x200B;**[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;> &#39;> &#39; **[!UICONTROL External accounts]**。

1. 按一下&#x200B;**[!UICONTROL New]** ，然後選擇&#x200B;**[!UICONTROL External database]**&#x200B;作為&#x200B;**[!UICONTROL Type]**。

1. 要配置&#x200B;**[!UICONTROL Sybase IQ]**&#x200B;外部帳戶，您必須指定：

   * **[!UICONTROL Type]**:ODBC(Sybase ASE、Sybase IQ)

   * **[!UICONTROL Server]**:與步驟5中定義的ODBC`<server_alias>`連接()相對應。不一定是伺服器本身的名稱。

   * **[!UICONTROL Account]**:用戶名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼

   * **[!UICONTROL Database]**:資料庫的名稱

>[!NOTE]
>
>對於Windows，必須在Adobe Campaign伺服器上安裝Sybase IQ客戶端並建立ODBC連接。 請確定您在Windows中以服務的形式執行Adobe Campaign伺服器(nlserver)時建立系統資料來源。

