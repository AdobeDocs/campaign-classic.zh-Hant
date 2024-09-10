---
product: campaign
title: 設定Netezza的存取權
description: 瞭解如何在FDA中設定Netezza存取權
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: b148d34b-4060-4c54-9cb2-9e712a7c17d7
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# 設定Netezza的存取權 {#configure-access-to-netezza}



使用Campaign [同盟資料存取](../../installation/using/about-fda.md) (FDA)選項來處理儲存在外部資料庫中的資訊。 請依照下列步驟設定對Netezza的存取權。

1. 安裝及設定[Netezza驅動程式](#netezza-config)
1. 在Campaign中設定Netezza[外部帳戶](#netezza-external)

## netezza設定 {#netezza-config}

若要在FDA中連線至Netezza外部資料庫，必須在Adobe Campaign伺服器上設定以下其他設定：

1. 根據您使用的作業系統，安裝用於Netezza的ODBC驅動程式：

   * 適用於Linux的&#x200B;**nz-linuxclient-v7.2.0.0.tar.gz** 選取與作業系統（linux或linux64）對應的資料夾，然後啟動unpack指令。 您可以將安裝保留在預設建議的存放庫中執行：「/usr/local/nz」。
   * **nz-winclient-v7.2.0.0.zip** for Windows。 解壓縮檔案並啟動與您的作業系統對應的可執行指令碼： nzodbcsetup.exe或nzodbcsetup64.exe。 請依照助理員指示完成驅動程式的安裝。

1. 設定ODBC驅動程式。 可在標準檔案中執行組態： **/etc/odbc.ini**&#x200B;用於一般引數，**/etc/odbcinst.ini**&#x200B;用於宣告驅動程式。

   * **/etc/odbc.ini**

     ```
     [ODBC]
     InstallDir=/etc/
     ```

     「InstallDir」對應至odbcinst.ini檔案的位置。

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

   * **LD_LIBRARY_PATH**： /usr/local/nz/lib和/usr/local/nz/lib64。 「/usr/local/nz」對應於安裝驅動程式時預設提供的安裝存放庫。 您必須在此指定您為安裝選取的存放庫。
   * **ODBCINI**： odbc.ini檔案的位置(例如/etc/odbc.ini)。
   * **NZ_ODBC_INI_PATH**： odbc.ini檔案的位置。 使用odbc.ini檔案時，Netezza也需要此第二個變數。

## netezza外部帳戶 {#netezza-external}

netezza外部帳戶可讓您將您的Campaign執行個體連線至Netezza外部資料庫。

1. 從行銷活動&#x200B;**[!UICONTROL Explorer]**，按一下&#x200B;**[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 按一下&#x200B;**[!UICONTROL New]**&#x200B;並選取&#x200B;**[!UICONTROL External database]**&#x200B;作為&#x200B;**[!UICONTROL Type]**。

1. 若要設定&#x200B;**[!UICONTROL Netezza]**&#x200B;外部帳戶，您必須指定：

   * **[!UICONTROL Type]**：Netezza

   * **[!UICONTROL Server]**：Netezza伺服器的URL

   * **[!UICONTROL Account]**：使用者名稱

   * **[!UICONTROL Password]**：使用者帳戶密碼

   * **[!UICONTROL Database]**：資料庫的名稱

>[!NOTE]
>
>未考慮對包含自動產生之主索引鍵的結構描述進行的操作。
>
>資料表將在結構描述中定義的第一個索引上使用&#x200B;**Organize on**&#x200B;子句。 由於此子句限製為1到4個具有Netezza的資料行，所以此索引不能包含超過4個資料行。
