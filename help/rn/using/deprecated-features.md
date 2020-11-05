---
title: Campaign Classic 已棄用和移除的功能
description: 本頁列出 Adobe Campaign Classic 已棄用和已移除的功能
page-status-flag: never-activated
contentOwner: simonetn
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: campaign-classic-deprecated-features
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 48acf8cbc52a54a2dd08f0b8f29be57d4e5e006f
workflow-type: tm+mt
source-wordcount: '1621'
ht-degree: 99%

---


# 已棄用及已移除的功能{#deprecated-and-removed-features}

Adobe 持續評估產品功能，尋找應以更現代的替代方式來取代舊的功能，以提升整體客戶價值，並時時考慮回溯相容性。由於 Adobe Campaign Classic 可以搭配協力廠商工具使用，產品相容性將定期更新，以僅實施所支援的版本。不再與 Adobe Campaign Classic 相容的版本列於下方及[「相容性矩陣」](../../rn/using/compatibility-matrix.md)中。

為通知即將移除/遭取代的 Campaign Classic 功能，我們採用下列規則：

* 首先我們發佈功能棄用的消息。雖然已棄用的功能仍支援現有使用者，但是這些功能將不會進一步增強或記錄。
* 後續最新發行版本，則將最先移除已棄用的功能。本頁面將公佈實際的移除日期。

此流程讓客戶在實際移除之前，至少可以適應一個版本發行週期，以調整實作方式，及適應已棄用功能的新版本或後繼功能。

>[!NOTE]
>[發行說明](../../rn/using/latest-release.md)將列出 Adobe Campaign 發行版本和新功能。

## 棄用的功能{#deprecated-features}

本節列出最新 Campaign Classic 發行版本中已標示為棄用的功能。

通常，未來新發行版本預計移除的功能，將先設為棄用。新的 Campaign Classic 客戶將無法使用這些功能，或者這些功能將不用於任何新實施。產品文件亦將移除這些功能。

建議客戶檢視是否在目前部署運用了棄用的功能，並規劃實施變更的計畫。請參閱目標移除日期，據此規劃您的環境和專案更新。

