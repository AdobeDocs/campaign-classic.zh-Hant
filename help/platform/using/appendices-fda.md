---
title: 附錄
seo-title: FDA附錄
description: FDA附錄
seo-description: null
page-status-flag: never-activated
uuid: 2596fabc-679a-45c8-a62a-165c221654b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: a84a73a9-9930-449f-8b81-007a0e9d5233
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1416'
ht-degree: 0%

---


# 附錄 {#fda-appendices}

## Teradata其他配置 {#teradata-configuration}

### 相容性 {#teradata-compatibility}

**以Unicode為基礎**

| 資料庫版本 | 驅動程式版本 | 需要的促銷活動版本最低 | 注意 |
|:-:|:-:|:-:|:-:|
| 15 | 15 | Campaign Classic 17.9 | 在Linux下：具有時間戳記的查詢可能失敗（在build 8937中針對18.4修正，在8977中針對18.10修正）在除錯模式中，可能會發生與驅動程式中記憶體使用不良相關的警告。 |
| 15 | 16 | Campaign Classic 17.9 | 建議在Linux下為Teradata 15資料庫設定。 |
| 16 | 16 | Campaign Classic 18.10 | 未完全處理具有替代對的Unicode字元。 在資料中使用替代字元應能運作。 若未進行此變更，在查詢的篩選條件中使用替代項將無法運作。 |
| 16 | 15 | 不支援 |   |

**以拉丁語為基礎1**

Adobe Campaign Classic 17.9之前的版本僅支援Teradata Latin-1資料庫。

從Adobe Campaign Classic 17.9開始，我們現在依預設支援Unicode中的Teradata資料庫。

擁有Latin-1 Teradata資料庫的客戶必須在外部帳戶的選項中新增參數APICharSize=1，才能移轉至最新的Campaign Classic版本。

### 資料庫配置 {#database-configuration}

#### 用戶配置 {#user-configuration}

需要下列權利：建立／刪除／執行自定義過程、建立／刪除／插入／選擇表。 如果您想在Adobe Campaign例項上使用md5和sha2函式，您也必須建立使用者模式函式。

請務必設定正確的時區。 它應符合在Adobe Campaign例項中建立的外部帳戶中所設定的內容。

Adobe Campaign不會針對它將在資料庫中建立的物件設定保護模式（後援）。 您可能需要在Adobe Campaign使用下列查詢來連線至Teradata資料庫的使用者上設定預設值：

| 禁用預設後援 |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

#### MD5安裝 {#md5-installation}

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

#### SHA2安裝 {#sha2-installation}

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

#### UDF_UTF16TO8安裝 {#UDF-UTF16TO8-installation}

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

### Linux的促銷活動伺服器設定 {#campaign-server-linux}

安裝驅動程式時需要以下操作：

* Teradata ODBC驅動程式，可在本頁中找 [到](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Teradata工具與公用程式（用於大量載入），可在本頁中找 [到](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

檔案名和sha1:

* tdobc1620_linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f44fd

* TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dba6f8639387b19c563

如果您的Linux散發沒有套件，您可以如CentOS 7中所述安裝（例如使用docker），然後複製Adobe Campaign伺服器上/opt/teradata的內容。

#### ODBC驅動程式安裝 {#odbc-installation}

要安裝ODBC驅動程式：

1. 解壓縮tdobc1620__linux_indep.16.20.00.00-1.tar.gz檔案。

1. 前往tdobc1620目錄。

1. 您可能需要修正安裝指令碼：

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. 運行setup_wrapper.sh。

#### Teradata工具和公用程式安裝 {#teradata-tools-installation}

安裝工具：

1. 解壓縮TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz檔案。

1. 前往TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu目錄。

1. 運行setup_wrapper.sh。

1. 前往TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2目錄。

1. 運行setup_wrapper.sh。

1. 前往TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase目錄。

1. 運行setup_wrapper.sh。

1. libtelapi.so檔案應可在/opt/teradata/client/16.20/lib64中使用。

#### 驅動程式配置 {#driver-configuration}

To learn more on driver configuration, refer to this [section](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

#### 環境變數 {#environment-varaiables}

若要進一步瞭解Adobe Campaign伺服器的環境變數，請參閱本 [節](../../platform/using/legacy-connectors.md#configure-access-to-teradata)。

### Windows的促銷活動伺服器設定 {#campaign-server-windows}

您首先需要下載適用於Windows的Teradata工具和公用程式。 您可從此頁面下 [載](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

確保安裝ODBC驅動程式和Teradata Parallel Transporter Base。 它將安裝用於在Teradata資料庫上批量載入的telapi.dll。

確保驅動程式和實用程式的路徑位於nlserver在執行期間將具有的PATH變數中。 預設情況下，路徑為C:\Program Files (x86)\Teradata\Client\15.10\bin on Windows 32 bits or C:\Program Files\Teradata\Client\15.10\bin on 64 bit)。

### 外部帳戶疑難排解 {#external-account-troubleshooting}

如果在測試連接 **TIM-030008日期&#39;2&#39;時出現以下錯誤：缺少字元(iRc=-53)** ，請確保ODBC驅動程式已正確安裝，並且已為Campaign伺服器設定了LD_LIBRARY_PATH(Linux)/PATH(Windows)。

錯誤 **ODB-240000 ODBC錯誤：[未找到Microsoft][ODBC Driver Manager]資料源名稱，且未指定預設驅動程式。** 在Windows中執行。 Adobe Campaign預期teradata會在odbcinst.ini中命名為&#39;{teradata}&#39;。
如果您有18.10 Adobe Campaign伺服器版本，可在外部帳戶的選項中新增ODBCDriverName=&quot;Teradata Database ODBC Driver 16.10&quot;。 版本號可以更改，通過運行odbcad32.exe並訪問「Drivers（驅動程式）」頁籤可以找到確切的名稱。
對於18.10以下版本，您必須將驅動程式安裝建立的odbcinst.ini的Teradata部分複製到名為Teradata的新部分，在本例中可使用regedit。

如果您的基本數為latin1，則必須在選項中添加APICharSize=1。

### 時區 {#timezone}

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

## MySQL 5.7配置 {#mysql-57-configuration}

### 伺服器組態 {#server-configuration-mysql}

伺服器配置不需要任何特定的安裝步驟。 Adobe Campaign應使用latin1資料庫、MySQL上的預設資料庫或Unicode資料庫。

### 驅動程式安裝 {#driver-installation-mysql}

#### Debian {#debian-mysql}

從此頁下載mysql-apt-config.deb [](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en)。

安裝客戶端庫：

```
$ dpkg -i mysql-apt-config_*_all.deb # choose mysql-5.7 in the configuration menu
$ apt update
$ apt install libmysqlclient20
```

#### Windows {#windows-mysql}

從此頁面下載C連 [接器](https://dev.mysql.com/downloads/connector/c)。 我們建議下載5.7版。

請確定包含libmysqlclient.dll的目錄已添加到nlserver將使用的PATH環境變數中。

#### CentOS {#centos-mysql}

從本頁下載mysql57-community-release.noarch.rpm [版](https://dev.mysql.com/downloads/repo/yum)。

安裝客戶端庫：

$ yum install mysql57-community-release-el7-9.noarch.rpm$ yum install mysql-community-libs

### 外部帳戶設定 {#external-account-mysql}

外部帳戶設定不需要任何特定步驟。 確保根據資料庫設定時區和「使用Unicode」資料。
