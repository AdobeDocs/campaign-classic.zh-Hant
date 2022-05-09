---
product: campaign
title: 伺服器設定檔
description: 伺服器設定檔
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 70cd6a4b-c839-4bd9-b9a7-5a12e59c0cbf
source-git-commit: 02eebe83de49ee97e573b0c47ca1fddb2195b991
workflow-type: tm+mt
source-wordcount: '7957'
ht-degree: 5%

---

# 伺服器設定檔{#the-server-configuration-file}

![](../../assets/v7-only.svg)

Adobe Campaign的總體配置在 **serverConf.xml** 檔案，位於 **會議** 目錄。 本節列出了所有不同的節點和 **serverConf.xml** 的子菜單。

>[!NOTE]
>
>伺服器端配置只能通過Adobe執行由Adobe承載的部署。 要瞭解有關不同部署的詳細資訊，請參閱 [托管模型](../../installation/using/hosting-models.md) 或 [此頁](../../installation/using/capability-matrix.md)。 本節介紹了托管和混合型號的安裝和配置步驟 [節](../../installation/using/hosting-models.md)。

第一個參數位於 **共用** 的下界。 這些與實例相關。 它們可能被所有nlserver命令（nlserver web 、 nlserver wfserver等）使用。 其他部分與特定的nlserver子命令相關。

**共用參數**

