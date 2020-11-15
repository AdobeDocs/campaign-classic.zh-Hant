---
title: 配置對Teradata的訪問
description: 瞭解如何在FDA中設定Teradata的存取權
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 022fe39e849ceafa6678120ff455d07432fb9a1f
workflow-type: tm+mt
source-wordcount: '1613'
ht-degree: 0%

---


# 配置對Teradata的訪問 {#configure-access-to-teradata}

使用Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA)選項來處理儲存在外部資料庫中的資訊。 請遵循下列步驟來設定Teradata的存取權。

1. 安裝和配置 [Teradata驅動程式](#teradata-config)
1. 在Campaign中設定Teradata [外部](#teradata-external) 帳戶
1. 為Teradata和 [Campaign伺服器設定](#teradata-additional-configurations) 其他設定

## Teradata組態 {#teradata-config}

您需要安裝Teradata的驅動程式，才能建置與Campaign的連線。

1. 安裝Teradata [的ODBC驅動程式](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)。

   它由三個軟體包組成，可以按以下順序安裝在Red Hat（或CentOS）/Suse上：

   * TeraGSS
   * tdicu1510（使用setup_wrapper.sh安裝）
   * tdobc1510（使用setup_wrapper.sh安裝）

1. 配置ODBC驅動程式。 配置可在標準檔案中執行： **/etc/odbc.ini** for general parameters and /etc/odbcinst.ini for sclariting drivers:

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot;與 **odbcinst.ini檔案的位置對應** 。

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      teradata=Installed
      
      [teradata]
      Driver=/opt/teradata/client/15.10/lib64/tdata.so
      APILevel=CORE
      ConnectFunctions=YYY
      DriverODBCVer=3.51
      SQLLevel=1
      ```

1. 指定Adobe Campaign伺服器的環境變數：

   * **LD_LIBRARY_PATH**:/opt/teradata/client/15.10/lib64和/opt/teradata/client/15.10/odbc_64/lib。
   * **ODBCINI**:odbc.ini檔案的位置(例如/etc/odbc.ini)。
   * **NLSPATH**:opermsgs.cat檔案的位置(/opt/teradata/client/15.10/msg/opermsgs.cat)

>[!NOTE]
>
>在FDA中連線至Teradata外部資料庫需要Adobe Campaign伺服器上執行其他設定步驟。 [進一步瞭解](#teradata-additional-configurations)。


## Teradata外部帳戶{#teradata-external}

Teradata外部帳戶可讓您將Campaign例項連接至Teradata外部資料庫。

1. 在促銷 **[!UICONTROL Explorer]**&#x200B;活動中，按 **[!UICONTROL Administration]** 一下 **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**。

1. 按一 **[!UICONTROL New]** 下並選 **[!UICONTROL External database]** 擇為 **[!UICONTROL Type]**。

   ![](assets/ext_account_19.png)

1. 若要設定外 **[!UICONTROL Teradata]** 部帳戶，您必須指定：

   * **[!UICONTROL Type]**:選擇類 **[!UICONTROL Teradata]** 型。

   * **[!UICONTROL Server]**:Teradata伺服器的URL或名稱

   * **[!UICONTROL Account]**:用於訪問Teradata資料庫的帳戶的名稱

   * **[!UICONTROL Password]**:用於連接到Teradata資料庫的口令

   * **[!UICONTROL Database]**:資料庫名稱（可選）

   * 
      * **[!UICONTROL Options]**:要通過Teradata傳遞的選項。 使用下列格式：&#39;parameter=value&#39;。 使用半欄作為值之間的分隔符。
   * 
      * **[!UICONTROL Timezone]**:Teradata中設定的時區。 [進一步瞭解](#timezone)


### 查詢色帶

當多個Adobe Campaign使用者連線至相同的FDA Teradata外部帳戶時，標籤可讓您在作業階段上設定查詢頻帶，即一組金鑰／值配對。 **[!UICONTROL Query banding]**

![](assets/ext_account_20.png)

設定此選項時，每當Campaign使用者對Teradata資料庫執行查詢時，Adobe Campaign會傳送中繼資料，其中包含與此使用者相關的索引鍵清單。 然後Teradata管理員就可以將這些資料用於稽核或管理存取權限。

>[!NOTE]
>
>For more information on **[!UICONTROL Query banding]**, refer to the [Teradata documentation](https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw).

要配置查詢條帶，請執行以下步驟：

1. 使用 **[!UICONTROL Default]** 輸入預設查詢節區，在用戶沒有關聯的查詢節區時將使用該節區。 如果此欄位留空，則沒有查詢節區的使用者將無法使用Teradata。

1. 使用欄 **[!UICONTROL Users]** 位為每個使用者指定查詢節區。 您可以根據需要添加任意數量的鍵／值對，例如priority=1;workload=high。 如果用戶未分配查詢節區，則 **[!UICONTROL Default]** 將應用該欄位。

1. 勾選方 **[!UICONTROL Active]** 塊以啟用此功能

#### 外部帳戶疑難排解 {#external-account-troubleshooting}

如果在測試連接 **TIM-030008日期&#39;2&#39;時出現以下錯誤：缺少字元(iRc=-53)** ，請確保ODBC驅動程式已正確安裝，並且已為Campaign伺服器設定了LD_LIBRARY_PATH(Linux)/PATH(Windows)。

錯誤 **ODB-240000 ODBC錯誤： [未找到Microsoft][ODBC Driver Manager] 資料源名稱，且未指定預設驅動程式。** 在Windows中執行。 Adobe Campaign預期teradata會在odbcinst.ini中命名為&#39;{teradata}&#39;。

* 啟動Campaign 18.10後，可以在外部帳戶的選項中添加ODBCDriverName=&quot;Teradata Database ODBC驅動程式16.10&quot;。 版本號可以更改，通過運行odbcad32.exe並訪問「Drivers（驅動程式）」頁籤可以找到確切的名稱。

* 如果您使用舊版的促銷活動，則必須將驅動程式安裝建立的odbcinst.ini的Teradata部分複製到名為Teradata的新部分。 Regedit可用於此情況。 如果您的基本數為latin1，則必須在選項中添 **加APICharSize=1** 。

## 其他配置 {#teradata-additional-configurations}

<!--
### Compatibility {#teradata-compatibility}

**Based in Unicode**

| Database version | Driver version |  Minimal Campaign version required |  Note |
|:-:|:-:|:-:|:-:|
| 15  |  15 |  Campaign Classic 17.9 | Under Linux: Queries with timestamp may fail (fixed in build 8937 for 18.4 and 8977 for 18.10) In debug mode, warnings relative to bad memory usage in the driver may occur. |
| 15  | 16  | Campaign Classic 17.9  | Recommended setup for a Teradata 15 database under Linux.  |
|  16 | 16  | Campaign Classic 18.10 |  Unicode characters with surrogate pairs are not fully handled. Using surrogate characters in data should work. Using surrogates in a filtering condition of a query will not work without this change. |
| 16  |  15 |  Campaign Classic 19.0 |  &nbsp; |

**Based in Latin1**

Versions previous to Adobe Campaign Classic 17.9 only supported Teradata Latin-1 database.

Starting from Adobe Campaign Classic 17.9, we now support by default Teradata database in Unicode.

Customers with a Latin-1 Teradata database migrating to a recent Campaign Classic release will have to add the parameter APICharSize=1 in the options of the external account.
-->

### 用戶配置 {#user-configuration}

外部資料庫需要以下權限：建立／刪除／執行自定義過程、建立／刪除／插入／選擇表。 如果您想在Adobe Campaign例項上使用md5和sha2函式，您也必須建立使用者模式函式。

請務必設定正確的時區。 它應符合在Adobe Campaign例項中建立的外部帳戶中所設定的內容。

Adobe Campaign不會針對它將在資料庫中建立的物件設定保護模式（後援）。 您可能需要在Adobe Campaign使用下列查詢來連線至Teradata資料庫的使用者上設定預設值：

| 禁用預設後援 |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

### MD5安裝 {#md5-installation}

如果您想在Adobe Campaign實例中使用md5函式，則必須從此頁面 [](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) (md5_20080530.zip)在Teradata資料庫上安裝用戶模式函式。

下載檔案的sha1如下： 65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e。

要安裝md5:

1. 解壓縮md5_20080530.zip檔案。

1. 轉到md5/src目錄。

1. 使用方法連接到您的Teradata資料庫。

1. 運行以下beq命令：

   ```
   .run file = hash_md5.btq
   ```

### SHA2安裝 {#sha2-installation}

如果您想在Adobe Campaign實例中使用sha2函式，則必須從此頁面 [](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) (teradata-udf-sha2-1.0.zip)在Teradata資料庫上安裝使用者模式函式。

下載檔案的sha1如下：e87438d37424836358bd3902cf1adeb629349780。

要安裝sha2:

1. 解壓縮teradata-udf-sha2-1.0.zip檔案。

1. 前往teradata-udf-sha2-1.0/src目錄。

1. 使用方法連接到您的Teradata資料庫。

1. 運行以下兩個beq命令：

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

### UDF_UTF16TO8安裝 {#UDF-UTF16TO8-installation}

如果您想在Adobe Campaign實例中使用udf_utf16to8函式，則必須從本頁的 ****[](https://downloads.teradata.com/download/tools/unicode-tool-kit) Teradataunicode工具套件(utk_release1.7.0.0.zip)在Teradata資料庫上安裝用戶模式函式。

下載檔案的sha1如下： e58235f434f52c71316a577cb48e20b97d24f470。

若要安裝udf_utf16to8:

1. 解壓縮utk_release1.7.0.0.zip檔案。

1. 在擷取的檔案中尋找udf_utf16to8.o，並導覽至包含檔案的目錄。 它應命名為utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01 Teradata UDFs/suselinux-x8664/udf_installation/。

1. 使用方法連接到您的Teradata資料庫。

1. 鍵入以下beq命令：

   ```
   REPLACE FUNCTION udf_utf16to8 (
   inputString VARCHAR(8000) CHARACTER SET UNICODE
   ) RETURNS VARCHAR(16000) CHARACTER SET LATIN
   LANGUAGE C
   NO SQL
   EXTERNAL NAME 'CO!i18n103!udf_utf16to8.o!F!udf_utf16to8'
   PARAMETER STYLE SQL;
   
   -- Test: should return 410042
   SELECT CAST(Char2HexInt(UDF_UTF16to8(_UNICODE'004100000042'XC)) AS VARCHAR(100));
   ```

## Linux的促銷活動伺服器設定 {#campaign-server-linux}

安裝驅動程式時需要以下操作：

* Teradata ODBC驅動程式，可在本頁中找 [到](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Teradata工具與公用程式（用於大量載入），可在本頁中找 [到](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

檔案名和sha1:

* tdobc1620_linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f44fd

* TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dba6f8639387b19c563

如果您的Linux散發沒有套件，您可以如CentOS 7中所述安裝（例如使用docker），然後複製Adobe Campaign伺服器上/opt/teradata的內容。

### ODBC驅動程式安裝 {#odbc-installation}

要安裝ODBC驅動程式：

1. 解壓縮tdobc1620__linux_indep.16.20.00.00-1.tar.gz檔案。

1. 前往tdobc1620目錄。

1. 您可能需要修正安裝指令碼：

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. 運行setup_wrapper.sh。

### Teradata工具和公用程式安裝 {#teradata-tools-installation}

安裝工具：

1. 解壓縮TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz檔案。

1. 前往TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu目錄。

1. 運行setup_wrapper.sh。

1. 前往TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2目錄。

1. 運行setup_wrapper.sh。

1. 前往TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase目錄。

1. 運行setup_wrapper.sh。

1. libtelapi.so檔案應可在/opt/teradata/client/16.20/lib64中使用。

## Windows的促銷活動伺服器設定 {#campaign-server-windows}

您首先需要下載適用於Windows的Teradata工具和公用程式。 您可從此頁面下 [載](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

確保安裝ODBC驅動程式和Teradata Parallel Transporter Base。 它將安裝用於在Teradata資料庫上批量載入的telapi.dll。

確保驅動程式和實用程式的路徑位於nlserver在執行期間將具有的PATH變數中。 預設情況下，路徑為C:\Program Files (x86)\Teradata\Client\15.10\bin on Windows 32 bits or C:\Program Files\Teradata\Client\15.10\bin on 64 bit)。

## 時區 {#timezone}

Teradata使用非標準的時區名稱，您可以在 [Teradata網站上找到清單](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA)。 Adobe Campaign會嘗試將外部設定中的時區轉換為Teradata所瞭解的時區。 如果找不到對應，則會找到會話的壁櫥GMT+X（或GMT-X）時區，日誌中會出現警告。

轉換完成時，會讀取名為teradata_timezones.txt的檔案，該檔案應位於下列datakit目錄：/usr/local/neolane/nl6/datakit under linux. 如果您編輯此檔案，請務必連絡Adobe Campaign團隊，以變更原始碼，否則下次促銷活動更新時，此檔案將會覆寫。

使用-verbose開關運行nlserver時，將指示用於連接的時區，例如：

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

如果使用的時區不正確，則可在外部帳戶上新增名為「TimeZoneName」的選項。 在這種情況下，請使用Teradata值，例如&quot;TimeZoneName=Europe Central&quot;。

當在Teradata檔案中使用大量載入或「快速載入」時，Campaign無法指出時區。 因此，建議您設定促銷活動用來連線之使用者的預設時區：

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```
