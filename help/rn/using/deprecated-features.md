---
product: campaign
title: Campaign Classic 已棄用和移除的功能
description: 本頁列出 Adobe Campaign Classic 已過時和已移除的功能
feature: Release Notes
role: User
level: Beginner
exl-id: d60d67de-6618-4f3b-be4a-ad7633ab5645
source-git-commit: ef89551952cfbfd525a4dff716fe4676c1252d05
workflow-type: tm+mt
source-wordcount: '1653'
ht-degree: 98%

---

# 已棄用及已移除的功能 {#deprecated-and-removed-features}



Adobe 持續評估產品功能，尋找應以更現代的替代方式來取代舊的功能，以提升整體客戶價值，並時時考慮回溯相容性。由於 Adobe Campaign Classic 可以搭配協力廠商工具使用，產品相容性將定期更新，以僅實施所支援的版本。不再與 Adobe Campaign Classic 相容的版本列於下方及[「相容性矩陣」](../../rn/using/compatibility-matrix.md)中。

為通知即將移除/遭取代的 Campaign Classic 功能，我們採用下列規則：

* 首先我們發佈功能棄用的消息。雖然已棄用的功能仍支援現有使用者，但是這些功能將不會進一步增強或記錄。
* 後續最新發行版本，則將最先移除已棄用的功能。本頁面將公佈實際的移除日期。

此流程讓客戶在實際移除之前，至少可以適應一個版本發行週期，以調整實作方式，及適應已棄用功能的新版本或後繼功能。

>[!NOTE]
>[發行說明](../../rn/using/latest-release.md)將列出 Adobe Campaign 發行版本和新功能。

## 已棄用功能 {#deprecated-features}

本節列出最新 Campaign Classic 發行版本中已標示為棄用的功能。

通常，未來新發行版本預計移除的功能，將先設為棄用。新的 Campaign Classic 客戶將無法使用這些功能，或者這些功能將不用於任何新實施。產品文件亦將移除這些功能。

建議客戶檢視是否在目前部署運用了棄用的功能，並規劃實施變更的計畫。請參閱目標移除日期，據此規劃您的環境和專案更新。

<table> 
 <tbody> 
   <tr>
   <td><strong>功能</strong></td>
   <td><strong>詳細資料</strong></td>
  </tr>
  <tr>
 <td>Campaign (Neolane) 舊版 SDK</td>
 <td><p>適用於行動應用程式的 Campaign (Neolane) SDK 現已棄用。請改為在資料彙集 UI 設定 Adobe Campaign 擴充功能，以便使用 Adobe Experience Platform Mobile SDK。Adobe Experience Platform Mobile SDK 有助於在行動應用程式中，強化 Adobe Experience Cloud 解決方案與服務。 SDK 設定可透過資料彙集 UI 來管理，提供靈活的設定與可擴充的規則式整合。 若要了解如何設定行動應用程式管道，請參閱 <a href="https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/send/push/push-settings">Campaign v8 文件</a>。</p>
<p>目標移除日期：2025 年夏 </p>
</td>
</tr>
<tr>
 <td>使用 Facebook 進行社交行銷</td>
 <td><p>使用 Facebook 的社交行銷現已棄用。您可以使用 X (原 Twitter) 整合在社交媒體上發佈貼文，或使用 Adobe 建立自訂通道。</p>
  <!--p>Target removal date: End of 2023</p-->
  </td>
</tr>
<tr>
 <td>ACS Connector</td>
 <td><p>ACS Connector (Prime 產品) 現已棄用。 您可以使用 Campaign 匯出/匯入功能，在兩個產品中擷取和插入資料。</p>
  <!--p>Target removal date: End of 2023</p-->
  </td>
</tr>
 </tbody> 
</table>

## 已移除的功能 {#removed-features}

本節列出已從 Campaign Classic 移除的功能。

