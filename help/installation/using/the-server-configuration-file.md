---
solution: Campaign Classic
product: campaign
title: 伺服器設定檔
description: 伺服器設定檔
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 70cd6a4b-c839-4bd9-b9a7-5a12e59c0cbf
translation-type: tm+mt
source-git-commit: 0c83c989c7e3718a989a4943f5cde7ad4717fddc
workflow-type: tm+mt
source-wordcount: '7970'
ht-degree: 4%

---

# 伺服器設定檔{#the-server-configuration-file}

Adobe Campaign的總體配置在安裝目錄的&#x200B;**conf**&#x200B;目錄下的&#x200B;**serverConf.xml**&#x200B;檔案中定義。 本節列出&#x200B;**serverConf.xml**&#x200B;檔案的所有不同節點和參數。

>[!NOTE]
>
>伺服器端組態只能透過AdobeAdobe代管的部署來執行。 若要進一步瞭解不同的部署，請參閱[代管模型](../../installation/using/hosting-models.md)一節或[本頁](../../installation/using/capability-matrix.md)。 代管型號和混合型號的安裝和配置步驟在[部分](../../installation/using/hosting-models.md)中介紹。

第一參數位於&#x200B;**shared**&#x200B;節點內。 這些與實例相關。 所有nlserver命令（nlserver web 、 nlserver wfserver等）都可能使用這些命令。 其他部分與特定的nlserver子命令相關。

**共用參數**

