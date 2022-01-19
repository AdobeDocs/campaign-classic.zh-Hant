---
product: campaign
title: '[!DNL Gold Standard] 版本'
description: 發行說明和 Campaign Classic 相容性對照表 [!DNL Gold Standard]
feature: Overview
role: User
level: Beginner
exl-id: 9e3a11b1-3070-4d90-91d5-7c559bdd500e
source-git-commit: f20ac97be9390fd7e6fd6a6c4d738c0fde9c72c3
workflow-type: ht
source-wordcount: '1676'
ht-degree: 100%

---

# [!DNL Gold Standard] 版本{#gold-standard}

![](../../assets/v7-only.svg)

您可以在本頁面的發行說明和相容性對照表中找到 [!DNL Gold Standard] 版本。

## [!DNL Gold Standard] 發行說明


### ![](assets/do-not-localize/limited_2.png) [!DNL Gold Standard] 第 12 發行版本{#gs-12}

_2021 年 9 月 7 日_

建置 9032@554dbcd 包含以下修正：

* 修正在啟用追蹤的 Line 傳遞中開啟連結至 Web 應用程式時，導致錯誤 500 的問題。

_2021 年 8 月 27 日_

建置 9032@99a3894 包含以下修正：

* 追蹤簽章功能已經過改良，以防止連結至協力廠商工具 (電子郵件用戶端、網際網路瀏覽器等) 的錯誤 處理特殊字元。 URL 參數現在已編碼。
* 修正日期選擇器可能導致主控台顯示封鎖程式錯誤訊息的問題。 (NEO-36345)

### ![](assets/do-not-localize/limited_2.png) [!DNL Gold Standard] 第 11 發行版本{#gs-11}

_2021年 4 月 14 日_

建置 9032@d030c36 包含以下修正：

* 修正 IMS 連線畫面上造成持續錯誤訊息的用戶端主控台迴歸。 (NEO-34821)
* 維護 [IMS 存取](../../technotes/using/ims-updates.md)需要此主控台建置。

**僅主控台升級為強制性。不需要升級伺服器。**

