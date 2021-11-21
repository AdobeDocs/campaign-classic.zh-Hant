---
product: campaign
title: 伺服器設定檔
description: 伺服器設定檔
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 70cd6a4b-c839-4bd9-b9a7-5a12e59c0cbf
source-git-commit: e719c8c94f1c08c6601b3386ccd99d250c9e606b
workflow-type: tm+mt
source-wordcount: '7969'
ht-degree: 5%

---

# 伺服器設定檔{#the-server-configuration-file}

![](../../assets/v7-only.svg)

Adobe Campaign的整體設定定義於 **serverConf.xml** 檔案，位於 **conf** 安裝目錄的目錄。 本節列出 **serverConf.xml** 檔案。

>[!NOTE]
>
>伺服器端設定只能由Adobe執行，以供Adobe托管的部署使用。 若要進一步了解不同部署，請參閱 [托管模型](../../installation/using/hosting-models.md) 區段或 [本頁](../../installation/using/capability-matrix.md). 本節將介紹托管模型和混合模型的安裝和配置步驟 [節](../../installation/using/hosting-models.md).

第一個參數位於 **共用** 節點。 這些與例項相關。 所有nlserver命令（nlserver web、nlserver wfserver等）都可能使用它們。 其他部分與特定nlserver子命令相關。

**共用參數**