* [身份驗證](#authentication)
* [dataStore](#datastore)
* [dnsConfig](#dnsconfig)
* [執行](#exec)
* [htmlToPdf](#htmltopdf)
* [ims](#ims)
* [javaScript](#javascript)
* [mailExchanger](#mailexchanger)
* [模組](#module)
* [監控](#monitoring)
* [烏孔夫](#ooconv)
* [proxyConfig](#proxyconfig)
* [threadPool](#threadpool)
* [urlPermission](#urlpermission)
* [xtkJobs](#xtkjobs)

**其他參數**

* [歸檔](#archiving)
* [inMail](#inmail)
* [interactiond](#interactiond)
* [mta](#mta)
* [nmac](#nmac)
* [流水線](#pipelined)
* [修理](#repair)
* [securityZone](#securityzone)
* [sms](#sms)
* [stat](#stat)
* [syslogd](#syslogd)
* [追蹤](#tracking)
* [trackinglogd](#trackinglogd)
* [web](#web)
* [wfserver](#wfserver)

## 驗證{#authentication}

以下是&#x200B;**authentication**&#x200B;節點的不同參數：

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> checkIPConsistent<br /> </td> 
   <td> 啟用IP位址檢查。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultMode<br /> </td> 
   <td> 預設標識模式。<br /> </td> 
   <td> String<br /> </td> 
   <td> 'nl'<br /> </td> 
  </tr> 
  <tr> 
   <td> longSessionTimeOutSec<br /> </td> 
   <td> 長會話超時（秒）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> 安全令牌超時（秒）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> 快取持續時間：以秒為單位快取會話資訊。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> 會話超時（秒）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

以下是&#x200B;**authentication > XTK**&#x200B;節點的不同參數：

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> internalPassword<br /> </td> 
   <td> 內部帳戶的密碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> internalSecurityZone<br /> </td> 
   <td> 內部帳戶安全區：內部帳戶的授權區域。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'lan'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## dataStore {#datastore}

以下是&#x200B;**dataStore**&#x200B;節點的不同參數。 這是定義伺服器資料來源的位置。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> exportDirectory<br /> </td> 
   <td> 導出目錄：導出資料的目標目錄路徑。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/export/' <br /> </td> 
  </tr> 
  <tr> 
   <td> extraSandboxDirectories<br /> </td> 
   <td> 額外的沙盒目錄：要添加到沙盒中的其他路徑（分隔彗差）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '/home/customers/,/sftp/' <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> 表單快取過期延遲：超時秒數，在此秒數後快取項無效。 O意指快取項目僅在發佈時重新整理。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> hosts<br /> </td> 
   <td> DNS遮罩：此實例所服務的DNS掩碼清單(逗號分隔，可使用*和？ )。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> interactionCacheTimeToLive<br /> </td> 
   <td> 交互JSSP快取過期延遲：超時秒數，在此秒數後快取項無效。 負值表示快取始終無效。 '0'，空值或無效值被視為60。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> 例項語言（列舉）。 可能的值為'fr_FR'(Français)、'en_GB'(英文(UK))、'en_US'(英文（美國）)、'de_DE'（德文）和'ja_JP'（日文）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'en_US'<br /> </td> 
  </tr> 
  <tr> 
   <td> uploadDirectory<br /> </td> 
   <td> 上傳資料夾：已上載資料的目標目錄路徑。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/' <br /> </td> 
  </tr> 
  <tr> 
   <td> uploadAllowlist<br /> </td> 
   <td> 要下載的已授權檔案由','分隔。 字串必須是有效的規則Java運算式。 請參閱<a href="../../installation/using/configuring-campaign-server.md#limiting-uploadable-files" target="_blank">限制可上載檔案</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> 將機密儲存在Vault中：使用Hashicorp Vault。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultSecretPath<br /> </td> 
   <td> 儲存庫中的機密路徑<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '/v1/secret/campaign/'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> 包含Vault Token的檔案的本地路徑。 $(HOME)可用於此路徑（但不能用於其他env變數）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '$(HOME)/.vaulttoken'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> Hashicorp Vault URL <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> 檢視快取的有效期：超時秒數，在此秒數後快取項無效。 負值表示快取始終無效。 '0'，空值或無效值被視為60。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> 工作目錄的XPath。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> workingDirectory:工作目錄的XPath。 預設值：'$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/'<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

以下是&#x200B;**dataStore > proxyAdjust**&#x200B;節點的不同參數。 符合規則運算式的URL會根據在urlBase中定義的URL重新產生。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> urlBase<br /> </td> 
   <td> 產生外部URL時使用的基本URL。 例如：https://server.domain.com<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> 規則運算式以符合URL。 例如：http://server\.lan\.net.*<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

### dataSource {#datasource}

以下是&#x200B;**dataStore > dataSource**&#x200B;節點的不同參數。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> 資料源名稱<br /> </td> 
   <td> 字串<br /> </td> 
   <td> default<br /> </td> 
  </tr> 
 </tbody> 
</table>

在&#x200B;**dataStore > dataSource > dbcnx**&#x200B;節點中，配置連接設定：

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NChar<br /> </td> 
   <td> Unicode儲存空間<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> dbSchema<br /> </td> 
   <td> 工作區<br /> </td> 
   <td> 字串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 加密<br /> </td> 
   <td> 加密密碼<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> login<br /> </td> 
   <td> 帳戶<br /> </td> 
   <td> 字串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> password<br /> </td> 
   <td> 密碼<br /> </td> 
   <td> 字串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> provider<br /> </td> 
   <td> 類型（枚舉）。 可能的值包括'Oracle'、'MSSQL'(Microsoft SQL Server)、'PostgreSQL'(PostgreSQL, Greenplum)、'Teradata'、'DB2'、'MySQL'、'Netezza'、'AsterData'、'SAPHANA'(SAP HANA)、'RedShift'(Amazon)Redshift)、「ODBC」(ODBC(Sybase ASE,Sybase IQ))、「中繼」（HTTP中繼到遠程資料庫）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'Oracle'<br /> </td> 
  </tr> 
  <tr> 
   <td> 伺服器<br /> </td> 
   <td> 伺服器<br /> </td> 
   <td> 字串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 時區<br /> </td> 
   <td> 時區：請參閱<a href="../../installation/using/time-zone-management.md" target="_blank">時區管理</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> unicodeData<br /> </td> 
   <td> 資料庫中的Unicode資料<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> useTimestampTZ<br /> </td> 
   <td> 含時區的日期欄位：請參閱<a href="../../installation/using/time-zone-management.md" target="_blank">時區管理</a>。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

在&#x200B;**dataStore > dataSource > sqlParams**&#x200B;節點中，配置SQL參數：

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> funcPrefix<br /> </td> 
   <td> 函式前置詞<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

在&#x200B;**dataStore > dataSource > pool**&#x200B;節點中，配置關聯連接池的參數：

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> aliveTestDelaySec<br /> </td> 
   <td> 連接有效性檢查之間的延遲。<br /> </td> 
   <td> 短<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> 池中保留的空閒連接數。<br /> </td> 
   <td> 短<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> 拒絕新連接前允許的最大連接數。 請參閱此<a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">technote</a>。<br /> </td> 
   <td> 短<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> 連接的最大空閒時間。 0表示預設值。<br /> </td> 
   <td> 短<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

以下是&#x200B;**dataStore > virtualDir**&#x200B;節點的不同參數。 這是虛擬目錄到實際目錄映射的配置。

有關其他資訊，請參閱[管理公共資源](../../installation/using/configuring-campaign-server.md#managing-public-resources)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> 虛擬目錄的名稱<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 路徑<br /> </td> 
   <td> 實際目錄的完整路徑<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是預設設定：

```
<virtualDir name="images" path="$(XTK_INSTALL_DIR)/var/res/img/"/>
<virtualDir name="formCache" path="$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/formCache/"/>
<virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)"/>
```

### preproseCommand {#preprocesscommand}

以下是&#x200B;**dataStore > preproceCommand**&#x200B;節點的不同參數。 這些是用於預處理「載入檔案」工作流活動的授權命令。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 命令<br /> </td> 
   <td> 命令行<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 標籤<br /> </td> 
   <td> 命令行標籤<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> 命令行名稱<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是預設設定：

```
<preprocessCommand command="" label="None" name="none"/>
<preprocessCommand command="zcat &quot;$fileName&quot;" label="Decompression" name="zcat"/><preprocessCommand command="gpg --decrypt &quot;$fileName&quot;" label="Decrypt" name="gpg"/>
```

## dnsConfig {#dnsconfig}

以下是&#x200B;**dnsConfig**（DNS配置）節點的不同參數。

如需詳細資訊，請參閱此[節](../../installation/using/configuring-campaign-server.md)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> 域名：預設域名。 由SMTP HELO命令使用。 預設情況下，使用Windows中聲明的第一個網路介面的網路參數；或在Linux（域或搜索條目）下解析file/etc/resolv.conf。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServers<br /> </td> 
   <td> DNS伺服器：域名伺服器(DNS)的逗號分隔清單。 請參閱下面的注釋。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 重試<br /> </td> 
   <td> DNS查詢的重試次數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> DNS查詢的超時（毫秒）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>**nameSevers**上的注意事項：預設情況下，使用網路
>在Windows中聲明的第一個網路介面的參數
>未定義。 定義域名伺服器(DNS)
>MTA用來取得Mail Exchanger宣告為
>域。
>
>如果未定義此值，MTA會在主機網路組態中搜尋此資訊。 如果可能有數個DNS，則不同的DNS位址必須以逗號分隔(例如：212.155.207.1,212.155.207.2)。 如果您的傳送伺服器有數個網路介面，則MTA使用的DNS清單是第一個。 在這種情況下，我們建議指定&#x200B;**nameServer**&#x200B;參數，以避免任何歧義。

>[!CAUTION]
>
>如果網路主機配置使用DHCP,MTA將找不到DHCP提供的DNS清單。 在這種情況下，我們建議在Windows控制面板的網路參數中指定DNS清單。

## exec {#exec}

以下是&#x200B;**exec**（命令執行）節點的不同參數。

有關其他資訊，請參閱[限制授權外部命令](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> blacksitFile<br /> </td> 
   <td> 包含要添加到allowlist的命令的檔案的路徑。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> user<br /> </td> 
   <td> 以不同的用戶身份執行命令。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

以下是&#x200B;**htmlToPdf**&#x200B;節點的不同參數。 這是將網頁轉換為PDF檔案的服務組態。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 命令<br /> </td> 
   <td> 用於運行轉換的命令行（在'other'模式下）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessusCount<br /> </td> 
   <td> Max. 一台電腦上允許的一次轉換進程數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> mode<br /> </td> 
   <td> 用於轉換的工具。 可能的值包括：phantomjs, wkhtmltopdf, other, disabled<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'phantomjs' <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> 轉換逾時：最大轉換時間（以秒為單位）。 超過此閾值時，轉換過程將停止，並且會引起錯誤。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> verbose<br /> </td> 
   <td> 詳細模式：以詳細模式啟動以診斷可能的錯誤。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> 等待進程時延遲：在秒內延遲，即在同時使用所有進程和等待進程釋放時延遲。 如果超過此延遲，則會停止轉換並引發錯誤。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

phantomjs的範例：

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## ims {#ims}

以下是&#x200B;**ims**&#x200B;節點的不同參數。 這是使用[IMS](../../integrations/using/about-adobe-id.md)連線至其他服務之促銷活動的設定。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> authIMSClientId<br /> </td> 
   <td> 用戶端ID<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSClientSecret<br /> </td> 
   <td> 密鑰（在AES中加密）<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSCode<br /> </td> 
   <td> 授權碼（在AES中加密）<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSEndpoint<br /> </td> 
   <td> IMS伺服器URL<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'https://ims-na1.adobelogin.com'<br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientId<br /> </td> 
   <td> 技術帳戶客戶端ID<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientSecret<br /> </td> 
   <td> Technical Account Secret金鑰（在AES中加密）<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAId<br /> </td> 
   <td> 技術帳戶ID<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAPrivateKey<br /> </td> 
   <td> 技術帳戶私密金鑰（在AES中加密）<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## javaScript {#javascript}

以下是&#x200B;**javaScript**&#x200B;節點的不同參數。 這是JavaScript解釋器的配置。

如需詳細資訊，請參閱[報告檔案](../../reporting/using/actions-on-reports.md#memory-allocation)和此[technote](https://helpx.adobe.com/campaign/kb/out-of-memory-error-in-js-code-activity-in-workflows.html)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxMB<br /> </td> 
   <td> 運行廢棄項目收集器前的最大大小(MB)。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> stackSizeKB<br /> </td> 
   <td> 每個堆棧塊的大小（以千公斤八位元為單位）。 這是記憶體管理調整參數，大部分使用者不應加以調整。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchanger {#mailexchanger}

以下是&#x200B;**mailExchanger**&#x200B;節點的不同參數。 這是SMTP伺服器的配置。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> mxAddress<br /> </td> 
   <td> SMTP伺服器：用於傳輸電子郵件的SMTP伺服器的IP地址。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> mxPort<br /> </td> 
   <td> 用於電子郵件傳輸的SMTP伺服器的TCP埠。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 模組{#module}

以下是&#x200B;**module**&#x200B;節點的不同參數。 這是名稱空間限制模組xtk的配置。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> defaultNameSpace<br /> </td> 
   <td> 建立新實體時使用的預設命名空間。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'cus'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 監視{#monitoring}

以下是&#x200B;**monitoring**&#x200B;節點的不同參數。 這是監視服務配置。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPreparationJobsSec<br /> </td> 
   <td> 最大準備時間：持續時間（秒），在此秒後傳送動作不應再準備。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
  <tr> 
   <td> unixScript<br /> </td> 
   <td> 由監視服務運行的Unix指令碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> winScript<br /> </td> 
   <td> 由監視服務執行的Windows指令碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## ooconv {#ooconv}

以下是&#x200B;**ooconv**&#x200B;節點的不同參數。 這是文檔轉換伺服器的配置。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxConversions<br /> </td> 
   <td> 允許OpenOffice伺服器執行的最大轉換數。 除此數字外，伺服器將重新啟動。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> 強制關閉前OpenOffice伺服器的最大空閒時間。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 7200<br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> OpenOffice伺服器監聽的埠間隔。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 8101-8110<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> 文檔轉換伺服器的URL。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

以下是&#x200B;**proxyConfig**&#x200B;節點的不同參數。 這是Proxy參數的設定。

有關其他資訊，請參閱[代理連接配置](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabled<br /> </td> 
   <td> 使用代理伺服器。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> override<br /> </td> 
   <td> 例外：應忽略代理參數的地址清單。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'localhost*' <br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> 唯一代理伺服器：對所有類型的代理使用相同的配置。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### HTTP代理／安全代理{#http-proxy---secure-proxy-}

在&#x200B;**proxyConfig > HTTP Proxy / Secure proxy**&#x200B;節點中，設定下列參數。

有關其他資訊，請參閱[代理連接配置](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 地址<br /> </td> 
   <td> 代理伺服器的地址<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> login<br /> </td> 
   <td> 登錄到代理伺服器的連接<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> password<br /> </td> 
   <td> 與代理伺服器連接的口令<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 埠<br /> </td> 
   <td> 代理伺服器埠<br /> </td> 
   <td> 短<br /> </td> 
  </tr> 
 </tbody> 
</table>

## threadPool {#threadpool}

以下是&#x200B;**threadPool**&#x200B;節點的不同參數。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxThreadCount<br /> </td> 
   <td> 池中的線程數上限。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

以下是&#x200B;**urlPermission**&#x200B;節點的不同參數。 這是Javascript程式碼可存取的URL清單。

網域和規則運算式清單，指定Javascript程式碼中遇到的URL是否可供Adobe Campaign伺服器使用。

如果找不到URL，則會根據指定的預設模式執行預設動作。

有關其他資訊，請參閱[傳出連接保護](../../installation/using/configuring-campaign-server.md#url-permissions)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> action<br /> </td> 
   <td> 如果URL不在授權清單中，則預設動作（列舉）。 可能的值包括「ignore」（授權而無警告訊息，這需要停用保護）、「warn」（授權並發出警告訊息）和「deny」（禁止存取URL）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> deny<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> URL選擇機制的除錯追蹤：在URL驗證過程中發出其他消息。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### url {#url}

對於每個URL，請新增&#x200B;**url**&#x200B;節點，其參數如下：

有關其他資訊，請參閱[傳出連接保護](../../installation/using/configuring-campaign-server.md#url-permissions)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dnsSuffix<br /> </td> 
   <td> 網域名稱或網域父項，由URL所關注：要驗證的全部或部分URL網域，以加速驗證。 僅當URL的域包含dsnSuffix時，才對規則表達式進行驗證。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> 規則運算式，可調整驗證屬於此網域的URL:如果URL與dnsSuffix對應，則URL必須驗證的規則運算式。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

如果記錄滿足&#x200B;**dnsSuffix**&#x200B;但不滿足&#x200B;**urlRegEx**，則檢查以下記錄。

例如，若要授權存取網域business.com的所有URL，我們可以定義兩個記錄：

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;http://。*&quot;

和

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;https://。*&quot;

以下是預設設定：

```
<url dnsSuffix="api.omniture.com" urlRegEx="https://api.omniture.com/genesis/i/3.1.*"   />
<url dnsSuffix="omniture.com" urlRegEx="https://api[1-5].omniture.com/genesis/i/3.1.*"  />
<url dnsSuffix="marketing.adobe.com"                     urlRegEx="https://.*"                                    />
<url dnsSuffix="fcm.googleapis.com"                      urlRegEx="https://fcm.googleapis.com/fcm/send.*"       />
<url dnsSuffix="graph.facebook.com"                      urlRegEx="https://.*"                                    />
<url dnsSuffix="api.line.me"                             urlRegEx="https://api.line.me/.*"                      />
<url dnsSuffix="api.twitter.com"                         urlRegEx="https://api.twitter.com/1.1.*"              />
<url dnsSuffix="adobeid-na1.services.adobe.com"          urlRegEx="https://.*"                                    />
<url dnsSuffix="adobeid-na1-stg1.services.adobe.com"     urlRegEx="https://.*"                                    />
<url dnsSuffix="deliverability.neolane.net"              urlRegEx="https://deliverability.neolane.net/jssp/dm/renderingSeed.jssp" />
<url dnsSuffix="deliverability.neolane.net"              urlRegEx="https://deliverability.neolane.net/nl/jsp/soaprouter.jsp" />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nms/jsp/.*"              />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nl/jsp/.*"               />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/xtk/jsp/.*"              />
```

## xtkJobs {#xtkjobs}

以下是&#x200B;**xtkJobs**&#x200B;節點的不同參數。 這是伺服器作業的配置。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> 伺服器處理的記憶體狀態刷新週期（毫秒）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 歸檔{#archiving}

以下是&#x200B;**archiving**&#x200B;節點的不同參數。 這是在後台執行的歸檔操作的配置。

如需詳細資訊，請參閱[啟用電子郵件封存（內部部署）](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> acquireLimit<br /> </td> 
   <td> 同時處理的EML數<br /> </td> 
   <td> 長<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> archivingType<br /> </td> 
   <td> 已發送消息的歸檔策略（枚舉）。 可能的值為'0'（無歸檔）和'1'（將已發送消息的歸檔傳輸到SMTP伺服器）。<br /> </td> 
   <td> 位元組<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> compressBatchSize<br /> </td> 
   <td> 壓縮存檔的大小：壓縮存檔中的最大檔案數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressionFormat<br /> </td> 
   <td> 封存（列舉）期間使用的壓縮格式。 可能的值為'0'（無壓縮）和'1'（使用zip格式壓縮已發送的消息）。<br /> </td> 
   <td> 位元組<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationDelay<br /> </td> 
   <td> 在自動封存未處理的電子郵件之前延遲：封存未處理電子郵件的天數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：警告：特定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> 每個更新事件之間的延遲（以秒為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> 刪除未處理電子郵件的天數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此， syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpBccAddress<br /> </td> 
   <td> 存檔目標目標<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpEnableTLS<br /> </td> 
   <td> 啟動SMTPS支援：在遠端伺服器支援時，以安全模式(STARTTLS/SMTPS)啟動電子郵件傳送。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> 到歸檔SMTP伺服器的連接數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayAddress<br /> </td> 
   <td> 要使用的SMTP中繼的DNS名稱或IP地址的逗號分隔清單。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayPort<br /> </td> 
   <td> SMTP伺服器的IP埠。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

以下是&#x200B;**inMail**&#x200B;節點的不同參數。 這是入站電子郵件管理模組的配置。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> checkInstanceName<br /> </td> 
   <td> 驗證實例名稱：如果為true，則Message-ID標題中包含的Adobe Campaign實例的名稱必須與當前實例相同。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> 轉發地址：規則未處理預設電子郵件轉送位址。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> errorForwardAddress<br /> </td> 
   <td> 錯誤地址：用於傳輸無效電子郵件的預設地址（錯誤的MIME編碼）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> 忽略消息大小：用於忽略POP3伺服器返回的消息的大小。 在這種情況下，模組需要「.」 消息結尾處。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> 訊息閱讀時段：消息隊列輪詢頻率。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> 要更新的最大日誌數：定義在更新資料庫之前要保留在記憶體中的日誌消息的最大數量。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> POP3會話期間要讀取的消息數上限。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：警告：特定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> 會話持續時間：消息處理會話的最大持續時間。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> POP3輪詢週期<br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> 讀取消息的隊列大小<br /> </td> 
   <td> 長<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> 使用POP3伺服器的通訊逾時。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriodSec<br /> </td> 
   <td> 要輪詢的帳戶的資料庫重新載入頻率。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此， syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msgDump {#msgdump}

在&#x200B;**inMail > msgDump**&#x200B;節點中，配置以下參數。 這是已處理消息的轉儲配置。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dump<br /> </td> 
   <td> 以文本格式保存所有入站消息。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> msgPath<br /> </td> 
   <td> 消息轉儲路徑。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '/tmp/inMail'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## interactiond {#interactiond}

以下是&#x200B;**interactiond**&#x200B;節點的不同參數。 這是入站交互事件的寫入守護程式的配置。

有關其他資訊，請參閱[Interaction - Data buffer](../../installation/using/interaction---data-buffer.md)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> callDataSize<br /> </td> 
   <td> Max. 共用記憶體中儲存的用於調用資料的字元數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript ID<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：警告：特定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> Max. 共用記憶體中儲存的事件數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> 符合資格的選件數量上限，直接在主張後排序，以便儲存以供統計資料使用。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此， syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> 響應時間統計資訊的聚合持續時間（秒）。 0表示統計儲存已停用。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> Max. 儲存在共用記憶體中以識別個人的字元數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta {#mta}

以下是&#x200B;**mta**&#x200B;節點的不同參數。 這是傳送代理的配置。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '-tracefilter:nlmta' <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataLogPath<br /> </td> 
   <td> 儲存傳送的電子郵件路徑：如果不是空的，則會儲存所傳送電子郵件的所有來源檔案的路徑。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> 轉儲目錄：i如果不為空，則複製此目錄中已發送郵件的MIME封套。 用於診斷故障。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> DNS查詢日誌延遲：顯示日誌的時間（以毫秒為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> 錯誤統計頻率：資料庫中統計和儲存之間的時間。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> 生成錯誤統計資訊並將其儲存在資料庫中。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> 顯示日誌消息的級別。 資料庫中寫入的日誌的嚴重性級別。 MTA生成的日誌消息不一定都寫入資料庫中。 使用此參數，可以定義在資料庫中寫入消息的級別。 如果定義級別2，則也會寫入級別1和0的消息，而如果定義級別1，則只寫入級別1和0的消息。 可能的值包括：0（錯誤）、1（警告）、2（資訊）<br /> </td> 
   <td> 長<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> mta進程可使用的最大記憶體大小(MB)。 超過此限制後，將重新啟動進程，以便將其使用的記憶體釋放到系統。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：警告：特定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> 要考慮的連接閾值。 如果errorPeriodSec指定期間的連接總數嚴格低於閾值，則不為給定路徑生成錯誤統計資訊。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> 要考慮的錯誤閾值：如果errorPeriodSec指定的時段的錯誤總數嚴格低於閾值，則不為給定路徑生成錯誤統計資訊。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> 要考慮的消息閾值。 如果為errorPeriodSec指定的時段發送的消息總數嚴格低於閾值，則不為給定路徑生成錯誤統計資訊。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> 通知中繼：HostName：用於中繼通知的埠。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> 刪除已封存電子郵件之前的延遲：清除dataLogPath中指定目錄中已存檔電子郵件的天數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessages<br /> </td> 
   <td> 重試丟失的消息：如果子進程無效，則將重試傳送的部分。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此， syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> signEmailLinks<br /> </td> 
   <td> 啟用簽名機制。 這可改善電子郵件中追蹤連結的安全性。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> true<br /> </td> 
  </tr>
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> 傳送統計資料伺服器的位址，指定為 
    &lt;dns or ip&gt; 
      <code>[</code>: 
     &lt;port&gt; 
       <code>]</code>。 請參閱 
      <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">統計伺服器的坐標</a>。 
      <br /> 
     </td> 
   <td> 字串<br /> </td> 
   <td> 如果未定義，則預設埠為7777。<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSSupport<br /> </td> 
   <td> 按域啟用TLS:啟用由MX配置的TLS（需要最新的統計伺服器）。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> true <br /> </td> 
  </tr> 
  <tr> 
   <td> statServerVersion<br /> </td> 
   <td> 使用的協定版本：通信協定版本（v5.11和6.0.2伺服器為1,v6.1伺服器為2）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 如果未定義，則使用最新版本。<br /> </td> 
  </tr> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> 如果設為"true"，則您的實例使用<a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">增強的MTA</a>。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> 驗證模式：激活驗證模式(不實際傳輸消息；用於模擬和測試)。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> workingPath<br /> </td> 
   <td> 工作目錄：MTA用於與其子進程通信的臨時檔案的位置。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/mta/' <br /> </td> 
  </tr> 
  <tr> 
   <td> xMailer<br /> </td> 
   <td> X-Mailer欄位：SMTP郵件標題中欄位'X-Mailer'的值。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'nlserver, Build $(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### 快取{#cache}

在&#x200B;**cache**&#x200B;節點中，配置以下參數。 這是本機檔案快取組態。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPeriodSec<br /> </td> 
   <td> 回收後：句點，以秒錶示，之後檔案自動從快取中刪除以回收儲存。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> 最大快取大小(Mb)。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> 清除頻率：執行快取清除機制之間的句點（秒）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 中繼{#relay}

在&#x200B;**mta > relay**&#x200B;節點中，配置以下參數。 這是郵件發送的郵件伺服器配置。

清單的處理方式與MX DNS查詢傳回的MX清單相同，通常只要第一個MX可用，就會使用下一個MX，依此類推。

有關其他資訊，請參閱[SMTP中繼](../../installation/using/configuring-campaign-server.md#smtp-relay)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 地址<br /> </td> 
   <td> 要使用的SMTP中繼的DNS名稱或IP地址的逗號分隔清單。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 埠<br /> </td> 
   <td> SMTP伺服器的IP埠。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

### master {#master}

在&#x200B;**mta > master**&#x200B;節點中，配置以下參數。 這是主伺服器的配置。

如需詳細資訊，請參閱此[節](../../installation/using/configuring-campaign-server.md#mta-child-processes)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> 要傳送作業的資料庫輪詢頻率。 此值指示資料庫輪詢頻率（以秒為單位）。 為獲得等待傳送的作業清單，MTA會定期輪詢資料庫。 當沒有等待的作業時，輪詢週期由此值定義。 否則，如果作業已傳輸到子伺服器，則該輪詢持續時間將自動縮短為一秒，以便新作業能夠盡快被再次處理，即當子伺服器再次可用時。 這並不表示在子伺服器再次可用之前，將每秒執行一次資料庫查詢。 事實上，只有當至少一個子伺服器可用時，才能執行資料庫訪問。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> 資料庫連接失敗後的等待期。 資料庫連接故障通常由資料庫伺服器本身引起。 例如，伺服器也可以停止維護。 DataBaseRetryDelay參數定義在資料庫連接失敗時兩次連接嘗試之間的持續時間。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> 私密金鑰快取的有效期間(DomainKeys)。 用於在DomainKeys建議(http://antispam.yahoo.com/domainkeys)之後簽署電子郵件的私密金鑰會儲存為資料庫中的選項。 domainKeysReloadPeriodSec參數定義MTA可將這些金鑰保留在快取中的秒數。 在此延遲後，必須從資料庫重新載入所有鍵。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> 子伺服器的最大數量。 表示正在運行的伺服器的最大數量。 建議將此數量限制在與伺服器記憶體資源相容的最佳值。 在傳送期間可以檢查此項。 使用的記憶體不應超過可用物理記憶體的三分之一，否則將使用交換。 請參閱<a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">MTA子進程</a>。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> 子伺服器的最小數量。 MTA會嘗試至少維持這些伺服器數目。 如果數量較少，則會每秒重新啟動新伺服器，直到達到此值。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> 啟動時的子伺服器數。 動態監控子伺服器的數量；當MTA啟動時，它會建立此值所指示的任意多個子伺服器。 通常，子伺服器的啟動速度不能快於每秒一個伺服器，以便節省主機資源。 但是，當MTA啟動時，會排除此限制，以便盡快提供子伺服器。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 子{#child}

在&#x200B;**mta > child**&#x200B;節點中，配置以下參數。 這是子伺服器的配置。

如需詳細資訊，請參閱[電子郵件傳送最佳化](../../installation/using/email-deliverability.md#email-sending-optimization)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> extraArgs<br /> </td> 
   <td> 可選命令行參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> 在停止空閒子伺服器之前超時。 如果子伺服器的空閒時間大於此參數，則它將自動自毀以釋放主機資源。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> 最大郵件保留時間。 如果由於頻寬限制而無法發送準備的消息或無法連接到目標MTA，則消息將被放棄，並將在下次重試時被處理。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> 每個子伺服器啟動的對FCM的並行Http請求數上限。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> 每個子伺服器的消息數上限。 每個MTA子系都會處理此數量的訊息並終止。 請務必指定一個數字，使MTA中的記憶體或資源洩漏無害（通常數以千計）。 即使MTA程式碼中沒有已知的記憶體洩漏，內嵌的JavaScript和XSL引擎也不完全可靠。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> 待審消息：等待傳送的記憶體中消息的最大數量。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> 子進程可使用的最大記憶體大小(MB)。 超過此限制後，進程將停止，以便將其使用的記憶體釋放到系統。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> 超時（以秒為單位），之後會放棄傳送連接器的SOAP連線。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> startWithFirstMX<br /> </td> 
   <td> 始終從最高優先順序的MX開始。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> 恢復時連續嘗試的最大數量。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

在&#x200B;**mta >子代> smtp**&#x200B;節點中，配置以下參數。 這是SMTP會話的配置。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enableTLS<br /> </td> 
   <td> 當遠端伺服器支援時，以安全模式(STARTTLS/SMTPS)啟動傳送電子郵件。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> 空閒會話超時。 此參數僅在會話被重複用於向給定域發送多個消息時才使用。 當MTA完成消息傳輸時，它所使用的SMTP會話不會被系統關閉。 如果消息已準備好要針對此域發送，則將重複使用同一SMTP會話，因此不會自動關閉會話。 參數IdleSessionTimeout可讓您定義SMTP會話可在何時保持活動狀態以等待另一條消息。 持續時間過去後，會話自動關閉。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> 重試連接前的初始延遲。 每次連接失敗時，此延遲會加倍。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> 子伺服器的SMTP會話數上限。 要發送消息，MTA將初始化與接收方MTA的SMTP連接。 給定子伺服器的併發和活動SMTP會話的最大數量受此值的限制。 如果將此值乘以maxSpareServers，則可獲得指定子伺服器可同時處理的消息數上限。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

在&#x200B;**mta >子代> smtp > IPAffinity**&#x200B;節點中，配置以下參數。 這是針對優化的傳出SMTP通信量的IP地址相關性管理的配置。

有關詳細資訊，請參閱[要使用](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)和[管理具有相關性的出站SMTP通信的IP地址清單。](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> 域名：連結至IP位址的本機網域名稱。 發出SMTP HELO命令時使用。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> 邏輯名稱：使用者連結至相似性的名稱。 名稱使用分號分隔；<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

在&#x200B;**mta >子代> smtp > IP**&#x200B;節點中，配置以下參數。

如需詳細資訊，請參閱[要使用的IP位址清單](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 地址<br /> </td> 
   <td> 相關物理地址。 例如：'192.168.0.1'<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> 關聯的公用地址ID。 用作統計伺服器的密鑰。 必須是數值。 請參閱此<a href="../../installation/using/email-deliverability.md#managing-ip-addresses">節</a>。<br /> </td> 
   <td> 長<br /> </td> 
  </tr> 
  <tr> 
   <td> 重量<br /> </td> 
   <td> 指定此IP相對於其他IP的使用頻率（權重越大，頻率越高）。<br /> </td> 
   <td> 長<br /> </td> 
  </tr> 
  <tr> 
   <td> includeDomains<br /> </td> 
   <td> 以逗號分隔的要包含的域掩碼清單。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> excludeDomains<br /> </td> 
   <td> 要排除的域掩碼清單（以逗號分隔）。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> heloHost<br /> </td> 
   <td> 連結至IP位址的電腦名稱。 發出SMTP HELO命令時使用。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

## nmac {#nmac}

以下是&#x200B;**nmac**&#x200B;節點的不同參數。 這是推播通知傳送的設定。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> useHTTPProxy<br /> </td> 
   <td> 使用shared/proxyHTTP中定義的HTTP Proxy。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 中繼{#relay-1}

以下是&#x200B;**nmac > relay**&#x200B;節點的不同參數。 這將配置消息傳送的中繼（ios http2連接器）的使用。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 地址<br /> </td> 
   <td> 要使用的中繼的DNS地址或名稱。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 埠<br /> </td> 
   <td> 中繼埠<br /> </td> 
   <td> 長<br /> </td> 
   <td> 443<br /> </td> 
  </tr> 
  <tr> 
   <td> trustedCertsChain<br /> </td> 
   <td> 憑證鏈（PEM檔案）。 在使用模擬伺服器時很有用。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 流水線{#pipelined}

以下是&#x200B;**pipelined**&#x200B;節點的不同參數。 這是Pipeline Services事件處理模組的配置。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> appName<br /> </td> 
   <td> 儲存公開金鑰時，在「開發人員」連線中產生的應用程式名稱。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authGatewayEndpoint<br /> </td> 
   <td> 取得閘道Token的URL。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> 取得Token的私密金鑰（在AES中使用XtkKey選項加密）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> disableAuth<br /> </td> 
   <td> 禁用驗證：不需驗證即可連線至Pipeline Services。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> discoverPipelineEndpoint<br /> </td> 
   <td> 用於發現Pipeline Services URL的URL。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> 狀態儲存期間：進程內部資訊保存在檔案中的頻率。 如果為0，則為非活動。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> 監聽URL:強制Pipeline Services的監聽URL。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：警告：特定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> 狀態伺服器埠：HTTP伺服器埠允許您查詢進程的狀態。 如果為0，則為非活動。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 7781<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushMessageCount<br /> </td> 
   <td> 每次處理此數量的消息時，指針都將儲存在資料庫中。<br /> </td> 
   <td> <br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushPeriodSec<br /> </td> 
   <td> 儲存指針之前的延遲：此期間，指針將至少儲存在資料庫中一次（在活動量低時很有用）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThreads<br /> </td> 
   <td> 使用個人化JavaScript連接器進行事件處理的執行緒數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> processingThreads<br /> </td> 
   <td> 事件處理的線程數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> retryPeriodSec<br /> </td> 
   <td> 如果發生故障，則處理之間的延遲。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> 在此時段後放棄：如果處理在此時段後仍然失敗，請放棄事件。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此， syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 修復{#repair}

以下是&#x200B;**repair**&#x200B;節點的不同參數。 這是資料庫修復模組的配置。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> repairActionDelayMin<br /> </td> 
   <td> 交貨操作修復模組：延遲（以分鐘為單位），之後可由修復模組處理傳送操作。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

以下是&#x200B;**securityZone**&#x200B;節點的不同參數。

有關其他資訊，請參閱[定義安全區](../../installation/using/security-zones.md)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> allowDebug<br /> </td> 
   <td> 授權Web應用程式的除錯模式。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> 授權使用者使用應用程式，但無密碼。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowHTTP<br /> </td> 
   <td> 授權使用HTTP進行操作員登錄。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInjeption<br /> </td> 
   <td> 授權在表達式中使用SQLDATA。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserPassword<br /> </td> 
   <td> 授權使用者／密碼作業Token。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> 標籤<br /> </td> 
   <td> 標籤<br /> </td> 
   <td> 字串<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> 內部名稱<br /> </td> 
   <td> 字串<br /> </td> 
   <td> NewName()<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTokenOnly<br /> </td> 
   <td> 請勿使用安全性Token。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> showErrors<br /> </td> 
   <td> 顯示錯誤詳細資訊<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是預設設定：

```
<securityZone allowDebug="false" allowHTTP="false" allowSQLInjection="false" label="Public Network" name="public">
  <subNetwork name="all" label="All addresses" mask="*" proxy="127.0.0.1, ::1"/>

  <securityZone allowDebug="true" allowHTTP="false" allowSQLInjection="false" label="Private Network (VPN)"
                name="vpn" showErrors="true">

    <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" allowUserPassword="false"
                  allowSQLInjection="false" label="Private Network (LAN)" name="lan" sessionTokenOnly="true"
                  showErrors="true">
      <subNetwork name="lan1" label="Lan 1" mask="192.168.0.0/16" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan2" label="Lan 2" mask="172.16.0.0/12" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan3" label="Lan 3" mask="10.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost" label="Localhost" mask="127.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6"  label="Lan (IPv6)" mask="fc00::/7" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6b" label="Lan (IPv6)" mask="fe80::/10" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost6" label="Localhost (IPv6)" mask="::1/128" proxy="127.0.0.1, ::1"/>
    </securityZone>

  </securityZone>
</securityZone>
```

### subNetwork {#subnetwork}

以下是&#x200B;**securityZone > subNetwork**&#x200B;節點的不同參數。

有關其他資訊，請參閱[定義安全區](../../installation/using/security-zones.md)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 標籤<br /> </td> 
   <td> 標籤<br /> </td> 
   <td> 字串<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> 掩碼<br /> </td> 
   <td> 掩碼或地址<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> 內部名稱<br /> </td> 
   <td> 字串<br /> </td> 
   <td> NewName()<br /> </td> 
  </tr> 
  <tr> 
   <td> proxy<br /> </td> 
   <td> 此子網路用於訪問實例的（反向）代理的掩碼或地址。 在這種情況下，將測試「X-Forwarded-For」標頭，而不是此proxy。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## sms {#sms}

以下是&#x200B;**sms**&#x200B;節點的不同參數。 這是入站SMS管理模組的配置。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataRetentionDays<br /> </td> 
   <td> SMPP連接器保存的檔案工作檔案的最大天數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> dataSizeMo<br /> </td> 
   <td> SMPP工作檔案的最大大小(MB)。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 512<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> 會話連續性幀的週期：max. 兩幀之間的句點（秒），以通知接收會話仍處於啟用狀態。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：警告：特定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> 搜尋頻率：SMS帳戶輪詢期間。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod<br /> </td> 
   <td> 帳戶重新載入頻率：資料庫重新載入要輪詢的帳戶頻率。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此， syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> SR處理的延遲秒數：只有恢復日期早於當前時間的SR減去srReadDelay指定的持續時間（秒）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> SMS閘道的通訊逾時。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

以下是&#x200B;**sms > netsize**&#x200B;節點的不同參數。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> netsizeConnectionTimeout<br /> </td> 
   <td> 建立與Netsize的連接時的超時秒數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## stat {#stat}

以下是&#x200B;**stat**&#x200B;節點的不同參數。 這是MTA統計模組的配置。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：警告：特定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> 埠<br /> </td> 
   <td> 伺服器偵聽埠。 請參閱此<a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">節</a>。<br /> </td> 
   <td> 短<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此， syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslogd {#syslogd}

以下是&#x200B;**syslogd**&#x200B;節點的不同參數。 這是日誌管理模組的配置。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> 日誌檔案的最大大小（以Mb為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> 要保留的登入。log檔案數上限。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：警告：特定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此， syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 追蹤{#tracking}

以下是&#x200B;**tracking**&#x200B;節點的不同參數。 這是追蹤伺服器的設定。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> blockRedirectForUnsignedTrackingLink<br /> </td> 
   <td> 停用從舊版建置產生的格式錯誤URL。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> consolidationPeriodSec<br /> </td> 
   <td> 合併期間<br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> 消除重複空缺：移除重複開啟的追蹤記錄，以限制郵件閱讀程式（例如Outlook）中的郵件預覽效果。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> 忽略最多X%的錯誤：只要未考慮的日記帳比率未達到此值，請不要更新跟蹤指標。<br /> </td> 
   <td> 位元組<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> 更新錯誤指示：重新計算錯誤指示符前的最大持續時間。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> indicatorsDuration<br /> </td> 
   <td> 計算指標：交貨的有效日期之後的持續時間，在此之後將不再計算合併指標。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程<br />時要執行的JavaScript ID </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> 呼叫遠端追蹤伺服器所請求的記錄檔數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：警告：特定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceAPIKey<br /> </td> 
   <td> Phishbowl服務端點整合的API金鑰。 這可保護重新導向由舊版建置產生的格式錯誤URL。<br /> </td> 
   <td> 長<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Phishbowl服務端點整合的端點。 這可保護重新導向由舊版建置產生的格式錯誤URL。<br /> </td> 
   <td> 長<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此， syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> 忽略最多X%的追蹤：只要未考慮的日記帳比率未達到此值，請不要更新跟蹤指標。<br /> </td> 
   <td> 位元組<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> 更新追蹤指標：重新計算追蹤指標前的最大持續時間。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> 瀏覽器標識符快取的大小。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogd {#trackinglogd}

以下是&#x200B;**trackinglogd**&#x200B;節點的不同參數。 這是跟蹤日誌寫入守護程式的配置。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程<br />時要執行的JavaScript ID </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> 最大寫入重試次數：在日誌檔案中寫入失敗時可建立的最大檔案數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> 最大日誌大小：磁碟上記錄檔使用的最大空間(MB)。 不得少於100 MB。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：警告：特定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> 最大日誌計數：共用記憶體中儲存的日誌的最大數量。 不能少於10000。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> 清除前的日誌數：開始清除日誌檔案之前插入的日誌數。 不得低於50000。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此， syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> 共用記憶體中儲存的字元數上限，以取得額外的網頁追蹤參數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## web {#web}

以下是&#x200B;**web**&#x200B;節點的不同參數。 這是Web模組的配置。

如需詳細資訊，請參閱此[節](../../installation/using/configuring-campaign-server.md#default-port-for-tomcat)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> JVMOptions<br /> </td> 
   <td> 作為字串傳遞的JVM的選項。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 最大線程數<br /> </td> 
   <td> 線程數上限。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> MinSpareThreads<br /> </td> 
   <td> 線程的最小數量。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> controlPort<br /> </td> 
   <td> Tomcat監聽控制埠：請參閱<a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">配置Tomcat</a>。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Tomcat HTTP監聽埠：請參閱<a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">配置Tomcat</a>。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> SubmitDelivery呼叫的佇列大小：可排入佇列的SubmitDelivery SOAP呼叫數上限。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：警告：特定進程消耗的RAM量（以Mb為單位）<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> 通知中繼：HostName：啟用通知中繼的埠。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此， syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> startSoapRouterInModule<br /> </td> 
   <td> 以模組模式啟動SOAP路由器。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### jsp {#jsp}

以下是&#x200B;**web > jsp**&#x200B;節點的不同參數。 這是JSP所使用參數的配置。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> debug<br /> </td> 
   <td> 是否在調試模式下執行JSP。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> downloadPath<br /> </td> 
   <td> 下載資料夾：客戶端控制台的安裝程式下載路徑。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/datakit/nl/eng/jsp'<br /> </td> 
  </tr> 
  <tr> 
   <td> foFileName<br /> </td> 
   <td> .fo檔案的路徑。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> soapRouter<br /> </td> 
   <td> SOAP路由器的URL(http://myserver/xxx、http://jni或mailto:xxx)。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'http://jni'<br /> </td> 
  </tr> 
 </tbody> 
</table>

**web > jsp > classpath**&#x200B;節點包含啟動JVM時要使用的所有類路徑的清單。 以下是預設設定：

```
'$(XTK_INSTALL_DIR)/tomcat-8/bin/bootstrap.jar
          $(XTK_INSTALL_DIR)/tomcat-8/bin/tomcat-juli.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-coyote.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-util.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/servlet-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/jsp-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/el-api.jar
          $(XTK_INSTALL_DIR)/java/lib/log4j-1.2.11.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/annotations-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/catalina.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/websocket-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat7-websocket.jar
          $(XTK_INSTALL_DIR)/java/lib/pdfbox-2.0.4.jar
          $(XTK_INSTALL_DIR)/java/lib/FontBox-0.1.0.jar
          $(XTK_INSTALL_DIR)/java/lib/AGJavaEndpoint.22.jar
          $(XTK_INSTALL_DIR)/java/lib/NSGConstants.jar
          $(XTK_INSTALL_DIR)/java/lib/smpp.jar
          $(XTK_INSTALL_DIR)/java/lib/nlweb.jar
          $(XTK_INSTALL_DIR)/java/lib/jcaptcha-all.jar
          $(XTK_INSTALL_DIR)/java/lib/apns-1.0.0.Beta6-jar-with-dependencies.jar
          $(XTK_INSTALL_DIR)/java/lib/commons-collections-3.2.2.jar
          $(XTK_INSTALL_DIR)/java/lib/jcommon-1.0.16.jar
          $(XTK_INSTALL_DIR)/java/lib/jfreechart-1.0.13.jar
          $(XTK_INSTALL_DIR)/java/lib/barcode4j-light.jar
          $(XTK_INSTALL_DIR)/java/lib/zxing.jar
          $(XTK_INSTALL_DIR)/java/lib/raztec.jar
          $(XTK_INSTALL_DIR)/java/lib/gson-2.7.jar
          $(XTK_INSTALL_DIR)/java/lib/alpn-api-1.1.3.v20160715.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-all-4.1.6.Final.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-tcnative-boringssl-static-1.1.33.Fork22.jar
          $(XTK_INSTALL_DIR)/java/lib/pushy-0.8.1.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-api-1.7.21.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-simple-1.7.21.jar'
```

### jssp {#jssp}

以下是&#x200B;**web > jssp**&#x200B;節點的不同參數。 這是JSSP所使用參數的配置。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> collectsGarbageAfterRequest<br /> </td> 
   <td> 在每個查詢後啟用JavaScript上下文的廢棄項目收集器。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> JavaScript內容所提供的頁面數上限。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

**web > jsp > classpath**&#x200B;節點包含啟動JVM時要使用的所有類路徑的清單。

### 中繼{#relay-2}

以下是&#x200B;**web > relay**&#x200B;節點的不同參數。 這是兩個區域之間HTTP請求的中繼配置。

如需詳細資訊，請參閱此[節](../../installation/using/deploying-an-instance.md#synchronizing-public-resources)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> debugRelay<br /> </td> 
   <td> 以調試模式啟動Web伺服器中的HTTP中繼模組。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInAuthority<br /> </td> 
   <td> 禁止字元（網域）:URI的「authority」部分中的禁用字元清單。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '.?#@/:' <br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInPath<br /> </td> 
   <td> 禁止字元（路徑）:URI的「路徑」部分中的禁用字元清單。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '?#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> 「mod_dir」模組選項的值：資料夾查詢期間要使用的檔案清單。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'index.md' <br /> </td> 
  </tr> 
  <tr> 
   <td> startRelay<br /> </td> 
   <td> 啟動HTTP中繼模組。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> 在Web伺服器中啟動HTTP中繼模組。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> 刪除禁止的URL之前等待時間。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '60'<br /> </td> 
  </tr> 
 </tbody> 
</table>

使用以下參數為每個要中繼的URL添加&#x200B;**web > relay > url**&#x200B;節點（插入順序定義優先順序）。

如需詳細資訊，請參閱[動態頁面安全性和中繼](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays)和[章節](../../installation/using/deploying-an-instance.md#synchronizing-public-resources)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IPMask<br /> </td> 
   <td> 授權IP:允許使用此掩碼中繼的源IP地址清單（以逗號分隔）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> deny<br /> </td> 
   <td> 拒絕存取這些URL（傳回HTTP 403錯誤）<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> 要中繼的DNS別名：要中繼的DNS別名掩碼清單(例如：'*.adobe.com')。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllowed<br /> </td> 
   <td> 無論安全區域（如webApps）為何，HTTP存取都經過授權。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayHost<br /> </td> 
   <td> 添加原始主機：中繼時使用原始請求的HTTP 'Host'標頭。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayPath<br /> </td> 
   <td> 新增初始URL路徑：附加URL的完整路徑，以中繼至目標頁面的URL。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> status<br /> </td> 
   <td> 公共資源的同步狀態（枚舉）。 可能的值有'normal'（正常執行）、 'blicklist'（在發生錯誤404時添加到denylist的URL）和'spare'（如果存在，則檔案上載在備用伺服器上）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> normal<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> 目標頁面的URL:請參閱<a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">配置Tomcat</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> 正在中繼的請求的最大執行時間（以秒為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> urlPath<br /> </td> 
   <td> 要中繼的URL遮色片(例如：'/nl*', '*.jsp')。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是預設設定：

```
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true"
     status="normal" targetUrl="http://localhost:7781" timeout="" urlPath="/pipelined/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/view/*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="*ooconv.jsp*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/res/*.jsp*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/sc.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/interactionProposal.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/zoneJson.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/barcode.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/captcha.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/webForm.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/xtk/jsp/zoneinfo.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/facebookCallback.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/m.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/s.jsp"/>

<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nms/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/xtk/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nl/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="*.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="true" urlPath="/webApp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/report/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/jssp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/strings/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/interaction/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/barcode/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/lineImage/*"/>

<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/favicon.*"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.md"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.png"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.jpg"/>
```

為每個HTTP標頭添加&#x200B;**Web > relay > responseHeader**&#x200B;節點，以添加轉發到中繼的回覆。

如需詳細資訊，請參閱[管理HTTP標題](../../installation/using/configuring-campaign-server.md#managing-http-headers)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> 標題名稱<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> value<br /> </td> 
   <td> 標題值<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是預設設定：

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### 重定向{#redirection}

以下是&#x200B;**web > redirection**&#x200B;節點的不同參數。 這是重定向模組的配置。

如需詳細資訊，請參閱此[節](../../installation/using/deploying-an-instance.md#synchronizing-public-resources)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IMSOrgId<br /> </td> 
   <td> Identity Management系統(IMS)組織識別碼：Adobe Experience Cloud內的獨特組織識別碼，尤其用於VisitorID服務和IMS SSO。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> 描述永久Cookie所用原則的值（與P3P精簡版原則格式相容）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 「CAO DSP COR CURa DEVa TAIaOUR BUS IND UNI COM NAV」<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> 以逗號分隔的網域清單，以明確指出要設定Cookie的網域。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> 與跟蹤實例關聯的資料庫標識符。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> 呼叫記錄計數：呼叫方法GetTrackingLogs時預設傳回的記錄數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationURL<br /> </td> 
   <td> 過期的重新指示頁面：當傳送動作的重新導向已過期時，重新導向伺服器預設會使用的網頁URL。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> 最大作業數：快取中傳送動作的最大數目。 不得低於50。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirection<br /> </td> 
   <td> 啟動重定向服務。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectionInModule<br /> </td> 
   <td> 以模組模式啟動重定向服務。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> trackWebVisitors<br /> </td> 
   <td> 網路追蹤：為未知使用者瀏覽的頁面建立記錄檔。<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingPassword<br /> </td> 
   <td> 重定向伺服器使用的口令。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是&#x200B;**web >重定向> spareServer**&#x200B;節點的不同參數。

如需詳細資訊，請參閱[冗餘追蹤](../../installation/using/configuring-campaign-server.md#redundant-tracking)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabledIf<br /> </td> 
   <td> 在下列情況下，請考慮：如果運算式傳回true，則會考量追蹤伺服器。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> id<br /> </td> 
   <td> 名稱<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> 額外的重定向伺服器URL<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

### spamCheck {#spamcheck}

以下是&#x200B;**web > spamCheck**&#x200B;節點的不同參數。 這是「電子郵件反垃圾郵件計分」評估參數的配置。

有關其他資訊，請參閱[配置SpamAssassin](../../installation/using/configuring-spamassassin.md)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 命令<br /> </td> 
   <td> 執行命令以評估電子郵件的反垃圾郵件分數(例如'perl spamcheck.pl')。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

以下是&#x200B;**wfserver**&#x200B;節點的不同參數。 這是工作流進程配置。

如需詳細資訊，請參閱[高可用性工作流程與相關性](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities)。

<table> 
 <thead> 
  <tr> 
   <th> 參數 </th> 
   <th> 說明 </th> 
   <th> 類型 </th> 
   <th> 預設值 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> affinity<br /> </td> 
   <td> 相關性<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> 句點<br /> </td> 
   <td> 長<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：警告：特定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> 通知中繼：HostName：啟用通知中繼的埠。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱<a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此， syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>
