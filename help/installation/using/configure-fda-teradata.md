---
product: campaign
title: 配置對Teradata的訪問
description: 了解如何在FDA中設定Teradata的存取權
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3a5856c3-b642-4722-97ff-6ae7107efdbe
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1613'
ht-degree: 0%

---

# 配置對Teradata的訪問 {#configure-access-to-teradata}

![](../../assets/v7-only.svg)

使用Campaign [同盟資料存取](../../installation/using/about-fda.md) (FDA)處理儲存在外部資料庫中的資訊的選項。 請依照下列步驟來設定對Teradata的存取權。

1. 安裝和配置 [Teradata驅動程式](#teradata-config)
1. 設定Teradata [外部帳戶](#teradata-external) 在Campaign
1. 設定 [其他設定](#teradata-additional-configurations) (適用於Teradata和Campaign伺服器)

## Teradata配置 {#teradata-config}

您需要安裝Teradata的驅動程式，才能實作與Campaign的連線。

1. 安裝 [用於Teradata的ODBC驅動程式](https://downloads.teradata.com/download/connectivity/odbc-driver/linux).

   它由三個軟體包組成，可以按以下順序安裝在Red Hat（或CentOS）/Suse上：

   * TeraGSS
   * tdicu1510（使用setup_wrapper.sh安裝）
   * tdodbc1510（使用setup_wrapper.sh安裝）

1. 配置ODBC驅動程式。 可在標準檔案中執行設定： **/etc/odbc.ini** 對於常規參數，對於聲明驅動程式，請使用/etc/odbcinst.ini:

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot;對應於 **odbcinst.ini** 檔案。

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
   * **奧德比尼**:odbc.ini檔案的位置(例如/etc/odbc.ini)。
   * **NLSPATH**:opermsgs.cat檔案的位置(/opt/teradata/client/15.10/msg/opermsgs.cat)

>[!NOTE]
>
>在FDA中連線至Teradata外部資料庫需要在Adobe Campaign伺服器上執行額外的設定步驟。 [深入瞭解](#teradata-additional-configurations)。

## Teradata外部帳戶{#teradata-external}

teradata外部帳戶可讓您將Campaign執行個體連結至Teradata外部資料庫。

1. 從促銷活動 **[!UICONTROL Explorer]**，按一下 **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 按一下 **[!UICONTROL New]** 選取 **[!UICONTROL External database]** as **[!UICONTROL Type]**.

   ![](assets/ext_account_19.png)

1. 若要設定 **[!UICONTROL Teradata]** 外部帳戶，您必須指定：

   * **[!UICONTROL Type]**:選擇 **[!UICONTROL Teradata]** 類型。

   * **[!UICONTROL Server]**:您的Teradata伺服器的URL或名稱

   * **[!UICONTROL Account]**:用於訪問Teradata資料庫的帳戶名

   * **[!UICONTROL Password]**:用於連接到Teradata資料庫的密碼

   * **[!UICONTROL Database]**:資料庫名稱（可選）

   * **[!UICONTROL Options]**:要傳遞的選項Teradata。 使用下列格式：&#39;parameter=value&#39;。 使用半欄作為值之間的分隔符。

   * **[!UICONTROL Timezone]**:teradata中設定的時區。 [了解更多](#timezone)

### 查詢區

當多個Adobe Campaign使用者連線至相同的FDATeradata外部帳戶時， **[!UICONTROL Query banding]** 索引標籤可讓您在工作階段上設定查詢頻段，即一組索引鍵/值組。

![](assets/ext_account_20.png)

設定此選項時，每當Campaign使用者對Teradata資料庫執行查詢時，Adobe Campaign就會傳送中繼資料，其中包含與此使用者相關聯的索引鍵清單。 然後，Teradata管理員便可將此資料用於稽核或管理存取權限。

>[!NOTE]
>
>如需 **[!UICONTROL Query banding]**，請參閱 [Teradata檔案](https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw).

要配置「查詢段」，請執行以下步驟：

1. 使用  **[!UICONTROL Default]** 要輸入預設查詢帶，在用戶沒有關聯的查詢帶時將使用該帶。 如果此欄位留空，則沒有查詢帶的使用者將無法使用Teradata。

1. 使用 **[!UICONTROL Users]** 欄位來指定每個使用者的查詢頻段。 您可以新增所需的索引鍵/值組數，例如priority=1;workload=high。 如果用戶未分配查詢帶，則 **[!UICONTROL Default]** 欄位。

1. 檢查 **[!UICONTROL Active]** 啟用此功能的方塊

#### 外部帳戶疑難排解 {#external-account-troubleshooting}

如果在測試連線時出現下列錯誤 **TIM-030008日期&#39;2&#39;:缺少字元(iRc=-53)** 請確定已正確安裝ODBC驅動程式，並且已為Campaign伺服器設定LD_LIBRARY_PATH(Linux)/ PATH(Windows)。

錯誤 **ODB-240000 ODBC錯誤： [Microsoft][ODBC Driver Manager] 未找到資料源名稱，且未指定預設驅動程式。** 使用16.X驅動程式時，在Windows中發生。 Adobe Campaign預期teradata在odbcinst.ini中命名為「{teradata}」。

* 從Campaign 18.10開始，您可以在外部帳戶的選項中新增ODBCDriverName=&quot;Teradata資料庫ODBC驅動程式16.10&quot;。 版本號可以更改，通過運行odbcad32.exe並訪問「驅動程式」(Drivers)頁簽，可以找到確切的名稱。

* 如果您使用舊版的Campaign，則必須將驅動程式安裝所建立的odbcinst.ini的Teradata區複製到名為Teradata的新區段。 Regedit可用於此情況。 如果您的基數為latin1，則必須新增 **APICharSize=1** 中。

## 其他設定 {#teradata-additional-configurations}

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

### 使用者設定 {#user-configuration}

外部資料庫需要以下權限：建立/刪除/執行自定義過程，建立/刪除/插入/選擇表。 如果您想在Adobe Campaign執行個體上使用md5和sha2函式，也可能必須建立使用者模式函式。

請務必設定正確的時區。 它應符合將在Adobe Campaign例項中建立的外部帳戶中設定的內容。

Adobe Campaign不會針對將在資料庫中建立的物件設定保護模式（後援）。 您可能需要對Adobe Campaign將使用來連線至Teradata資料庫的使用者設定預設值，使用下列查詢：

| 禁用預設回退 |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

### MD5安裝 {#md5-installation}

如果要在Adobe Campaign實例中使用md5函式，則必須從此在Teradata資料庫上安裝用戶模式函式 [頁面](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) (md5_20080530.zip)。

下載檔案的sha1如下：65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e。

安裝md5:

1. 將md5_20080530.zip檔案解壓縮。

1. 轉到md5/src目錄。

1. 使用beq連接到Teradata資料庫。

1. 執行下列beq命令：

   ```
   .run file = hash_md5.btq
   ```

### SHA2安裝 {#sha2-installation}

如果您想在Adobe Campaign例項中使用sha2函式，必須透過此在Teradata資料庫上安裝使用者模式函式 [頁面](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) (teradata-udf-sha2-1.0.zip)。

下載檔案的sha1如下e87438d37424836358bd3902cf1adeb629349780。

安裝sha2:

1. 將teradata-udf-sha2-1.0.zip檔案解壓縮。

1. 前往teradata-udf-sha2-1.0/src目錄。

1. 使用beq連接到Teradata資料庫。

1. 執行下列兩個beq命令：

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

### UDF_UTF16TO8安裝 {#UDF-UTF16TO8-installation}

如果您想在Adobe Campaign例項中使用udf_utf16to8函式，則必須從以下位置將使用者模式函式安裝在Teradata資料庫上： **Teradataunicode工具套件** 這個 [頁面](https://downloads.teradata.com/download/tools/unicode-tool-kit) (utk_release1.7.0.0.zip)。

下載檔案的sha1如下e58235f434f52c71316a577cb48e20b97d24f470。

要安裝udf_utf16to8:

1. 將utk_release1.7.0.0.zip檔案解壓縮。

1. 在擷取的檔案中尋找udf_utf16to8.o，並導覽至包含檔案的目錄。 它的名稱應為utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01TeradataUDFs/suselinux-x8664/udf_installation/。

1. 使用beq連接到Teradata資料庫。

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

## 適用於Linux的Campaign伺服器設定 {#campaign-server-linux}

安裝驅動程式時需要：

* TeradataODBC驅動程式，可在此中找到 [頁面](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Teradata工具和實用程式（用於批量載入），可在此 [頁面](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

檔案名和sha1:

* tdodbc1620__linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f44fd

* TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbbaa6f8639387b19c563

如果您的Linux發佈沒有套件，您可以依照CentOS 7上所述（例如使用docker）安裝，然後複製Adobe Campaign伺服器上/opt/teradata的內容。

### ODBC驅動程式安裝 {#odbc-installation}

安裝ODBC驅動程式：

1. 解壓tdodbc1620__linux_indep.16.20.00.00-1.tar.gz檔案。

1. 轉到tdodbc1620目錄。

1. 您可能需要修正設定指令碼：

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. 運行setup_wrapper.sh。

### Teradata工具和實用程式安裝 {#teradata-tools-installation}

安裝工具：

1. 解壓TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz檔案。

1. 轉到TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu目錄。

1. 運行setup_wrapper.sh。

1. 轉到TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2目錄。

1. 運行setup_wrapper.sh。

1. 轉到TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase目錄。

1. 運行setup_wrapper.sh。

1. libtelapi.so檔案應可在/opt/teradata/client/16.20/lib64中使用。

## 適用於Windows的Campaign伺服器設定 {#campaign-server-windows}

您首先需要下載Windows適用的Teradata工具和實用程式。 您可以從這裡下載 [頁面](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

確保安裝ODBC驅動程式和Teradata並行傳輸庫。 它將安裝用於在Teradata資料庫上進行批量載入的telapi.dll。

確保驅動程式和實用程式的路徑位於nlserver在執行期間將具有的PATH變數中。 預設情況下，路徑為C:\Program Files (x86)\Teradata\Client\15.10\bin on Windows 32 bits or C:\Program Files\Teradata\Client\15.10\bin on 64 bit)。

## 時區 {#timezone}

Teradata使用的時區名稱不是標準名稱，您可以在 [Teradata網站](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA). Adobe Campaign會嘗試將外部設定中指定的時區轉換為Teradata了解的時區。 如果找不到通信，則會找到工作階段的壁櫥GMT+X（或GMT-X）時區，記錄中會出現警告。

轉換完成，會讀取檔名為「teradata時區.txt」的檔案，該檔案應位於下列datakit目錄中：在linux下/usr/local/neolane/nl6/datakit。 如果您編輯此檔案，請務必聯絡Adobe Campaign團隊，在原始碼中進行變更，否則下次促銷活動更新時將會覆寫此檔案。

使用 — verbose開關運行nlserver時，將指示用於連接的時區，例如：

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

如果使用的時區不正確，可在外部帳戶上新增名為「TimeZoneName」的選項。 在這種情況下，請使用Teradata值，例如&quot;TimeZoneName=Europe Central&quot;。

在Teradata檔案中使用大量載入或「快速載入」時，Campaign無法指出時區。 因此，建議您設定Campaign用來連線之使用者的預設時區：

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```