<table> 
 <tbody> 
   <tr>
   <td><strong>功能</strong></td>
   <td><strong>取代的功能</strong></td>
  </tr>
  <tr>
  <td>CRM 連接器<br></td>
   <td><p>下列 CRM 連接器自 Campaign 第 20.3 發行版本開始將不再使用。</p>
   <ul>
   <li>Soap API - 內部部署：2007、2015、2016 年</li>
   <li>Soap API - 線上：2015、2016 年</li>
   <li>Web API - Microsoft Dynamics CRM內部部署：2016, 2016更新1</li>
   <li>Web API - Microsoft Dynamics CRM線上：2016, 2016更新1</li>
   </ul>
  <p><em>目標移除日期：2021 年</em></p>
  </td>
 </tr>
  <tr>
  <td>舊的 iOS 二進位<br></td>
  <td><p>自 Campaign 第 20.3 發行版本開始，已棄用舊的 iOS 二進位連接器。<p>
  <p> 如果您使用此連接器，則需要據此調整實施。<a href="https://helpx.adobe.com/tw/campaign/kb/migrate-to-http2.html">進一步瞭解</a></p>
  <p><em>目標移除日期：2021 年</em></p>
  </td>
 </tr>
   <tr>
  <td>Demdex 網域<br></td>
  <td><p> 自 Campaign 第 20.3 發行版本開始，已棄用使用於匯入和匯出受眾至 Adobe Experience Cloud 的 Demdex 網域。<p>
  <p>如果您使用 Demdex 網域作為匯入/匯出的外部帳戶，則需要依此調整實施。<a href="../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md">進一步瞭解</a></p> 
  <p><em>目標移除日期：2021 年</em></p>
  </td>
  <tr>
  <td>OAuth 驗證（OAuth 和 JWT）<br></td>
  <td><p> 自 Campaign 第 20.3發行版本開始，已變更原本以 oAUTH 驗證設定為基礎而用於存取管道的觸發器整合驗證，並將其移動至 Adobe I/O。 <p>
  <p>如果您使用觸發器整合，則需要據此調整實施。<a href="../../integrations/using/configuring-adobe-io.md">進一步瞭解</a></p> 
  <p>如需與 OAuth 驗證折舊相關的資訊，請參閱第 <a href="https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md"> 頁</a></p> 
  <p><em>目標移除日期：2021 年 4 月</em></p>
  </td>
  </tr>
  <td>SMS 連接器<br></td>
  <td><p> 下列 SMS 連接器自 Campaign 20.2 發行版本開始將不再使用。<p>
   <ul>
   <li>NetSize</li>
   <li>Generic SMPP（支援二進位模式的 SMPP 第 3.4 版本）</li>
   <li>Sybase365 (SAP SMS 365)</li>
   <li>CLX Communications</li>
   <li>Tele2</li>
   <li>O2</li>
   <li>iOS</li>
   </ul>
  <p>如果您使用其中一個連接器，則需要據此調整實施。<a href="../../delivery/using/sms-channel.md">瞭解更多</a></p> 
  <p>閱讀此<a href="https://helpx.adobe.com/tw/campaign/kb/sms-connector.html">技術文件</a>，瞭解如何移轉舊連接器。</p>
  <p><em>目標移除日期：2021 年</em></p>
  </td> 
 </tr>
  <tr>  
   <td>傳真頻道<br></td>
   <td><p>傳真頻道自 Campaign 20.2 發行版本開始不再使用。</p> 
   <p>如果您使用此頻道，則需要據此調整實施。<a href="../../delivery/using/steps-about-delivery-creation-steps.md">瞭解更多</a> Campaign 頻道。</p>
   <p><em>目標移除日期：2021 年</em></p></td>
  </tr>
 </tbody> 
</table>

## 已移除的功能{#removed-features}

本節列出已從 Campaign Classic 移除的功能。

<table> 
 <tbody> 
  <tr> 
   <td><strong>區域——功能</strong></td>
   <td><strong>取代的功能</strong></td> 
  </tr> 
   <tr> 
   <td>Windows NT 驗證<br></td>
   <td><p>自 Campaign 第 20.3 發行版本開始，在使用 Microsoft SQL Server 配置新的資料庫時，已將 Windows NT 驗證從可用的驗證方法中移除。<a href="../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine">進一步瞭解</a></p></td>
  </tr>
   <tr> 
   <td>檔案式電子郵件封存<br></td>
   <td><p>自 Campaign 第 20.2 發行版本開始，不再提供檔案式電子郵件封存功能。電子郵件封存現在透過專屬的 BCC 電子郵件地址提供。<a href="../../installation/using/email-archiving.md">瞭解更多</a></p></td>
  </tr> 
   <tr> 
   <td>銷售機會管理</td>
   <td><p>自 Campaign 第 20.2 發行版本開始，將不再提供銷售機會管理套件。類似的功能可以透過其他原生工作流程活動和資料模型修改來實施。</p></td>
   </tr>
   <tr>
   <td>Campaign API 文件 - jsapi.chm 檔案</td>
   <td>自 Campaign 第 19.1 發行版本開始，可以透過專屬頁面使用 Campaign Classic API。如果您使用舊版 jsapi.chm 檔案，現在應參考<a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">新的線上版本</a>。</td>
  </tr> 
  <tr> 
   <td>Campaign Orchestration - 預測式行銷</td>
   <td>自 Campaign 18.10 發行版本開始，已無法再使用預測式行銷功能。</td>
  </tr> 
  <tr> 
   <td>網頁應用程式 - Microsites</td>
   <td>自 Campaign 18.10 發行版本開始，已不再提供 Microsites。您可以在 Adobe Campaign 配置檔案，限制僅能存取專屬網存取，並使用 DNS 別名在 Campaign 中使用個人化 URL，藉此提高安全性。<a href="https://helpx.adobe.com/tw/campaign/kb/domain-name-delegation.html">瞭解更多</a></td>
  </tr> 
  <tr> 
   <td>推播通知 - iOS Binary Connector</td>
   <td>根據 Apple 的建議，Adobe 自 Campaign 18.10 發行版本起，移除舊版的 iOS Binary Connector。目前則提供功能更強大、效率更高的 HTTP/2 連接器。</td>
  </tr> 
  <tr> 
   <td>decryptString API</td>
   <td><p>出於安全原因，自 Campaign 18.6 發行版本起，新的安裝已不再預設提供 <em>decryptString</em> API。</p> 
   <p>在 18.6 版本升級後（及更新版本）的設定檔，不再啟用此 API，並已由 <em>decryptPassword</em> 函式取代。<a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/f-decryptPassword.html?hl=decrypt">瞭解更多</a></p></td>
  </tr> 
   <tr> 
   <td>行動裝置頻道 - MMS 和 WAP 推播訊息</td>
   <td>自 Campaign 第 18.4 發行版本開始，不再提供 MMS 和 Wap 推播頻道。作為取代，您可以利用 <a href="../../delivery/using/sms-channel.md">SMS </a> 和 <a href="../../delivery/using/about-mobile-app-channel.md">Push</a> 傳遞。</td>
  </tr> 
   <tr> 
   <td>行動裝置頻道 - LINE v1</td>
   <td>自 Campaign 第 18.4 發行版本開始，不再提供 LINE Connect 套件。Adobe 建議使用新的 LINE Channel 套件取而代之。<a href="../../delivery/using/line-channel.md">瞭解更多</a></td>
  </tr> 
 </tbody> 