* [驗證](#authentication)
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

* [封存](#archiving)
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

## 驗證 {#authentication}

以下是 **驗證** 節點：

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
   <td> 啟用IP地址檢查。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultMode<br /> </td> 
   <td> 預設標識模式。<br /> </td> 
   <td> 字串<br /> </td> 
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
   <td> 快取持續時間：會話資訊快取（秒）。<br /> </td> 
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

以下是 **authentication > XTK** 節點：

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

以下是 **dataStore** 節點。 這是定義伺服器資料來源的位置。

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
   <td> 額外的沙盒目錄：要在沙箱中添加的其他路徑（以逗號分隔）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '/home/customers/,/sftp/ <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> 表單快取過期延遲：快取項失效的逾時秒數。 O表示快取項僅在發佈時刷新。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> 主機<br /> </td> 
   <td> DNS掩碼：此執行個體提供的DNS遮罩清單(以逗號分隔，可以使用*和？ 模式)。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> interactionCacheTimeToLive<br /> </td> 
   <td> 交互JSSP快取過期延遲：快取項失效的逾時秒數。 負值表示快取一律失效。 「0」、空值或無效值視為60。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> 朗<br /> </td> 
   <td> 例項語言（枚舉）。 可能的值包括「fr_FR」（法文）、「en_GB」(英文（英國）)、「en_US」(英文（美國）)、「de_DE」（德文）和「ja_JP」（日文）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'en_US'<br /> </td> 
  </tr> 
  <tr> 
   <td> uploadDirectory<br /> </td> 
   <td> 上傳資料夾：上傳資料的目標目錄路徑。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/' <br /> </td> 
  </tr> 
  <tr> 
   <td> uploadAllowlist<br /> </td> 
   <td> 要下載的授權檔案由「，」分隔。 字串必須是有效的規則java運算式。 請參閱 <a href="file-res-management.md" target="_blank">限制可上載的檔案</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> 將機密儲存在Vault中：使用Hashicorp Vault。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultSecretPath<br /> </td> 
   <td> 保險庫中的機密路徑<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '/v1/secret/campaign/'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> 包含保管庫令牌的檔案的本地路徑。 $(HOME)可用於此路徑（但不能用於其他env變數）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '$(HOME)/.vaulttoken'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> Hashicorp保管庫URL <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> 視圖快取的有效期：快取項失效的逾時秒數。 負值表示快取一律失效。 「0」、空值或無效值視為60。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> 工作目錄的XPath。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> workingDirectory :工作目錄的XPath。 預設值：'$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/'<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

以下是 **dataStore > proxyAdjust** 節點。 符合規則運算式的URL會根據urlBase中定義的URL重新產生。

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
   <td> 產生外部URL時使用的基礎。 例如：https://server.domain.com<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> 符合URL的規則運算式。 例如：http://server\.lan\.net.*<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

### dataSource {#datasource}

以下是 **dataStore > dataSource** 節點。

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

在 **dataStore > dataSource > dbcnx** 節點，配置連接設定：

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
   <td> 加密<br /> </td> 
   <td> 加密密碼<br /> </td> 
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
   <td> 類型（分項清單）。 可能的值有：「Oracle」、「MSSQL」(Microsoft SQL Server)、「PostgreSQL」(PostgreSQL)、「Teradata」、「DB2」、「MySQL」、「Netezza」、「AsterData」、「SAPHANA」(SAP HANA)、「RedShift」(Amazon紅移)、「ODBC」(ODBC(SybaseASE,Sybase IQ)、「中繼」(HTTP)。<br /> </td> 
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
   <td> 帶時區的日期欄位：請參閱 <a href="../../installation/using/time-zone-management.md" target="_blank">時區管理</a>.<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

在 **dataStore > dataSource > sqlParams** 節點，配置SQL參數：

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

在 **dataStore > dataSource > pool** 節點，配置關聯連接池的參數：

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
   <td> 簡短<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> 池中保留的空閒連接數。<br /> </td> 
   <td> 簡短<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> 拒絕新連接前允許的最大連接數。 看這個 <a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">技術檔案</a>.<br /> </td> 
   <td> 簡短<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> 連接的最大空閒時間。 0表示預設值。<br /> </td> 
   <td> 簡短<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

以下是 **dataStore > virtualDir** 節點。 這是虛擬目錄到真實目錄映射的配置。

如需詳細資訊，請參閱 [管理公共資源](file-res-management.md).

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

預設設定如下：

```
<virtualDir name="images" path="$(XTK_INSTALL_DIR)/var/res/img/"/>
<virtualDir name="formCache" path="$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/formCache/"/>
<virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)"/>
```

### preprocessCommand {#preprocesscommand}

以下是 **dataStore > preproceCommand** 節點。 這些是預處理「載入檔案」工作流活動的授權命令。

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
   <td> label<br /> </td> 
   <td> 命令行標籤<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 名稱<br /> </td> 
   <td> 命令行名稱<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

預設設定如下：

```
<preprocessCommand command="" label="None" name="none"/>
<preprocessCommand command="zcat &quot;$fileName&quot;" label="Decompression" name="zcat"/><preprocessCommand command="gpg --decrypt &quot;$fileName&quot;" label="Decrypt" name="gpg"/>
```

## dnsConfig {#dnsconfig}

以下是 **dnsConfig** （DNS配置）節點。

如需詳細資訊，請參閱 [節](../../installation/using/configuring-campaign-server.md).

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
   <td> 域名：預設域名。 由SMTP HELO命令使用。 預設情況下，使用在Windows中聲明的第一個網路介面的網路參數；或在Linux（網域或搜尋項目）下解析file/etc/resolv.conf 。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServers<br /> </td> 
   <td> DNS伺服器：域名伺服器(DNS)的逗號分隔清單。 請參閱下方的備注。<br /> </td> 
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
>附註 **nameSevers**:依預設，會使用網路
>在Windows中聲明的第一個網路介面的參數
>未在UNIX中定義。 定義域名伺服器(DNS)
>由MTA用於獲取為
>網域。
>
>如果未定義此值，MTA會在主機網路配置中搜索此資訊。 如果可能有數個DNS，則不同的DNS位址必須以逗號分隔(範例：212.155.207.1,212.155.207.2)。 如果您的傳送伺服器有數個網路介面，則MTA使用的DNS清單是第一個。 在此情況下，建議您指定 **nameServer** 參數來避免任何模糊。

>[!CAUTION]
>
>如果您的網路主機配置使用DHCP，則MTA將找不到DHCP提供的DNS清單。 在此情況下，建議在Windows控制面板的網路參數中指定DNS清單。

## 執行 {#exec}

以下是 **執行** （命令執行）節點。

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
   <td> 包含要添加到允許清單的命令的檔案的路徑。 <br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用者<br /> </td> 
   <td> 以其他用戶身份執行命令。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

以下是 **htmlToPdf** 節點。 這是將網頁轉換為PDF檔案的服務的設定。

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
   <td> 用於運行轉換的命令行（在「其他」模式下）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessusCount<br /> </td> 
   <td> Max。 一台電腦上一次允許的轉換程式數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> 模式<br /> </td> 
   <td> 用於轉換的工具。 可能的值包括：phantomjs, wkhtmltopdf，其他，已停用<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'phantomjs' <br /> </td> 
  </tr> 
  <tr> 
   <td> 逾時<br /> </td> 
   <td> 轉換逾時：最大轉換時間（秒）。 超過此臨界值時，轉換程式會停止，並引發錯誤。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> verbose<br /> </td> 
   <td> 詳細模式：以詳細模式啟動以診斷可能的錯誤。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> 等待進程時延遲：延遲秒數，即所有進程同時使用以及等待進程釋放時。 如果超過此延遲，則會停止轉換並引發錯誤。 <br /> </td> 
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

以下是 **ims** 節點。 這是Campaign連線至其他服務的設定，使用 [IMS](../../integrations/using/about-adobe-id.md).

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
   <td> 授權代碼（在AES中加密）<br /> </td> 
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
   <td> 技術帳戶密鑰（在AES中加密）<br /> </td> 
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

## JavaScript {#javascript}

以下是 **javaScript** 節點。 這是JavaScript解釋器的配置。

如需詳細資訊，請參閱 [報表檔案](../../reporting/using/actions-on-reports.md#memory-allocation) 和這個 [技術檔案](https://helpx.adobe.com/campaign/kb/out-of-memory-error-in-js-code-activity-in-workflows.html).

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
   <td> 運行垃圾收集器之前的最大大小(MB)。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> stackSizeKB<br /> </td> 
   <td> 每個堆棧塊的大小（以千位八位元組為單位）。 這是記憶體管理調整參數，大多數用戶不應加以調整。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchanger {#mailexchanger}

以下是 **mailExchanger** 節點。 這是SMTP伺服器的配置。

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

## 模組 {#module}

以下是 **模組** 節點。 這是命名空間限制模組xtk的設定。

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

## 監控 {#monitoring}

以下是 **監控** 節點。 這是監視服務配置。

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
   <td> 最大準備時間：持續時間（以秒為單位），之後傳送動作不應再準備中。<br /> </td> 
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
   <td> 要由監視服務執行的Windows指令碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 烏孔夫 {#ooconv}

以下是 **烏孔夫** 節點。 這是文檔轉換伺服器的配置。

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
   <td> 允許OpenOffice伺服器執行的最大轉換數。 除此數字外，伺服器重新啟動。<br /> </td> 
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
   <td> OpenOffice伺服器正在偵聽的埠間隔。<br /> </td> 
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

以下是 **proxyConfig** 節點。 這是Proxy參數的設定。

如需詳細資訊，請參閱 [代理連接配置](file-res-management.md).

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
   <td> 使用代理伺服器。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> 覆寫<br /> </td> 
   <td> 例外：應忽略代理參數的地址清單。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'localhost*' <br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> 唯一代理伺服器：對所有類型的代理使用相同的配置。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### HTTP代理/安全代理 {#http-proxy---secure-proxy-}

在 **proxyConfig > HTTP Proxy/Secure Proxy** 節點，請配置以下參數。

如需詳細資訊，請參閱 [代理連接配置](file-res-management.md).

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
   <td> 登入<br /> </td> 
   <td> 登錄到代理伺服器的連接<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 密碼<br /> </td> 
   <td> 與代理伺服器連接的密碼<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 埠<br /> </td> 
   <td> 代理伺服器埠<br /> </td> 
   <td> 簡短<br /> </td> 
  </tr> 
 </tbody> 
</table>

## threadPool {#threadpool}

以下是 **threadPool** 節點。

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
   <td> 池中的最大線程數。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

以下是 **urlPermission** 節點。 這是Javascript程式碼可存取的URL清單。

網域清單和規則運算式，指定Javascript程式碼中遇到的URL是否可供Adobe Campaign伺服器使用。

如果找不到URL，則會根據指定的預設模式執行預設動作。

如需詳細資訊，請參閱 [傳出連線保護](../../installation/using/configuring-campaign-server.md#url-permissions).

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
   <td> 如果URL不在授權清單中，則預設動作（列舉）。 可能的值包括「忽略」（授權時沒有警告消息，這要求禁用保護）、「警告」（授權並發出警告消息）和「拒絕」（禁止訪問URL）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 拒絕<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> URL選取機制的偵錯追蹤：在URL驗證程式期間會發出其他訊息。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### url {#url}

為每個URL新增 **url** 節點，且參數如下：

如需詳細資訊，請參閱 [傳出連線保護](../../installation/using/configuring-campaign-server.md#url-permissions).

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
   <td> 網域名稱或網域父項，由URL關注：要驗證的URL網域的全部或部分，以加速驗證。 只有在規則運算式的域包含dsnSuffix時，才會驗證URL。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> 規則運算式，用於精簡屬於此網域的URL:URL必須驗證的規則運算式，其是否對應至dnsSuffix。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

如果記錄滿足 **dnsSuffix** 但 **urlRegEx**，將檢查以下記錄。

例如，要授權訪問域business.com的所有URL，我們可以定義兩條記錄：

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;http://.*」

和

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;https://.*」

預設設定如下：

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

以下是 **xtkJobs** 節點。 這是伺服器作業的配置。

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
   <td> 伺服器處理的記憶體狀態刷新週期（以毫秒為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 封存 {#archiving}

以下是 **封存** 節點。 這是後台執行的存檔操作的配置。

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
   <td> 同時處理的EML數量<br /> </td> 
   <td> 長<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> archivingType<br /> </td> 
   <td> 已傳送訊息的封存策略（分項清單）。 可能的值為「0」（無存檔）和「1」（將已發送郵件的存檔傳輸到SMTP伺服器）。<br /> </td> 
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
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> compressBatchSize<br /> </td> 
   <td> 壓縮的存檔大小：壓縮的存檔中檔案的最大數量。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressionFormat<br /> </td> 
   <td> 存檔（枚舉）期間使用的壓縮格式。 可能的值為「0」（無壓縮）和「1」（使用zip格式壓縮已傳送的訊息）。<br /> </td> 
   <td> 位元組<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationDelay<br /> </td> 
   <td> 自動封存未處理電子郵件之前的延遲：封存未處理電子郵件的天數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動程式時要執行的JavaScript ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：有關給定進程消耗的RAM量（以Mb為單位）的警告。<br /> </td> 
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
   <td> 自動重新啟動程式的當天時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動處理重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> 刪除未處理電子郵件的天數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 簡短<br /> </td> 
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
   <td> 激活SMTPS支援：當遠端伺服器支援時，會以安全模式(STARTTLS/SMTPS)啟用電子郵件傳送。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> 與存檔SMTP伺服器的連接數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayAddress<br /> </td> 
   <td> 要使用的SMTP中繼的DNS名稱或IP位址清單（以逗號分隔）。 <br /> </td> 
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

以下是 **inMail** 節點。 這是傳入電子郵件管理模組的設定。

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
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> checkInstanceName<br /> </td> 
   <td> 驗證實例名稱：若為true,Message-ID標題中包含的Adobe Campaign例項名稱必須與目前例項相同。 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> 轉發地址：規則未處理預設的電子郵件傳送地址。 <br /> </td> 
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
   <td> 忽略消息大小：用於忽略POP3伺服器返回的消息的大小。 在此情況下，模組會預期「。」 訊息的結尾。 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> 消息讀取期間：消息隊列輪詢頻率。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動程式時要執行的JavaScript ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> 要更新的日誌數上限：定義在更新資料庫之前要保留在記憶體中的日誌消息的最大數量。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> POP3會話期間要讀取的最大消息數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：有關給定進程消耗的RAM量（以Mb為單位）的警告。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> 工作階段持續時間：消息處理會話的最大持續時間。<br /> </td> 
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
   <td> 與POP3伺服器的通信超時。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 自動重新啟動程式的當天時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動處理重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriodSec<br /> </td> 
   <td> 要輪詢的帳戶的資料庫重新載入頻率。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 簡短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msgDump {#msgdump}

在 **inMail > msgDump** 節點，請配置以下參數。 這是已處理訊息的傾印設定。

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
   <td> 轉儲<br /> </td> 
   <td> 以文字格式儲存所有傳入訊息。 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> msgPath<br /> </td> 
   <td> 消息轉儲路徑。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 「/tmp/inMail」<br /> </td> 
  </tr> 
 </tbody> 
</table>

## interactiond {#interactiond}

以下是 **interactiond** 節點。 這是入站交互事件的寫入守護程式的配置。

如需詳細資訊，請參閱 [互動 — 資料緩衝](../../installation/using/interaction---data-buffer.md).

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
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> callDataSize<br /> </td> 
   <td> Max。 共用記憶體中儲存的呼叫資料字元數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動程式時要執行的JavaScript ID<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：有關給定進程消耗的RAM量（以Mb為單位）的警告。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> Max。 儲存在共用記憶體中的事件數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> 按主張排序的合格優惠方案的最大數量，要儲存以進行統計。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 自動重新啟動程式的當天時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動處理重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 簡短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> 響應時間統計資訊的聚合持續時間（秒）。 0表示已停用統計儲存。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> Max。 儲存在共用儲存器中用於識別個人的字元數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta {#mta}

以下是 **mta** 節點。 這是傳遞代理的設定。

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
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataLogPath<br /> </td> 
   <td> 儲存已傳送電子郵件的路徑：若非空白，則會儲存已傳送電子郵件之所有來源檔案的路徑。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> 轉儲目錄：如果不為空，則複製此目錄中已發送郵件的MIME信封。 用於疑難排解。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> DNS查詢日誌延遲：顯示日誌的時間（毫秒）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> 錯誤統計頻率：在生成統計資訊和儲存資料庫之間的時間。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動程式時要執行的JavaScript ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> 生成錯誤統計資訊並將其儲存在資料庫中。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> 顯示日誌消息的級別。 寫入資料庫中的日誌的嚴重性級別。 MTA產生的記錄訊息不一定都會寫入資料庫中。 使用此參數，您可以定義您認為必須在資料庫中寫入訊息的層級。 如果定義級別2，則也會寫入級別1和級別0的消息，而如果定義級別1，則僅寫入級別1和級別0的消息。 可能的值包括：0（錯誤）、1（警告）、2（資訊）<br /> </td> 
   <td> 長<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> mta進程可使用的最大記憶體大小（以MB為單位）。 超過此限制後，將重新啟動該進程，以釋放它使用的記憶體到系統。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：有關給定進程消耗的RAM量（以Mb為單位）的警告。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> 要考慮的連接閾值。 如果errorPeriodSec指定的期間的連接總數嚴格低於閾值，則不會為給定路徑生成錯誤統計資訊。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> 要考慮的錯誤閾值：如果errorPeriodSec指定的期間的錯誤總數嚴格低於閾值，則不會為給定路徑生成錯誤統計資訊。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> 要考慮的訊息臨界值。 如果為errorPeriodSec指定的期間發送的消息總數嚴格低於閾值，則不會為給定路徑生成錯誤統計資訊。<br /> </td> 
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
   <td> 自動重新啟動程式的當天時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動處理重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> 刪除已封存電子郵件前的延遲：清除dataLogPath中指定目錄中已存檔電子郵件的天數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessages<br /> </td> 
   <td> 重試丟失的消息：如果子進程死亡，將重試部分傳送。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 簡短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> signEmailLinks<br /> </td> 
   <td> 啟用簽名機制。 這可改善電子郵件中追蹤連結的安全性。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> true<br /> </td> 
  </tr>
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> 傳遞統計資訊伺服器的地址，為 
    &lt;dns or="" ip=""&gt; 
      <code>[</code>: 
     &lt;port&gt; 
       <code>]</code>. 請參閱 
      <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">統計伺服器的坐標</a>. 
      <br /> 
     </td> 
   <td> 字串<br /> </td> 
   <td> 如果未定義，預設埠為7777。<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSSupport<br /> </td> 
   <td> 按域啟用TLS:啟用由MX配置的TLS（需要最新的統計伺服器）。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> true <br /> </td> 
  </tr> 
  <tr> 
   <td> statServerVersion<br /> </td> 
   <td> 使用的協定版本：通信協定版本（v5.11和6.0.2伺服器為1,v6.1伺服器為2）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 如果未定義，則使用最新版本。 <br /> </td> 
  </tr> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> 若設為「true」，您的執行個體會使用 <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">增強的MTA</a>.<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> 驗證模式：激活驗證模式(不實際傳輸消息；用於模擬和測試)。<br /> </td> 
   <td> 布林值<br /> </td> 
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
   <td> X-Mailer欄位：SMTP郵件標題中欄位「X-Mailer」的值。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'nlserver，版本$(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### 快取 {#cache}

在 **快取** 節點，請配置以下參數。 這是本機檔案快取配置。

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
   <td> 回收後：句點，以秒為單位表示，之後會自動從快取中刪除檔案，以回收儲存。<br /> </td> 
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
   <td> 清除頻率：快取清除機制執行之間的時段（以秒為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 中繼 {#relay}

在 **mta >中繼** 節點，請配置以下參數。 這是郵件傳送的郵件伺服器配置。

該清單的處理方式與MX DNS查詢返回的MX清單相同，通常只要第一個MX可用，就使用下一個MX，以此類推。

如需詳細資訊，請參閱 [SMTP中繼](../../installation/using/configuring-campaign-server.md#smtp-relay).

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
   <td> 要使用的SMTP中繼的DNS名稱或IP位址清單（以逗號分隔）。 <br /> </td> 
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

### 主版 {#master}

在 **mta > master** 節點，請配置以下參數。 這是主伺服器的配置。

如需詳細資訊，請參閱 [節](../../installation/using/configuring-campaign-server.md#mta-child-processes).

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
   <td> 要傳遞的作業的資料庫輪詢頻率。 此值指示資料庫輪詢頻率（以秒為單位）。 為了取得等待傳送的作業清單，MTA會定期輪詢資料庫。 當沒有等待的作業時，輪詢期間由此值定義。 否則，如果作業已轉移到子伺服器，則此輪詢持續時間會自動縮短為一秒，以便能夠盡快重新處理新作業，即當子伺服器重新可用時。 這並不表示在子伺服器重新可用之前，將每秒執行資料庫查詢。 事實上，只有當至少一個子伺服器可用時，才會執行資料庫存取。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> 資料庫連接失敗後的等待期。 資料庫連接故障通常是由資料庫伺服器本身引起的。 例如，伺服器也可能因維護目的而停止。 DataBaseRetryDelay參數定義了資料庫連接失敗時兩次連接嘗試之間的持續時間。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> 私鑰快取(DomainKeys)的有效期。 在DomainKeys建議(http://antispam.yahoo.com/domainkeys)之後用於簽署電子郵件的私密金鑰會儲存為資料庫中的選項。 domainKeysReloadPeriodSec參數定義MTA可將這些金鑰保留在快取中的秒數。 在此延遲後，必須從資料庫重新載入所有鍵。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> 子伺服器的最大數量。 代表執行中的伺服器數上限。 建議以與伺服器記憶體資源相容的最佳方式限制此數量。 傳送期間可以檢查此項目。 使用的記憶體不應超過可用物理記憶體的三分之一，否則將使用交換。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">MTA子進程</a>.<br /> </td> 
   <td> 長<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> 子伺服器的最小數量。 MTA會嘗試至少讓這些伺服器數保持運作。 如果數量較少，則每秒都會重新啟動新伺服器，直到達到此值為止。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> 啟動時的子伺服器數。 動態監視子伺服器的數量；MTA啟動時，會建立如此值所示的多個子伺服器。 通常，子伺服器的啟動速度不能快於每秒一個伺服器，以便節省主機資源。 但是，當MTA啟動時，此限制會被否決，以便盡快提供子伺服器。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 子項 {#child}

在 **mta >子項** 節點，請配置以下參數。 這是子伺服器的配置。

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
   <td> 可選命令行參數 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> 超時，直到空閒的子伺服器停止。 如果子伺服器的空閒時間大於此參數，則會自動終止它以釋放主機資源。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> 最大郵件保留時間。 如果因為限制而無法傳送已準備的郵件，或無法連線至目標MTA，則會放棄該郵件，並在下次重試時加以處理。<br /> </td> 
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
   <td> 每個子伺服器的最大消息數。 每個MTA子項都會處理此數量的訊息和失效。 請務必指定數字，使MTA中的記憶體或資源洩漏無害（通常幾千個）。 即使MTA程式碼中沒有已知記憶體洩漏，內嵌的JavaScript和XSL引擎也不完全可靠。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> 待定消息：記憶體中等待傳遞的最大消息數。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 2000年<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> 子進程可使用的最大記憶體大小(MB)。 超過此限制後，進程將停止，以釋放它使用的記憶體到系統。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> 逾時（以秒為單位），在此之後會捨棄傳送連接器的SOAP連線。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> startWithFirstMX<br /> </td> 
   <td> 始於最高優先順序的MX。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> 恢復時連續嘗試的最大數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

在 **mta >子項> smtp** 節點，請配置以下參數。 這是SMTP會話的配置。

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
   <td> 當遠端伺服器支援時，啟用以安全模式(STARTTLS/SMTPS)傳送電子郵件。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> 空閒會話超時。 只有在會話被重複用於向給定域發送多個消息時，才會使用此參數。 當MTA完成郵件傳輸時，它所使用的SMTP會話不會被系統關閉。 如果郵件已準備好針對此相同域發送，則將重複使用相同的SMTP會話，因此不會自動關閉會話。 參數IdleSessionTimeout可讓您定義SMTP工作階段在等待其他郵件時可維持作用中的時間。 持續時間結束後，會自動關閉工作階段。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> 重試連接前的初始延遲。 每次連線失敗時，此延遲都會加倍。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> 按子伺服器的SMTP會話數上限。 為了傳送訊息，MTA會初始化與收件者MTA的SMTP連線。 指定子伺服器的併發和活動SMTP會話的最大數量受此值限制。 如果將此值乘以maxSpareServers，則可獲得指定子伺服器可同時處理的最大消息數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

在 **mta > child > smtp > IPAffinity** 節點，請配置以下參數。 這是管理與IP位址相關性的設定，以最佳化傳出SMTP流量。

如需詳細資訊，請參閱 [要使用的IP位址清單](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use) 和 [管理具有相關性的傳出SMTP流量](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities).

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
   <td> 名稱<br /> </td> 
   <td> 邏輯名稱：由使用者連結至相關性的名稱。 名稱使用分號分隔；<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

在 **mta >子項> smtp > IP** 節點，請配置以下參數。

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
   <td> 關聯的物理地址。 例如：'192.168.0.1'<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> 關聯的公用地址ID。 用作統計資訊伺服器的密鑰。 必須為數值。 看這個 <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">節</a>.<br /> </td> 
   <td> 長<br /> </td> 
  </tr> 
  <tr> 
   <td> 權重<br /> </td> 
   <td> 指定此IP的使用頻率，相對於其他IP（權重越大，頻率越高）。<br /> </td> 
   <td> 長<br /> </td> 
  </tr> 
  <tr> 
   <td> includeDomains<br /> </td> 
   <td> 要包含的以逗號分隔的域掩碼清單。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> excludeDomains<br /> </td> 
   <td> 要排除的網域遮罩清單（以逗號分隔）。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> heloHost<br /> </td> 
   <td> 連結到IP地址的電腦名。 發出SMTP HELO命令時使用。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

## nmac {#nmac}

以下是 **nmac** 節點。 這是推播通知傳送的設定。

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
   <td> 使用在shared/proxyHTTP中定義的HTTP代理。 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 中繼 {#relay-1}

以下是 **nmac >中繼** 節點。 這會設定訊息傳送（ios http2連接器）的中繼使用。

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
   <td> 要使用的中繼的DNS地址或名稱。 <br /> </td> 
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
   <td> 憑證鏈（PEM檔案）。 使用模擬伺服器時很實用。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 流水線 {#pipelined}

以下是 **流水線** 節點。 這是Pipeline Services的事件處理模組的設定。

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
   <td> 儲存公開金鑰時，在Developer連線中產生的應用程式名稱。 <br /> </td> 
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
   <td> 取得閘道權杖的URL。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> 取得權杖的私密金鑰（使用XtkKey選項在AES中加密）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> 自動啟動 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> disableAuth<br /> </td> 
   <td> 禁用身份驗證：不進行驗證即可連線至Pipeline Services 。 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> discoverPipelineEndpoint<br /> </td> 
   <td> 用於發現管道服務URL的URL。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> 狀態保存期：將進程內部資訊保存在檔案中的頻率。 非作用中（若為0）。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> 監聽URL:強制管道服務的監聽URL。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動程式時要執行的JavaScript ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：有關給定進程消耗的RAM量（以Mb為單位）的警告。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> 狀態伺服器埠：允許您查詢進程狀態的HTTP伺服器埠。 非作用中（若為0）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 7781<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushMessageCount<br /> </td> 
   <td> 每次處理此數量的郵件時，指針都將儲存在資料庫中。<br /> </td> 
   <td> <br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushPeriodSec<br /> </td> 
   <td> 儲存指針之前的延遲：在此期間，指針將至少儲存在資料庫中一次（在活動低時非常有用）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 自動重新啟動程式的當天時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動處理重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThreads<br /> </td> 
   <td> 使用個人化JavaScript連接器進行事件處理的執行緒數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> processingThreads<br /> </td> 
   <td> 用於事件處理的線程數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> retryPeriodSec<br /> </td> 
   <td> 如果發生故障，則兩次處理之間的延遲。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> 此時段後放棄：如果此時段後處理仍失敗，請放棄事件。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 簡短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 修理 {#repair}

以下是 **修理** 節點。 這是資料庫修復模組的配置。

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
   <td> 傳遞操作修復模組：延遲（以分鐘為單位），之後修復模組可處理傳送動作。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

以下是 **securityZone** 節點。

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
   <td> 授權Web應用程式的調試模式。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> 授權使用者不使用密碼使用應用程式。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowHTTP<br /> </td> 
   <td> 授權將HTTP用於操作員登錄。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInjents<br /> </td> 
   <td> 授權在表達式中使用SQLDATA。<br /> </td> 
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
   <td> 請勿使用安全性代號。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> showErrors<br /> </td> 
   <td> 顯示錯誤詳細資訊<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

預設設定如下：

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

以下是 **securityZone > subNetwork** 節點。

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
   <td> 遮罩<br /> </td> 
   <td> 掩碼或地址<br /> </td> 
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
   <td> 代理<br /> </td> 
   <td> 此子網路用於訪問實例的掩碼或反向代理的地址。 在此情況下，將測試「X-Forwarded-For」標頭，而非此Proxy。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## sms {#sms}

以下是 **sms** 節點。 這是傳入SMS管理模組的設定。

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
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataRetentionDays<br /> </td> 
   <td> SMPP連接器保留的工作檔案的最大天數。<br /> </td> 
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
   <td> 啟動程式時要執行的JavaScript ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> 會話連續性幀的重複：max。 兩個幀之間的句點（以秒為單位），用於通知接收會話仍處於啟用狀態。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：有關給定進程消耗的RAM量（以Mb為單位）的警告。<br /> </td> 
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
   <td> 自動重新啟動程式的當天時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動處理重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod<br /> </td> 
   <td> 帳戶重新載入頻率：要輪詢的帳戶的資料庫重新載入頻率。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 簡短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> 延遲SR處理的秒數：只有恢復日期早於當前時間的SR減去srReadDelay提供的持續時間（以秒為單位）。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> 逾時<br /> </td> 
   <td> 與SMS閘道的通訊逾時。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

以下是 **sms > netsize** 節點。

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
   <td> 使用Netsize建立連線時的逾時（秒）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## stat {#stat}

以下是 **stat** 節點。 這是MTA統計模組的設定。

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
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動程式時要執行的JavaScript ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：有關給定進程消耗的RAM量（以Mb為單位）的警告。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> 埠<br /> </td> 
   <td> 伺服器偵聽埠。 看這個 <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">節</a>.<br /> </td> 
   <td> 簡短<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 自動重新啟動程式的當天時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動處理重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 簡短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslogd {#syslogd}

以下是 **syslogd** 節點。 這是日誌管理模組的配置。

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
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動程式時要執行的JavaScript ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> 日誌檔案的最大大小(MB)。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> 要保留的最大登入數.log檔案數。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：有關給定進程消耗的RAM量（以Mb為單位）的警告。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 自動重新啟動程式的當天時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動處理重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 簡短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 追蹤 {#tracking}

以下是 **追蹤** 節點。 這是追蹤伺服器的設定。

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
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> blockRedirectForUnsignedTrackingLink<br /> </td> 
   <td> 停用從舊版組建產生的格式錯誤的URL。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> consolidationPeriodSec<br /> </td> 
   <td> 合併期<br /> </td> 
   <td> 長<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> 刪除重複的開口：移除重複的開啟追蹤記錄，以限制Outlook等郵件閱讀器中郵件預覽的效果。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> 忽略最多X%的錯誤：只要尚未考慮的日記帳比率未達到此值，請不要更新跟蹤指標。 <br /> </td> 
   <td> 位元組<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> 更新錯誤指示器：重新計算錯誤指標前的最大持續時間。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> indicatorsDuration<br /> </td> 
   <td> 計算指標：傳送有效日期之後的持續時間，此時將不再計算合併指標。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動程式時要執行的JavaScript ID <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> 呼叫遠端追蹤伺服器請求的記錄數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：有關給定進程消耗的RAM量（以Mb為單位）的警告。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceAPIKey<br /> </td> 
   <td> Phishbowl服務端點整合的API金鑰。 這可保護從舊版組建產生的格式錯誤URL的重新導向。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Phishbowl服務端點整合的端點。 這可保護從舊版組建產生的格式錯誤URL的重新導向。<br /> </td> 
   <td> 長<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 自動重新啟動程式的當天時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動處理重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 簡短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> 忽略最多X%的追蹤：只要尚未考慮的日記帳比率未達到此值，請不要更新跟蹤指標。<br /> </td> 
   <td> 位元組<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> 更新追蹤指標：會重新計算追蹤指標前的最大持續時間。<br /> </td> 
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

以下是 **trackinglogd** 節點。 這是跟蹤日誌寫入守護程式的配置。

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
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動程式時要執行的JavaScript ID <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> 最大寫入重試次數：在日誌檔案中寫入失敗時可建立的檔案數上限。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> 最大日誌大小：磁碟上日誌使用的最大空間(MB)。 不得小於100 MB。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：有關給定進程消耗的RAM量（以Mb為單位）的警告。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> 最大日誌計數：儲存在共用記憶體中的日誌數上限。 不能小於10000。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 自動重新啟動程式的當天時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動處理重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> 清除前的日誌數：開始清除日誌檔案之前插入的日誌數。 不得低於50000。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 簡短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> 共用記憶體中儲存的字元數上限，以供額外的Web追蹤參數使用。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## web {#web}

以下是 **web** 節點。 這是Web模組的配置。

如需詳細資訊，請參閱 [節](configuring-campaign-server.md#default-port-for-tomcat).

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
   <td> 以字串形式傳遞的JVM的選項。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 最大線程數<br /> </td> 
   <td> 最大線程數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> MinSpareThreads<br /> </td> 
   <td> 最小線程數。<br /> </td> 
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
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> controlPort<br /> </td> 
   <td> Tomcat偵聽控制埠：請參閱 <a href="configure-tomcat.md" target="_blank">配置Tomcat</a>.<br /> </td> 
   <td> 簡短<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Tomcat HTTP偵聽埠：請參閱 <a href="configure-tomcat.md" target="_blank">配置Tomcat</a>.<br /> </td> 
   <td> 簡短<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動程式時要執行的JavaScript ID。<br /> </td> 
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
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：有關給定進程消耗的RAM量（以Mb為單位）的警告<br /> </td> 
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
   <td> 自動重新啟動程式的當天時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動處理重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 簡短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> startSoapRouterInModule<br /> </td> 
   <td> 以模組模式啟動SOAP路由器。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### jsp {#jsp}

以下是 **web > jsp** 節點。 這是JSP所使用參數的配置。

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
   <td> 是否在調試模式下執行JSP。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> downloadPath<br /> </td> 
   <td> 下載資料夾：用於客戶端控制台的安裝程式的下載路徑。<br /> </td> 
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

此 **web > jsp >類路徑** 節點包含啟動JVM時要使用的所有類路徑的清單。 預設設定如下：

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

以下是 **web > jssp** 節點。 這是JSSP所使用參數的配置。

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
   <td> 在每次查詢後啟用JavaScript上下文的垃圾回收器。<br /> </td> 
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

此 **web > jsp >類路徑** 節點包含啟動JVM時要使用的所有類路徑的清單。

### 中繼 {#relay-2}

以下是 **web >中繼** 節點。 這是兩個區域之間HTTP請求的中繼設定。

如需詳細資訊，請參閱 [節](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> 在調試模式下啟動Web伺服器內的HTTP中繼模組。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInAuthority<br /> </td> 
   <td> 禁止字元（域）:URI的「授權」部分中禁止字元的清單。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '?#@/:' <br /> </td> 
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
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> 在Web伺服器內啟動HTTP中繼模組。 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> 逾時<br /> </td> 
   <td> 刪除禁止的url之前等待時間。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』60年<br /> </td> 
  </tr> 
 </tbody> 
</table>

新增 **web >中繼> url** 每個要中繼的URL的節點（插入順序定義優先順序），其參數如下。

如需詳細資訊，請參閱 [動態頁面安全性和中繼](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) 和 [節](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> 授權IP:允許對此掩碼使用中繼的源IP地址清單（以逗號分隔）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 拒絕<br /> </td> 
   <td> 拒絕存取這些URL（傳回HTTP 403錯誤）<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> 要中繼的DNS別名：要中繼的DNS別名掩碼清單(例如：「*.adobe.com」)。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllowed<br /> </td> 
   <td> 無論安全區域（如webApps）為何，HTTP存取都經過授權。 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayHost<br /> </td> 
   <td> 添加原始主機：中繼時，請使用原始請求的HTTP「Host」標題。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayPath<br /> </td> 
   <td> 新增初始URL路徑：附加URL的完整路徑，以中繼至目標頁面的URL。 <br /> </td> 
   <td> 布林值<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 狀態<br /> </td> 
   <td> 公用資源的同步狀態（枚舉）。 可能的值為「normal」（正常執行）、「blacklist」（在發生錯誤404時添加到禁止清單的url）和「spare」（如果存在，則檔案上載到備用伺服器）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 正常<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> 目標頁面的URL:請參閱 <a href="configure-tomcat.md" target="_blank">配置Tomcat</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 逾時<br /> </td> 
   <td> 中繼請求的最大執行時間（以秒為單位）。<br /> </td> 
   <td> 長<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> urlPath<br /> </td> 
   <td> 中繼URL的遮罩(例如：「/nl*」、「*.jsp」)。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

預設設定如下：

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

新增 **web > relay > responseHeader** 節點，用於添加轉發到中繼的回復。

如需詳細資訊，請參閱 [管理HTTP標題](../../installation/using/configuring-campaign-server.md#managing-http-headers).

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
   <td> 標題名稱<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> value<br /> </td> 
   <td> 標題值 <br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

預設設定如下：

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### 重定向 {#redirection}

以下是 **Web >重定向** 節點。 這是重定向模組的配置。

如需詳細資訊，請參閱 [節](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> Identity Management系統(IMS)組織識別碼：Adobe Experience Cloud內的唯一組織識別碼，尤其用於VisitorID服務和IMS SSO。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> 說明用於永久Cookie的原則的值（符合P3P緊密政策格式）。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'CAO DSP COR CURa DEVaTAIa我們的巴士IND UNI COM導航'<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> 要設定的網域清單（以逗號分隔）明確指出要設定Cookie的網域。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> 與追蹤例項相關聯的資料庫識別碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> 按呼叫記錄計數：呼叫方法GetTrackingLogs時，預設傳回的記錄數。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationURL<br /> </td> 
   <td> 過期重新指示的頁面：當傳送動作的重新導向已過期時，重新導向伺服器預設會使用的網頁URL。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> 最大作業數：快取中的傳送動作數上限。 不得低於50。 <br /> </td> 
   <td> 長<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirection<br /> </td> 
   <td> 啟動重定向服務。<br /> </td> 
   <td> 布林值<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectionInModule<br /> </td> 
   <td> 以模組模式啟動重定向服務。<br /> </td> 
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
   <td> 重定向伺服器使用的密碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是 **web >重定向> spareServer** 節點。

如需詳細資訊，請參閱 [冗餘跟蹤](../../installation/using/configuring-campaign-server.md#redundant-tracking).

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
   <td> 若：如果運算式傳回true，則會考量追蹤伺服器。 <br /> </td> 
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
   <td> 額外重定向伺服器URL<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

### spamCheck {#spamcheck}

以下是 **web > spamCheck** 節點。 這是電子郵件反垃圾郵件計分評估參數的配置。

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
   <td> 執行以評估電子郵件的反垃圾郵件分數的命令(例如'perl spamcheck.pl')。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

以下是 **wfserver** 節點。 這是工作流程程式設定。

如需詳細資訊，請參閱 [高可用性工作流程和相關性](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

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
   <td> 布林值<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> 時段<br /> </td> 
   <td> 長<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動程式時要執行的JavaScript ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM量（以Mb為單位）的警報。<br /> </td> 
   <td> 長<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：有關給定進程消耗的RAM量（以Mb為單位）的警告。<br /> </td> 
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
   <td> 自動重新啟動程式的當天時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動處理重新啟動</a>.<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 』06年:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組會先啟動後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 簡短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>
