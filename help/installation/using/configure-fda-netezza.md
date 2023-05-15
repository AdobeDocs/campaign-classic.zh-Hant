---
product: campaign
title: 配置訪問Netezza
description: 了解如何在FDA中設定Netezza存取權
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: b148d34b-4060-4c54-9cb2-9e712a7c17d7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# 配置訪問Netezza {#configure-access-to-netezza}



使用Campaign [同盟資料存取](../../installation/using/about-fda.md) (FDA)處理儲存在外部資料庫中的資訊的選項。 請依照下列步驟來設定存取Netezza。

1. 安裝和配置 [Netezza驅動程式](#netezza-config)
1. 設定Netezza [外部帳戶](#netezza-external) 在Campaign

## Netezza配置 {#netezza-config}

在FDA中連線至Netezza外部資料庫需要Adobe Campaign伺服器下方的其他設定：

1. 根據您使用的作業系統安裝Netezza的ODBC驅動程式：

   * **nz-linuxclient-v7.2.0.0.tar.gz** Linux版。 選擇與作業系統（linux或linux64）對應的資料夾，然後啟動解壓縮命令。 您可以讓安裝程式在預設建議的存放庫中執行：&quot;/usr/local/nz&quot;。
   * **nz-winclient-v7.2.0.0 zip** Windows版。 解壓縮檔案，然後啟動與作業系統對應的執行檔指令碼：nzodbcsetup.exe或nzodbcsetup64.exe。 按照嚮導說明完成驅動程式的安裝。

1. 配置ODBC驅動程式。 可在標準檔案中執行設定： **/etc/odbc.ini** 一般參數和 **/etc/odbcinst.ini** 用於聲明司機。

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot;對應於odbcinst.ini檔案的位置。

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

   * **LD_LIBRARY_PATH**:/usr/local/nz/lib和/usr/local/nz/lib64。 &quot;/usr/local/nz&quot;對應於安裝驅動程式時預設提供的安裝儲存庫。 您需要在此處指定您為安裝選擇的儲存庫。
   * **奧德比尼**:odbc.ini檔案的位置(例如/etc/odbc.ini)。
   * **NZ_ODBC_INI_PATH**:odbc.ini檔案的位置。 Netezza還需要此第二個變數才能使用odbc.ini檔案。

## Netezza外部帳戶 {#netezza-external}

netezza外部帳戶可讓您將Campaign執行個體連結至Netezza外部資料庫。

1. 從促銷活動 **[!UICONTROL Explorer]**，按一下 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 按一下 **[!UICONTROL New]** 選取 **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. 若要設定 **[!UICONTROL Netezza]** 外部帳戶，您必須指定：

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**:netezza伺服器的URL

   * **[!UICONTROL Account]**:使用者名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼

   * **[!UICONTROL Database]**:資料庫的名稱

>[!NOTE]
>
>系統不會考慮包含自動產生主要金鑰之結構的操作。
>
>表格將使用 **組織** 子句。 由於此子句限制為1到4列，且Netezza，因此此索引不能包含超過4列。
