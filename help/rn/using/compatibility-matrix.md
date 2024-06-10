---
product: campaign
title: Campaign Classic 相容性矩陣
description: Campaign Classic 相容性矩陣
feature: Release Notes
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: 28302b40d4fa43b400a3e1b6dd3e133976a01418
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 86%

---

# 相容性比較表{#compatibility-matrix}



本文件列出 [最新版本編號](../../rn/using/latest-release.md)之 **Adobe Campaign Classic v7** 支援的所有系統及元件。此清單上未列出的產品和版本即與 Adobe Campaign 不相容。

如果您是 [!DNL Gold Standard] 使用者，請參閱 [[!DNL Gold Standard]  相容性矩陣](../../rn/using/gold-standard.md#compatibility-matrix-gs)。

## 重要備註{#important-notes}

除非另有提及，否則支援所有次要版本。

在其[最新建置版本](../../rn/using/latest-release.md)中，Adobe Campaign Classic 與此頁面列出的所有系統和工具相容。這些協力廠商系統和工具的特定版本生命週期結束 (EOL) 時，Adobe Campaign 不再與那些版本相容：我們將不再使用這些系統和功能，後續的產品發行版本亦會將這些系統和功能從我們的相容性矩陣移除。請確保您使用相容性矩陣列出的任何系統的支援版本，以避免出現任何問題。

若要進一步瞭解已棄用的項目，請瀏覽[本頁面](../../rn/using/deprecated-features.md)。

>[!CAUTION]
>
>此矩陣會定期更新、新增支援的項目，並會移除已啟用的項目。

## 作業系統 {#OperatingSystems}

身為內部部署/混合部署客戶，您必須在下列其中一種作業系統中安裝Adobe Campaign。 若要深入瞭解Campaign Classic v7的安裝步驟，請參閱 [此頁面](../../installation/using/application-server.md).


<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>7.x</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>11 (自 Campaign v7.3 起)、</p>
<p>10</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>8.x</p>
<p>7.x</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2019 (自 Campaign v7.2 起)</p>
<p>2016</p>
</td>
</tr>
</tbody>
</table>

>[!IMPORTANT]
>
>如果您使用 RHEL，您必須願意停用 SELinux，或讓架構設計人員編寫自訂 SELinux 規則，以檢查啟用的 SELinux 是否不會造成 Campaign 作業的問題。

## 網頁伺服器 {#WebServers}

身為內部部署/混合部署客戶，根據您的作業系統，您必須將Campaign整合至下列其中一個Web伺服器。 進一步瞭解Web伺服器設定步驟，請參閱 [此頁面](../../installation/using/integration-into-a-web-server-for-windows.md) （適用於Windows）和 [此頁面](../../installation/using/integration-into-a-web-server-for-linux.md) （適用於Linux） 。

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>Windows Server 2016 與 2019 上的 10.0</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 for RHEL7 - CentOS 7、Debian 8/9、Windows</p>
</td>
</tr>
</tbody>
</table>

## 工具 {#Tools}

身為內部部署/混合部署客戶，您必須安裝並設定下列工具。 [了解更多](../../installation/using/application-server.md)。

<table>
<tbody>
<tr>
<td>Java 開發套件 (JDK)</td>
<td>
<p>11</p>
<p>9</p>
<p>8</p>
<p>閱讀有關JDK和Campaign的詳細資訊，請參閱 <a href="https://experienceleague.adobe.com/en/docs/campaign-classic/using/installing-campaign-classic/install-campaign-on-prem/deployment-guidelines/application-server#java-development-kit---jdk" target="_blank">此頁面</a>.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>7 (及舊版，若是內嵌在您的系統中)</p>
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

## 關係資料庫管理系統 (RDBMS){#RDBMSservers}

身為內部部署/混合部署客戶，您必須安裝並設定下列其中一個資料庫。 [了解更多](../../installation/using/creating-and-configuring-the-database.md)。


<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x (自 Campaign v7.3.2 起)</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
<p><strong>請注意：</strong>您也可以將 Amazon RDS for PostgreSQL 與上述指定版本搭配使用。</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p><strong>重要：</strong>當 Campaign 伺服器在 Linux 上執行時，不支援 Microsoft SQL Server 作為主要資料庫。<a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/install-campaign-on-prem/installing-campaign-in-linux/prerequisites-of-campaign-installation-in-linux.html?lang=zh-Hant#database-access-layers" target="_blank">了解更多</a>。</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* RDBMS 驅動程式必須與 RDBMS 伺服器版本相符。
>
>* PostgreSQL是用於託管/受管理Cloud Service環境的RDBMS。

## CRM 連接器{#CRMconnectors}

與 Adobe Campaign 相容的客戶關係管理 (CRM) 系統列於下方。 [進一步瞭解](../../platform/using/crm-connectors.md) Campaign CRM 連接器。

<table>
<tbody>
<tr>
<td>Salesforce 連接器 API</td>
<td>
<p>API 49 版本</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics 連接器</td>
<td>
<p>Web API</p>
</td>
</tr>
</tbody>
</table>

## 同盟資料存取 (FDA){#FederatedDataAccessFDA}

與 Adobe Campaign [同盟資料存取模組](../../installation/using/about-fda.md)相容的外部資料庫如下所列。相容性取決於您的[託管模式](../../installation/using/hosting-models.md)。

**受託服務** (託管)、**混合**&#x200B;及&#x200B;**內部部署**&#x200B;環境可使 Campaign 連線下列外部資料庫系統：

<table>
<tbody>
<td><strong>資料庫系統</strong></td>
<td><strong>資料庫版本</strong></td>
<td><strong>Campaign 版本</strong></td>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
<td>v7.0 19.1.4 及以上</td>
</td>
</tr>
<tr>
<td>Google BigQuery</td>
<td> </td>
<td>7.2 及以上</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>v7.0 19.1.4 及以上</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
<td>7.2 及以上</td>
</tr>
<tr>
<td>Vertica Analytics</td>
<td> </td>
<td>v7.0 19.1.4 及以上</td>
</tr>
</tbody>
</table>

此外，**混合**&#x200B;及&#x200B;**內部部署**&#x200B;環境可使 Campaign 連線下列外部資料庫系統。這些系統跟 Campaign **Managed Services** (託管) 環境&#x200B;**不相容**。

<table>
<tbody>
<td><strong>資料庫系統</strong></td>
<td><strong>資料庫版本</strong></td>
<td><strong>Campaign 版本</strong></td>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
<td>v7.0 19.1.4 及以上</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>8</p>
<p>5.7</p>
</td>
<td>
<p>v7.3 及以上</p>
<p>v7.0 及以上</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
<td>v7.0 及以上</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
<td>
<p>v7.0 及以上</p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>第 1 版 SPS 12</p>
</td>
<td>v7.0 及以上</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 及 SP2</p>
</td>
<td>v7.0 及以上</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
<td>v7.0 及以上</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>17.x</p>
<p>16.x (最新版本)</p>
</td>
<td>v7.0 及以上</td>
</tr>
<tr><td>透過 HiveSQL 提供的 Hadoop</td>
<td>
<p>HortonWorks HDP 2.4.X、2.5.x、2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4)、3.5 (HDP 2.5)、3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td>v7.0 及以上</td>
</tr>
</tbody>
</table>