</table>

## 已棄用的相容性{#deprecated-compatibility}

Campaign Classic 不再使用下列系統。請參閱[相容性矩陣](../../rn/using/compatibility-matrix.md)，以升級到更新版本，或在相容性結束之前移至新系統。

### Adobe Campaign 20.2 發行版本{#compat-20-2-release}

舊的 SMS 連接器自第 20.2 版開始將不再使用。請參閱「[已棄用的功能」部分](#deprecated-features)

## 相容性終止{#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic 與[「相容性矩陣」](../../rn/using/compatibility-matrix.md)所列的所有系統和工具相容。這些協力廠商系統和工具的特定版本生命週期結束 (EOL) 時，Adobe Campaign 不再與這些版本相容：我們將不再使用這些系統和功能，後續的產品發行版本亦會將這些系統和功能從我們的相容性矩陣移除。請確保您使用相容性矩陣列出的任何系統的支援版本，以避免出現任何問題。

### 用戶端主控台{#client-console-eol}

Adobe Campaign Classic 用戶端主控台無法在下列系統執行，因為編輯者已不使用這些系統。客戶若其中一個版本執行 Campaign 用戶端主控台，必須在目標移除日期前升級至最新版本。請參閱「[相容性矩陣](../../rn/using/compatibility-matrix.md)」。

* Windows Server 2003、2008、2008 R2
* Windows 7、XP、Vista

>[!NOTE]
>自 Campaign 20.1 發行版本開始，Campaign Classic 用戶端主控台 32 位元已不再與 Campaign 最新版本相容。您需要使用 64 位元版本的用戶端主控台。


### 作業系統 {#o-s-eol}

自 19.1 發行版本開始，Adobe Campaign 不再與下列作業系統相容。

* CentOS 6 [瞭解更多](https://wiki.centos.org/Download)
* Debian 7。[瞭解更多](https://wiki.debian.org/DebianReleases)
* RHEL 6.x。[瞭解更多](https://access.redhat.com/support/policy/updates/errata)
* Windows Server 2008。[瞭解更多](https://support.microsoft.com/en-us/lifecycle/search/1163)
* SLES 11。[瞭解更多](https://www.suse.com/lifecycle)

### Web 伺服器{#web-server-eol}

自 19.1 春季發行版本開始，Adobe Campaign 不再與下列 Web 伺服器相容。

* Apache 2.2. [瞭解更多](https://httpd.apache.org/)
* Microsoft IIS 7。[瞭解更多](https://support.microsoft.com/en-us/lifecycle/search/810)

### 工具{#tools-eol}

自 19.1 春季發行版本開始，Adobe Campaign 不再與下列工具相容。

* Java JDK 7。[瞭解更多](http://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5 / 4.3 / 5.x，但內嵌於其他工具則除外。[瞭解更多](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### 資料庫引擎{#dbe-eol}

Adobe 不支援下列資料庫引擎，因為其編輯者已不建議使用這些引擎。客戶若執行這些版本，需要升級至最新版本或改用其他引擎。

請參閱 [Campaign 相容性矩陣](../../rn/using/compatibility-matrix.md)，以取得相容版本清單。

**同盟資料存取 (FDA)**

自第 20.2 發行版本開始，Adobe Campaign 不再與下列 FDA 伺服器相容：

* DB2 UDB 10.5

自第 19.1 春季發行版本開始，Adobe Campaign 不再與下列 FDA 伺服器相容：

* PostgreSQL 9.3。[瞭解更多](https://www.postgresql.org/support/versioning)
* MySQL 5.5。[瞭解更多](http://www.fromdual.com/support-for-mysql-from-oracle)
* DB2 9.5。[瞭解更多](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Teradata 14 - 14.1。[瞭解更多](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)

Campaign Classic 與下列同盟資料存取 (FDA) 的伺服器不相容。

* DB2 UDB 9.5、9.7。透過同盟資料存取 (FDA) 支援更新版本的 DB2。[瞭解更多](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Oracle 9i、10G R2。透過同盟資料存取 (FDA) 支援更新版本的 Oracle。[瞭解更多](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)
* PostgreSQL 8.3、8.4、9.0、9.1、9.2。透過同盟資料存取 (FDA) 支援更新版本的 PostgreSQL。[瞭解更多](https://www.postgresql.org/support/versioning)
* MSSQL 2000、2005、2008 R2。透過同盟資料存取 (FDA) 支援更新版本的 SQL Server。[瞭解更多](https://support.microsoft.com/en-us/lifecycle/search/1044)
* MySQL 5.1。透過同盟資料存取 (FDA) 支援更新版本的 MySQL。[瞭解更多](https://en.wikipedia.org/wiki/InfiniDB)
* InfiniDB 生命週期結束。[瞭解更多](https://www.mysql.com/support)
* Teradata 13、13.1。透過同盟資料存取 (FDA) 支援更新版本的 Teradata。[瞭解更多](https://www.info.teradata.com/download.cfm?ItemID=1007255)
* Netezza 6.02、7.0。Netezza 生命週期結束。[瞭解更多](https://en.wikipedia.org/wiki/Netezza)
* AsterData 5.0。AsterData 生命週期結束。[瞭解更多](https://en.wikipedia.org/wiki/Aster_Data_Systems)
* Sybase IQ 15.2、15.4、15.5 和 Sybase ASE 15.0。透過同盟資料存取 (FDA) 支援更新版本的 Sybase。[瞭解更多](https://sites.google.com/site/dbatipsandtricks/time-tracker)
* Hadoop via HiveSQL：Hadoop 2.7.3、HiveSQL 1.2.1。Adobe Campaign Classic 仍將透過同盟資料存取 (FDA) 支援所列的 Hadoop via HiveSQL 版本，但是這些版本與：HortonWorks (HDP 2.4.X、2.5.x、2.6.x) 及 HDInsight 3.4 (HDP 2.4)、3.5 (HDP 2.5)、3.6 (HDP 2.6) 合併

**RDBMS 伺服器**

Adobe Campaign 與下列 RDBMS 伺服器不相容：
* Oracle 10GR2
* PostgreSQL 9.0 到 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
