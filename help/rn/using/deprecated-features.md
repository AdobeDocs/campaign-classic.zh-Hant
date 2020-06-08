---
title: Campaign Classic已過時和移除的功能
description: 本頁列出Adobe Campaign Classic已過時和已移除的功能
page-status-flag: never-activated
uuid: null
contentOwner: simonetn
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: campaign-classic-deprecated-features
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e46325ab8f68a0b71198aee9cf04f2b1eb97fdd3
workflow-type: tm+mt
source-wordcount: '1468'
ht-degree: 0%

---


# 已棄用及已移除的功能 {#deprecated-and-removed-features}

Adobe會持續評估產品功能，以找出應以更現代的替代方式來取代的舊功能，以提升整體客戶價值，並時時考慮回溯相容性。 當Adobe Campaign Classic與協力廠商工具搭配使用時，相容性會定期更新，以便僅實作支援的版本。 不再與Adobe Campaign Classic相容的版本列於下方和「相容性」 [表中](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。

若要通知即將移除／取代Campaign Classic功能，請套用下列規則：

* 首先宣佈放棄。 雖然已過時的功能仍可供現有使用者使用並支援，但是這些功能將無法進一步增強，也無法記錄在案。
* 在以下版本中，將最早移除已過時的功能。 本頁會公佈實際的移除目標日期。

此程式可讓客戶在實際移除之前，至少有一個發行週期，以調整其實作方式，以適應已過時功能的新版本或後繼版本。

>[!NOTE]
>Adobe Campaign發行和新功能列在發行說 [明中](../../rn/using/latest-release.md)。

## Deprecated features {#deprecated-features}

本節列出最新Campaign Classic發行中已標示為已過時的功能和功能。

通常，計畫在未來版本中移除的功能會先設為不建議使用。 這些新Campaign Classic客戶無法再使用這些功能，或者不應用於任何新實作。 也會從產品檔案中移除它們。

建議客戶檢閱他們是否在目前部署中運用了功能／功能，並規劃變更實施。 請參閱目標刪除日期以規劃您的環境和項目更新。

<table> 
 <tbody> 
   <tr>
   <td><strong>功能</strong></td>
   <td><strong>取代</strong></td> 
  </tr>
   <tr>
  <td>SMS連接器<br></td>
  <td><p> 從20.2版開始，下列SMS連接器已過時。<p>
   <ul>
   <li>NetSize</li>
   <li>通用SMPP（支援二進位模式的SMPP 3.4版）</li>
   <li>Sybase365(SAP SMS 365)</li>
   <li>CLX通信</li>
   <li>Tele2</li>
   <li>O2</li>
   <li>iOS</li>
   </ul>
  <p>如果您使用其中一個連接器，則需要相應地調整實施。 <a href="../../delivery/using/sms-channel.md">進一步瞭解</a></p> 
  <p>瞭解如何在此技術中移轉舊 <a href="https://helpx.adobe.com/campaign/kb/sms-connector.html">版連接器</a>。</p>
  <p><em>目標刪除日期： 2021年</em></p>
  </td> 
 </tr>
  <tr>  
   <td>傳真頻道<br></td>
   <td><p>從20.2版開始，傳真頻道已過時。</p> 
   <p>如果您使用此渠道，則需要據以調整實作。 <a href="../../delivery/using/communication-channels.md">進一步瞭解</a> 「促銷活動」渠道。</p>
   <p><em>目標刪除日期： 2021年</em></p></td>
  </tr>
 </tbody> 
</table>

## 已移除功能 {#removed-features}

本節列出已從Campaign Classic移除的功能和功能。

<table> 
 <tbody> 
  <tr> 
   <td><strong>區域——功能</strong></td>
   <td><strong>取代</strong></td> 
  </tr> 
   <tr> 
   <td>檔案式電子郵件封存<br></td>
   <td><p>從Campaign 20.2版開始，檔案式電子郵件封存功能不再提供。 電子郵件封存現在可透過專屬的密件副本電子郵件地址提供。 <a href="../../installation/using/email-archiving.md">進一步瞭解</a></p></td>
  </tr> 
   <tr> 
   <td>銷售線索管理</td>
   <td><p>從Campaign 20.2發行開始，銷售機會管理套件將不再提供。 類似的功能可透過其他原生工作流程活動和資料模型修改來實施。</p></td>
   </tr>
   <tr>
   <td>促銷活動API檔案- jsapi.chm檔案</td>
   <td>從Campaign 19.1版開始，Campaign Classic API可在專用頁面中使用。 如果您使用舊版jsapi.chm檔案，現在應參考新 <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">的線上版本</a>。</td>
  </tr> 
  <tr> 
   <td>宣傳協調——預測式行銷</td>
   <td>從Campaign 18.10版開始，就無法再使用預測式行銷功能。</td>
  </tr> 
  <tr> 
   <td>Web應用程式- Microsites</td>
   <td>從Campaign 18.10版開始，Microsoftsites已不再提供。 您可以限制對Adobe Campaign設定檔案上專用網域的存取，並使用DNS別名在Campaign中使用個人化URL，借以提高安全性。 <a href="https://helpx.adobe.com/campaign/kb/domain-name-delegation.html">進一步瞭解</a></td>
  </tr> 
  <tr> 
   <td>推播通知- iOS二進位連接器</td>
   <td>根據Apple的建議，Adobe已移除舊版iOS二進位連接器，啟動Campaign 18.10版本。 目前已提供功能更強大、效率更高的HTTP/2連接器。</td>
  </tr> 
  <tr> 
   <td>decryptString API</td>
   <td><p>由於安全原因，啟動Campaign 18.6版本時， <em>decryptString</em> API預設不再適用於新安裝。</p> 
   <p>在18.6版（及更新版本）的設定檔中，此API不再啟動，而且已由decryptPassword函式 <em>取代</em> 。 <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/f-decryptPassword.html?hl=decrypt">進一步瞭解</a></p></td>
  </tr> 
   <tr> 
   <td>行動頻道- MMS和WAP推播訊息</td>
   <td>從Campaign 18.4版開始，MMS和Wap推播頻道已不再提供。 您可以利用 <a href="../../delivery/using/sms-channel.md">SMS</a> 和 <a href="../../delivery/using/about-mobile-app-channel.md">Push</a> 傳送。</td>
  </tr> 
   <tr> 
   <td>行動頻道- LINE v1</td>
   <td>從Campaign 18.4版開始，LINE Connect套件已不再提供。 Adobe建議使用新的LINE Channel套件做為替代項目。 <a href="../../delivery/using/line-channel.md">進一步瞭解</a></td>
  </tr> 
 </tbody> 
</table>

## 不建議使用的相容性 {#deprecated-compatibility}

Campaign Classic不再支援下列系統。 請參閱相容性 [表](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) ，以升級到較新版本，或在相容性結束之前移至新系統。

### Adobe Campaign 20.2版本 {#compat-20-2-release}

從20.2版開始，Campaign Classic已不再支援下列系統。 相容性將於20.3版本中終止- 2020年9月。

* 客戶端控制台： Windows 7
* 舊版SMS連接器（請參閱下方的「已過時功能」一節）

### Adobe Campaign 19.2版本  {#compat-19-2-release}

從19.2版開始，Campaign Classic不再支援下列作業系統。 相容性將於2020年結束。

* Web伺服器： Apache 2.2.
* 作業系統： CentOS 6.

請參閱「兼 [容性表](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) 」以升級至較新版本或移至新系統。

## 相容性終止 {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic與「相容性」矩陣中所列的所有系統和工具 [相容](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。 當這些協力廠商系統和工具的特定版本與其各自的建立者達成生命週期結束(EOL)時，Adobe Campaign不再與這些版本相容： 它們被宣佈為不再提倡，然後在後續的產品版本中從我們的相容性矩陣中移除。 請確保您使用相容性矩陣中列出的任何系統的支援版本，以避免出現任何問題。

### 客戶機控制台 {#client-console-eol}

Adobe Campaign Classic Client Console無法再在下列系統上執行，因為編輯器已不建議使用這些系統。 在其中一個版本上執行Campaign Client Console的客戶，必須在目標移除日期之前升級至最新版本。 請參閱「 [Compatibility matrix(相容性表](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html))」。

* Windows Server 2003、2008、2008 R2
* Windows XP、Vista

>[!NOTE]
>從Campaign 20.1版開始，Campaign Classic Client Console 32位元已不再與Campaign最新版本相容。 您需要使用64位客戶端控制台。


### 作業系統 {#o-s-eol}

從19.1版開始，Adobe Campaign已不再與下列作業系統相容。

* 德比安7號。 [進一步瞭解](https://wiki.debian.org/DebianReleases)
* RHEL 6.x. [進一步瞭解](https://access.redhat.com/support/policy/updates/errata)
* Windows Server 2008。 [進一步瞭解](https://support.microsoft.com/en-us/lifecycle/search/1163)
* SLES 11. [進一步瞭解](https://www.suse.com/lifecycle)

### Web伺服器 {#web-server-eol}

從19.1春季版開始，Adobe Campaign已不再與下列網頁伺服器相容。

* Microsoft IIS 7。 [進一步瞭解](https://support.microsoft.com/en-us/lifecycle/search/810)

### 工具 {#tools-eol}

從19.1春季版開始，Adobe Campaign不再與下列工具相容。

* Java JDK 7. [進一步瞭解](http://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5 / 4.3 / 5.x，但嵌入其他工具時除外。 [進一步瞭解](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### 資料庫引擎 {#dbe-eol}

Adobe不支援下列資料庫引擎，因為其編輯器已不建議使用這些引擎。 在這些版本中執行的客戶需要升級至最新版本或改用其他版本。

請參閱 [Campaign Classic相容性矩陣](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) ，以存取相容版本的清單。

**同盟資料存取(FDA)**

從19.1春季版開始，Adobe Campaign不再與下列FDA伺服器相容。

* PostgreSQL 9.3. [進一步瞭解](https://www.postgresql.org/support/versioning)
* MySQL 5.5. [進一步瞭解](http://www.fromdual.com/support-for-mysql-from-oracle)
* DB2 9.5. [進一步瞭解](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Teradata 14 - 14.1. [進一步瞭解](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)

Campaign Classic與Federated Data Access(FDA)中的下列伺服器不相容。

* DB2 UDB 9.5、9.7。 Federated Data Access(FDA)支援較新版本的DB2。 [進一步瞭解](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Oracle 9i、10G R2。 Federated Data Access(FDA)支援更新版本的Oracle。 [進一步瞭解](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)
* PostgreSQL 8.3、8.4、9.0、9.1、9.2。 PostgreSQL的較新版本通過Federated Data Access(FDA)受支援。 [進一步瞭解](https://www.postgresql.org/support/versioning)
* MSSQL 2000、2005、2008 R2。 Federated Data Access(FDA)支援較新版本的SQL Server。 [進一步瞭解](https://support.microsoft.com/en-us/lifecycle/search/1044)
* MySQL 5.1. MySQL的更新版本通過Federated Data Access(FDA)受支援。 [進一步瞭解](https://en.wikipedia.org/wiki/InfiniDB)
* InfiniDB已經壽終正寢。 [進一步瞭解](https://www.mysql.com/support)
* Teradata 13, 13.1. Teradata的更新版本可透過Federated Data Access(FDA)獲得支援。 [進一步瞭解](https://www.info.teradata.com/download.cfm?ItemID=1007255)
* Netezza 6.02, 7.0 內泰扎已經壽終正寢。 [進一步瞭解](https://en.wikipedia.org/wiki/Netezza)
* AsterData 5.0. AsterData終於壽終正寢。 [進一步瞭解](https://en.wikipedia.org/wiki/Aster_Data_Systems)
* Sybase IQ 15.2、15.4、15.5和Sybase ASE 15.0。 Sybase的最新版本通過Federated Data Access(FDA)受到支援。 [進一步瞭解](https://sites.google.com/site/dbatipsandtricks/time-tracker)
* 通過HiveSQL的Hadoop: Hadoop 2.7.3、HiveSQL 1.2.1。 Adobe Campaign Classic仍將透過HiveSQL透過Federated Data Access(FDA)支援列出的Hadoop版本，但是這些版本與： HortonWorks(HDP 2.4.X、2.5.x、2.6.x)和HDInsight 3.4(HDP 2.4)、3.5(HDP 2.5)、3.6(HDP 2.6)

**RDBMS伺服器**

Adobe Campaign與下列RDBMS伺服器不相容：
* Oracle 10GR2
* PostgreSQL 9.0到9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
