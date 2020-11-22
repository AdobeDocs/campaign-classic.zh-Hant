---
solution: Campaign Classic
product: campaign
title: 配置對Netezza的訪問
description: 瞭解如何設定FDA的Netezza存取權
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# 配置對Netezza的訪問 {#configure-access-to-netezza}

使用Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA)選項來處理儲存在外部資料庫中的資訊。 請遵循下列步驟來設定Netezza的存取權。

1. 安裝和配置 [Netezza驅動程式](#netezza-config)
1. 在促銷活動中設 [定Netezza外部](#netezza-external) 帳戶

## Netezza配置 {#netezza-config}

在FDA中連線至Netezza外部資料庫需要Adobe Campaign伺服器下的其他設定：

1. 根據您使用的作業系統，安裝Netezza的ODBC驅動程式：

   * **nz-linuxclient-v7.2.0.0.tar.gz** for Linux。 選擇與作業系統（linux或linux64）對應的資料夾，然後啟動unpack命令。 您可以保留在預設建議的儲存庫中執行的安裝：&quot;/usr/local/nz&quot;。
   * **nz-winclient-v7.2.0.0.zip** for Windows。 解壓縮檔案並啟動與您的作業系統對應的可執行指令碼：nzodbcsetup.exe或nzodbcsetup64.exe。 按照嚮導說明完成驅動程式的安裝。

1. 配置ODBC驅動程式。 配置可在標準檔案中執行： **/etc/odbc.ini** ，用於一般參數， **/etc/odbcinst.ini** ，用於聲明驅動程式。

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot;與odbcinst.ini檔案的位置相對應。

   * **/etc/odbcinst.ini**

      ```
      [ODBC Drivers]
      NetezzaSQL = Installed
      
      [NetezzaSQL]
      Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
      Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
      APILevel         = 1
      ConnectFunctions = YYN
      Description      = Netezza ODBC driver
      DriverODBCVer    = 03.51
      DebugLogging     = false
      LogPath          = /tmp
      UnicodeTranslationOption = utf8
      CharacterTranslationOption = all
      PreFetch         = 256
      Socket           = 16384
      ```

1. 指定Adobe Campaign伺服器的環境變數：

   * **LD_LIBRARY_PATH**:/usr/local/nz/lib和/usr/local/nz/lib64。 &quot;/usr/local/nz&quot;與安裝驅動程式時預設提供的安裝儲存庫相對應。 您需要在此處指定已為安裝選擇的儲存庫。
   * **ODBCINI**:odbc.ini檔案的位置(例如/etc/odbc.ini)。
   * **NZ_ODBC_INI_PATH**:odbc.ini檔案的位置。 Netezza還需要此第二個變數來使用odbc.ini檔案。

## Netezza外部帳戶 {#netezza-external}

Netezza外部帳戶可讓您將Campaign實例連接到Netezza外部資料庫。

1. 在促銷 **[!UICONTROL Explorer]**&#x200B;活動中，按 **[!UICONTROL Administration]** 一下「>」 **[!UICONTROL Platform]** 「>」 **[!UICONTROL External accounts]**。

1. 按一 **[!UICONTROL New]** 下並選 **[!UICONTROL External database]** 擇為 **[!UICONTROL Type]**。

1. 若要設定外 **[!UICONTROL Netezza]** 部帳戶，您必須指定：

   * **[!UICONTROL Type]**:內泰扎

   * **[!UICONTROL Server]**:Netezza伺服器的URL

   * **[!UICONTROL Account]**:用戶名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼

   * **[!UICONTROL Database]**:資料庫的名稱

>[!NOTE]
>
>不考慮對包含自動生成的主鍵的方案的操作。
>
>表將在模式中定義的第 **一個索引上使用** Organize on子句。 由於此子句限制為1到4個Netezza列，因此此索引不能包含4個以上的列。
