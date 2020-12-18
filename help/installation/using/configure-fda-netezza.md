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


# 配置對Netezza {#configure-access-to-netezza}的訪問

使用Campaign [Federated Data Access](../../installation/using/about-fda.md)(FDA)選項來處理儲存在外部資料庫中的資訊。 請遵循下列步驟來設定Netezza的存取權。

1. 安裝和配置[Netezza驅動程式](#netezza-config)
1. 在促銷活動中設定Netezza [外部帳戶](#netezza-external)

## Netezza配置{#netezza-config}

在FDA中連線至Netezza外部資料庫需要Adobe Campaign伺服器下的其他設定：

1. 根據您使用的作業系統，安裝Netezza的ODBC驅動程式：

   * **nz-linuxclient-v7.2.0.0.tar.** gzfor Linux。選擇與作業系統（linux或linux64）對應的資料夾，然後啟動unpack命令。 您可以保留在預設建議的儲存庫中執行的安裝：&quot;/usr/local/nz&quot;。
   * **nz-winclient-v7.2.0.0.** zippfor Windows。解壓縮檔案並啟動與您的作業系統對應的可執行指令碼：nzodbcsetup.exe或nzodbcsetup64.exe。 按照嚮導說明完成驅動程式的安裝。

1. 配置ODBC驅動程式。 配置可在標準檔案中執行：**/etc/odbc.ini**&#x200B;用於一般參數，**/etc/odbcinst.ini**&#x200B;用於聲明驅動程式。

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

   * **LD_LIBRARY_PATH**:/usr/local/nz/lib和/usr/local/nz/lib64。&quot;/usr/local/nz&quot;與安裝驅動程式時預設提供的安裝儲存庫相對應。 您需要在此處指定已為安裝選擇的儲存庫。
   * **ODBCINI**:odbc.ini檔案的位置(例如/etc/odbc.ini)。
   * **NZ_ODBC_INI_PATH**:odbc.ini檔案的位置。Netezza還需要此第二個變數來使用odbc.ini檔案。

## Netezza外部帳戶{#netezza-external}

Netezza外部帳戶可讓您將Campaign實例連接到Netezza外部資料庫。

1. 在促銷活動&#x200B;**[!UICONTROL Explorer]**&#x200B;中，按一下&#x200B;**[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;> &#39;> &#39; **[!UICONTROL External accounts]**。

1. 按一下&#x200B;**[!UICONTROL New]** ，然後選擇&#x200B;**[!UICONTROL External database]**&#x200B;作為&#x200B;**[!UICONTROL Type]**。

1. 要配置&#x200B;**[!UICONTROL Netezza]**&#x200B;外部帳戶，您必須指定：

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**:Netezza伺服器的URL

   * **[!UICONTROL Account]**:用戶名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼

   * **[!UICONTROL Database]**:資料庫的名稱

>[!NOTE]
>
>不考慮對包含自動生成的主鍵的方案的操作。
>
>該表將在模式中定義的第一個索引上使用&#x200B;**Organize on**&#x200B;子句。 由於此子句限制為1到4個Netezza列，因此此索引不能包含4個以上的列。
