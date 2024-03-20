---
product: campaign
title: 伺服器設定檔
description: 伺服器設定檔
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 70cd6a4b-c839-4bd9-b9a7-5a12e59c0cbf
source-git-commit: 67a6e03318a74b665dc6928028470f98c0abae5e
workflow-type: tm+mt
source-wordcount: '8075'
ht-degree: 3%

---

# 伺服器設定檔{#the-server-configuration-file}

Adobe Campaign的整體設定在 **serverConf.xml** 檔案，位於 **conf** 安裝目錄的目錄。 本節列出所有不同的節點和引數， **serverConf.xml** 檔案。

>[!NOTE]
>
>伺服器端設定只能由Adobe代管的部署Adobe執行。 若要瞭解不同部署的詳細資訊，請參閱 [託管模型](../../installation/using/hosting-models.md) 區段或至 [此頁面](../../installation/using/capability-matrix.md). 本課程介紹託管及混合模式的安裝及設定步驟 [區段](../../installation/using/hosting-models.md).

第一個引數位於 **已共用** 節點。 這些都會與執行個體相關。 它們可能會被所有nlserver命令（nlserver web、nlserver wfserver等）使用。 其他段落與特定的nlserver子指令有關。

**共用引數**

* [驗證](#authentication)
* [dataStore](#datastore)
* [dnsConfig](#dnsconfig)
* [執行](#exec)
* [htmlToPdf](#htmltopdf)
* [ims](#ims)
* [javascript](#javascript)
* [mailExchange](#mailexchanger)
* [模組](#module)
* [監視](#monitoring)
* [ooconv](#ooconv)
* [proxyConfig](#proxyconfig)
* [threadPool](#threadpool)
* [urlPermission](#urlpermission)
* [cusHeaders](#cusheaders)
* [xtkJobs](#xtkjobs)

**其他引數**

* [封存](#archiving)
* [inMail](#inmail)
* [互動](#interactiond)
* [mta](#mta)
* [nmac](#nmac)
* [已管線](#pipelined)
* [修復](#repair)
* [securityZone](#securityzone)
* [簡訊](#sms)
* [stat](#stat)
* [syslogd](#syslogd)
* [追蹤](#tracking)
* [trackinglogd](#trackinglogd)
* [網頁](#web)
* [wfserver](#wfserver)

## 驗證 {#authentication}

以下是的不同引數 **authentication** 節點：

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
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> 預設模式<br /> </td> 
   <td> 預設識別模式。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'nl'<br /> </td> 
  </tr> 
  <tr> 
   <td> longSessionTimeOutSec<br /> </td> 
   <td> 長工作階段的逾時（秒）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> 安全性權杖逾時（秒）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> 快取持續時間：工作階段資訊的快取（以秒為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> 工作階段逾時（秒）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

以下是的不同引數 **驗證> XTK** 節點：

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
   <td> 內部帳戶安全區域：內部帳戶的授權區域。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'lan'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## dataStore {#datastore}

以下是的不同引數 **dataStore** 節點。 這是定義伺服器資料來源的位置。

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
   <td> 匯出目錄：匯出資料的目標目錄路徑。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/export/' <br /> </td> 
  </tr> 
  <tr> 
   <td> extraSandboxedDirectories<br /> </td> 
   <td> 額外的沙箱目錄：要新增至沙箱的其他路徑（以逗號分隔）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '/home/customers/，/sftp/' <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> 表單快取到期延遲：快取專案失效後的逾時（以秒為單位）。 O表示快取專案只會在發佈時重新整理。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> 主機<br /> </td> 
   <td> DNS遮罩：此例項提供的DNS遮罩清單(以逗號分隔，可以使用*和？ 模式)。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> interactionCacheTimeToLive<br /> </td> 
   <td> 互動JSSP快取到期延遲：快取專案失效後的逾時（以秒為單位）。 負值表示快取一律會失效。 '0'、空白或無效的值會視為60。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> 例項語言（分項清單）。 可能的值包括「fr_FR」(Français)、「en_GB」(English (UK))、「en_US」(English (US))、「de_DE」(Deutsch)和「ja_JP」(Japan)。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'en_US'<br /> </td> 
  </tr> 
  <tr> 
   <td> uploaddirectory<br /> </td> 
   <td> 上傳資料夾：上傳資料的目的地目錄路徑。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/' <br /> </td> 
  </tr> 
  <tr> 
   <td> uploadAllowlist<br /> </td> 
   <td> 要下載的已授權檔案，以「，」分隔。 字串必須是有效的規則Java運算式。 另請參閱 <a href="file-res-management.md" target="_blank">限制可上傳的檔案</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> 將密碼儲存在儲存庫中：使用Hashicorp儲存庫。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> Vaultsecretpath<br /> </td> 
   <td> 儲存庫中的密碼路徑<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '/v1/secret/campaign/'<br /> </td> 
  </tr> 
  <tr> 
   <td> Vaulttokentpath<br /> </td> 
   <td> 包含儲存庫權杖的檔案的本機路徑。 $(HOME)可以在此路徑中使用（但不能用於其他環境變數）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '$(HOME)/.vaulttoken'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> Hashicorp儲存庫URL <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> 檢視快取的有效期：快取專案失效後的逾時（以秒為單位）。 負值表示快取一律會失效。 '0'、空白或無效的值會視為60。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> 工作目錄<br /> </td> 
   <td> 工作目錄的XPath。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> workdirectory ：工作目錄的XPath。 預設值： '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/'<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

以下是的不同引數 **dataStore > proxyAdjust** 節點。 根據urlBase中定義的URL重新產生符合規則運算式的URL。

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
   <td> 產生外部URL時要使用的基底。 例如： https://server.domain.com<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> 符合URL的規則運算式。 例如： http://server\.lan\.net.*<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 資料來源 {#datasource}

以下是的不同引數 **dataStore > dataSource** 節點。

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
   <td> 名稱<br /> </td> 
   <td> 資料來源名稱<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 預設<br /> </td> 
  </tr> 
 </tbody> 
</table>

在 **dataStore > dataSource > dbcnx** 節點，設定連線設定：

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
   <td> Unicode儲存<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> dbSchema<br /> </td> 
   <td> 工作區<br /> </td> 
   <td> 字串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> encrypted<br /> </td> 
   <td> 加密的密碼<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 登入<br /> </td> 
   <td> 帳戶<br /> </td> 
   <td> 字串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 密碼<br /> </td> 
   <td> 密碼<br /> </td> 
   <td> 字串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 提供者<br /> </td> 
   <td> 型別（分項清單）。 可能的值包括「Oracle」、「MSSQL」(Microsoft SQL Server)、「PostgreSQL」(PostgreSQL)、「Teradata」、「DB2」、「MySQL」、「Netezza」、「AsterData」、「SAPHANA」(SAP HANA)、「RedShift」(Amazon Redshift)、「ODBC」(ODBC (Sybase ASE、Sybase IQ))、「轉送」（HTTP轉送至遠端資料庫）。<br /> </td> 
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
   <td> 時區：請參閱 <a href="../../installation/using/time-zone-management.md" target="_blank">時區管理</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> unicodeData<br /> </td> 
   <td> 資料庫中的Unicode資料<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> useTimestampTZ<br /> </td> 
   <td> 包含時區的日期欄位：請參閱 <a href="../../installation/using/time-zone-management.md" target="_blank">時區管理</a>.<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

在 **dataStore > dataSource > sqlParams** 節點，設定SQL引數：

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

在 **dataStore > dataSource >集區** 節點，設定關聯連線集區的引數：

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
   <td> 連線有效性檢查之間的延遲。<br /> </td> 
   <td> 短<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> 集區中保留的可用連線數目。<br /> </td> 
   <td> 短<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> 拒絕新連線之前允許的最大連線數量。 檢視此 <a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">技術備註</a>.<br /> </td> 
   <td> 短<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> 連線的最大閒置時間。 0表示預設值。<br /> </td> 
   <td> 短<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

以下是的不同引數 **dataStore > virtualdir** 節點。 這是虛擬目錄到真實目錄對應的組態。

如需詳細資訊，請參閱 [管理公用資源](file-res-management.md).

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
   <td> 名稱<br /> </td> 
   <td> 虛擬目錄的名稱 <br /> </td> 
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

### preprocessCommand {#preprocesscommand}

以下是的不同引數 **dataStore > preprocessCommand** 節點。 這些是預先處理「載入檔案」工作流程活動的授權命令。

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
   <td> 命令列 <br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 標籤<br /> </td> 
   <td> 命令列標籤<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 名稱<br /> </td> 
   <td> 命令列名稱<br /> </td> 
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

以下是的不同引數 **dnsConfig** （DNS設定）節點。

如需詳細資訊，請參閱此 [區段](../../installation/using/configuring-campaign-server.md).

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
   <td> 網域名稱：預設網域名稱。 由SMTP HELO命令使用。 依預設，會使用在Windows中宣告的第一個網路介面的網路引數；或剖析Linux下的file/etc/resolv.conf （網域或搜尋專案）。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServer<br /> </td> 
   <td> DNS伺服器：網域名稱伺服器(DNS)的逗號分隔清單。 請參閱下方的注意事項。<br /> </td> 
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
   <td> 逾時<br /> </td> 
   <td> DNS查詢的逾時（毫秒）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>附註： **nameServer**：預設情況下，使用網路
>在Windows中宣告的第一個網路介面的引數
>未定義於UNIX。 定義網域名稱伺服器(DNS)
>MTA用來取得宣告給的郵件交換器
>網域。
>
>如果未定義此值，MTA會在主機網路設定中尋找此資訊。 如果可能有數個DNS，不同的DNS位址必須以逗號分隔（例如：212.155.207.1,212.155.207.2）。 如果您的傳送伺服器具有數個網路介面，則MTA使用的DNS清單是第一個清單。 在此情況下，我們建議指定 **nameServer** 引數，以避免任何模稜兩可。

>[!CAUTION]
>
>如果您的網路主機設定使用DHCP，MTA將無法找到DHCP提供的DNS清單。 在此情況下，我們建議在Windows控制檯的網路引數中指定DNS清單。

## 執行 {#exec}

以下是的不同引數 **執行** （命令執行）節點。

如需詳細資訊，請參閱 [限制授權的外部命令](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands).

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
   <td> blacklistFile<br /> </td> 
   <td> 包含要新增至允許清單之命令的檔案路徑。 <br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用者<br /> </td> 
   <td> 以其他使用者身分執行命令。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

以下是的不同引數 **htmlToPdf** 節點。 這是將網頁轉換為PDF檔案的服務的設定。

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
   <td> 執行轉換的命令列（在「其他」模式中）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessusCount<br /> </td> 
   <td> 最大 一部電腦上一次允許的轉換處理序數目。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> 模式<br /> </td> 
   <td> 用於轉換的工具。 可能的值包括：phantomjs、wkhtmltopdf、other、disabled<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'phantomjs' <br /> </td> 
  </tr> 
  <tr> 
   <td> 逾時<br /> </td> 
   <td> 轉換逾時：最長轉換時間（以秒為單位）。 超過此臨界值時，轉換程式將停止並引發錯誤。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> 詳細資訊<br /> </td> 
   <td> 詳細模式：以詳細模式啟動以診斷可能的錯誤。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waittime<br /> </td> 
   <td> 等待處理序時的延遲：同時使用所有處理序以及等待處理序釋放時的延遲（以秒為單位）。 如果超過此延遲，轉換就會停止並引發錯誤。 <br /> </td> 
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

以下是的不同引數 **ims** 節點。 這是Campaign連線至其他服務的設定，使用 [IMS](../../integrations/using/about-adobe-id.md).

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
   <td> 使用者端ID<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSClientSecret<br /> </td> 
   <td> 秘密金鑰（以AES加密）<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSCode<br /> </td> 
   <td> 授權代碼（以AES加密）<br /> </td> 
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
   <td> 技術帳戶使用者端ID<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientSecret<br /> </td> 
   <td> 技術帳戶秘密金鑰（以AES加密）<br /> </td> 
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
   <td> 技術帳戶私密金鑰（以AES加密）<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## JavaScript {#javascript}

以下是的不同引數 **javascript** 節點。 這是JavaScript解譯器的設定。

如需詳細資訊，請參閱 [報表檔案](../../reporting/using/actions-on-reports.md#memory-allocation).

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
   <td> 執行記憶體回收行程之前的大小上限（以MB為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> Stacksizekb<br /> </td> 
   <td> 每個棧疊區塊的大小（以kilo octet為單位）。 這是記憶體管理調整引數，大多數使用者不應加以調整。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchange {#mailexchanger}

以下是的不同引數 **mailExchange** 節點。 這是SMTP伺服器的設定。

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
   <td> SMTP伺服器：用於傳輸電子郵件的SMTP伺服器的IP位址。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> mxPort<br /> </td> 
   <td> 用於電子郵件傳輸的SMTP伺服器的TCP連線埠。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 模組 {#module}

以下是的不同引數 **模組** 節點。 這是名稱空間限制模組xtk的設定。

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
   <td> 預設名稱空間<br /> </td> 
   <td> 建立新實體時使用的預設名稱空間。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'cus'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 監視 {#monitoring}

以下是的不同引數 **監視** 節點。 這是監控服務組態。

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
   <td> 最長準備時間：不再準備傳遞動作的持續時間（以秒為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
  <tr> 
   <td> unixScript<br /> </td> 
   <td> 監視服務執行的Unix指令碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> winScript<br /> </td> 
   <td> 監視服務要執行的Windows指令碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## ooconv {#ooconv}

以下是的不同引數 **ooconv** 節點。 這是檔案轉換伺服器的設定。

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
   <td> maxConversion<br /> </td> 
   <td> 允許OpenOffice伺服器執行的最大轉換次數。 超出此數目後，伺服器就會重新啟動。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> 強制關閉前OpenOffice伺服器的最長閒置時間。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 7200<br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> OpenOffice伺服器接聽的連線埠間隔。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 8101-8110<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> 檔案轉換伺服器的URL<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

以下是的不同引數 **proxyConfig** 節點。 這是Proxy引數的設定。

如需詳細資訊，請參閱 [Proxy連線設定](file-res-management.md).

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
   <td> 已啟用<br /> </td> 
   <td> 使用Proxy伺服器<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> 覆寫<br /> </td> 
   <td> 例外：應忽略Proxy引數的位址清單。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'localhost*' <br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> 唯一的Proxy伺服器：對所有型別的Proxy使用相同的設定。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### HTTP Proxy/安全Proxy {#http-proxy---secure-proxy-}

在 **proxyConfig > HTTP Proxy / Secure Proxy** 節點，請設定下列引數。

如需詳細資訊，請參閱 [Proxy連線設定](file-res-management.md).

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
   <td> Proxy伺服器的位址<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 登入<br /> </td> 
   <td> 用於連線Proxy伺服器的登入<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 密碼<br /> </td> 
   <td> 用於與Proxy伺服器連線的密碼<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 連線埠<br /> </td> 
   <td> Proxy伺服器連線埠<br /> </td> 
   <td> 短<br /> </td> 
  </tr> 
 </tbody> 
</table>

## threadPool {#threadpool}

以下是的不同引數 **threadPool** 節點。

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
   <td> 集區中的最大執行緒數量。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

以下是的不同引數 **urlPermission** 節點。 這是Javascript程式碼可以存取的URL清單。

網域和規則運算式的清單，指定Adobe Campaign伺服器能否使用在Javascript程式碼中遇到的URL。

如果找不到URL，則會根據指定的預設模式執行預設動作。

如需詳細資訊，請參閱 [傳出連線的保護](../../installation/using/configuring-campaign-server.md#url-permissions).

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
   <td> 動作<br /> </td> 
   <td> URL不在授權清單（分項清單）中的預設動作。 可能的值包括「忽略」（在沒有警告訊息的情況下授權，這需要停用保護）、「警告」（授權並發出警告訊息）和「拒絕」（禁止存取URL）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 拒絕<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> URL選擇機制的偵錯追蹤：在URL驗證過程中發出其他訊息。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

## cusHeaders {#cusheaders}

此節點可讓您在從外部伺服器上傳檔案時執行的請求中新增特定標頭。 內容傳遞網路(CND)可以要求特定標頭，以信任請求者。 這些標頭可用來改善對Campaign請求的信任，尤其是在傳遞執行步驟下載每位收件者的個人化檔案時。 大量資源下載要求可解譯為DDos攻擊。 dnsPattern可讓您根據網域名稱為不同的CDN設定特定的標頭名稱和值。

```
  <!-- List of custom headers added to request. 
         -->
    <cusHeaders>

    <!-- Pattern of DNS name or domain 
         value :  dnsPattern: All or part of the URL's domain to verify, * is a wild card Default:  -->
      <dnsPattern value="">

    <!-- Header Name and Value 
           headerName :  Header Name 
           headerValue :  Header Value -->
        <headerDef headerName="" headerValue=""/>

      </dnsPattern>

    </cusHeaders> 
```

### URL {#url}

針對每個URL，新增 **url** 節點與下列引數：

如需詳細資訊，請參閱 [傳出連線的保護](../../installation/using/configuring-campaign-server.md#url-permissions).

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
   <td> URL涉及的網域名稱或網域父系：要驗證的URL網域的所有或部分名稱，可加速驗證。 只有當URL的網域包含dsnSuffix時，才會針對規則運算式驗證URL。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> 用於改善屬於此網域的驗證URL的規則運算式：URL必須驗證的規則運算式（如果它對應到dnsSuffix）。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

如果記錄符合 **dnsSuffix** 但不是 **urlRegEx**，則會檢查下列記錄。

例如，若要授權存取網域business.com的所有URL，我們可以定義兩個記錄：

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;http://.&#42;&quot;

和

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;https://.&#42;&quot;

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
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nms/jsp/.*"              />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nl/jsp/.*"               />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/xtk/jsp/.*"              />
```

## xtkJobs {#xtkjobs}

以下是的不同引數 **xtkJobs** 節點。 這是伺服器作業的設定。

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
   <td> 伺服器處理的記憶體狀態重新整理週期（以毫秒為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 封存 {#archiving}

以下是的不同引數 **封存** 節點。 這是在背景執行的封存作業的設定。

如需詳細資訊，請參閱 [啟用電子郵件封存（內部部署）](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-).

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
   <td> 要同時處理的EML數量<br /> </td> 
   <td> 長<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> archivingType<br /> </td> 
   <td> 已傳送訊息的封存策略（分項清單）。 可能的值為「0」（無封存）和「1」（將已傳送訊息的封存傳輸至SMTP伺服器）。<br /> </td> 
   <td> 位元組<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> 引數<br /> </td> 
   <td> 啟動引數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動開始<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> compressBatchSize<br /> </td> 
   <td> 壓縮封存檔的大小：壓縮封存檔中的檔案數上限。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressionformat<br /> </td> 
   <td> 封存期間使用的壓縮格式（列舉）。 可能的值是'0' （無壓縮）和'1' （使用zip格式壓縮已傳送的訊息）。<br /> </td> 
   <td> 位元組<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationDelay<br /> </td> 
   <td> 自動封存未處理電子郵件之前的延遲：封存未處理電子郵件之前的天數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動處理序時要執行的JavaScript識別碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定處理序耗用的RAM數量(Mb)的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：有關指定處理序耗用的RAM數量(Mb)的警告。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> 每個更新事件之間的延遲（秒）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 處理序自動重新啟動的時間（一天中的時間）。 另請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動程式重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00` <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> 刪除未處理的電子郵件之前的天數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動和最後停止。 因此，syslogd模組的優先順序必須為0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpBccAddress<br /> </td> 
   <td> 正在封存目標目的地<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpEnableTLS<br /> </td> 
   <td> 啟用SMTPS支援：當遠端伺服器支援時，在安全模式(STARTTLS/SMTPS)下啟用電子郵件的傳遞。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> 與封存SMTP伺服器的連線數目。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayAddress<br /> </td> 
   <td> 要使用的SMTP轉送的DNS名稱或IP位址的逗號分隔清單。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayPort<br /> </td> 
   <td> smtp伺服器的IP連線埠。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

以下是的不同引數 **inMail** 節點。 這是傳入電子郵件管理模組的設定。

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
   <td> 引數<br /> </td> 
   <td> 啟動引數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動開始<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> checkInstanceName<br /> </td> 
   <td> 驗證執行個體名稱：如果為true，則Message-ID標頭中包含的Adobe Campaign執行個體的名稱必須與目前的執行個體相同。 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> 轉寄地址：規則未處理的預設電子郵件轉寄地址。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> errorForwardAddress<br /> </td> 
   <td> 錯誤地址：用於傳輸無效電子郵件的預設地址（錯誤的MIME編碼）。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> 忽略訊息大小：用於忽略POP3伺服器傳回的訊息大小。 在此情況下，模組需要「。」 在訊息結束時。 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> 訊息讀取週期：訊息佇列輪詢頻率。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動處理序時要執行的JavaScript識別碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> 要更新的最大記錄數量：定義在更新資料庫之前保留在記憶體中的最大記錄訊息數量。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> POP3工作階段期間要讀取的最大訊息數量。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定處理序耗用的RAM數量(Mb)的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：有關指定處理序耗用的RAM數量(Mb)的警告。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> 工作階段持續時間：訊息處理工作階段的最長持續時間。<br /> </td> 
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
   <td> 已讀取訊息的佇列大小<br /> </td> 
   <td> 長<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> 與POP3伺服器的通訊逾時。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 處理序自動重新啟動的時間（一天中的時間）。 另請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動程式重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00` <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriodSec<br /> </td> 
   <td> 要輪詢的帳戶的資料庫重新載入頻率。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動和最後停止。 因此，syslogd模組的優先順序必須為0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msgDump {#msgdump}

在 **inMail > msgDump** 節點，請設定下列引數。 這是已處理訊息傾印的設定。

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
   <td> 傾印<br /> </td> 
   <td> 以文字格式儲存所有傳入訊息。 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> msgPath<br /> </td> 
   <td> 訊息傾印路徑。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '/tmp/inMail'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 互動 {#interactiond}

以下是的不同引數 **互動** 節點。 這是輸入互動事件的寫入精靈設定。

如需詳細資訊，請參閱 [互動 — 資料緩衝](../../installation/using/interaction-data-buffer.md).

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
   <td> 引數<br /> </td> 
   <td> 啟動引數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動開始<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> callDataSize<br /> </td> 
   <td> 最大 儲存在共用記憶體中用於呼叫資料的字元數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動處理序時要執行的JavaScript識別碼<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定處理序耗用的RAM數量(Mb)的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：有關指定處理序耗用的RAM數量(Mb)的警告。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> 最大 儲存在共用記憶體中的事件數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> 直接在主張之後排序的合格優惠方案的最大數量，將儲存以供統計之用。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 處理序自動重新啟動的時間（一天中的時間）。 另請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動程式重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00` <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動和最後停止。 因此，syslogd模組的優先順序必須為0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> 回應時間統計資料的彙總持續時間（秒）。 0表示統計儲存已停用。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> 最大 儲存在共用記憶體中用於識別個人的字元數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta {#mta}

以下是的不同引數 **mta** 節點。 這是傳遞代理程式的設定。

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
   <td> 引數<br /> </td> 
   <td> 啟動引數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '-tracefilter：nlmta' <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動開始<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> 資料記錄路徑<br /> </td> 
   <td> 已傳送電子郵件的儲存路徑：如果不為空，將會儲存已傳送電子郵件的所有來源檔案的路徑。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 偵錯路徑<br /> </td> 
   <td> 傾印目錄：如果不為空，則將已傳送郵件訊息的MIME信封複製到此目錄中。 用於疑難排解。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> DNS查詢記錄延遲：顯示記錄的時間（毫秒）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> 錯誤統計資料頻率：產生統計資料與資料庫中儲存之間的時間。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動處理序時要執行的JavaScript識別碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> 產生錯誤統計資料並將其儲存在資料庫中。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> 顯示記錄訊息的層級。 資料庫中寫入之記錄檔的嚴重性層級。 MTA產生的記錄訊息並非總是會寫入資料庫中。 使用此引數，您可以定義您認為必須在資料庫中寫入訊息的層級。 如果您定義層級2，也會寫入層級1和0的訊息，而如果您定義層級1，則只會寫入層級1和0的訊息。 可能的值為：0 （錯誤）、1 （警告）、2 （資訊）<br /> </td> 
   <td> 長<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> mta處理序可以使用的記憶體大小上限(MB)。 超過此限制後，程式將重新啟動，以便將其使用的記憶體釋放給系統。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定處理序耗用的RAM數量(Mb)的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：有關指定處理序耗用的RAM數量(Mb)的警告。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> 要考慮的連線臨界值。 如果errorPeriodSec指定的時段內的連線總數確實低於臨界值，則不會為給定路徑產生錯誤統計資料。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsTolog<br /> </td> 
   <td> 要考慮的錯誤臨界值：如果errorPeriodSec指定的時段內的錯誤總數確實低於臨界值，則不會為給定路徑產生錯誤統計資料。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesTolog<br /> </td> 
   <td> 要考慮的訊息臨界值。 如果errorPeriodSec指定的時段內的已傳送訊息總數確實低於臨界值，則不會為給定路徑產生錯誤統計資料。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> 通知轉送：用來轉送通知的HostName：Port。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 處理序自動重新啟動的時間（一天中的時間）。 另請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動程式重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00` <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> 刪除已封存電子郵件之前的延遲：清除dataLogPath中所指定目錄中的已封存電子郵件之前的天數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessages<br /> </td> 
   <td> 重試遺失的訊息：如果子處理序已終止，將會重試部分傳送。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動和最後停止。 因此，syslogd模組的優先順序必須為0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> signEmailLinks<br /> </td> 
   <td> 啟用簽章機制。 如此可改善電子郵件中追蹤連結的安全性。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> true<br /> </td> 
  </tr>
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> 傳遞統計伺服器的位址，指定為 
    &lt;dns or="" ip=""&gt; 
      <code>[</code>： 
     &lt;port&gt; 
       <code>]</code>. 另請參閱 
      <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">統計伺服器的座標</a>. 
      <br /> 
     </td> 
   <td> 字串<br /> </td> 
   <td> 如果未定義，預設連線埠為7777。<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSSupport<br /> </td> 
   <td> 依網域啟用TLS：啟用可由MX設定的TLS （需要最新的統計伺服器）。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> true <br /> </td> 
  </tr> 
  <!--tr> 
   <td> statServerVersion<br /> </td> 
   <td> Protocol version used: communication protocol version (1 for a v5.11 and 6.0.2 server, 2 for a v6.1 server).<br /> </td> 
   <td> String<br /> </td> 
   <td> If undefined, the latest version is used. <br /> </td> 
  </tr--> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> 如果設為「true」，表示您的執行個體使用 <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">增強的MTA</a>.<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifymode<br /> </td> 
   <td> 驗證模式：啟動驗證模式（無實際的訊息傳輸；用於模擬和測試）。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> 工作路徑<br /> </td> 
   <td> 工作目錄： MTA用來與其子處理序通訊的暫存檔的位置。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/mta/' <br /> </td> 
  </tr> 
  <tr> 
   <td> xMailer<br /> </td> 
   <td> X-Mailer欄位： SMTP郵件標頭中'X-Mailer'欄位的值。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'nlserver， Build $(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### 快取 {#cache}

在 **快取** 節點，請設定下列引數。 這是本機檔案快取設定。

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
   <td> 在以下時段後回收：時段（以秒為單位），過了這段時間後，檔案將自動從快取中刪除，以回收儲存空間。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> 快取大小上限(Mb)。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> 清除頻率：快取清除機制執行之間的時段（秒）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 轉送 {#relay}

在 **mta >轉送** 節點，請設定下列引數。 這是郵件傳遞的郵件伺服器設定。

此清單的處理方式與MX DNS查詢傳回的MX清單相同，通常只要第一個MX可用，就會使用下一個MX，依此類推。

如需詳細資訊，請參閱 [SMTP轉送](../../installation/using/configuring-campaign-server.md#smtp-relay).

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
   <td> 要使用的SMTP轉送的DNS名稱或IP位址的逗號分隔清單。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 連線埠<br /> </td> 
   <td> smtp伺服器的IP連線埠。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 主版 {#master}

在 **mta >主版** 節點，請設定下列引數。 這是主要伺服器的設定。

如需詳細資訊，請參閱此 [區段](../../installation/using/configuring-campaign-server.md#mta-child-processes).

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
   <td> 要傳遞的工作的資料庫輪詢頻率。 此值代表資料庫輪詢頻率（以秒為單位）。為了取得等待傳送的工作清單，MTA會定期輪詢資料庫。當沒有工作等待時，輪詢週期就會由此值定義。否則，如果工作已傳輸到子伺服器，則此輪詢持續時間會自動縮短為一秒，以便新工作可以儘快再次處理，亦即子伺服器再次可用時。這並不意味著每秒都會執行資料庫查詢，直到子伺服器再次可用為止。 事實上，只有當至少有一部子伺服器可供使用時，才會進行資料庫存取。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> 資料庫連線失敗後的等待期間。 資料庫連線失敗通常是由資料庫伺服器本身所造成。例如，伺服器也可能因維護目的而停止。 DataBaseRetryDelay引數定義在資料庫連線失敗的情況下兩次連線嘗試之間的持續時間。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> 私密金鑰(DomainKeys)快取的有效期。 用於根據DomainKeys建議(http://antispam.yahoo.com/domainkeys)簽署電子郵件的私密金鑰會儲存為資料庫中的選項。domainKeysReloadPeriodSec引數會定義MTA可以在快取中保留這些金鑰的秒數。 在此延遲之後，所有金鑰都必須從資料庫重新載入。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> 子伺服器的最大數量。 代表執行中的伺服器數目上限。建議將此數目限制在與伺服器記憶體資源相容的最佳值。這可以在傳遞期間進行檢查。 使用的記憶體不應超過可用的實體記憶體的三分之一，否則將會使用交換功能。 另請參閱 <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">MTA子處理序</a>.<br /> </td> 
   <td> 長<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> 子伺服器的最小數量。 MTA會嘗試至少將此數量的伺服器保持執行。 如果少於此值，它會每秒重新啟動新伺服器一次，直到達到此值為止。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> 啟動時的子伺服器數目。 動態監控子伺服器的數量；當MTA啟動時，它會建立此值所指示的子伺服器數量。通常，為了節省主機資源，子伺服器的啟動速度不能超過每秒一部伺服器。 不過，當MTA啟動時，此限制會遭撤銷，以便儘快提供子伺服器。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 子項 {#child}

在 **mta >子項** 節點，請設定下列引數。 這是子伺服器的設定。

如需詳細資訊，請參閱 [電子郵件傳送最佳化](../../installation/using/email-deliverability.md#email-sending-optimization).

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
   <td> 選用的命令列引數 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> 閒置子伺服器停止之前的逾時。 如果子伺服器的閒置時間大於此引數，它會自動終止以釋放主機資源。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> 最長訊息保留時間。 如果準備好的訊息由於節流而無法傳送或無法連線到目標MTA，則該訊息將會捨棄並於下次重試時進行處理。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> 每部子伺服器向FCM起始的最大平行HTTP請求數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> 每部子伺服器的最大訊息數量。 每個MTA子系都會處理此數量的訊息並終止。請務必指定一個數字，讓MTA中的記憶體或資源流失不會造成損害（通常為幾千）。 即使MTA程式碼中沒有已知的記憶體流失，內嵌JavaScript和XSL引擎也並非完全可靠。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> 擱置中的訊息：在記憶體中等待傳遞的訊息數上限。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> 子處理序可以使用的記憶體大小上限（以MB為單位）。 若超過此限制，處理程式將停止，以便將其使用的記憶體釋放給系統。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> 逾時（以秒為單位），過了這段時間，就會捨棄傳遞聯結器的SOAP連線。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> Startwithfirstmx<br /> </td> 
   <td> 一律從最高優先順序的MX開始。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> 恢復時連續嘗試的最大次數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

在 **mta >子項> smtp** 節點，請設定下列引數。 這是SMTP工作階段的設定。

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
   <td> 受到遠端伺服器支援時，在安全模式(STARTTLS/SMTPS)下啟用電子郵件的傳遞。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> 閒置工作階段逾時。 只有在工作階段被重複用來將數個訊息傳輸至指定網域時，才會使用此引數。當MTA完成訊息傳輸時，它使用的SMTP工作階段沒有系統地關閉。如果訊息已準備好傳送給這個相同的網域，則會重複使用相同的SMTP工作階段，這就是工作階段未自動關閉的原因。引數IdleSessionTimeout引數可讓您定義SMTP工作階段可以保持作用中狀態以等待其他訊息的時間。 持續時間過後，工作階段會自動關閉。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> 重試連線之前的初始延遲。 每次連線失敗時，此延遲都會加倍。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> 子伺服器的最大SMTP工作階段數目。 為了傳遞訊息，MTA會初始化與收件者MTA的SMTP連線。指定子伺服器的並行與作用中SMTP工作階段數上限受此值限制。 若將此值乘以maxSpareServers，您會得到指定的子伺服器可並行處理的訊息數目上限。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

在 **mta >子項> smtp > IPAffinity** 節點，請設定下列引數。 這是針對最佳化的傳出SMTP流量，設定與IP位址的相似性管理。

如需詳細資訊，請參閱 [要使用的IP位址清單](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use) 和 [管理具有相似性之輸出SMTP流量](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities).

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
   <td> 網域名稱：連結至IP位址的本機網域名稱。 發出SMTP HELO命令時使用。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 名稱<br /> </td> 
   <td> 邏輯名稱：使用者連結至相似性的名稱。 名稱使用分號分隔；<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

在 **mta >子項> smtp > IP** 節點，請設定下列引數。

如需詳細資訊，請參閱 [要使用的IP位址清單](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).

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
   <td> 關聯的實體地址。 例如：「192.168.0.1」<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> 關聯的公用位址ID。用作統計伺服器的金鑰。 必須為數字。 檢視此 <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">區段</a>.<br /> </td> 
   <td> 長<br /> </td> 
  </tr> 
  <tr> 
   <td> 權重<br /> </td> 
   <td> 指定此IP相對於其他IP的使用頻率（權重越大，頻率越高）。<br /> </td> 
   <td> 長<br /> </td> 
  </tr> 
  <tr> 
   <td> includeDomains<br /> </td> 
   <td> 要包含的網域遮罩的逗號分隔清單。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> excludeDomains<br /> </td> 
   <td> 要排除的網域遮罩的逗號分隔清單。<br /> </td> 
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

以下是的不同引數 **nmac** 節點。 這是用於推播通知傳送的設定。

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
   <td> 使用shared/proxyHTTP中定義的HTTP Proxy。 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 轉送 {#relay-1}

以下是的不同引數 **nmac >轉送** 節點。 這會設定訊息傳送（ios http2聯結器）的轉送使用。

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
   <td> 要使用的轉送的DNS位址或名稱。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 連線埠<br /> </td> 
   <td> 轉送連線埠<br /> </td> 
   <td> 長<br /> </td> 
   <td> 443<br /> </td> 
  </tr> 
  <tr> 
   <td> trustedCertsChain<br /> </td> 
   <td> 憑證鏈結（PEM檔案）。 使用模擬伺服器時很有用。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 已管線 {#pipelined}

以下是的不同引數 **已管線** 節點。 這是管道服務的事件處理模組設定。

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
   <td> 儲存公開金鑰時在Developer Connection中產生的應用程式名稱。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 引數<br /> </td> 
   <td> 啟動引數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authGatewayEndpoint<br /> </td> 
   <td> 用於取得閘道權杖的URL。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> 用於取得權杖的私密金鑰（使用XtkKey選項以AES加密）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動開始 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> disableAuth<br /> </td> 
   <td> 停用驗證：無需驗證即可連線到管道服務。 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> discoverPipelineEndpoint<br /> </td> 
   <td> 用於探索管道服務URL的URL。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> 狀態儲存週期：將處理序的內部資訊儲存在檔案中的頻率。 如果為0，則不啟用。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> 接聽URL：強制管道服務的接聽URL。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動處理序時要執行的JavaScript識別碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定處理序耗用的RAM數量(Mb)的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：有關指定處理序耗用的RAM數量(Mb)的警告。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> 狀態伺服器連線埠：可讓您查詢處理序狀態的HTTP伺服器連線埠。 如果為0，則不啟用。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 7781<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushMessageCount<br /> </td> 
   <td> 每次處理此數量的訊息時，指標都會儲存在資料庫中。<br /> </td> 
   <td> <br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushPeriodSec<br /> </td> 
   <td> 儲存指標之前的延遲：在此期間指標將至少儲存到資料庫中一次（在活動較少的情況下很有用）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 處理序自動重新啟動的時間（一天中的時間）。 另請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動程式重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00` <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThreads<br /> </td> 
   <td> 使用個人化JavaScript聯結器進行事件處理的執行緒數量。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> processingThreads<br /> </td> 
   <td> 事件處理的執行緒數目。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> retryPeriodSec<br /> </td> 
   <td> 發生失敗時處理之間的延遲。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> 在此時段後捨棄：如果在此時段後處理仍失敗，則捨棄事件。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動和最後停止。 因此，syslogd模組的優先順序必須為0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 修復 {#repair}

以下是的不同引數 **修復** 節點。 這是資料庫修復模組的組態。

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
   <td> 傳遞動作修復模組：延遲（以分鐘為單位），過了這段時間，修復模組可以處理傳遞動作。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

以下是的不同引數 **securityZone** 節點。

如需詳細資訊，請參閱 [定義安全區域](../../installation/using/security-zones.md).

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
   <td> 授權Web應用程式的偵錯模式。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> 授權使用者在沒有密碼的情況下使用應用程式。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowHTTP<br /> </td> 
   <td> 授權使用HTTP進行操作者登入。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInjection<br /> </td> 
   <td> 授權在運算式中使用SQLDATA。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserPassword<br /> </td> 
   <td> 授權使用者/密碼工作階段權杖。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> 標籤<br /> </td> 
   <td> 標籤<br /> </td> 
   <td> 字串<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> 名稱<br /> </td> 
   <td> 內部名稱<br /> </td> 
   <td> 字串<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTokenOnly<br /> </td> 
   <td> 請勿使用安全性權杖。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> showErrors<br /> </td> 
   <td> 顯示錯誤詳細資料<br /> </td> 
   <td> 布林值<br /> </td> 
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

### 子網路 {#subnetwork}

以下是的不同引數 **securityZone > subNetwork** 節點。

如需詳細資訊，請參閱 [定義安全區域](../../installation/using/security-zones.md).

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
   <td> 遮色片<br /> </td> 
   <td> 遮罩或位址<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 名稱<br /> </td> 
   <td> 內部名稱<br /> </td> 
   <td> 字串<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> proxy<br /> </td> 
   <td> 此子網路用於存取執行個體的（反向） Proxy遮罩或位址。 在這種情況下，將測試「X-Forwarded-For」標頭而不是此Proxy。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 簡訊 {#sms}

以下是的不同引數 **簡訊** 節點。 這是傳入SMS管理模組的設定。

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
   <td> 引數<br /> </td> 
   <td> 啟動引數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動開始<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataRetentionDays<br /> </td> 
   <td> SMPP聯結器保留工作檔案的最大天數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> dataSizeMo<br /> </td> 
   <td> SMPP工作檔案的大小上限（以MB為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 512<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動處理序時要執行的JavaScript識別碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> 工作階段持續性框架的週期：最大值。 兩個框架之間的時段（以秒為單位），用於通知接收工作階段仍處於啟用狀態。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定處理序耗用的RAM數量(Mb)的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：有關指定處理序耗用的RAM數量(Mb)的警告。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> 搜尋頻率：簡訊帳戶輪詢週期。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 處理序自動重新啟動的時間（一天中的時間）。 另請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動程式重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00` <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPerod<br /> </td> 
   <td> 帳戶重新載入頻率：要輪詢之帳戶的資料庫重新載入頻率。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動和最後停止。 因此，syslogd模組的優先順序必須為0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> SR處理延遲的秒數：僅限復原日期早於目前時間減去srReadDelay所給定的持續時間（以秒為單位）的SR。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> 逾時<br /> </td> 
   <td> 與簡訊閘道的通訊逾時。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

以下是的不同引數 **sms > netsize** 節點。

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
   <td> 與Netsize建立連線時的逾時（秒）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## stat {#stat}

以下是的不同引數 **stat** 節點。 這是MTA統計模組的設定。

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
   <td> 引數<br /> </td> 
   <td> 啟動引數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動開始<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動處理序時要執行的JavaScript識別碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定處理序耗用的RAM數量(Mb)的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：有關指定處理序耗用的RAM數量(Mb)的警告。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> 連線埠<br /> </td> 
   <td> 伺服器接聽連線埠。 檢視此 <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">區段</a>.<br /> </td> 
   <td> 短<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 處理序自動重新啟動的時間（一天中的時間）。 另請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動程式重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00` <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動和最後停止。 因此，syslogd模組的優先順序必須為0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslogd {#syslogd}

以下是的不同引數 **syslogd** 節點。 這是記錄管理模組的設定。

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
   <td> 引數<br /> </td> 
   <td> 啟動引數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動開始<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動處理序時要執行的JavaScript識別碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> 記錄檔的大小上限（以Mb為單位）。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> 要保留的logins.log檔案的最大數量。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定處理序耗用的RAM數量(Mb)的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：有關指定處理序耗用的RAM數量(Mb)的警告。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 處理序自動重新啟動的時間（一天中的時間）。 另請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動程式重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00` <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動和最後停止。 因此，syslogd模組的優先順序必須為0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 追蹤 {#tracking}

以下是的不同引數 **追蹤** 節點。 這是追蹤伺服器的設定。

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
   <td> 引數<br /> </td> 
   <td> 啟動引數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動開始<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> blockRedirectForUnsignedTrackingLink<br /> </td> 
   <td> 停用從先前組建產生的格式錯誤的URL。<br /> </td> 
   <td> 布林值<br /> </td> 
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
   <td> 刪除重複的開啟專案：移除重複的開啟追蹤記錄，以限制郵件閱讀程式（例如Outlook）中郵件預覽的影響。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> 忽略最多X%的錯誤：只要尚未考慮的分錄比率未達到此值，就不會更新追蹤指標。 <br /> </td> 
   <td> 位元組<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> 更新錯誤指標：重新計算錯誤指標之前的最長持續時間。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> 指示器持續時間<br /> </td> 
   <td> 計算期間內的指標：傳遞有效日期之後的期間，過了這段期間後，將不再計算合併的指標。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動處理序時要執行的JavaScript識別碼 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> 透過呼叫遠端追蹤伺服器所請求的記錄數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定處理序耗用的RAM數量(Mb)的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：有關指定處理序耗用的RAM數量(Mb)的警告。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceAPIKey<br /> </td> 
   <td> Phishbowl服務端點整合的API金鑰。 這樣可保護從舊組建產生之格式錯誤的URL的重新導向。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Phishbowl服務端點整合的端點。 這樣可保護從舊組建產生之格式錯誤的URL的重新導向。<br /> </td> 
   <td> 長<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 處理序自動重新啟動的時間（一天中的時間）。 另請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動程式重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00` <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動和最後停止。 因此，syslogd模組的優先順序必須為0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> 忽略最多X%的追蹤：只要尚未考慮的分錄比率未達到此值，就不會更新追蹤指標。<br /> </td> 
   <td> 位元組<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> 更新追蹤指標：重新計算追蹤指標之前的最長持續時間。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> 瀏覽器識別碼快取的大小。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogd {#trackinglogd}

以下是的不同引數 **trackinglogd** 節點。 這是追蹤記錄寫入精靈的設定。

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
   <td> 引數<br /> </td> 
   <td> 啟動引數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動開始<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動處理序時要執行的JavaScript識別碼 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> 最大寫入重試次數：在記錄檔寫入失敗時可建立的最大檔案數量。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> 最大記錄檔大小：記錄檔在磁碟上使用的最大空間(MB)。 不得少於100 MB。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定處理序耗用的RAM數量(Mb)的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：有關指定處理序耗用的RAM數量(Mb)的警告。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> 最大記錄計數：共用記憶體中儲存的最大記錄數。 不得小於10000。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 處理序自動重新啟動的時間（一天中的時間）。 另請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動程式重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00` <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> 清除之前的記錄數：開始清除記錄檔之前插入的記錄數。 不得低於50000。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動和最後停止。 因此，syslogd模組的優先順序必須為0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> 為額外的網頁追蹤引數儲存在共用記憶體中的最大字元數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 網頁 {#web}

以下是的不同引數 **網頁** 節點。 這是Web模組的設定。

如需詳細資訊，請參閱此 [區段](configuring-campaign-server.md#default-port-for-tomcat).

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
   <td> 以字串形式傳遞的JVM選項。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 最大執行緒<br /> </td> 
   <td> 最大對話次數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> MinspareThreads<br /> </td> 
   <td> 最小對話次數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> 引數<br /> </td> 
   <td> 啟動引數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動開始<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> 控制埠<br /> </td> 
   <td> Tomcat聆聽控制連線埠：請參閱 <a href="configure-tomcat.md" target="_blank">設定Tomcat</a>.<br /> </td> 
   <td> 短<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Tomcat HTTP接聽連線埠：請參閱 <a href="configure-tomcat.md" target="_blank">設定Tomcat</a>.<br /> </td> 
   <td> 短<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動處理序時要執行的JavaScript識別碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> SubmitDelivery呼叫的佇列大小：可佇列的SubmitDelivery SOAP呼叫數上限。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定處理序耗用的RAM數量(Mb)的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：關於指定處理序耗用的RAM數量(Mb)的警告<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> 通知轉送：啟用通知轉送的HostName：Port。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 處理序自動重新啟動的時間（一天中的時間）。 另請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動程式重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00` <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動和最後停止。 因此，syslogd模組的優先順序必須為0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> Startsoaprouterinmodule<br /> </td> 
   <td> 以模組模式啟動SOAP路由器。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### jsp {#jsp}

以下是的不同引數 **web > jsp** 節點。 這是JSP使用的參陣列態。

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
   <td> 偵錯<br /> </td> 
   <td> 是否在偵錯模式下執行JSP。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> downloadpath<br /> </td> 
   <td> 下載資料夾：使用者端主控台安裝程式的下載路徑。<br /> </td> 
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
   <td> soaprouter<br /> </td> 
   <td> SOAP路由器的URL (http://myserver/xxx、http://jni或mailto:xxx)。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'http://jni'<br /> </td> 
  </tr> 
 </tbody> 
</table>

此 **web > jsp >類別路徑** node包含啟動JVM時要使用的所有類別路徑清單。 以下是預設設定：

```
'$(XTK_INSTALL_DIR)/tomcat-8/bin/bootstrap.jar
          $(XTK_INSTALL_DIR)/tomcat-8/bin/tomcat-juli.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-coyote.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-util.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/servlet-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/jsp-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/el-api.jar
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

以下是的不同引數 **web > jssp** 節點。 這是JSSP使用的引數設定。

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
   <td> collectoragemafterrequest<br /> </td> 
   <td> 在每次查詢後啟用JavaScript內容的記憶體回收行程。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> JavaScript內容提供的最大頁數。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

此 **web > jsp >類別路徑** node包含啟動JVM時要使用的所有類別路徑清單。

### 轉送 {#relay-2}

以下是的不同引數 **web >轉送** 節點。 這是兩個區域之間HTTP要求的轉送設定。

如需詳細資訊，請參閱此 [區段](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> 以偵錯模式啟動網頁伺服器中的HTTP轉送模組。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInAuthority<br /> </td> 
   <td> 禁用的字元（網域）： URI「許可權」區段中的禁用字元清單。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '.？#@/：' <br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInPath<br /> </td> 
   <td> 禁用的字元（路徑）： URI 「路徑」區段中的禁用的字元清單。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '？#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> 'mod_dir'模組選項的值：查詢資料夾時要使用的檔案清單。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'index.md' <br /> </td> 
  </tr> 
  <tr> 
   <td> startRelay<br /> </td> 
   <td> 啟動HTTP轉送模組。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> 在網頁伺服器內啟動HTTP轉送模組。 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> 逾時<br /> </td> 
   <td> 刪除禁止的url之前的等待時間。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '60'<br /> </td> 
  </tr> 
 </tbody> 
</table>

新增 **web >轉送> url** 每個要轉送URL的節點（插入順序定義優先順序），包含下列引數。

如需詳細資訊，請參閱 [動態頁面安全性和轉送](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) 和 [區段](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> 已授權的IP：逗號分隔的來源IP位址清單，允許使用此遮罩的轉送。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 拒絕<br /> </td> 
   <td> 拒絕存取這些URL （傳回HTTP 403錯誤）<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> 要轉送的DNS別名：要轉送的DNS別名遮罩的逗號分隔清單（例如：「*.adobe.com」）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllowed<br /> </td> 
   <td> 無論安全區域是什麼，HTTP存取已授權（如webApps）。 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayHost<br /> </td> 
   <td> 新增原始主機：中繼時使用原始請求的HTTP「主機」標頭。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 轉送路徑<br /> </td> 
   <td> 新增初始URL路徑：附加URL的完整路徑，以轉送至目標頁面的URL。 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 狀態<br /> </td> 
   <td> 公用資源的同步狀態（列舉）。 可能的值包括「正常」（一般執行）、「黑名單」（在錯誤404的情況下將url新增到封鎖清單）和「備用」（如果存在，檔案會上傳到備用伺服器）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 一般<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> 目標頁面的URL：請參閱 <a href="configure-tomcat.md" target="_blank">設定Tomcat</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 逾時<br /> </td> 
   <td> 被轉送的請求的最長執行時間（以秒為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> url路徑<br /> </td> 
   <td> 要轉送的URL遮罩（例如：「/nl*」、「*.jsp」）。<br /> </td> 
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

新增 **web > relay > responseHeader** 節點，用於新增轉發至轉送的回覆。

如需詳細資訊，請參閱 [管理HTTP標頭](../../installation/using/configuring-campaign-server.md#managing-http-headers).

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
   <td> 名稱<br /> </td> 
   <td> 頁首名稱<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 值<br /> </td> 
   <td> 標頭值 <br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是預設設定：

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### 重新導向 {#redirection}

以下是的不同引數 **網頁>重新導向** 節點。 這是重新導向模組的設定。

如需詳細資訊，請參閱此 [區段](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> Imsrogid<br /> </td> 
   <td> 組織ID： Adobe Experience Cloud中的唯一組織識別碼，特別用於VisitorID服務和IMS SSO。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> 描述用於永久Cookie的原則值（符合P3P壓縮原則格式）。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'CAO DSP COR CURa DEVa TAI我們的巴士IND UNI COM NAV'<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> 要設定以逗號分隔的網域清單，以明確指示要設定Cookie的網域。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseid<br /> </td> 
   <td> 與追蹤執行個體相關聯的資料庫識別碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> Deflogcount<br /> </td> 
   <td> 依據呼叫的記錄計數：在呼叫GetTrackingLogs方法時，預設會傳回的記錄數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> 過期網址<br /> </td> 
   <td> 過期重新導向的頁面：當傳遞動作的重新導向過期時，重新導向伺服器預設會使用的網頁URL。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> 最大工作計數：快取中的最大傳遞動作數。 不得低於50。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> showSourceIp<br /> </td> 
   <td> 設為false時，r/test傳回之回應中的sourceIP值為空字串。 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirection<br /> </td> 
   <td> 啟動重新導向服務。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectionInModule<br /> </td> 
   <td> 以模組模式啟動重新導向服務。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> trackWebVisitors<br /> </td> 
   <td> 網路追蹤：為未知使用者造訪的頁面建立記錄。 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingPassword<br /> </td> 
   <td> 重新導向伺服器使用的密碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是的不同引數 **web >重新導向> spareServer** 節點。

如需詳細資訊，請參閱 [備援追蹤](../../installation/using/configuring-campaign-server.md#redundant-tracking).

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
   <td> 出現時納入考量：如果運算式傳回true，則納入追蹤伺服器考量。 <br /> </td> 
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
   <td> 額外的重新導向伺服器URL<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

### 垃圾郵件檢查 {#spamcheck}

以下是的不同引數 **網頁> spamCheck** 節點。 這是電子郵件反垃圾郵件評分評估引數的設定。

如需詳細資訊，請參閱 [設定SpamAssassin](../../installation/using/configuring-spamassassin.md).

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
   <td> 評估電子郵件的反垃圾郵件分數要執行的命令（例如「perl spamcheck.pl」）。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

以下是的不同引數 **wfserver** 節點。 這是工作流程程式設定。

如需詳細資訊，請參閱 [高可用性工作流程與相關性](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

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
   <td> 相似性<br /> </td> 
   <td> 相似性<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 引數<br /> </td> 
   <td> 啟動引數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動開始<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> 期間<br /> </td> 
   <td> 長<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動處理序時要執行的JavaScript識別碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體耗用警報：有關給定處理序耗用的RAM數量(Mb)的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體耗用警告：有關指定處理序耗用的RAM數量(Mb)的警告。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> 通知轉送：啟用通知轉送的HostName：Port。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 處理序自動重新啟動的時間（一天中的時間）。 另請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動程式重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00` <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動和最後停止。 因此，syslogd模組的優先順序必須為0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>