<table> 
 <tbody>
  <tr> 
   <td><strong>功能</strong></td>
   <td><strong>詳細資料</strong></td>
  <tr>  
      <tr>
  <td>Adobe Analytics 資料連接器<br></td>
   <td><p>Adobe Analytics 資料連接器已於 2022 年 8 月 17 日移除。 已在 Campaign 21.1.3 版中棄用。</p>
   <p>如果您使用此連接器，則需要據此調整實施。<a href="../../integrations/using/gs-aa.md">瞭解更多</a></p>
  </td>
 </tr>
    <tr>
  <td>技術傳遞能力監視報告<br></td>
   <td><p>不再提供「技術傳遞能力監視報告」。 已在 Campaign 21.1.3 版中棄用。</p>
   <!--p>If needed, you can receive this report daily by email until the feature removal date. To request it, open a specific <a href="https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html">Support Case</a> and specify the name of the instance and the email address(es) to send the report to.</p--> 
  </td>
 </tr>
  <tr>
  <td>OAuth 驗證（OAuth 和 JWT）<br></td>
  <td><p> 原本根據 OAuth 驗證設定以存取管道的的觸發程序整合驗證，現已變更並移至 Adobe I/O。此驗證模式已在 Campaign 20.3 版本棄用。<p>
  <p>如果您使用觸發器整合，請在<a href="../../integrations/using/about-triggers.md#implement">此頁面</a>瞭解如何調整實施。</p> 
  <p>如需與 OAuth 驗證折舊相關的資訊，請參閱第 <a href="https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md"> 頁</a></p> 
  <!--p><em>Target removal date: October 20, 2021. Hosted environments benefit from an extension until May 25, 2022. </em></p-->
  </td>
  </tr>
   <td>報告<br></td>
   <td><p>在 Adobe Flash Player 終結壽命後，量規報告和圖表轉譯引擎將不再可用。 <a href="../../reporting/using/creating-a-new-report.md">瞭解更多</a></p>
  </tr>
  <tr>  
   <td>傳真頻道<br></td>
   <td><p>自 Campaign 21.1.3 版開始，不再提供傳真頻道。 <a href="../../delivery/using/steps-about-delivery-creation-steps.md">瞭解更多</a></p>
  </tr>
  <tr>
  <td>Demdex 網域<br></td>
  <td><p> 自 Campaign 第 21.1.3 發行版本開始，已棄用使用於匯入和匯出客群至 Adobe Experience Cloud 的 Demdex 網域。<a href="../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md">瞭解更多</a></p> 
  </td>
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
   <td>自 Campaign 第 19.1 發行版本開始，可以透過專屬頁面使用 Campaign Classic API。如果您使用舊版 jsapi.chm 檔案，現在應參考<a href="https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hant">新的線上版本</a>。</td>
  </tr> 
  <tr> 
   <td>Campaign Orchestration - 預測式行銷</td>
   <td>自 Campaign 18.10 發行版本開始，已無法再使用預測式行銷功能。</td>
  </tr> 
  <tr> 
   <td>網頁應用程式 - Microsites</td>
   <td>自 Campaign 18.10 發行版本開始，已不再提供 Microsites。若要提高安全性，您可以在 Adobe Campaign 設定檔案限制僅能存取專屬網域，並使用 DNS 別名在 Campaign 中使用個人化 URL。</td>
  </tr> 
  <tr> 
   <td>推播通知 - iOS Binary Connector</td>
   <td>根據 Apple 的建議，Adobe 自 Campaign 18.10 發行版本起，移除舊版的 iOS Binary Connector。目前則提供功能更強大、效率更高的 HTTP/2 連接器。</td>
  </tr> 
  <tr> 
   <td>decryptString API</td>
   <td><p>出於安全原因，自 Campaign 18.6 發行版本起，新的安裝已不再預設提供 <em>decryptString</em> API。</p> 
   <p>在 18.6 版本升級後（及更新版本）的設定檔，不再啟用此 API，並已由 <em>decryptPassword</em> 函式取代。<a href="https://experienceleague.adobe.com/developer/campaign-api/api/f-decryptPassword.html?hl=decrypt">瞭解更多</a></p></td>
  </tr> 
   <tr> 
   <td>行動裝置頻道 - MMS 和 WAP 推播訊息</td>
   <td>自 Campaign 第 18.4 發行版本開始，不再提供 MMS 和 Wap 推播頻道。作為取代，您可以利用<a href="../../delivery/using/sms-channel.md">簡訊</a>和<a href="../../delivery/using/about-mobile-app-channel.md">推播</a>傳遞。</td>
  </tr> 
   <tr> 
   <td>行動裝置頻道 - LINE v1</td>
   <td>自 Campaign 第 18.4 發行版本開始，不再提供 LINE Connect 套件。Adobe 建議使用新的 LINE Channel 套件取而代之。<a href="../../delivery/using/line-channel.md">瞭解更多</a></td>
  </tr>
 </tbody> 
</table>

<!--## Deprecated compatibility {#deprecated-compatibility}

The following systems are deprecated for Campaign Classic. Please refer to the [Compatibility matrix](../../rn/using/compatibility-matrix.md) to upgrade to a newer version or move to a new system before the compatibility ends.-->

## 相容性終止 {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic 與[「相容性矩陣」](../../rn/using/compatibility-matrix.md)所列的所有系統和工具相容。這些協力廠商系統和工具的特定版本生命週期結束 (EOL) 時，Adobe Campaign 不再與這些版本相容：我們將不再使用這些系統和功能，後續的產品發行版本亦會將這些系統和功能從我們的相容性矩陣移除。請確保您使用相容性矩陣列出的任何系統的支援版本，以避免出現任何問題。

### 用戶端主控台 {#client-console-eol}

Adobe Campaign Classic 用戶端主控台無法在下列系統執行，因為編輯者已不使用這些系統。客戶若其中一個版本執行 Campaign 用戶端主控台，必須在目標移除日期前升級至最新版本。請參閱「[相容性矩陣](../../rn/using/compatibility-matrix.md)」。

* Windows Server 2003、2008、2008 R2
* Windows 7、XP、Vista