>[!CAUTION]
>
> * 如果您使用 Adobe ID 並透過 Adobe Identity Management Service (IMS) 連線至 Campaign，則必須升級 Campaign 伺服器和用戶端主控台，才能在 2021 年 6 月 30 日&#x200B;**之後連線至 Campaign**。[深入瞭解](../../technotes/using/ims-updates.md)
> * 此版本隨附[安全性修正](https://helpx.adobe.com/tw/security/products/campaign/apsb21-04.html)：升級為強制性以便強化環境安全性。
> * 如果您透過 oAuth 驗證使用 Experience Cloud 觸發程式整合，您必須依照[本頁](../../integrations/using/configuring-adobe-io.md)所述移至 Adobe I/O。**2021 年 9 月**[已淘汰](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)具有 Campaign 的舊版 oAuth 驗證模式。 直到 **2022 年 2 月 23 日**&#x200B;為止，託管環境可利用擴充功能。若為內部部署或混合客戶，請聯絡 Adobe 客戶服務，將支援延長至 2022 年 2 月。 您必須向 Adobe 提供 [OAuth 應用程式的 AppID](../../integrations/using/configuring-pipeline.md?lang=en#step-optional)。
>
>進一步瞭解[[!DNL Gold Standard] 第 11 版升級常見問題](https://helpx.adobe.com/tw/campaign/kb/gold-standard-upgrade.html)

_2021年 3 月 2 日_

建置 9032@10c2709 包含以下修正：

* 修正迴歸，防止在傳遞中使用主控台的某些元件，例如日期選擇器和影像管理。 （NEO-31453、NEO-31454）

**僅主控台升級為強制性。不需要升級伺服器。**

>[!NOTE]
>
> 連線 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 以下載新版本。 瞭解如何在本頁](../../installation/using/client-console-availability-for-windows.md)中向所有終端使用者[建議主控台更新。

_2020 年 12 月 22 日_

版本編號 9032@d3b452f 包含下列增強功能及修正檔：

* 已更新連線通訊協定，以遵循新的 IMS 驗證機制。

* 已變更原本以 oAUTH 驗證設定為基礎而用於存取管道的觸發器整合驗證，並將其移動至 Adobe I/O。[瞭解更多](../../integrations/using/configuring-adobe-io.md)

* [在 iOS APN 舊版二進位通訊協定支援結束之後，在升級後期間，](https://developer.apple.com/news/?id=c88acm2b)使用此通訊協定的所有執行個體都會更新為 HTTP/2 通訊協定。

* 修正了安全性問題，以針對伺服器端請求偽造 (SSRF) 問題而加強保護。(NEO-27777)

* 修正執行&#x200B;**擴充**&#x200B;活動時，工作流程可能失敗的問題。(NEO-17338)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 第 10 發行版本{#gs-10}

_2020 年 7 月 7 日_

建置 9032@efd8a94 包含以下修正：

修正了在停用簽名功能時，無法進行追蹤的問題。(NEO-26411)

>[!CAUTION]
>
>我們建議您使用此版本中可用的用戶端控制台進行升級。請參見[此頁面](../../installation/using/installing-the-client-console.md)。

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 第 9 發行版本{#gs-9}

_2020 年 6 月 22 日_

建置 9032@800be2e 包含以下修正：

* 改善了 iOS HTTP2 連接器（協力廠商更新和錯誤管理）。(NEO-25904、NEO-25903、NEO-25799)

以下為與追蹤連結安全性機制相關之修正（參閱[「安全性與隱私權檢查清單](https://helpx.adobe.com/tw/campaign/kb/acc-security.html#signature-mechanism)」以瞭解更多）：

* 修正了「通知單擊」無法進行追蹤的問題（iOS 和 Android 推播通知）。(NEO-25965)
* 修正了在使用某些特定 Outlook 舊版本時，無法開啟/按一下追蹤 URL 的問題。(NEO-25688)
* 修正了在個人化參數（井字鍵符號的錨點標記）中無法使用片段追蹤 URL 的問題。(NEO-25774)
* 修正了反網路釣魚服務的問題。(NEO-25283)
* 修正了在使用特定自訂追蹤公式時的追蹤問題。(NEO-25277)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 第 8 發行版本{#gs-8}

_2020 年 4 月 29 日_

建置 9032@3a9dc9c 包含以下修正：

* 改善了電子郵件中追蹤連結的安全性。依預設為所有客戶啟用此功能。另外還提供增強的安全性功能，您可以透過連絡客戶服務來啟用此功能。有關非托管客戶啟用此功能的詳細資訊和步驟，請參閱 [「安全性與隱私權」檢查清單](https://helpx.adobe.com/tw/campaign/kb/acc-security.html#signature-mechanism)。

>[!CAUTION]
>
>如果您在使用追蹤連結或使用錨點標籤時，遇到推播通知的問題，我們建議您停用追蹤連結的新簽名機制。[本頁面](https://helpx.adobe.com/tw/campaign/kb/acc-security.html#signature-mechanism)詳細介紹此程序

* 修正了無法在 Line 傳遞顯示影像的問題。(NEO-23207)
* 修正&#x200B;**檔案傳輸**&#x200B;活動使 SFTP 金鑰驗證無法在 Debian 9 運作的問題。(NEO-23183)
* 修正了在高頻率傳送時，可能影響推播通知的問題。(NEO-20516)
* 修正了在優惠方案回應管理中，可能導致 Web 伺服器當機的問題。(NEO-19482)
* 修正了在 LibreOffice 管理中，無法匯出報告的錯誤。(NEO-20982)
* 修正了使用意見調查活動升級許多工作流程時，而導致錯誤的問題。
* 改善了 LibreOffice 管理，以防止在電子郵件預覽時，無法預覽 .odt 檔案。
* 改善了 Apache 連線管理，以防止網站服務的延遲。
* 改善了在&#x200B;**「關於」**&#x200B;功能表中的版本標籤顯示（7 位數）。
* 修正了清單管理中，造成無法發佈優惠方案的迴歸。
* 修正了造成清理工作流程當機的迴歸。
* 修正了清理工作流程記錄檔的次要迴歸。

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 第 6 發行版本{#gs-6}

_2020 年 3 月 9 日_

建置 9032@19f73c5 包含以下修正：

* 修正了使用 FTP over SSL 的外部帳戶的問題。(NEO-20498)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 第 5 發行版本{#gs-5}

_2019 年 12 月 17 日_

建置 9032@d6b8062 包含以下修正：

* 修正以下通訊頻道的追蹤問題：行動（SMS、MMS）、推播（iOS、Android）和社交網路（Facebook、Twitter）。(NEO-19595)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 第 4 發行版本{#gs-4}

_2019 年 12 月 11 日_

建置 9032@bc4a935 包含以下修正：

* 修正了在使用 MSSQL 資料庫傳送訊息時，所導致的效能問題。(NEO-17558)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 第 3 發行版本{#gs-3}

_2019 年 11 月 20 日_

建置 9032@3468c7b 包含以下修正：

* 修正了透過 IMS 驗證的登入問題。(NEO-17312)
* 修正了在多個傳遞顯示累積報告時所產生的問題。(NEO-18165)
* 修正了可能封鎖或造成 Web 伺服器當機的問題。

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 第 2 發行版本{#gs-2}

_2019 年 9 月 19 日_

建置 9032@cee805c 包含以下修正：

* 修正了為 Salesforce 而使用 CRM 連接器所產生的問題。(NEO-17712)
* 修正了正在傳送異動訊息時，可能導致效能問題的索引問題。

### ![](assets/do-not-localize/red_2.png) 發行版本 19.1.4 - 版本編號 9032{#release-19-1-4-build-9032}

_2019 年 8 月 13 日_

初始 19.1.4 版本編號包含以下修正：

* 修正了在配置精靈時，排程器活動產生無用錯誤訊息的問題。正在還原 NEO-11662 更新。(NEO-17097)
* 修正了 NEO-12727 所導致的迴歸，其在執行兩次測試活動時，可能會導致工作流程停止運行。(NEO-16835)
* 修正了在 API 調用中使用無效或過期的續存期間權杖時，導致回傳錯誤 HTTP 代碼的問題（為 HTTP 200 OK，而非 HTTP 403 Forbidden）。(NEO-16826)
* 修正了 DKIM 金鑰不再內嵌在電子郵件中的問題，其導致的傳遞問題。(NEO-16804)
* 修正了各種工作流程排程的問題。排程工作流程以進行每天一次的運行，無需考慮排程器配置。(NEO-16619、NEO-16426)


## [!DNL Gold Standard] 相容性比較表{#compatibility-matrix-gs}

本節列出 **Adobe Campaign Classic[!DNL Gold Standard]** 19.1 版本編號支援的所有系統和元件。不屬於此清單的產品和版本與此版本的 Adobe Campaign 不相容。

>[!CAUTION]
>除非另有提及，否則支援所有次要版本。
>
>Adobe Campaign Classic 與此頁面列出的所有系統和工具相容。這些協力廠商系統和工具的特定版本生命週期結束 (EOL) 時，Adobe Campaign 不再與那些版本相容：我們將不再使用這些系統和功能，後續的產品發行版本亦會將這些系統和功能從我們的相容性矩陣移除。請確保您使用相容性矩陣列出的任何系統的支援版本，以避免出現任何問題。

### 作業系統{#OperatingSystems-gs}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8.x（64 位元）</p>
<p>7.x（64 位元）</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>9（64 位元）</p>
<p>8（64 位元）</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>7.x（64 位元）</p>
<p><strong>重要：</strong>如果您使用 RHEL，您必須願意停用 SELinux，或讓架構設計人員編寫自訂 SELinux 規則，以檢查啟用的 SELinux 是否不會造成 Campaign 作業的問題。</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012 R2</p>
<p>2012</p>
</td>
</tr>
</tbody>
</table>

### 網頁伺服器{#WebServers-gs}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>Windows Server 2016 上的 10.0</p>
<p>Windows Server 2012 R2 上的 8.5</p>
<p>Windows Server 2012 上的 8.0 - Windows 8</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 for RHEL7 - CentOS 7、Debian 8/9、Windows（64 位元）</p>
<p>2.2 for RHEL6 - 僅限於 CentOS 6（64 位元）</p>
</td>
</tr>
</tbody>
</table>

### 工具{#Tools-gs}

<table>
<tbody>
<tr>
<td>Java 開發套件 (JDK)</td>
<td>
<p>8</p>
<p>此應用程式已獲得核准，而可用於 Oracle 及 OpenJDK 開發的 Java 開發套件 (JDK)。</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>6（及舊版，若是內嵌在您的系統中）</p>
</td>
</tr>
<tr>
<td>SpamAssassin</td>
<td>
<p>3.4.x</p>
</td>
</tr>
</tbody>
</table>

### RDBMS 伺服器{#RDBMSservers-gs}

>[!NOTE]
>
>RDBM S驅動程式必須與 RDBMS 伺服器版本相符。

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
<p>注意：您也可以將 Amazon RDS for PostgreSQL 與上述指定版本搭配使用。</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 - SP1 及 SP2</p>
<p>警告：當 Campaign 伺服器在 Linux 上執行時，不支援 Microsoft SQL Server 作為主要資料庫。</p>
</td>
</tr>
<tr>
<td>DB2 UDB</td>
<td>
<p>9.7</p>
<p>警告：不允許針對新安裝使用 DB2 UDB。</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL 是託管環境的預設資料庫伺服器。

### CRM 連接器{#CRMconnectors-gs}

<table>
<tbody>
<tr>
<td>Salesforce 連接器 API</td>
<td>
<p>API 37 版</p>
</td>
</tr>
<tr>
<td>SFDC API</td>
<td>
<p>API 21 版</p>
<p>API 15 版</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics</td>
<td>
<p>Soap API - 內部部署：2007、2015、2016 年</p>
<p>Soap API - 線上：2015、2016 年</p>
<p>Web API - 內部部署與線上：365、2016、2016 更新 1</p>
</td>
</tr>
</tbody>
</table>

### 同盟資料存取 (FDA){#FederatedDataAccessFDA-gs}

<table>
<tbody>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.4.x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 及 SP2</p>
</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>5.7</p>
</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>16.20</p>
<p>16</p>
<p>15.10</p>
<p>15.0</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>第 1 版 SPS 12</p>
</td>
</tr>
<tr><td>透過 HiveSQL 提供的 Hadoop</td>
<td>
<p>HortonWorks HDP 2.4.X、2.5.x、2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4)、3.5 (HDP 2.5)、3.6 (HDP 2.6)</p>
</td>
</tr>
</tbody>
</table>


### 用戶端主控台 {#ClientConsoleoperatingsystems}

:warning: 使用「Campaign 用戶端主控台」時，需要下列作業系統和瀏覽器。

### 作業系統

<table>
<tbody>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Microsoft Windows</td>
<td>
<p>8</p>
<p>10（建議用於日文執行個體）</p>
</td>
</tr>
</tbody>
</table>

#### 瀏覽器

<table>
<tbody>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>

### 行動 SDK{#MobileSDK}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x、8.x、9.0</p>
<p>搭配行動 SDK 建置版本 1.0.27。</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9 - 14</p>
<p>與行動 SDK 建置版本 1.0.26 相容，與 32 及 64 位元版本相容。</p>
</td>
</tr>
</tbody>
</table>

### 瀏覽器{#Browsers}

下列瀏覽器與 Campaign for Web Access 相容。

<table>
<tbody>
<tr>
<td>
<p>Microsoft Edge</p>
</td>
<td>
<p>最新版本</p>
</td>
</tr>
<tr>
<td>
<p>Mozilla Firefox</p>
</td>
<td>
<p>最新版本</p>
</td>
</tr>
<tr>
<td>
<p>Google Chrome</p>
</td>
<td>
<p>最新版本</p>
</td>
</tr>
<tr>
<td>
<p>Safari</p>
</td>
<td>
<p>最新版本</p>
</td>
</tr>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>