* [認證](#authentication)
* [資料儲存](#datastore)
* [dns配置](#dnsconfig)
* [執行](#exec)
* [htmlToPdf](#htmltopdf)
* [IMS](#ims)
* [javaScript](#javascript)
* [郵件交換器](#mailexchanger)
* [模組](#module)
* [監控](#monitoring)
* [烏孔](#ooconv)
* [代理配置](#proxyconfig)
* [線程池](#threadpool)
* [url權限](#urlpermission)
* [xtk作業](#xtkjobs)

**其他參數**

* [歸檔](#archiving)
* [郵件](#inmail)
* [交互](#interactiond)
* [門](#mta)
* [NMAC](#nmac)
* [流水線](#pipelined)
* [修復](#repair)
* [安全區域](#securityzone)
* [簡訊](#sms)
* [統計](#stat)
* [syslog](#syslogd)
* [跟蹤](#tracking)
* [跟蹤日誌](#trackinglogd)
* [網](#web)
* [wf伺服器](#wfserver)

## 認證 {#authentication}

以下是 **認證** 節點：

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
   <td> 檢查IPConsistent<br /> </td> 
   <td> 啟用IP地址檢查。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> 預設模式<br /> </td> 
   <td> 預設標識模式。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 「nl」<br /> </td> 
  </tr> 
  <tr> 
   <td> longSessionTimeOutSec<br /> </td> 
   <td> 長會話超時（秒）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> 安全超時秒<br /> </td> 
   <td> 安全令牌超時（秒）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> 會話快取秒<br /> </td> 
   <td> 快取持續時間：會話資訊的快取（秒）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> 會話超時秒<br /> </td> 
   <td> 會話超時（秒）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

以下是 **驗證> XTK** 節點：

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
   <td> 內部密碼<br /> </td> 
   <td> 內部帳戶的密碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 內部安全區域<br /> </td> 
   <td> 內部帳戶安全區域：內部帳戶的授權區域。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'lan'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 資料儲存 {#datastore}

以下是 **資料儲存** 的下界。 這是定義伺服器資料源的位置。

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
   <td> 導出目錄<br /> </td> 
   <td> 導出目錄：導出資料的目標目錄的路徑。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 「$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/export/」 <br /> </td> 
  </tr> 
  <tr> 
   <td> extraSandboxed目錄<br /> </td> 
   <td> 額外沙盒目錄：要添加到沙箱中的其他路徑（彗差分離）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 「/home/customers/,/sftp/」 <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> 表單快取過期延遲：超時（以秒為單位），在此之後快取項無效。 O表示只在發佈時刷新快取項。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> 主機<br /> </td> 
   <td> DNS掩碼：此實例所服務的DNS掩碼清單(逗號分隔，可以使用*和？ 模式)。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 「*」<br /> </td> 
  </tr> 
  <tr> 
   <td> 交互CacheTimeToLive<br /> </td> 
   <td> 交互JSSP快取過期延遲：超時（以秒為單位），在此之後快取項無效。 負值表示快取始終無效。 「0」、空值或無效值被視為60。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> 朗<br /> </td> 
   <td> 實例語言（枚舉）。 可能的值為「fr_FR」(Français)、「en_GB」(英語（英國）)、「en_US」(英語（美國）)、「de_DE」(Deutsch)和「ja_JP」（日語）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'en_US'<br /> </td> 
  </tr> 
  <tr> 
   <td> 上載目錄<br /> </td> 
   <td> 上載資料夾：上載資料的目標目錄的路徑。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 「$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/」 <br /> </td> 
  </tr> 
  <tr> 
   <td> 上載允許清單<br /> </td> 
   <td> 要下載的授權檔案以「，」分隔。 該字串必須是有效的正則java表達式。 請參閱 <a href="file-res-management.md" target="_blank">限制可上載檔案</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 「。+」 <br /> </td> 
  </tr> 
  <tr> 
   <td> 使用保管庫<br /> </td> 
   <td> 將機密儲存在保管庫中：用Hashicorp Vault。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> 保管庫密鑰路徑<br /> </td> 
   <td> 保管庫中的秘密路徑<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 「/v1/secret/campign/」<br /> </td> 
  </tr> 
  <tr> 
   <td> 保管庫令牌路徑<br /> </td> 
   <td> 包含保管庫令牌的檔案的本地路徑。 $(HOME)可以用於此路徑（但不能用於其他環境變數）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 「$(HOME)/.vaulttoken」<br /> </td> 
  </tr> 
  <tr> 
   <td> 保管庫URL<br /> </td> 
   <td> Hashicorp保管庫URL <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> 視圖快取的有效期：超時（以秒為單位），在此之後快取項無效。 負值表示快取始終無效。 「0」、空值或無效值被視為60。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> 工作目錄<br /> </td> 
   <td> 工作目錄的XPath。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 工作目錄：工作目錄的XPath。 預設值：「$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/」<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 代理調整 {#proxyadjust}

以下是 **資料儲存>代理調整** 的下界。 根據urlBase中定義的URL重新生成與規則運算式匹配的URL。

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
   <td> url基<br /> </td> 
   <td> 生成外部URL時使用的基本。 例如：https://server.domain.com<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> 匹配URL的規則運算式。 例如：http://server\.lan\.net。*<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 資料源 {#datasource}

以下是 **資料儲存>資料源** 的下界。

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
   <td> 資料源名稱<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 預設<br /> </td> 
  </tr> 
 </tbody> 
</table>

在 **資料儲存>資料源> dbcnx** 節點，配置連接設定：

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
   <td> 布爾型<br /> </td> 
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
   <td> 布爾型<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 登錄<br /> </td> 
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
   <td> 提供程式<br /> </td> 
   <td> 類型（枚舉）。 可能的值為「Oracle」、「MSSQL」(MicrosoftSQL Server)、「PostgreSQL」(PostgreSQL)、「Teradata」、「DB2」、「MySQL」、「Netezza」、「AsterData」、「SAPHANA」(SAP HANA)、「RedShift」(Amazon Redshift)、ODBC」(ODBC(Sybase ASE,Sybase IQ))、「中繼」（HTTP中繼到遠程資料庫）。<br /> </td> 
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
   <td> 時區：見 <a href="../../installation/using/time-zone-management.md" target="_blank">時區管理</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> unicode資料<br /> </td> 
   <td> 資料庫中的Unicode資料<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> useTimestampTZ<br /> </td> 
   <td> 帶時區的日期欄位：見 <a href="../../installation/using/time-zone-management.md" target="_blank">時區管理</a>。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

在 **資料儲存>資料源> sqlParams** 節點，配置SQL參數：

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

在 **資料儲存>資料源>池** 節點，配置關聯連接池的參數：

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
   <td> 免費Cnx<br /> </td> 
   <td> 池中保留的可用連接數。<br /> </td> 
   <td> 短<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> 拒絕新連接前允許的連接的最大數量。 查看 <a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">技術</a>。<br /> </td> 
   <td> 短<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> 連接的最大空閒時間。 0表示預設值。<br /> </td> 
   <td> 短<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 虛擬目錄 {#virtualdir}

以下是 **資料儲存> virtualDir** 的下界。 這是虛擬目錄到實際目錄映射的配置。

有關其他資訊，請參閱 [管理公共資源](file-res-management.md)。

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

以下是預設配置：

```
<virtualDir name="images" path="$(XTK_INSTALL_DIR)/var/res/img/"/>
<virtualDir name="formCache" path="$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/formCache/"/>
<virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)"/>
```

### preprocessCommand {#preprocesscommand}

以下是 **dataStore > precossCommand** 的下界。 這些是用於預處理「載入檔案」工作流活動的授權命令。

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
   <td> 命令行 <br /> </td> 
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

以下是預設配置：

```
<preprocessCommand command="" label="None" name="none"/>
<preprocessCommand command="zcat &quot;$fileName&quot;" label="Decompression" name="zcat"/><preprocessCommand command="gpg --decrypt &quot;$fileName&quot;" label="Decrypt" name="gpg"/>
```

## dns配置 {#dnsconfig}

以下是 **dns配置** （DNS配置）節點。

有關其他資訊，請參閱 [節](../../installation/using/configuring-campaign-server.md)。

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
   <td> 本地域<br /> </td> 
   <td> 域名：預設域名。 由SMTP HELO命令使用。 預設情況下，使用在Windows中聲明的第一個網路介面的網路參數；或在Linux（域或搜索條目）下解析file/etc/resolv.conf。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 名稱伺服器<br /> </td> 
   <td> DNS伺服器：以逗號分隔的域名伺服器(DNS)清單。 請參閱下面的注釋。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 重試<br /> </td> 
   <td> DNS查詢的重試次數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> 逾時<br /> </td> 
   <td> DNS查詢超時（毫秒）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>注釋 **名稱伺服器**:預設情況下，使用網路
>在Windows中聲明的第一個網路介面的參數
>未在UNIX中定義。 定義域名伺服器(DNS)
>MTA用於獲取已聲明為的郵件交換器
>域。
>
>如果未定義此值，MTA將在主機網路配置中查找此資訊。 如果可以使用多個DNS，則不同的DNS地址必須用逗號分隔(例如：212.155.207.1,212.155.207.2)。 如果您的傳遞伺服器具有多個網路介面，則MTA使用的DNS清單是第一個。 在這種情況下，建議指定 **名稱伺服器** 來避免任何模糊。

>[!CAUTION]
>
>如果網路主機配置使用DHCP，則MTA將找不到DHCP提供的DNS清單。 在這種情況下，建議在Windows控制面板的網路參數中指定DNS清單。

## 執行 {#exec}

以下是 **執行** （命令執行）節點。

有關其他資訊，請參閱 [限制授權的外部命令](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)。

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
   <td> 黑名單檔案<br /> </td> 
   <td> 包含要添加到允許清單的命令的檔案的路徑。 <br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 用戶<br /> </td> 
   <td> 以其他用戶身份執行命令。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

以下是 **htmlToPdf** 的下界。 這是將網頁轉換為PDF文檔的服務的配置。

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
   <td> 麥克斯。 在一台電腦上一次允許的轉換進程數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> 模式<br /> </td> 
   <td> 用於轉換的工具。 可能的值為：phantomjs、wkhtmltopdf，其他，已禁用<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 「phantomjs」 <br /> </td> 
  </tr> 
  <tr> 
   <td> 逾時<br /> </td> 
   <td> 轉換超時：最大轉換時間（秒）。 超過此閾值後，轉換進程將停止，並引發錯誤。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> 詳細<br /> </td> 
   <td> 詳細模式：以詳細模式啟動以診斷可能的錯誤。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> 等待時間<br /> </td> 
   <td> 等待進程時延遲：延遲（秒），即同時使用所有進程和等待進程釋放時。 如果超過此延遲，則停止轉換並引發錯誤。 <br /> </td> 
   <td> 龍<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

phantomjs示例：

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## IMS {#ims}

以下是 **IMS** 的下界。 這是市場活動連接到另一個服務的配置，使用 [IMS](../../integrations/using/about-adobe-id.md)。

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
   <td> 客戶端ID<br /> </td> 
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
   <td> https://ims-na1.adobelogin.com'<br /> </td> 
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
   <td> 技術帳戶私鑰（在AES中加密）<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## JavaScript {#javascript}

以下是 **javaScript** 的下界。 這是JavaScript解釋器的配置。

有關其他資訊，請參閱 [報告文檔](../../reporting/using/actions-on-reports.md#memory-allocation)。

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
   <td> 最大MB<br /> </td> 
   <td> 運行垃圾回收器前的最大大小(MB)。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> 堆棧大小KB<br /> </td> 
   <td> 每個堆棧塊的大小（千位八位位元組）。 這是大多數用戶不應調整的記憶體管理調整參數。 <br /> </td> 
   <td> 龍<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 郵件交換器 {#mailexchanger}

以下是 **郵件交換器** 的下界。 這是SMTP伺服器的配置。

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
   <td> mx地址<br /> </td> 
   <td> SMTP伺服器：用於傳輸電子郵件的SMTP伺服器的IP地址。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> mx埠<br /> </td> 
   <td> 用於電子郵件傳輸的SMTP伺服器的TCP埠。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 模組 {#module}

以下是 **模組** 的下界。 這是命名空間限制模組xtk的配置。

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
   <td> 建立新實體時使用的預設命名空間。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 「cus」<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 監控 {#monitoring}

以下是 **監控** 的下界。 這是監視服務配置。

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
   <td> 最大準備時間：持續時間（秒），在此之後，交付操作不應再在準備中。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
  <tr> 
   <td> unix指令碼<br /> </td> 
   <td> 監視服務運行的Unix指令碼。<br /> </td> 
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

## 烏孔 {#ooconv}

以下是 **烏孔** 的下界。 這是文檔轉換伺服器的配置。

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
   <td> 最大轉換<br /> </td> 
   <td> 允許OpenOffice伺服器執行的最大轉換數。 除此數目外，伺服器將重新啟動。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> 強制關閉前OpenOffice伺服器的最大空閒時間。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 7200<br /> </td> 
  </tr> 
  <tr> 
   <td> 埠範圍<br /> </td> 
   <td> OpenOffice伺服器偵聽的埠間隔。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 8101-8110<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> 文檔轉換伺服器的URL。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 代理配置 {#proxyconfig}

以下是 **代理配置** 的下界。 這是代理參數的配置。

有關其他資訊，請參閱 [代理連接配置](file-res-management.md)。

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
   <td> 啟用<br /> </td> 
   <td> 使用代理伺服器。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> 覆蓋<br /> </td> 
   <td> 例外：應忽略代理參數的地址清單。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'localhost* <br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> 唯一代理伺服器：對所有類型的代理使用相同的配置。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
 </tbody> 
</table>

### HTTP代理/安全代理 {#http-proxy---secure-proxy-}

在 **proxyConfig > HTTP Proxy / Secure代理** 節點，配置以下參數。

有關其他資訊，請參閱 [代理連接配置](file-res-management.md)。

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
   <td> 代理伺服器地址<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 登錄<br /> </td> 
   <td> 登錄以連接代理伺服器<br /> </td> 
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
   <td> 短<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 線程池 {#threadpool}

以下是 **線程池** 的下界。

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
   <td> 龍<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## url權限 {#urlpermission}

以下是 **url權限** 的下界。 這是Javascript代碼可以訪問的URL清單。

域和規則運算式清單，指定Javascript代碼中遇到的URL是否可供Adobe Campaign伺服器使用。

如果找不到URL，則根據指定的預設模式執行預設操作。

有關其他資訊，請參閱 [傳出連接保護](../../installation/using/configuring-campaign-server.md#url-permissions)。

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
   <td> 如果URL不在授權清單（枚舉）中，則執行預設操作。 可能的值為「ignore」（授權時無警告消息，這要求禁用保護）、「warn」（授權並發出警告消息）和「deny」（禁止訪問URL）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 拒絕<br /> </td> 
  </tr> 
  <tr> 
   <td> 調試跟蹤<br /> </td> 
   <td> 調試URL選擇機制的跟蹤：在URL驗證過程中發出其他消息。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
 </tbody> 
</table>

### url {#url}

對於每個URL，添加 **url** 節點，其參數如下：

有關其他資訊，請參閱 [傳出連接保護](../../installation/using/configuring-campaign-server.md#url-permissions)。

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
   <td> dns尾碼<br /> </td> 
   <td> 域名或域父級，與URL相關：要驗證的所有或部分URL域，以加速驗證。 僅當URL的域包含dsnSuffix時，才對規則運算式進行驗證。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> 用於細化屬於此域的驗證URL的規則運算式：如果URL與dnsSuffix對應，則URL必須驗證的規則運算式。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

如果記錄滿足 **dns尾碼** 但 **urlRegEx**，檢查以下記錄。

例如，要授權訪問domain business.com的所有URL，可以定義兩條記錄：

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;http://。&#42;&quot;

和 

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;https://。&#42;&quot;

以下是預設配置：

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

## xtk作業 {#xtkjobs}

以下是 **xtk作業** 的下界。 這是伺服器作業的配置。

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
   <td> 龍<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 歸檔 {#archiving}

以下是 **歸檔** 的下界。 這是後台執行的存檔操作的配置。

有關其他資訊，請參閱 [激活電子郵件存檔（內部）](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-)。

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
   <td> acquireLimit（獲取限制）<br /> </td> 
   <td> 要同時處理的EML數<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> 存檔類型<br /> </td> 
   <td> 已發送消息的存檔策略（枚舉）。 可能的值為「0」（無存檔）和「1」（將已發送郵件的存檔傳輸到SMTP伺服器）。<br /> </td> 
   <td> 位元組<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> 角<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 自動啟動<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> compressBatchSize<br /> </td> 
   <td> 壓縮存檔的大小：壓縮存檔中的最大檔案數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> 壓縮格式<br /> </td> 
   <td> 存檔（枚舉）期間使用的壓縮格式。 可能的值為「0」（無壓縮）和「1」（使用zip格式壓縮發送的消息）。<br /> </td> 
   <td> 位元組<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> 過期延遲<br /> </td> 
   <td> 自動存檔未處理電子郵件之前的延遲：未處理電子郵件存檔前的天數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript的ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM（以Mb為單位）的警報。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：警告：給定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> 輪詢延遲<br /> </td> 
   <td> 每個更新事件之間的延遲（秒）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> 刪除未處理電子郵件前的天數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> 運行級別<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> smtp密件抄送地址<br /> </td> 
   <td> 存檔目標目標<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtp啟用TLS<br /> </td> 
   <td> 激活SMTPS支援：在遠程伺服器支援時，以安全模式(STARTTLS/SMTPS)激活電子郵件傳送。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> 到存檔SMTP伺服器的連接數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> smtp中繼地址<br /> </td> 
   <td> 要使用的SMTP中繼的DNS名稱或IP地址的逗號分隔清單。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtp中繼埠<br /> </td> 
   <td> SMTP伺服器的IP埠。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 郵件 {#inmail}

以下是 **郵件** 的下界。 這是入站電子郵件管理模組的配置。

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
   <td> 角<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 自動啟動<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> checkInstanceName<br /> </td> 
   <td> 驗證實例名稱：如果為true，則Message-ID標頭中包含的Adobe Campaign實例的名稱必須與當前實例相同。 <br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 真<br /> </td> 
  </tr> 
  <tr> 
   <td> 預設轉發地址<br /> </td> 
   <td> 轉發地址：規則未處理預設電子郵件傳送地址。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> 錯誤轉發地址<br /> </td> 
   <td> 錯誤地址：用於傳輸無效電子郵件的預設地址（錯誤的MIME編碼）。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 忽略大小<br /> </td> 
   <td> 忽略消息大小：用於忽略POP3伺服器返回的消息的大小。 在這種情況下，模組需要「。」 在留言結尾處。 <br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> 消息讀取期間：消息隊列輪詢頻率。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript的ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> 要更新的最大日誌數：定義更新資料庫前要保留在記憶體中的日誌消息的最大數量。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> 在POP3會話期間要讀取的最大消息數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM（以Mb為單位）的警報。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：警告：給定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> 會話持續時間：消息處理會話的最大持續時間。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> POP3輪詢週期<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> 讀取消息的隊列大小<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> 與POP3伺服器的通信超時。 <br /> </td> 
   <td> 龍<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriodSec<br /> </td> 
   <td> 要輪詢的帳戶的資料庫重裝頻率。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> 運行級別<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msg轉儲 {#msgdump}

在 **inMail > msgDump** 節點，配置以下參數。 這是已處理消息的轉儲配置。

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
   <td> 以文本格式保存所有入站消息。 <br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> msg路徑<br /> </td> 
   <td> 消息轉儲路徑。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 「/tmp/inMail」<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 交互 {#interactiond}

以下是 **交互** 的下界。 這是入站交互事件的寫入守護程式的配置。

有關其他資訊，請參閱 [交互 — 資料緩衝區](../../installation/using/interaction---data-buffer.md)。

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
   <td> 角<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 自動啟動<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> 調用資料大小<br /> </td> 
   <td> 麥克斯。 共用記憶體中儲存的呼叫資料字元數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript的ID<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM（以Mb為單位）的警報。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：警告：給定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> 麥克斯。 儲存在共用記憶體中的事件數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> 下一優惠大小<br /> </td> 
   <td> 在建議後排序的合格優惠的最大數量，要儲存以進行統計。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> 運行級別<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> 響應時間統計資訊的聚合持續時間（秒）。 0表示已停用統計儲存。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> 目標密鑰大小<br /> </td> 
   <td> 麥克斯。 儲存在共用儲存器中用於識別個人的字元數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 門 {#mta}

以下是 **門** 的下界。 這是傳遞代理的配置。

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
   <td> 角<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '-tracefilter:nlmta <br /> </td> 
  </tr> 
  <tr> 
   <td> 自動啟動<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> 資料日誌路徑<br /> </td> 
   <td> 保存已發送電子郵件的路徑：如果不為空，則保存已發送電子郵件的所有源檔案的路徑。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debug路徑<br /> </td> 
   <td> 轉儲目錄：如果不為空，請複製此目錄中已發送郵件的MIME信封。 用於故障診斷。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> DNS查詢日誌延遲：顯示日誌的時間（毫秒）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 錯誤PeriodSec<br /> </td> 
   <td> 錯誤統計頻率：統計資訊生成和資料庫中儲存之間的時間。 <br /> </td> 
   <td> 龍<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript的ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> 生成錯誤統計資訊並將其儲存在資料庫中。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 真<br /> </td> 
  </tr> 
  <tr> 
   <td> 日誌級別<br /> </td> 
   <td> 顯示日誌消息的級別。 寫入資料庫的日誌的嚴重性級別。 MTA生成的日誌消息並非總是寫入資料庫中。 使用此參數，可以定義您認為必須在資料庫中寫入消息的級別。 如果定義級別2，則還會寫入級別1和級別0的消息，而如果定義級別1，則只寫入級別1和級別0的消息。 可能的值為：0（錯誤）、1（警告）、2（資訊）<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> 最大記憶體Mb<br /> </td> 
   <td> mta進程可以使用的最大記憶體大小(MB)。 超過此限制後，將重新啟動進程，以便將其使用的記憶體釋放到系統。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM（以Mb為單位）的警報。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：警告：給定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> 要考慮的連接閾值。 如果errorPeriodSec指定的期間的連接總數嚴格低於閾值，則不會為給定路徑生成錯誤統計資訊。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> 要考慮的錯誤閾值：如果errorPeriodSec指定的期間的錯誤總數嚴格低於閾值，則不會為給定路徑生成錯誤統計資訊。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> 要考慮的消息閾值。 如果為errorPeriodSec指定的期間發送的消息總數嚴格低於閾值，則不為給定路徑生成錯誤統計資訊。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> notif中繼<br /> </td> 
   <td> 通知中繼：HostName：用於中繼通知的埠。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> 刪除存檔電子郵件之前的延遲：清除dataLogPath中指定的目錄中存檔電子郵件的天數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> 重試丟失消息<br /> </td> 
   <td> 重試丟失的消息：如果子進程已死，將重試部分交貨。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 真<br /> </td> 
  </tr> 
  <tr> 
   <td> 運行級別<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> 簽名電子郵件連結<br /> </td> 
   <td> 啟用簽名機制。 這提高了跟蹤電子郵件連結的安全性。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 真<br /> </td> 
  </tr>
  <tr> 
   <td> statServer地址<br /> </td> 
   <td> 傳遞統計伺服器的地址，給定為 
    &lt;dns or="" ip=""&gt; 
      <code>[</code>: 
     &lt;port&gt; 
       <code>]</code>。 請參閱 
      <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">統計伺服器的坐標</a>。 
      <br /> 
     </td> 
   <td> 字串<br /> </td> 
   <td> 如果未定義，預設埠為7777。<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSSupport<br /> </td> 
   <td> 按域啟用TLS:啟用MX可配置的TLS（需要最新的統計伺服器）。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 真 <br /> </td> 
  </tr> 
  <tr> 
   <td> statServer版本<br /> </td> 
   <td> 使用的協定版本：通信協定版本(v5.11和6.0.2伺服器為1,v6.1伺服器為2)。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 如果未定義，則使用最新版本。 <br /> </td> 
  </tr> 
  <tr> 
   <td> 使用動量<br /> </td> 
   <td> 如果設定為"true"，則實例使用 <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">增強的MTA</a>。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> 驗證模式<br /> </td> 
   <td> 驗證模式：激活驗證模式(不實際傳輸消息；用於模擬和test)。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> 工作路徑<br /> </td> 
   <td> 工作目錄：MTA用於與其子進程通信的臨時檔案的位置。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 「$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/mta/」 <br /> </td> 
  </tr> 
  <tr> 
   <td> xMailer<br /> </td> 
   <td> X-Mailer欄位：SMTP郵件頭中欄位「X-Mailer」的值。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'nlserver，內部版本$(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### 快取 {#cache}

在 **快取** 節點，配置以下參數。 這是本地檔案快取配置。

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
   <td> 回收時間：期間，以秒錶示，在此之後檔案將自動從快取中刪除以回收儲存。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> 最大快取大小(Mb)。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> 清除頻率：執行快取清除機制之間的時段（秒）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 中繼 {#relay}

在 **mta >中繼** 節點，配置以下參數。 這是郵件傳遞的郵件伺服器配置。

清單的處理方式與MX DNS查詢返回的MX清單相同，通常只要第一個MX可用，就使用下一個MX，依此類推。

有關其他資訊，請參閱 [SMTP中繼](../../installation/using/configuring-campaign-server.md#smtp-relay)。

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
   <td> 要使用的SMTP中繼的DNS名稱或IP地址的逗號分隔清單。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 埠<br /> </td> 
   <td> SMTP伺服器的IP埠。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 主 {#master}

在 **mta >母版** 節點，配置以下參數。 這是主伺服器的配置。

有關其他資訊，請參閱 [節](../../installation/using/configuring-campaign-server.md#mta-child-processes)。

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
   <td> 資料庫池期間秒<br /> </td> 
   <td> 要傳送的作業的資料庫輪詢頻率。 此值指示資料庫輪詢頻率（秒）。 要獲取等待傳遞的作業清單，MTA會定期輪詢資料庫。 當沒有作業等待時，輪詢週期由此值定義。 否則，如果作業已被轉移到子伺服器，則該輪詢持續時間自動縮短到一秒，以便能夠盡快重新處理新作業，即一旦子伺服器再次可用。 這並不意味著在子伺服器再次可用之前每秒鐘都會執行資料庫查詢。 事實上，資料庫訪問只在至少一個子伺服器可用時才執行。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> 資料庫重試延遲秒<br /> </td> 
   <td> 資料庫連接失敗後的等待期。 資料庫連接失敗通常由資料庫伺服器本身引起。 例如，伺服器也可以出於維護目的而停止。 DataBaseRetryDelay參數定義在資料庫連接失敗時兩次連接嘗試之間的持續時間。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> 私鑰快取(DomainKeys)的有效期。 用於在DomainKeys建議(http://antispam.yahoo.com/domainkeys)之後簽名電子郵件的私鑰作為選項儲存在資料庫中。 domainKeysReloadPeriodSec參數定義MTA可以將這些密鑰保留在快取中的秒數。 在此延遲後，必須從資料庫重新載入所有鍵。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> 子伺服器的最大數量。 表示正在運行的伺服器的最大數量。 建議將此數量限制為與伺服器記憶體資源相容的最佳值。 可以在交貨期間檢查此項。 使用的記憶體不應超過可用物理記憶體的三分之一，否則將使用交換。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">MTA子進程</a>。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> 最小子伺服器數。 MTA嘗試至少使此數量的伺服器保持運行。 如果數量較少，它會每秒重新啟動新伺服器，直到達到此值。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> 啟動時的子伺服器數。 動態監視子伺服器的數量；當MTA啟動時，它會建立此值所指示的任意多個子伺服器。 通常，為了節省主機資源，子伺服器的啟動速度不能超過每秒一台伺服器。 但是，當MTA啟動時，此限制被取消，以便盡快提供子伺服器。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 孩子 {#child}

在 **mta >子代** 節點，配置以下參數。 這是子伺服器的配置。

有關其他資訊，請參閱 [電子郵件發送優化](../../installation/using/email-deliverability.md#email-sending-optimization)。

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
   <td> 額外阿格斯<br /> </td> 
   <td> 可選命令行參數 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> 超時，直到停止空閒的子伺服器。 如果子伺服器的空閒時間大於此參數，則它將自動自毀以釋放主機資源。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> 最大年齡秒<br /> </td> 
   <td> 最大郵件保留時間。 如果由於限制而無法發送預準備的消息或無法連接到目標MTA，則該消息將被放棄，並將在下次重試時進行處理。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> 每個子伺服器啟動的對FCM的並行Http請求的最大值。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> 每個子伺服器的最大消息數。 每個MTA子級處理此數目的消息和死亡。 必須指定一個數字，使MTA中的記憶體或資源洩漏無害（通常為幾千個）。 即使MTA代碼中沒有已知的記憶體洩漏，嵌入式JavaScript和XSL引擎也不完全可靠。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 500000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> 掛起的消息：等待在記憶體中傳遞的最大消息數。 <br /> </td> 
   <td> 龍<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> 子進程可以使用的最大記憶體大小(MB)。 超過此限制後，進程將停止，以便其使用的記憶體釋放到系統。 <br /> </td> 
   <td> 龍<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> 超時（秒），在超時後，將放棄傳遞連接器的SOAP連接。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> 開始WithFirstMX<br /> </td> 
   <td> 始終以最高優先順序MX開頭。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> 時間到生存<br /> </td> 
   <td> 恢復時連續嘗試的最大數量。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

在 **mta >子> smtp** 節點，配置以下參數。 這是SMTP會話的配置。

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
   <td> 啟用TLS<br /> </td> 
   <td> 當遠程伺服器支援時，以安全模式(STARTTLS/SMTPS)激活電子郵件的傳送。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> 空閒會話超時。 此參數僅在會話被重用以向給定域發送多條消息時才使用。 當MTA完成消息傳輸時，它使用的SMTP會話不會系統關閉。 如果郵件已準備好為同一域發送，則將重用同一SMTP會話，因此不會自動關閉會話。 參數IdleSessionTimeout參數用於定義SMTP會話在等待另一消息時保持活動狀態的時間。 持續時間過後，會話將自動關閉。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> 初始延遲秒<br /> </td> 
   <td> 重試連接前的初始延遲。 每次連接失敗時，此延遲都會加倍。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> 按子伺服器列出的最大SMTP會話數。 要傳遞消息，MTA將初始化與收件人MTA的SMTP連接。 給定子伺服器的最大併發和活動SMTP會話數受此值的限制。 如果將此值乘以maxSpareServers，則可獲得給定子伺服器可併發處理的消息的最大數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

在 **mta >子> smtp > IPAfinity** 節點，配置以下參數。 這是管理與IP地址的關聯的配置，用於優化傳出SMTP通信。

有關其他資訊，請參閱 [要使用的IP地址清單](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use) 和 [管理具有關聯的出站SMTP通信](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)。

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
   <td> 本地域<br /> </td> 
   <td> 域名：連結到IP地址的本地域名。 發出SMTP HELO命令時使用。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 名稱<br /> </td> 
   <td> 邏輯名稱：用戶連結到關聯的名稱。 名稱使用分號分隔；<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

在 **mta >子> smtp > IP** 節點，配置以下參數。

有關其他資訊，請參閱 [要使用的IP地址清單](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)。

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
   <td> 關聯的物理地址。 例如：「192.168.0.1」<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 公共ID<br /> </td> 
   <td> 關聯的公共地址ID。 用作統計伺服器的密鑰。 必須是數字。 查看 <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">節</a>。<br /> </td> 
   <td> 龍<br /> </td> 
  </tr> 
  <tr> 
   <td> 重量<br /> </td> 
   <td> 指定此IP相對於其他IP的使用頻率（權重越大，頻率越高）。<br /> </td> 
   <td> 龍<br /> </td> 
  </tr> 
  <tr> 
   <td> 包括域<br /> </td> 
   <td> 要包括的以逗號分隔的域掩碼清單。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 排除域<br /> </td> 
   <td> 要排除的域掩碼清單（以逗號分隔）。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
  <tr> 
   <td> 黑羅主機<br /> </td> 
   <td> 連結到IP地址的電腦名。 發出SMTP HELO命令時使用。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

## NMAC {#nmac}

以下是 **NMAC** 的下界。 這是推送通知傳遞的配置。

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
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 中繼 {#relay-1}

以下是 **nmac >中繼** 的下界。 這將配置對消息傳遞（ios http2連接器）使用中繼。

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
   <td> 龍<br /> </td> 
   <td> 443<br /> </td> 
  </tr> 
  <tr> 
   <td> 可信鏈<br /> </td> 
   <td> 證書鏈（PEM檔案）。 在使用模擬伺服器時非常有用。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 流水線 {#pipelined}

以下是 **流水線** 的下界。 這是Pipeline Services的事件處理模組的配置。

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
   <td> 保存公鑰時在開發人員連接中生成的應用程式的名稱。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 角<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authGatewayEndpoint<br /> </td> 
   <td> 獲取網關令牌的URL。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> 獲取令牌（使用XtkKey選項在AES中加密）的私鑰。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 自動啟動<br /> </td> 
   <td> 自動啟動 <br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> 禁用身份驗證<br /> </td> 
   <td> 禁用身份驗證：連接到Pipeline Services而不進行身份驗證。 <br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> discoverPipelineEndpoint<br /> </td> 
   <td> 用於發現管道服務URL的URL。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> 狀態保存期：進程的內部資訊保存在檔案中的頻率。 如果為0，則處於非活動狀態。 <br /> </td> 
   <td> 龍<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> 偵聽URL:強制Pipeline Services的偵聽URL。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript的ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM（以Mb為單位）的警報。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：警告：給定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> 狀態伺服器埠：HTTP伺服器埠，用於查詢進程的狀態。 如果為0，則處於非活動狀態。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 7781<br /> </td> 
  </tr> 
  <tr> 
   <td> 指針FlushMessageCount<br /> </td> 
   <td> 每次處理此數量的消息時，指針都將儲存在資料庫中。<br /> </td> 
   <td> <br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> 指針FlushPeriodSec<br /> </td> 
   <td> 儲存指針之前的延遲：在此期間，指針將至少儲存一次在資料庫中（在活動量低時非常有用）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> 處理JSThreads<br /> </td> 
   <td> 使用個性化JavaScript連接器進行事件處理的線程數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> 處理線程<br /> </td> 
   <td> 用於事件處理的線程數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> retryPeriodSec<br /> </td> 
   <td> 如果出現故障，則處理之間的延遲。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> 在此期間後放棄：如果在此時段後處理仍然失敗，則放棄事件。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> 運行級別<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 修復 {#repair}

以下是 **修復** 的下界。 這是資料庫修復模組的配置。

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
   <td> 交貨操作修復模組：延遲（以分鐘為單位），在此之後修復模組可以處理傳遞操作。 <br /> </td> 
   <td> 龍<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 安全區域 {#securityzone}

以下是 **安全區域** 的下界。

有關其他資訊，請參閱 [定義安全區域](../../installation/using/security-zones.md)。

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
   <td> 允許調試<br /> </td> 
   <td> 授權Web應用程式的調試模式。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> 授權用戶使用無密碼的應用程式。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> 允許HTTP<br /> </td> 
   <td> 授權使用HTTP進行操作員登錄。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInjent<br /> </td> 
   <td> 授權在表達式中使用SQLDATA。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserPassword<br /> </td> 
   <td> 授權用戶/密碼會話令牌。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
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
   <td> 會話TokenOnly<br /> </td> 
   <td> 不要使用安全令牌。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> showErrors<br /> </td> 
   <td> 顯示錯誤詳細資訊<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是預設配置：

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

以下是 **securityZone >子網路** 的下界。

有關其他資訊，請參閱 [定義安全區域](../../installation/using/security-zones.md)。

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
   <td> 掩模<br /> </td> 
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
   <td> 此子網路用於訪問實例的代理（反向）的掩碼或地址。 在這種情況下，將測試「X-Forwarded-For」標頭，而不是此代理。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 簡訊 {#sms}

以下是 **簡訊** 的下界。 這是入站SMS管理模組的配置。

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
   <td> 角<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 自動啟動<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> 資料保留天數<br /> </td> 
   <td> SMPP連接器保存的檔案工作檔案的最大天數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> 資料大小<br /> </td> 
   <td> SMPP工作檔案的最大大小(MB)。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 512<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript的ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> 會話連續性框架的重複：最大。 兩個幀之間的時間段（秒），用於通知接收會話仍處於啟用狀態。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM（以Mb為單位）的警報。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：警告：給定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> 搜索頻率：SMS帳戶輪詢期間。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod（重裝期間）<br /> </td> 
   <td> 帳戶重新載入頻率：資料庫重新載入要輪詢的帳戶的頻率。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> 運行級別<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> SR處理延遲的秒數：只有恢復日期早於當前時間的SR減去srReadDelay給定的持續時間（秒）。 <br /> </td> 
   <td> 龍<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> 逾時<br /> </td> 
   <td> SMS網關通信超時。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 網路大小 {#netsize}

以下是 **sms>網路大小** 的下界。

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
   <td> 與Netsize建立連接時超時（秒）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 統計 {#stat}

以下是 **統計** 的下界。 這是MTA統計模組的配置。

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
   <td> 角<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 自動啟動<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript的ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM（以Mb為單位）的警報。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：警告：給定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> 埠<br /> </td> 
   <td> 伺服器偵聽埠。 查看 <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">節</a>。<br /> </td> 
   <td> 短<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> 運行級別<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslog {#syslogd}

以下是 **syslog** 的下界。 這是日誌管理模組的配置。

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
   <td> 角<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 自動啟動<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript的ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> 日誌檔案的最大大小(Mb)。 <br /> </td> 
   <td> 龍<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> 要保留的最大登錄名.log檔案數。 <br /> </td> 
   <td> 龍<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM（以Mb為單位）的警報。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：警告：給定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> 運行級別<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 跟蹤 {#tracking}

以下是 **跟蹤** 的下界。 這是跟蹤伺服器的配置。

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
   <td> 角<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 自動啟動<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> blockRedirectForUnsignedTrackingLink<br /> </td> 
   <td> 禁用從以前生成生成的格式錯誤的URL。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> consolidationPeriodSec<br /> </td> 
   <td> 合併期間<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> 消除重複的開口：刪除重複的開啟跟蹤日誌，以限制Outlook等郵件閱讀器中郵件預覽的效果。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> 錯誤忽略百分比<br /> </td> 
   <td> 最多忽略X%的錯誤：只要尚未考慮的日記帳比率未達到此值，請不要更新跟蹤指標。 <br /> </td> 
   <td> 位元組<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> 錯誤忽略期間<br /> </td> 
   <td> 更新錯誤指示符：重新計算錯誤指示符之前的最大持續時間。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> 指示符持續時間<br /> </td> 
   <td> 在以下期間計算指示符：交貨有效日期後的持續時間，此後不再計算合併指標。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript的ID <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> 調用遠程跟蹤伺服器請求的日誌數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM（以Mb為單位）的警報。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：警告：給定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> Phishbowl服務APIKey<br /> </td> 
   <td> Phishbowl服務端點整合的API鍵。 這可保護從舊版本生成的格式錯誤的URL的重定向。 <br /> </td> 
   <td> 龍<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Phishbowl服務端點整合的端點。 這可保護從舊版本生成的格式錯誤的URL的重定向。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> 運行級別<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟蹤忽略百分比<br /> </td> 
   <td> 忽略最多X%的跟蹤：只要尚未考慮的日記帳比率未達到此值，請不要更新跟蹤指標。<br /> </td> 
   <td> 位元組<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟蹤忽略期間<br /> </td> 
   <td> 更新跟蹤指標：在重新計算跟蹤指示符之前的最大持續時間。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> 瀏覽器標識符快取的大小。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 跟蹤日誌 {#trackinglogd}

以下是 **跟蹤日誌** 的下界。 這是跟蹤日誌寫入守護程式的配置。

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
   <td> 角<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 自動啟動<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript的ID <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> 最大寫入重試次數：在日誌檔案中寫入失敗時可建立的最大檔案數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> 最大日誌大小：磁碟上日誌使用的最大空間(MB)。 不得少於100 MB。 <br /> </td> 
   <td> 龍<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM（以Mb為單位）的警報。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：警告：給定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> 最大日誌計數：共用記憶體中儲存的最大日誌數。 不能少於10000。 <br /> </td> 
   <td> 龍<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> 清除前的日誌數：開始清除日誌檔案之前插入的日誌數。 不能低於50000。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> 運行級別<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> 共用記憶體中為額外Web跟蹤參數保存的最大字元數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 網 {#web}

以下是 **網** 的下界。 這是Web模組的配置。

有關其他資訊，請參閱 [節](configuring-campaign-server.md#default-port-for-tomcat)。

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
   <td> 作為字串傳遞的JVM選項。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 最大線程數<br /> </td> 
   <td> 最大線程數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> 最小備用線程<br /> </td> 
   <td> 最小線程數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> 角<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 自動啟動<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> 控制埠<br /> </td> 
   <td> Tomcat偵聽控制埠：參考 <a href="configure-tomcat.md" target="_blank">配置Tomcat</a>。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> http埠<br /> </td> 
   <td> Tomcat HTTP偵聽埠：參考 <a href="configure-tomcat.md" target="_blank">配置Tomcat</a>。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript的ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> SubmitDelivery呼叫的隊列大小：可排隊的SubmitDelivery SOAP調用的最大數量。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM（以Mb為單位）的警報。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：警告：給定進程消耗的RAM量（以Mb為單位）<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notif中繼<br /> </td> 
   <td> 通知中繼：HostName：埠啟用通知的中繼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> 運行級別<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> startSoapRouterInModule<br /> </td> 
   <td> 以模組模式啟動SOAP路由器。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
 </tbody> 
</table>

### jsp {#jsp}

以下是 **Web >** 的下界。 這是JSP使用的參數配置。

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
   <td> 調試<br /> </td> 
   <td> 是否在調試模式下執行JSP。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 下載路徑<br /> </td> 
   <td> 下載資料夾：客戶端控制台的安裝程式的下載路徑。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 「$(XTK_INSTALL_DIR)/datakit/nl/eng/jsp」<br /> </td> 
  </tr> 
  <tr> 
   <td> foFileName<br /> </td> 
   <td> .fo檔案的路徑。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> soap路由器<br /> </td> 
   <td> SOAP路由器的URL(http://myserver/xxx、http://jni或mailto:xxx)。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> http://jni'<br /> </td> 
  </tr> 
 </tbody> 
</table>

的 **web > jsp >類路徑** 節點包含啟動JVM時要使用的所有類路徑的清單。 以下是預設配置：

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

以下是 **web > jssp** 的下界。 這是JSSP使用的參數配置。

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
   <td> 收集GarbageAfterRequest<br /> </td> 
   <td> 在每個查詢後啟用JavaScript上下文的垃圾回收器。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 真<br /> </td> 
  </tr> 
  <tr> 
   <td> 時間到生存<br /> </td> 
   <td> JavaScript上下文所服務的最大頁數。 <br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

的 **web > jsp >類路徑** 節點包含啟動JVM時要使用的所有類路徑的清單。

### 中繼 {#relay-2}

以下是 **Web >中繼** 的下界。 這是兩個區域之間HTTP請求的中繼配置。

有關其他資訊，請參閱 [節](../../installation/using/deploying-an-instance.md#synchronizing-public-resources)。

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
   <td> 在調試模式下啟動Web伺服器中的HTTP中繼模組。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> 禁止的CharsInAuthority<br /> </td> 
   <td> 禁止字元（域）:URI「authority」部分中禁止的字元的清單。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '.?#@/: <br /> </td> 
  </tr> 
  <tr> 
   <td> 禁止字元InPath<br /> </td> 
   <td> 禁止字元（路徑）:URI「path」部分中禁止的字元的清單。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '?#/<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> 「mod_dir」模組選項的值：資料夾查詢期間要使用的檔案清單。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 'index.md' <br /> </td> 
  </tr> 
  <tr> 
   <td> 啟動中繼<br /> </td> 
   <td> 啟動HTTP中繼模組。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> 啟動Web伺服器中的HTTP中繼模組。 <br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 真<br /> </td> 
  </tr> 
  <tr> 
   <td> 逾時<br /> </td> 
   <td> 在刪除禁止的URL之前等待時間。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> '60'<br /> </td> 
  </tr> 
 </tbody> 
</table>

添加 **web >中繼>url** 用於每個要中繼的URL的節點（插入順序定義優先順序），具有以下參數。

有關其他資訊，請參閱 [動態頁安全和中繼](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) 和 [節](../../installation/using/deploying-an-instance.md#synchronizing-public-resources)。

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
   <td> 授權IP:允許使用此掩碼的中繼的源IP地址清單（以逗號分隔）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 拒絕<br /> </td> 
   <td> 拒絕訪問這些URL（返回HTTP 403錯誤）<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 主機掩碼<br /> </td> 
   <td> 要中繼的DNS別名：以逗號分隔的要中繼的DNS別名掩碼清單(例如：「*.adobe.com」)。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 允許的http<br /> </td> 
   <td> 無論安全區域（如webApps）如何，HTTP訪問都已授權。 <br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 中繼主機<br /> </td> 
   <td> 添加原始主機：中繼時使用原始請求的HTTP「Host」標頭。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayPath<br /> </td> 
   <td> 添加初始URL路徑：將要中繼到目標頁的URL的完整路徑追加到。 <br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 狀態<br /> </td> 
   <td> 公共資源的同步狀態（枚舉）。 可能的值為「normal」（正常執行）、「黑名單」（在出現錯誤404時添加到denylist的url）和「spare」（如果存在，則檔案上載到備用伺服器上）。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 正<br /> </td> 
  </tr> 
  <tr> 
   <td> 目標URL<br /> </td> 
   <td> 目標頁的URL:參考 <a href="configure-tomcat.md" target="_blank">配置Tomcat</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 逾時<br /> </td> 
   <td> 正在中繼的請求的最大執行時間（秒）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> url路徑<br /> </td> 
   <td> 要中繼的URL掩碼(例如：「/nl*」、「*.jsp」)。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是預設配置：

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

添加 **web >中繼> responseHeader** 節點，用於添加轉發到中繼的回復。

有關其他資訊，請參閱 [管理HTTP標頭](../../installation/using/configuring-campaign-server.md#managing-http-headers)。

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
   <td> 值<br /> </td> 
   <td> 標題值 <br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是預設配置：

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### 重定向 {#redirection}

以下是 **Web >重定向** 的下界。 這是重定向模組的配置。

有關其他資訊，請參閱 [節](../../installation/using/deploying-an-instance.md#synchronizing-public-resources)。

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
   <td> 組織ID:Adobe Experience Cloud內的唯一組織標識符，特別用於VisitorID服務和IMS SSO。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> 描述用於永久Cookie的策略的值（符合P3P壓縮策略格式）。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> 「CAO DSPCOR CURa DEVa TAI OUR BUS IND UNI COM NAV」<br /> </td> 
  </tr> 
  <tr> 
   <td> cookie域<br /> </td> 
   <td> 要配置為顯式指示要設定cookie的域的以逗號分隔的域清單。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 資料庫ID<br /> </td> 
   <td> 與跟蹤實例關聯的資料庫標識符。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> 按呼叫記錄計數：調用方法GetTrackingLogs時預設返回的日誌數。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> 過期URL<br /> </td> 
   <td> 過期重定向頁：重定向伺服器在傳遞操作的重定向已過期時預設使用的網頁URL。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> 最大作業計數：快取中最大傳遞操作數。 不得低於50。 <br /> </td> 
   <td> 龍<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> 啟動重定向<br /> </td> 
   <td> 啟動重定向服務。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 真<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectionInModule<br /> </td> 
   <td> 以模組模式啟動重定向服務。<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 真<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟蹤Web訪問者<br /> </td> 
   <td> Web跟蹤：為未知用戶訪問的頁建立日誌。 <br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟蹤密碼<br /> </td> 
   <td> 重定向伺服器使用的密碼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

以下是 **web >重定向> spareServer** 的下界。

有關其他資訊，請參閱 [冗餘跟蹤](../../installation/using/configuring-campaign-server.md#redundant-tracking)。

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
   <td> 在下列情況下，將考慮：如果表達式返回true，則會考慮跟蹤伺服器。 <br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ID<br /> </td> 
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

### 垃圾郵件檢查 {#spamcheck}

以下是 **web > spamCheck** 的下界。 這是Email anti-spam評分評估參數的配置。

有關其他資訊，請參閱 [配置SpamAssassin](../../installation/using/configuring-spamassassin.md)。

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
   <td> 執行命令以評估電子郵件的反垃圾郵件分數(例如「perl spamcheck.pl」)。<br /> </td> 
   <td> 字串<br /> </td> 
  </tr> 
 </tbody> 
</table>

## wf伺服器 {#wfserver}

以下是 **wf伺服器** 的下界。 這是工作流進程配置。

有關其他資訊，請參閱 [高可用性工作流和關聯](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities)。

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
   <td> 親緣<br /> </td> 
   <td> 親和<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 角<br /> </td> 
   <td> 啟動參數<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> 自動啟動<br /> </td> 
   <td> 自動啟動<br /> </td> 
   <td> 布爾型<br /> </td> 
   <td> 假<br /> </td> 
  </tr> 
  <tr> 
   <td> 資料庫池期間秒<br /> </td> 
   <td> 期間<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> 啟動進程時要執行的JavaScript的ID。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> 記憶體消耗警報：有關給定進程所消耗的RAM（以Mb為單位）的警報。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> 記憶體消耗警告：警告：給定進程消耗的RAM量（以Mb為單位）。<br /> </td> 
   <td> 龍<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notif中繼<br /> </td> 
   <td> 通知中繼：HostName：埠啟用通知的中繼。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> 進程自動重新啟動的一天中的時間。 請參閱 <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">自動進程重新啟動</a>。<br /> </td> 
   <td> 字串<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> 運行級別<br /> </td> 
   <td> 開始時的優先順序。 低優先順序模組首先啟動，最後停止。 因此，syslogd模組必須具有優先順序0。<br /> </td> 
   <td> 短<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>