## 用戶端主控台 {#ClientConsoleoperatingsystems}

使用 [Campaign 用戶端主控台](../../installation/using/installing-the-client-console.md)時，需要&#x200B;**使用**&#x200B;下列作業系統和瀏覽器。

### 作業系統

<table>
<tbody>
<td><strong>系統</strong></td>
<td><strong>作業系統版本</strong></td>
<td><strong>Campaign 版本</strong></td>
<tr>
<td>Microsoft Windows</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>v7.3 及以上</p>
<p></p>
<p></p>
</tr>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.2.1 及以上</p>
<p></p>
<p></p>
</tbody>
</table>

### Microsoft WebView 2 執行階段

Campaign 用戶端主控台必須使用 Microsoft Edge WebView2 執行階段最新版本。

從 [Microsoft 開發人員網站](https://www.adobe.com/go/acc-ms-webview2-runtime-download)下載 Microsoft Edge WebView2。


## 行動 SDK{#MobileSDK}

您可以在下列作業系統上使用 Campaign [來傳送推播通知](../../delivery/using/about-mobile-app-channel.md)，使用相關聯的[行動 SDK](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)。

您也可以在資料收集 UI 設定 Adobe Experience Platform 延伸功能，以便使用 Adobe Campaign Mobile SDK。

<table>
<tbody>
<tr>
<td>Google Android</td>
<td>
<p>12 (自 Campaign v7.3 起)、9.0、8.x、7.x</p>
<p>搭配行動 SDK 版本編號 1.1.1。</p>
</td>
</tr>
<tr>
<td>Apple iOS</td>
<td>
<p>iOS 9 - 15</p>
<p>與行動 SDK 建置版本 1.0.26 相容，與 32 及 64 位元版本相容。自 Campaing v7.3 開始支援 iOS 15。</p>
</td>
</tr>
</tbody>
</table>

## 瀏覽器{#Browsers}

下列瀏覽器的最新版本與 Campaign for [Web Access](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-) 相容。

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari



## 更多相關資訊 {#Morelikethis}

* [Campaign Classic 發行說明](../../rn/using/latest-release.md)
* [Campaign 一般架構](../../installation/using/general-architecture.md)
* [硬體尺寸建議](../../technotes/using/hardware-sizing.md)
* [已棄用的功能及系統](../../rn/using/deprecated-features.md)
* [組建升級程序](../../production/using/build-upgrade.md)