>[!NOTE]
>自 Campaign 20.1 發行版本開始，Campaign Classic 用戶端主控台 32 位元已不再與 Campaign 最新版本相容。您需要使用 64 位元版本的用戶端主控台。

### 作業系統 {#o-s-eol}

* 從7.3.1版開始，Adobe Campaign不再與Windows 8和Windows Server 2012相容。

* 從 22.1 版本開始，Adobe Campaign 不再相容於 CentOs 8.x (64 位元)。 CentOS Linux 8 於 2021 年 12 月 31 日終止使用 (EOL)。 [了解更多資訊](https://www.centos.org/centos-linux-eol/)。

  如果您使用此作業系統，請對應調整實施內容。 仍支援 CentOS 7.x (64 位元) 和 RHEL 8.x/7.x (64 位元)。

* 從 21.1.3 版本開始，Adobe Campaign 不再相容於 Debian 8。

* 自 19.1 發行版本開始，Adobe Campaign 不再與下列作業系統相容。

   * CentOS 6。[了解更多](https://wiki.centos.org/Download)
   * Debian 7。[瞭解更多](https://wiki.debian.org/DebianReleases)
   * RHEL 6.x。[瞭解更多](https://access.redhat.com/support/policy/updates/errata)
   * Windows Server 2008。[瞭解更多](https://support.microsoft.com/en-us/lifecycle/search/1163)
   * SLES 11。[瞭解更多](https://www.suse.com/lifecycle)

### Web 伺服器 {#web-server-eol}

自 19.1 春季發行版本開始，Adobe Campaign 不再與下列 Web 伺服器相容。

* Apache 2.2. [瞭解更多](https://httpd.apache.org/)
* Microsoft IIS 7。[瞭解更多](https://support.microsoft.com/en-us/lifecycle/search/810)

### 工具 {#tools-eol}

自 19.1 春季發行版本開始，Adobe Campaign 不再與下列工具相容。

* Java JDK 7。[瞭解更多](https://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5 / 4.3 / 5.x，但內嵌於其他工具則除外。[深入瞭解](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### 資料庫引擎 {#dbe-eol}

Adobe 不支援下列資料庫引擎，因為其編輯者已不建議使用這些引擎。客戶若執行這些版本，需要升級至最新版本或改用其他引擎。

請參閱 [Campaign 相容性矩陣](../../rn/using/compatibility-matrix.md)，以取得相容版本清單。

**同盟資料存取 (FDA)**

自第 20.2 發行版本開始，Adobe Campaign 不再與下列 FDA 伺服器相容：

* DB2 UDB 10.5

自第 19.1 春季發行版本開始，Adobe Campaign 不再與下列 FDA 伺服器相容：

* PostgreSQL 9.3.
* MySQL 5.5.
* DB2 9.5.
* Teradata 14 – 14.1.

Campaign Classic 與下列同盟資料存取 (FDA) 的伺服器不相容。請使用更新的版本或系統。

* DB2 UDB 9.5、9.7。
* Oracle 9i、10G R2。
* 9.6 版本的 PostgreSQL 版本已到期。
* MSSQL 2000、2005、2008 R2。
* MySQL 5.1.
* InfiniDB 生命週期結束。
* Teradata 13、13.1.
* Netezza 6.02、7.0. Netezza 生命週期結束。
* AsterData 5.0. AsterData 生命週期結束。
* Sybase IQ15.2、15.4、15.5 及 Sybase ASE 15.0。
* 透過 HiveSQL 的 Hadoop：Hadoop 2.7.3、HiveSQL 1.2.1。Adobe Campaign Classic 仍將透過同盟資料存取 (FDA) 支援所列透過 HiveSQL 的 Hadoop 版本，但是這些版本已與下列各項合併：HortonWorks (HDP 2.4.X、2.5.x、2.6.x) 及 HDInsight 3.4 (HDP 2.4)、3.5 (HDP 2.5)、3.6 (HDP 2.6)

**RDBMS 伺服器**

自第 19.1 春季發行版本開始，Adobe Campaign 不再與下列 RDBMS 伺服器相容：

* Oracle 10GR2
* PostgreSQL 9.0 到 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7

9.6 版本的 PostgreSQL 版本已到期。因此，Adobe Campaign 不支援這些建議。

### 簡訊連接器 {#sms-eol}

舊的簡訊連接器自第 20.2 版開始將不再使用。Adobe Campaign 跟以下內容不相容：

* Generic SMPP（支援二進位模式的 SMPP 第 3.4 版本）
* Sybase365 (SAP簡訊365)
* CLX Communications
* Tele2
* O2
* iOS

### CRM 連接器 {#crm-connectors}

下列 CRM 連接器自 Campaign 發行版本第 21.1 版起已棄用。

* Soap API - 內部部署：2007、2015、2016 年
* Soap API - 線上：2015、2016 年
* Web API - Microsoft Dynamics CRM 2016
* Web API – Microsoft Dynamics CRM 2016 更新第 1 版
* Oracle On Demand API
